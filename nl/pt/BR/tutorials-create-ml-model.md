---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window}.
{: tip}

# Criando um modelo de aprendizado de máquina
{: #wks_tutml_intro}

Este tutorial ajuda a entender o processo para construir um modelo de aprendizado de máquina que pode ser implementado e usado com outros serviços do {{site.data.keyword.watson}}.
{: shortdesc}

## Aprendendo objetivos

Depois de concluir as lições neste tutorial, você saberá como executar as tarefas a seguir:

- Criar conjuntos de documentos
- Pré-anotar documentos
- Criar tarefas para anotadores humanos
- Analisar a concordância entre anotadores e adjudicar conflitos em documentos anotados
- Criar anotadores de aprendizado de máquina

A conclusão do tutorial deve levar aproximadamente 60 minutos. Se você explorar outros conceitos relacionados a este tutorial, ele poderá levar mais tempo para ser concluído.

## Antes de Começar

- Você está usando um navegador suportado. Para obter informações, veja [Requisitos do navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- Você concluiu com êxito o [Tutorial: Criando uma área de trabalho](/docs/services/watson-knowledge-studio/tutorials-create-project.html).
- Deve-se ter pelo menos um ID do usuário na função de Administrador ou de ProjectManager.

    > **Nota:** se possível, use múltiplos IDs de usuário para as tarefas do modelo de aprendizado de máquina neste tutorial (um ID de usuário de Administrador ou ProjectManager e pelo menos dois IDs de usuário do HumanAnnotator). O uso de múltiplos IDs do usuário fornece a simulação mais realista de uma área de trabalho real do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}™ {{site.data.keyword.knowledgestudioshort}}, na qual um gerente de projeto deve coordenar e adjudicar a anotação executada por múltiplos anotadores humanos. No entanto, se você tem acesso a somente um único ID do usuário, ainda é possível simular a maioria das partes do processo.

    Para obter informações sobre funções de usuário, veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html).

## Resultados

Depois de concluir este tutorial, você terá um modelo de aprendizado de máquina customizado que pode ser usado com outros serviços do {{site.data.keyword.watson}}.

## Lição 1: incluindo documentos para anotação
{: #tut_lessml1}

Nesta lição, você aprenderá como incluir documentos em uma área de trabalho no {{site.data.keyword.knowledgestudioshort}} que podem ser anotados por anotadores humanos.

### Sobre essa Tarefa

Para obter mais informações sobre como incluir documentos, veja [Incluindo documentos em uma área de trabalho](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

### Procedimento

1. Faça download do arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv`<img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> para o seu computador. Esse arquivo contém documentos de exemplo adequados para upload.
1. Dentro de sua área de trabalho, clique em **Documentos** na barra lateral.
1. Na página Documentos, clique em **Fazer upload de conjuntos de documentos**.
1. Selecione o arquivo `documentos-new.csv` de seu computador e clique em **Fazer upload**. O arquivo transferido por upload é exibido na tabela.

### O que fazer em seguida

Agora é possível dividir o corpus em múltiplos conjuntos de documentos e designar os conjuntos de documentos a anotadores humanos.

## Lição 2: criando conjuntos de anotações
{: #wks_tutless_ml2}

Nesta lição, você aprenderá como criar conjuntos de anotações no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Um conjunto de anotações é um subconjunto de documentos de um conjunto de documentos transferido por upload que você designa a um anotador humano. O anotador humano anota os documentos no conjunto de anotações. Para usar posteriormente as pontuações entre anotadores para comparar as anotações que são incluídas pelos anotadores humanos, deve-se designar pelo menos dois anotadores humanos a conjuntos de anotações diferentes. Deve-se também especificar que alguma porcentagem de documentos se sobrepõe entre os conjuntos.

> **Nota:** em uma área de trabalho real, você criaria quantos conjuntos de anotações fossem necessários, com base no número de anotadores humanos que trabalham na área de trabalho. Neste tutorial, você criará dois conjuntos de anotações; se você não tiver acesso a múltiplos IDs de usuário, será possível designar ambos os conjuntos de anotações ao mesmo usuário.

Para obter mais informações sobre conjuntos de anotações, veja [Criando e designando conjuntos de anotações](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).

### Procedimento

1. Dentro de sua área de trabalho, clique em **Documentos** na barra lateral.
1. Clique em **Criar conjuntos de anotações**.

    A janela Criar conjuntos de anotações é aberta. Por padrão, essa janela mostra o conjunto de base (contendo todos os documentos), bem como os campos nos quais é possível especificar as informações para um novo conjunto de anotações.

1. Clique em **Incluir outro conjunto e anotador humano** para incluir campos para um conjunto de anotações adicional. É possível clicar para incluir quantos conjuntos de anotações você deseja criar; para este tutorial, somente dois são necessários.

    ![Uma captura de tela da página Criar conjuntos de anotações.](images/wks_tutdocset2.jpg)

1. No campo **Sobreposição**, especifique `100`. Isso especifica que você deseja que 100 por cento dos documentos no conjunto de base sejam incluídos em todos os novos conjuntos de anotações para que eles possam ser anotados por todos os anotadores humanos.
1. Para cada novo conjunto de anotações que você estiver criando, especifique as informações necessárias.

    - No campo **Anotador**, selecione um ID do usuário de anotador humano para designar ao novo conjunto de anotações. Cada conjunto de anotações deve ser designado a um anotador humano diferente.

        > **Nota:** se você tiver somente um único ID de administrador para usar para o tutorial, designe esse usuário a todos os conjuntos de anotações. Em uma área de trabalho real, você teria múltiplos anotadores humanos para designar, mas para o tutorial, o administrador pode agir como anotador humano.

    - No campo **Nome do conjunto**, especifique um nome descritivo para o conjunto de anotações (como `Set 1` ou `DaveSet`).

1. Clique em **Gerar**.

### Resultados

Os novos conjuntos de anotações são criados e agora aparecem na guia **Conjuntos de anotações** da página Documentos.

## Lição 3: pré-anotando com um anotador baseado em dicionário
{: #wks_tutless_ml3}

Nesta lição, você aprenderá como usar um anotador baseado em dicionário para pré-anotar documentos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

A pré-anotação de documentos é uma etapa opcional. No entanto, é uma etapa importante porque facilita a tarefa de anotadores humanos posteriormente.

Para obter mais informações sobre pré-anotação com anotadores baseados em dicionário, veja [Pré-anotando documentos com o pré-anotador Dicionário](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot).

### Procedimento

1. Em sua área de trabalho, na barra lateral **Ativos e ferramentas** > **Pré-anotadores**, clique em **Gerenciar dicionários**.

  O dicionário `Test dictionary` é aberto.

1. Na lista **Tipo de entidade**, selecione **ORGANIZATION** para mapear o tipo de entidade ORGANIZATION para o dicionário `Test dictionary` que você criou na lição [Incluindo um dicionário](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) do tutorial *Criando uma área de trabalho*.
1. Clique na seta voltar no canto superior esquerdo para retornar à página Pré-anotadores e clique em **Aplicar este pré-anotador**
1. Na página Executar anotador, clique nas caixas de seleção para selecionar ambos os conjuntos de anotações que você criou anteriormente no tutorial (não incluindo o conjunto de base).
1. Clique em **Run**.

    ![Esta captura de tela mostra a página Executar anotador. O botão Executar é destacado.](images/wks_tutanno3.jpg)

### Resultados

Os documentos nos conjuntos selecionados são pré-anotados usando o anotador de dicionário que você criou. Posteriormente, será possível usar o mesmo anotador para pré-anotar conjuntos de documentos adicionais clicando em **Aplicar este pré-anotador**.

## Lição 4: criando uma tarefa de anotação
{: #wks_tutless_ml4}

Nesta lição, você aprenderá como usar tarefas de anotação para controlar o trabalho de anotadores humanos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Para obter mais informações sobre as tarefas de anotação, veja [Criando uma tarefa de anotação](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask).

### Procedimento

1. Em sua área de trabalho, na barra lateral **Ativos e ferramentas** > **Documentos**, selecione a guia **Tarefas**.
1. Na página Tarefas, clique em **Incluir tarefa**.
1. Especifique os detalhes para a tarefa:

    - No campo **Nome da tarefa**, insira `Test`.
    - No campo **Prazo final**, selecione uma data no futuro.

1. Clique em **Criar**.
1. Na janela Incluir conjuntos de anotações na tarefa, clique nas caixas de seleção para selecionar ambos os conjuntos de anotações que você criou na [Lição 3: pré-anotando com um anotador baseado em dicionário](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3). Isso especifica que ambos os conjuntos de anotações devem ser anotados por seus anotadores humanos designados como parte desta tarefa.
1. Clique em **Criar tarefa**.
1. Para ver o progresso de trabalho de anotação humana no futuro, é possível clicar na tarefa para abri-la.

## Lição 5: anotando documentos
{: #wks_tutless_ml5}

Nesta lição, você aprenderá como usar o editor de verdade absoluta para anotar documentos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Para obter mais informações sobre anotação humana, veja [Anotação com o editor de verdade absoluta](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte).

### Procedimento

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como um anotador humano que está designado à tarefa de anotação criada por você na [Lição 4: criando uma tarefa de anotação](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).

    > **Nota:** se você tem acesso a somente um único ID de administrador para este tutorial, é possível usar esse ID para executar a anotação humana. No entanto, lembre-se que em uma área de trabalho real, a anotação humana é executada por múltiplos usuários diferentes com a função HumanAnnotator.

1. Abra a área de trabalho `Minha área de trabalho` .
1. Na barra lateral, clique em **Anotação de documento** > **Relações**.
1. Abra a tarefa de anotação `Test` que você criou na [Lição 4: criando uma tarefa de anotação](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).
1. Role para o documento *Technology - gmanews.tv* e clique para abri-lo para anotação. Observe que o termo `IBM` já foi anotado com o tipo de entidade ORGANIZATION; essa anotação foi incluída pelo pré-anotador de dicionário na [Lição 2: criando conjuntos de anotações](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2). Essa pré-anotação está correta, portanto não precisa ser modificada.

    ![Esta captura de tela mostra um documento aberto com uma pré-anotação existente para a IBM.](images/wks_tut_preannotation.png)

1. Anote uma menção:

    1. Clique no ícone **Menções** para começar a anotar menções.
    1. No corpo do documento, selecione o texto `Thomas Watson`.
    1. Na lista de tipos de entidade, clique em **PERSON**. O tipo de entidade PERSON é aplicado à menção selecionada.

        ![Esta captura de tela mostra o tipo de entidade PERSON aplicado à menção, Thomas Watson.](images/wks_tut_annotatemention3.png)

1. Clique em **Anotação de documento** > **Relações** da barra lateral para começar a anotar as relações.
1. Selecione as menções `Thomas Watson` e `IBM` (nessa ordem). Para selecionar uma menção, clique no rótulo de tipo de entidade acima do texto.
1. Na lista de tipos de relação, clique em **founderOf**. As duas menções são conectadas com um relacionamento founderOf.

    ![Esta captura de tela mostra duas menções conectadas pelo tipo de relação, founderOf.](images/wks_tut_annotaterelation.png)

1. No menu de status, selecione **Concluído** e, em seguida, clique no botão **Salvar**.
1. Retorne para a lista de documentos e clique em **Enviar todos os documentos** para enviar os documentos para aprovação.

    > **Nota:** em uma situação real, você criaria muito mais anotações e concluiria todos os documentos no conjunto antes de enviar.

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como o anotador humano que está designado a outro conjunto de documento na tarefa de anotação.
1. Repita as mesmas anotações no documento *Technology - gmanews.tv*, exceto que desta vez, use a relação employedBy em vez da relação founderOf.

  Efetuar login como outro usuário ajudará a ilustrar a concordância entre anotadores na próxima lição. Conclua as anotações e clique em **Enviar todos os documentos**.

## Lição 6: analisando a concordância entre anotadores
{: #wks_tutless_ml6}

Nesta lição, você aprenderá como comparar o trabalho de múltiplos anotadores humanos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Para determinar se diferentes anotadores humanos estão anotando documentos de sobreposição de forma consistente, revise as pontuações de concordância entre anotadores (`IAA`).

O {{site.data.keyword.knowledgestudioshort}} calcula pontuações IAA examinando todos os documentos de sobreposição em todos os conjuntos de documentos na tarefa, independentemente do status dos conjuntos de documentos. As pontuações do IAA mostram como diferentes anotadores humanos anotaram menções, relações e cadeias de correferência. É uma boa ideia verificar as pontuações do IAA periodicamente e verificar se os anotadores humanos são consistentes entre si.

Neste tutorial, os anotadores humanos enviaram todos os conjuntos de documentos para aprovação. Se as pontuações de concordância entre anotadores são aceitáveis, é possível aprovar os conjuntos de documentos. Se você rejeita um conjunto de documentos, ele é retornado ao anotador humano para melhoria.

### Procedimento

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como o administrador, selecione **Recursos e ferramentas** > **Documentos** e clique na tarefa `Testar`.

  Na coluna **Status**, é possível ver que os conjuntos de documentos são enviados.

1. Clique em **Calcular contrato de interanotador**.
1. Visualize as pontuações do IAA para menção, relações e cadeias de correferência clicando no primeiro menu. Também é possível visualizar a concordância por pares de anotadores humanos. Por exemplo, é possível comparar todas as anotações de Dave com todas as anotações de Phil. Também é possível visualizar a concordância por documentos específicos. Por exemplo, é possível visualizar anotações de Dave em um documento em comparação com as anotações de Phil no mesmo documento. Em geral, atinja uma pontuação de .8 de 1, em que 1 significa uma concordância perfeita. Como você anotou somente dois tipos de entidade neste tutorial, a maioria das pontuações de tipo de entidade são N/A (não aplicável), que significa que nenhuma informação está disponível para fornecer uma pontuação.

    *Figura 1. Revisando as pontuações entre anotadores com usuários denominados Dave e Phil*

    ![Esta captura de tela mostra as pontuações entre anotadores para uma tarefa.](images/wks_tutiaa2.gif)

1. Depois de revisar as pontuações, é possível decidir se você deseja aprovar ou rejeitar conjuntos de documentos que estão no status `Enviado`. Depois que um conjunto de documentos é enviado, uma caixa de seleção é exibida próximo ao seu nome. Tome uma destas ações:

    - Se as pontuações são aceitáveis para um conjunto de documentos, marque a caixa de seleção e clique em **Aceitar**. Documentos que não se sobrepõem com outros conjuntos de documentos são promovidos para verdade absoluta. Documentos que se sobreponham devem primeiro ser revisados por meio de adjudicação para que os conflitos possam ser resolvidos. Para este tutorial, aceite ambos os conjuntos de documentos.
    - Se as pontuações não são aceitáveis para um conjunto de documentos, marque a caixa de seleção e clique em **Rejeitar**. O conjunto de documentos precisa ser revisitado pelo anotador humano para melhorar as anotações.

### Resultados

Ao avaliar as pontuações de concordância entre anotadores, você viu como diferentes pares de anotadores humanos anotaram o mesmo documento. Se a pontuação de concordância entre anotadores foi aceitável, você aceitou o conjunto de documentos.

## Lição 7: adjudicando conflitos em documentos anotados
{: #wks_tutless_ml7}

Nesta lição, você aprenderá como adjudicar os conflitos em documentos que se sobrepõem entre conjuntos de documentos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Quando você aprova um conjunto de documentos, somente os documentos que não se sobrepõem com outros conjuntos de documentos são promovidos para verdade absoluta. Se um documento faz parte da sobreposição entre múltiplos conjuntos de documentos, deve-se adjudicar quaisquer conflitos de anotação antes que o documento possa ser promovido para verdade absoluta.

### Procedimento

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como o administrador, selecione **Recursos e ferramentas** > **Documentos** e clique na tarefa `Testar`.
1. Verifique se os dois conjuntos de documentos estão em um estado aprovado.
1. Clique em **Verificar documentos de sobreposição para conflitos**.

    É possível ver os documentos de sobreposição que foram anotados por mais de um anotador humano.

1. Para ver se existe algum conflito em como eles anotaram os documentos, clique em **Verificar conflitos**.
1. No modo de adjudicação, você pode ver quantas anotações estão em conflito e remover ou substituir anotações antes de promover os documentos para verdade absoluta.
1. Para este tutorial, suponha que você corrigiu todos os conflitos e aceitou as mudanças. Clique em **Promover para verdade absoluta**. Repita essas etapas para resolver conflitos no segundo conjunto de documentos.

    Como alternativa, é possível promover um documento para verdade absoluta clicando em **Aceitar** na página Documentos.

### Resultados

Depois de resolver os conflitos de anotação e promover os documentos para verdade absoluta, é possível usá-los para treinar o modelo de aprendizado de máquina.

## Lição 8: criando um modelo de aprendizado de máquina
{: #wks_tutless_ml8}

Nesta lição, você aprenderá como criar um modelo de aprendizado de máquina no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Ao criar um modelo de aprendizado de máquina, você seleciona os conjuntos de documentos define que deseja usar para treiná-lo. Você também especifica a porcentagem de documentos que devem ser usados como dados de treinamento, dados de teste e dados ocultos. Somente documentos que se tornaram verdade absoluta por meio de aprovação ou adjudicação podem ser usados para treinar o modelo de aprendizado de máquina.

### Procedimento

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como o administrador.
1. Na barra lateral **Gerenciamento de modelo** > **Desempenho**, clique em **Treinar e avaliar**.
1. Selecione os conjuntos de documentos que você deseja usar para criar um modelo de aprendizado de máquina. Clique na marca de seleção próxima a cada nome do conjunto de documentos.
1. Selecione os dois conjuntos de anotações para criar seus dados de teste, treinamento e ocultos. Em seguida, clique em **Treinar e avaliar**.

    > **Nota:** o treinamento pode levar mais de dez minutos, ou mesmo horas, dependendo do número de anotações humanas e o número total de palavras em documentos.

1. Após o modelo de aprendizado de máquina ser treinado, é possível exportá-lo ou visualizar informações detalhadas sobre seu desempenho clicando nos links **Estatísticas detalhadas** que estão localizados acima de cada um dos gráficos.
1. Para visualizar a página Conjuntos de treinamento/teste/cego, clique no botão **Treinar e avaliar**.
1. Para ver os documentos nos quais os anotadores humanos trabalharam, clique em **Visualizar verdade absoluta**.
1. Para ver as anotações que o modelo de aprendizado de máquina treinado criou no mesmo conjunto de documentos, clique em **Visualizar resultados de decodificação**.
1. Para visualizar detalhes sobre a precisão, rechamada e pontuações F1 para o modelo de aprendizado a máquina, selecione a página Desempenho.
1. Clique nos links **Estatísticas detalhadas** acima de cada um dos gráficos. Nessas páginas Estatísticas, é possível visualizar as pontuações para menções, relações e cadeias de correferência usando os botões de opções.

    É possível analisar o desempenho visualizando um resumo de estatísticas para tipos de entidade, tipos de relação e cadeias de correferência. Também é possível analisar estatísticas que são apresentadas em uma matriz de confusão selecionando **Matriz de confusão** no menu que é padronizado para **Resumo**. A *matriz de confusão* ajuda a comparar as anotações que foram incluídas pelo modelo de aprendizado de máquina com as anotações na verdade absoluta.

    > **Nota:** neste tutorial, você anotou documentos com somente um único dicionário para organizações. Portanto, as pontuações que você vê são `0` ou `N/A` para a maioria dos tipos de entidade, exceto `ORGANIZATION`. Os números são baixos, mas isso é esperado, porque você não fez nenhuma anotação humana ou correção.

    *Figura 2. Opções na página Estatísticas para um modelo de aprendizado de máquina*

    ![Esta captura de tela mostra a página Estatísticas.](images/wks_tutanno9.gif)

1. Na barra lateral, selecione **Gerenciamento de modelo** > **Versões**. Na página Versões, é possível tomar uma captura instantânea do modelo e dos recursos que foram usados para criá-lo (exceto para dicionários e tarefas de anotação). Por exemplo, você pode desejar tomar uma captura instantânea antes de treinar novamente o modelo. Se as estatísticas forem mais fracas na próxima vez que você o treinar, será possível promover a versão mais antiga e excluir a versão que retornou resultados mais fracos.

### Resultados

Você criou um modelo de aprendizado de máquina, treinou isso e avaliou o quão bem ele foi executado ao anotar dados de teste e dados ocultos. Ao explorar as métricas de desempenho, é possível identificar maneiras de melhorar a precisão do modelo de aprendizado de máquina.

## Resumo do tutorial
{: #wks_tutml_sum}

Ao aprender sobre o {{site.data.keyword.knowledgestudioshort}}, você criou um modelo de aprendizado de máquina.

### Lições aprendidas

Ao concluir este tutorial, você terá aprendido sobre os conceitos a seguir:

- Conjuntos de documentos
- Modelos de aprendizado de máquina
- Tarefas de anotação humana
- Concordância entre anotadores e adjudicação
