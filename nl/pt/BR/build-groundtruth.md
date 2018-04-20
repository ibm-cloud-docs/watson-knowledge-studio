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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/build-groundtruth.html){: new_window}.
{: tip}

# Construindo a verdade absoluta
{: #build-groundtruth}

O objetivo do projeto de anotação é obter a verdade absoluta, a coleção de dados examinados que são usados para adaptar o {{site.data.keyword.watson}} para um domínio específico. No {{site.data.keyword.knowledgestudioshort}}, os anotadores humanos, que são normalmente especialistas no assunto do domínio de destino, desempenham um papel importante na determinação da verdade absoluta.
{: shortdesc}

Um fluxo de trabalho típico inclui as etapas a seguir:

1. Os anotadores humanos enviam os documentos anotados para revisão.
1. O gerente de projeto (que pode ser um especialista de domínio sênior) revisa a precisão de seu trabalho e compara o nível de consistência com que os anotadores humanos anotaram os documentos que se sobrepõem entre os conjuntos de anotações.
1. Se a pontuação da concordância entre anotadores é muito baixa, o gerente de projeto rejeita o conjunto de anotações e o retorna ao anotador humano para ser melhorado. Quando um conjunto de anotações é rejeitado, todos os documentos no conjunto são colocados de volta no modo editável.
1. Se o gerente de projeto aprova um conjunto de anotações, os documentos que não se sobrepõem entre os conjuntos de anotações são promovidos para verdade absoluta para que as anotações possam ser usadas para treinar o modelo.
1. O gerente de projeto revisa os documentos de sobreposição e resolve os conflitos de anotação. Nessa etapa, referida como adjudicação, a equipe pode revisar as diretrizes de anotação para ajudar a esclarecer os equívocos que fizeram com o texto fosse anotado de forma incorreta ou inconsistente por diferentes anotadores humanos.

    Em alguns casos, um gerente de projeto pode desejar uma porcentagem mais alta de sobreposição para avaliar a concordância entre anotadores que a porcentagem de sobreposição para diferenças de adjudicação. Por exemplo, se a concordância entre anotadores parece OK, então o gerente de projeto pode decidir se está OK promover uma anotação para verdade absoluta.

1. À medida que o gerente de projeto resolve os conflitos de anotação, as anotações aprovadas são promovidas para verdade absoluta.

Tenha em mente que a anotação humana sempre requer chamadas de julgamento. As diretrizes de anotação podem fazer muito para assegurar que o texto seja anotado de forma correta e consistente, mas até mesmo as melhores diretrizes estão abertas para interpretação humana. Para obter a verdade absoluta, você desejará gastar tempo com treinamento e educação de anotadores humanos para que eles possam fazer os melhores julgamentos ao analisar o conteúdo de domínio.

## Concordância entre anotadores
{: #wks_haiaa}

Após os anotadores humanos terem anotado os documentos, deve-se determinar quais documentos promover para verdade absoluta. Comece revisando as pontuações de concordância entre anotadores. Documentos com pontuações baixas são candidatos a serem rejeitados e retornados ao anotador humano para melhoria.

Ao calcular pontuações de concordância entre anotadores, o sistema examina todos os documentos de sobreposição em todos os conjuntos de anotações na tarefa, independentemente do status dos conjuntos. Como não é possível aceitar ou rejeitar os conjuntos de anotações até que eles estejam no status Enviado, você pode não desejar avaliar a concordância entre anotadores até que todos os conjuntos de anotações sejam enviados ou pode desejar limitar sua revisão somente a anotadores humanos que enviaram seus conjuntos de anotações concluídos.

As pontuações de concordância entre anotadores mostram como os diferentes anotadores humanos anotaram menções, relações e cadeias de correferência. É possível visualizar as pontuações, comparando um par de anotadores humanos (por exemplo, comparar todas as anotações de menção de John com todas as anotações de menção de Mary). Também é possível visualizar as pontuações comparando documentos específicos (por exemplo, comparar as anotações de relação que John fez em um documento com as anotações de relação que Mary fez no mesmo documento).

Para ajudá-lo a identificar as áreas que requerem investigação, as pontuações que caem abaixo do valor que você especificou para o limite de concordância entre anotadores são destacadas em vermelho. Em estágios iniciais de seu projeto de anotação, você pode achar que as pontuações de relação são frequentemente piores do que as pontuações de menção porque uma anotação de relação perfeita requer que as menções que definem o relacionamento estejam em concordância primeiro.

A pontuação na coluna **Todos** é uma *pontuação Fleiss Kappa*. Ela representa o nível de consistência com que a mesma anotação foi aplicada por múltiplos anotadores humanos entre todos os documentos de sobreposição na tarefa. O valor, que pode variar até 1 e até ser negativo, pode ajudá-lo a identificar as fraquezas nas diretrizes de anotação ou anotadores humanos específicos. As diretrizes a seguir (*Landis e Koch, 1977*) fornecem um ponto de início para avaliar o desempenho geral:

<table cellpadding="4" cellspacing="0" summary="" id="wks_haiaa__table_p5s_dx1_f5" class="table" rules="rows" frame="void" border="0"><thead class="thead" align="left"><tr class="row"><th class="entry ncol thleft" align="left" valign="top" id="d12741e148">Pontuação</th>
<th class="entry ncol thleft" align="left" valign="top" id="d12741e150">Nível de concordância</th>
</tr>
</thead>
<tbody class="tbody"><tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">&lt; 0</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Fraco</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.01 - .20</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Pequeno</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.21 - .40</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Justo</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.41 - .60</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Moderado</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.61 - .80</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Substancial</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.81 - 1.0</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Perfeito</p></td>
</tr>
</tbody>
</table>

A pontuação nas outras colunas é uma *medida F1*. Ela representa o nível de consistência da anotação entre um par de anotadores humanos. O valor pode variar de 0 a 1, em que a concordância perfeita é indicada pela pontuação 1. O que constitui um nível aceitável de concordância depende de seus dados de domínio e sistema de tipo. Mas, para fornecer um exemplo, aqui estão os limites F1 que os gerentes de projeto esperam que sejam atendidos ou excedidos em projetos baseados no sistema de tipos KLUE:

- Menções com tipos de entidade: 0,85
- Relações: 0,8
- Cadeias de correferência: 0,9

A interpretação dos resultados depende da complexidade de seu sistema de tipos, a quantia e a complexidade do conteúdo anotado, o quanto os anotadores humanos são experientes e outros fatores. Por exemplo, se a tarefa de anotação é focada na identificação de partes do discurso, você pode esperar ver uma pontuação alta por causa do quão bem definidas estão as partes do discurso. Mas uma tarefa que requer análise mais profunda do texto, em que a interpretação humana é necessária, pode mostrar pontuações inferiores até que você tome execute as etapas para esclarecer as causas da ambiguidade.

Geralmente, um sistema de tipos que inclui muitos tipos de entidade e tipos de relação é aberto para mais interpretação, portanto, uma concordância entre anotadores pode ser inferior durante as fases iniciais do desenvolvimento de modelo. Olhando as pontuações, é possível ver quais tipos de entidade, por exemplo, têm pontuações baixas. Essas pontuações baixas são uma indicação de que as diretrizes de anotação precisam ser melhoradas. Olhando as pontuações entre pares de anotadores humanos, é possível identificar se um anotador específico mostra de forma consistente pontuações inferiores que outros. Este anotador pode estar tendo problemas em entender as diretrizes ou usar as ferramentas de anotação e, portanto, é um candidato para treinamento adicional.

## Revisando pontuações de concordância entre anotadores
{: #wks_haaccuracy}

Ao determinar quais documentos devem ser promovidos para verdade absoluta, deve-se revisar as pontuações de concordância entre anotadores. Documentos com pontuações baixas são candidatos a serem rejeitados e retornados ao anotador humano para melhoria.

### Sobre essa Tarefa

Ao examinar a concordância entre anotadores, você examina documentos que foram anotados por mais de um anotador humano. Se um documento não é compartilhado entre múltiplos conjuntos de anotações e anotadores humanos, não há nenhuma concordância entre anotadores para calcular. Quando você incluir conjuntos de anotações em uma tarefa, assegure-se de que os conjuntos que você deseja comparar contenham os mesmos documentos de sobreposição. É possível ver quais documentos estão em um conjunto de anotações abrindo a página **Ativos e ferramentas** > **Documentos**, clicando na guia **Conjuntos de anotações**, em seguida, clicando nos nomes dos conjuntos.

Você pode ter situações nas quais nenhum documento de sobreposição é localizado. Isso pode acontecer, por exemplo, se você cria os conjuntos de anotações em duas rodadas e os inclui na mesma tarefa. Embora os conjuntos de anotações tenham sido criados quase ao mesmo tempo, eles não têm nenhum documento em comum. Para outro exemplo, se você criar conjuntos de anotações com documentos de sobreposição, mas incluir um conjunto de anotações por tarefa em vez de incluir todos os conjuntos de anotações em uma única tarefa, nenhum documento de sobreposição será localizado e a concordância entre anotadores não poderá ser calculada.

### Procedimento

Para avaliar a concordância de anotação entre anotadores humanos:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Ativos e ferramentas** > **Documentos** > **Tarefas** e abra a tarefa que você deseja avaliar.
1. Clique em **Calcular contrato de interanotador**. A visualização padrão mostra as pontuações de concordância do nível de consistência com que os pares de anotadores humanos anotaram as menções. A linha superior mostra a consistência geral entre cada par de anotadores e a tabela abaixo mostra o nível de consistência com que um par de anotadores rotulou menções específicas no texto.
1. Para explorar o nível de consistência com que os pares de anotadores humanos anotaram relações e correferências, selecione **Relação** ou **Correferência** no primeiro menu.
1. Para explorar o nível de consistência com que um par de anotadores humanos anotaram entidades, relações ou correferências em documentos específicos de sobreposição, selecione **Documento** no segundo menu e, em seguida, selecione o par de anotadores que você deseja avaliar.
1. Depois de revisar as pontuações, é possível decidir se você deseja aprovar ou rejeitar conjuntos de anotações que estão no status Enviado. Após um conjunto de anotações ser enviado, uma caixa de seleção é exibida próximo ao seu nome. Tome uma destas ações:

    - Se as pontuações de concordância entre anotadores são aceitáveis para um conjunto de anotações, marque a caixa de seleção e clique em **Aceitar**. Os documentos que não se sobrepõem a outros conjuntos de anotações são promovidos para verdade absoluta. Documentos que se sobreponham devem primeiro ser revisados por meio de adjudicação para que os conflitos possam ser resolvidos.
    - Se as pontuações de concordância entre anotadores não são aceitáveis para um conjunto de anotações, marque a caixa de seleção e clique em **Rejeitar**. O conjunto de anotações precisa ser revisitado pelo anotador humano para melhorar as anotações.

## Adjudicação
{: #wks_haperform}

Se múltiplos anotadores humanos trabalharem no mesmo documento, você provavelmente desejará resolver inconsistências entre as anotações antes de promover as anotações para a verdade absoluta. Esse processo de resolução de conflito é conhecido como adjudicação.

Quando você aprova conjuntos de anotações que são enviados por anotadores humanos, os documentos que não se sobrepõem entre os conjuntos de anotações são promovidos para a verdade absoluta. Antes de promover documentos que se sobrepõem, deve-se verificar se há conflitos nas anotações. Quando você localiza instâncias de desacordo, deve-se decidir como resolver o conflito, selecionando a anotação correta entre aquelas aplicadas pelos anotadores humanos ou selecionando uma anotação diferente para aplicar.

Um documento está disponível para controle quando pelo menos uma das condições a seguir é verdadeira:

- O gerente de projeto aprova dois ou mais conjuntos de anotações em uma tarefa ao mesmo tempo e o mesmo documento existe em pelo menos dois dos conjuntos de anotações (um documento de sobreposição).
- O gerente de projeto aprova outro conjunto de anotações antes de os documentos nos conjuntos de anotações aprovados anteriormente serem adjudicados. Se você adjudica um documento que se sobrepõe entre o conjunto de anotações A e o conjunto anotação B, promove as anotações para verdade absoluta e então aprova outro conjunto de anotações, C, que possui o mesmo documento, as anotações no documento recentemente aprovado são promovidas automaticamente para verdade absoluta porque os conflitos não existem mais. Esteja ciente de que as anotações promovidas no conjunto de anotações C substituem a verdade absoluta estabelecida quando os documentos de sobreposição em conjuntos de anotações A e B foram adjudicados. Se você aprovar o conjunto de anotações C antes de promover as anotações nos conjuntos de anotações A e B, os documentos de sobreposição no conjunto C poderão ser verificados para conflitos e adjudicados.

A quantia de tempo gasto adjudicando poderá diminuir ao longo do tempo se você levar algum tempo para melhorar as diretrizes de anotação. Fornecendo exemplos e esclarecendo áreas que causaram confusão, é possível ajudar os anotadores humanos a aprenderem com seus erros e evitar conflitos futuros.

Aqui estão alguns exemplos de várias maneiras que os anotadores humanos discordam:

- **Menções**

    - O Annotator_1 coloca uma menção em um período de texto; o Annotator_2 não.
    - O índice do Annotator_1 inicia ou termina antes ou depois daquele do Annotator_2 (há uma sobreposição parcial ou subintervalo de texto).
    - O Annotator_1 designa um tipo de entidade que é diferente do tipo de entidade que o Annotator_2 designou.

- **Relações**

    - O Annotator_1 cria uma relação entre duas menções; o Annotator_2 não.
    - O Annotator_1 e o Annotator_2 criam uma relação entre as mesmas menções, mas com um tipo de relação diferente.
    - O Annotator_1 e o Annotator_2 criam uma relação entre as mesmas menções, mas na ordem inversa (raro, porque a relação entre a primeira menção e a segunda menção é restringida pelo sistema de tipos).

- **Cadeias de correferência**

    - A versão do Annotator_1 de uma cadeia de correferência inclui (ou exclui) as menções que a cadeia de correferência do Annotator_2 exclui (ou inclui). O alinhamento de entidades entre Annotator_1 e Annotator_2 torna-se uma questão de pontuação.

## Resolvendo conflitos de anotação
{: #wks_haadjudicate}

A adjudicação é uma etapa que permite revisar conflitos de anotação em documentos de sobreposição antes de promover as anotações para a verdade absoluta. É possível comparar as anotações incluídas por um par de anotadores humanos ou comparar as anotações humanas com a verdade absoluta atual.

### Antes de Começar

Clique [neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.youtube.com/watch?v=EbexfsuXxoQ&amp;feature=youtu.be){: new_window} para assistir a um vídeo de 3 minutos que ilustra como adjudicar documentos.

### Sobre essa Tarefa

Após os anotadores humanos concluírem suas tarefas de anotação, eles devem enviar seus conjuntos de anotações concluídos para revisão. Ao avaliar as pontuações de concordância entre anotadores, é possível ver como pares diferentes de anotadores anotaram o mesmo documento. Se a pontuação de concordância entre anotadores é aceitável, você aprova o conjunto de anotações. Se um documento não se sobrepõe em conjuntos de anotações na tarefa, as anotações no documento aprovado são promovidas para verdade absoluta. Se um documento se sobrepõe em conjuntos de anotações, é necessário adjudicar o documento e resolver quaisquer conflitos de anotação que existem antes de promover as anotações para verdade absoluta.

Por exemplo, ao adjudicar um documento, você pode ver que um anotador anotou a menção `Barack Obama` com o tipo de entidade `PeoplePerson`. Outro anotador anotou a mesma sequência de texto como duas menções, designando o tipo de entidade `Person` a `Barack` e o tipo de entidade `Person` a `Obama`. Para ajudar a assegurar o treinamento adequado do modelo de aprendizado de máquina, é necessário resolver essa consistência.

O {{site.data.keyword.knowledgestudioshort}} suporta a capacidade de adjudicar entre dois conjuntos de anotações de cada vez ou entre um conjunto de anotações e a verdade absoluta atual. Se um documento se sobrepõe em mais de dois conjuntos de anotações, adjudique os dois conjuntos de anotações em que você tem a maior confiança (talvez porque tem maior confiança nos anotadores humanos) para determinar a verdade absoluta para o documento. E, em seguida, adjudique o resto dos conjuntos de anotações com base nos resultados da adjudicação inicial.

### Procedimento

Para visualizar documentos de sobreposição e resolver conflitos:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Ativos e ferramentas** > **Documentos** > **Tarefas** e abra a tarefa que você deseja avaliar.
1. Confirme que pelo menos dois conjuntos de anotações estão no status **Em conflito**.
1. Clique em **Verificar documentos de sobreposição para conflitos**. Os documentos que estão em conflito são listados.
1. Se você deseja ignorar os conflitos em um documento de sobreposição e promover as anotações para verdade absoluta sem adjudicá-las, clique em **Aceitar**.
1. Para iniciar a resolução de conflitos em um documento de sobreposição, clique em **Verificar conflitos**.
1. Se houver três ou mais candidatos para adjudicação, incluindo conjuntos de anotações que foram anotados por meio de anotação humana e a verdade absoluta atual, selecione os dois candidatos que você deseja adjudicar e clique em **Verificar conflitos**. Se existirem somente dois candidatos, a ferramenta de adjudicação será iniciada automaticamente.

    A ferramenta de adjudicação mostra quantos conflitos de menção, relação e cadeia de correferência existem. Deve-se resolver conflitos de menção antes de mover-se para resolver conflitos entre relações e cadeias de correferência.

1. Clique para destacar uma sentença que contém conflitos. Para facilitar a manter o foco em conflitos não resolvidos, você pode desejar limpar a caixa de seleção **Resolvido** e assegurar-se de que a caixa de seleção **Não resolvido** esteja selecionada.
1. Clique em anotações individuais e, em seguida, clique em **Aceitar** ou **Rejeitar**. Para desfazer uma decisão que você acabou de tomar, pressione `Ctrl+Z`.

    Também é possível clicar em mais de uma anotação e, em seguida, clicar para aceitar ou rejeitar todas as anotações selecionadas. Se você decidir que deseja cancelar a seleção de uma anotação selecionada, limpe suas seleções clicando no espaço em branco entre as sentenças ou pressionando a tecla **Esc**.

    Se as diretrizes de anotação foram conectadas anteriormente ao projeto e você deseja obter ajuda com a escolha da anotação correta a ser aplicada, clique em **Visualizar diretrizes**. Dependendo das permissões de acesso configuradas no site em que as diretrizes são hospedadas, você pode ser capaz de atualizar as diretrizes após abri-las, por exemplo, para incluir esclarecimentos e exemplos.
    {: tip}

1. Para aplicar um tipo de entidade diferente a uma menção, rejeite a anotação atual, selecione a menção, como `Barack Obama`, em seguida, selecione o tipo de entidade correta, como `Person`.
1. Continue aceitando, rejeitando e revisando outros conflitos na sentença. Depois de resolver todos os conflitos em uma sentença, clique no link **Selecionar todas as anotações** e, em seguida, clique em **Aceitar**.
1. Clique no ícone de seta para acessar a próxima sentença. Continue até que todos os conflitos de menção no documento sejam resolvidos.

    Para salvar seu trabalho em andamento ou para suspender temporariamente a sessão de adjudicação atual, clique em **Salvar** a qualquer momento. Se você deseja descartar todas as mudanças feitas, clique em **Descartar**. Se você salvou a sessão de adjudicação anterior e está pronto para continuar a adjudicação, clique em **Continuar** para iniciar a adjudicação de conflitos de onde parou pela última vez. Se você descartou a sessão de adjudicação anterior, deve-se iniciar uma nova sessão de adjudicação.
    {: tip}

1. Depois de resolver conflitos de menção, alterne o modo de adjudicação para resolver quaisquer conflitos que ocorrem entre anotações de relação e anotações de cadeia de correferência.

    - Resolver conflitos no modo de relação é semelhante a como você resolve conflitos para menções. Você resolve conflitos em uma base sentença por sentença.
    - As cadeias de correferência podem existir em múltiplas sentenças. Ao mover-se para o modo de correferência, o sistema lista as cadeias de correferência que foram criadas por cada anotador humano em uma área de janela à direita. Selecione as cadeias que você deseja adjudicar e, em seguida, clique em **Rejeitar cadeia** ou **Aceitar cadeia** para rejeitar ou aceitar anotações em uma cadeia ou clique em **Mesclar cadeias** para mesclar as duas cadeias. Se você deseja remover uma menção de uma cadeia de correferência, clique no ícone de exclusão (-) no rótulo acima da menção na área de documento.

1. Após todos os conflitos no documento serem resolvidos, clique em **Promover para verdade absoluta**.
