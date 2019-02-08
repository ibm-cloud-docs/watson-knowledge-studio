---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/improve-ml.html){: new_window}.
{: tip}

# Fazendo melhorias no modelo de aprendizado de máquina
{: #improve-ml}

Depois de determinar áreas nas quais o modelo está tendo problemas, tome medidas para melhorar seu desempenho.
{: shortdesc}

## Criando versões do modelo
{: #wks_maversions}

Depois de criar um modelo de aprendizado de máquina, é possível tomar uma captura instantânea para manter uma versão de backup dos recursos atuais no caso de você desejar restaurar os recursos em uma iteração futura.

### Sobre essa Tarefa
{: #wks_maversions_about}

A pontuação F1 fornece uma indicação da qualidade do modelo. Se os resultados de desempenho do modelo forem bons, talvez você queira armazenar uma versão do componente antes de mudar qualquer um dos recursos. Se as mudanças que você faz resultam em qualidade mais fraca, é possível reverter para uma versão armazenada. Ao reverter para uma versão mais antiga, todas as tarefas de anotação são arquivadas porque elas não são mais válidas.

É possível ter um máximo de 10 versões de uma área de trabalho. Se você atingir esse limite, exclua versões mais antigas ou versões de que não precisa mais antes de criar uma nova versão.

Ao criar uma nova versão, os recursos a seguir são capturados:

- Sistema de tipos
- Corpus
- Verdade absoluta
- Modelo de aprendizado de máquina
- Resultados de avaliação do modelo de aprendizado de máquina

Os recursos a seguir são excluídos:

- Tarefas de anotação, porque elas são temporais por design, usadas somente para determinar a verdade absoluta
- Dicionários, porque os dicionários podem ser grandes, e vários tipos de dicionários são gerenciados de diferentes maneiras

### Procedimento
{: #wks_maversions_procedure}

Para criar e restaurar versões do modelo de aprendizado de máquina:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione  ** Modelo de Aprendizado de Máquina **  >  ** Desempenho **. As estatísticas de desempenho sobre a versão atual, rotulada versão 1.0, são exibidas.
1. Para tomar uma captura instantânea da versão atual, clique em **Modelo de aprendizado de máquina** > **Versões** e, em seguida, clique em **Tomar captura instantânea**. Os recursos na versão 1.0 são congelados e uma nova versão, rotulada como 1.1, se torna a versão atual. Para cada nova versão que você cria, o número da versão secundária é incrementado, por exemplo, 1.0 torna-se 1.1 e depois torna-se 1.2.
1. Revise os recursos da área de trabalho, conforme necessário, treine novamente e reavalie o modelo.
1. Se você estiver satisfeito com os resultados de desempenho e desejar armazenar a nova versão antes de fazer mudanças futuras, crie outra versão. Continue revisando os recursos e treinando novamente o modelo conforme necessário, criando uma nova versão para cada iteração que você deseja reter.
1. Se os resultados de desempenho são piores e você deseja reverter para uma versão anterior antes de testar mais adiante:

    1. Abra a página **Ativos** > **Dicionários** e faça download de quaisquer dicionários que você deseja reutilizar no modelo restaurado.
    1. Clique em **Modelo de aprendizado de máquina** > **Versões** e clique em **Promover** para a versão que você deseja restaurar. A versão que você promove se torna a atual e o número da versão muda para 2.0. Quando você promove uma versão, o número da versão principal é incrementado e o número da versão secundária se torna 0, por exemplo, 1.1 torna-se 2.0.
    1. Abra a página **Dicionários** e faça upload dos dicionários que você transferiu por download.
    1. Se o teste da nova versão requer mudanças na verdade absoluta, abra a página **Modelo de aprendizado de máquina** > **Tarefas de anotação** e crie uma nova tarefa de anotação.

## Modificando um sistema de tipos sem perder anotações humanas
{: #wks_projtypesysmod}

Você pode precisar fazer modificações enquanto treina um modelo, com base nas estatísticas de desempenho. Mas, geralmente, você deseja que o sistema de tipos esteja mais perto do final possível antes de iniciar as tarefas de anotação em larga escala. Se você mudar o sistema de tipos depois que os anotadores humanos iniciarem o trabalho, eles deverão revisitar os documentos que eles anotaram. Eles devem avaliar a aplicabilidade das mudanças do sistema de tipos.

### Sobre essa Tarefa
{: #wks_projtypesysmod_about}

Esse processo propaga o sistema de tipos atual, atalhos de teclado do editor de verdade absoluta e configurações de cores para todos os conjuntos de documentos em uma tarefa.

### Procedimento
{: #wks_projtypesysmod_procedure}

Para modificar o sistema de tipos sem perder o trabalho que foi feito por anotadores humanos:

1. Mude o sistema de tipos. Por exemplo, é possível incluir ou remover tipos de entidade ou tipos de relação.
1. Decida se você deseja propagar as mudanças para as tarefas de anotação humana existentes.
1. Na página **Modelo de aprendizado de máquina** > **Tarefas de anotação**, abra cada tarefa que você deseja atualizar e clique em **Aplicar atualizações do sistema de tipos**.

    Se você removeu tipos de entidade ou tipos de relação do sistema de tipos, todas as ocorrências desses tipos são destacadas em cinza nos documentos. Esses tipos inválidos são ignorados pelo modelo de aprendizado de máquina. Eles não evitam que você envie e aprove conjuntos de documentos.

1. Forneça detalhes para os anotadores humanos sobre o que mudou no sistema de tipos.
1. Peça aos anotadores humanos para atualizarem seus documentos para refletir as mudanças no sistema de tipos. Por exemplo, se você incluiu novos tipos de entidade ou tipos de relação, eles devem revisar seus documentos e anotá-los apropriadamente.

    > **Nota:** se a tarefa contém documentos concluídos, os anotadores humanos não podem alterar esses documentos para avaliar as mudanças do sistema de tipos até que estejam de volta em um estado editável. Para tornar editáveis, peça aos anotadores humanos para enviarem os conjuntos de documentos para que seja possível rejeitá-los.

**Conceitos relacionados**:
{: #wks_projtypesysmod_related}

[Sistema de tipos](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)

## Gerenciamento de conjunto de documentos
{: #wks_mamanagedata}

Use os conjuntos de dados certos para testar e treinar o modelo no momento certo.

Os documentos que você inclui no sistema devem ser alocados para os conjuntos de dados no nível do sistema ao criar um modelo de aprendizado de máquina:

- **Conjunto de treinamento**

    Um conjunto de documentos que foram anotados por meio de pré-anotação ou por anotadores humanos que é usado para treinar o modelo. O objetivo do conjunto de treinamento é ensinar o modelo de aprendizado de máquina sobre as anotações corretas, que inclui ensinar o modelo por meio de texto que não foi anotado.

- **Conjunto de testes**

    Um conjunto de documentos anotados que é usado para testar o modelo treinado. Depois de executar um teste no conjunto de testes, execute uma análise de erro detalhada com propósito de diagnóstico dos resultados. Fechar a análise ajuda você a localizar as falhas no modelo atual que podem ser direcionadas.

- **Conjunto cego**

    Um conjunto de documentos anotados que é separado e usado para testar o sistema periodicamente após várias iterações de teste e melhoria terem ocorrido. Para evitar que a precisão seja contaminada (por exemplo, fazendo mudanças com base somente em anotações em documentos conhecidos), os dados ocultos devem ser dados que não foram visualizados anteriormente pelos usuários envolvidos com a criação do modelo. Os resultados relatados devem vir somente de testes que são executados em dados ocultos. Depois de executar um teste no conjunto cego, veja somente as pontuações de nível mais alto, como as pontuações F1 de menção e relação geral. Você não deseja saber muitos detalhes sobre o desempenho ou pode influenciar as melhorias que escolhe fazer para o modelo.

O objetivo do {{site.data.keyword.knowledgestudioshort}} é permitir que grandes equipes trabalhem juntas para construir modelos. Como tal, ele supõe que os modelos estão sendo produzidos por uma equipe que inclui um grupo de anotadores humanos e uma pessoa separada ou grupo de pessoas que constrói e testa o modelo e faz melhorias nele. Devido a essa suposição, o aplicativo é configurado para enviar por push um agrupamento igualmente proporcional de documentos de um único conjunto de documentos para conjuntos de teste, treino e oculto. No entanto, se sua equipe não é segregada, se as pessoas que estão fazendo anotação humana também estão revisando os resultados de teste do modelo em detalhes, por exemplo, você pode precisar mudar a alocação de documentos para esses conjuntos para separar mais explicitamente os documentos que estão sendo usados em cada um.

### Por que eu preciso um conjunto cego?
{: #wks_mamanagedata_why}

Como você usa dados de teste para avaliar a precisão em detalhes, você conhece os documentos e seus recursos depois de um tempo. Por exemplo, você começa a saber quais tipos de entidade, de relação e de texto nos documentos são mais bem entendidos pelo modelo de aprendizado de máquina e quais não são. Essas informações são importantes porque ajudam a focar em fazer as melhorias certas, refinando o sistema de tipos, suplementando os dados de treinamento para preencher diferenças ou incluindo dicionários, por exemplo. Conforme os documentos de teste são usados iterativamente para melhorar o modelo, eles podem começar a influenciar o treinamento de modelo indiretamente. Por isso o conjunto "oculto" de documentos é tão importante.

### Como controlar quais documentos são alocados para um conjunto?
{: #wks_mamanagedata_how}

Ao criar um modelo de aprendizado de máquina, deve-se especificar a razão de documentos do conjunto para alocar para os conjuntos de treinamento, teste ou oculto. O {{site.data.keyword.knowledgestudioshort}} aplica automaticamente uma razão de 70/23/7 para os conjuntos de documentos que você usa para construir um modelo de aprendizado de máquina. É possível mudar esses valores.

- Para incluir um conjunto que foi anotado por humanos no conjunto de treinamento, especifique uma razão de detalhamento 100/0/0.
- Após o treinamento com um conjunto, é possível usá-lo para teste. Para usar um conjunto de documentos somente para teste, especifique uma razão de detalhamento 0/100/0.
- Inclua somente um conjunto de documentos que nunca tenha sido usado para treinamento ou teste no conjunto cego. Para fazer isso, especifique uma razão de detalhamento 0/0/100 para o conjunto de documentos.

Planeje parar de usar um conjunto cego após algumas iterações. Quanto mais você usa um conjunto cego, menos "cego" ele se torna. O mesmo vale para os seus dados de teste. Em vez de descartar os conjuntos, é possível migrá-los para servir um novo propósito. Siga este fluxo de migração:

```
cego --> teste --> treinamento
```
{: screen}

Conforme os conjuntos migram, é possível incluir novos documentos invisíveis como dados ocultos e como dados de teste. Mas certifique-se de reter um método para avaliar a precisão entre versões do modelo. Uma maneira de estabelecer uma linha de base é executar uma versão anterior do modelo nos novos conjuntos de documentos. Os resultados dessa execução fornecem uma base de comparação com execuções de modelos mais novos nos mesmos conjuntos.
