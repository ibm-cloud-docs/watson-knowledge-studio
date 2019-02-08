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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/user-guide.html){: new_window}.
{: tip}

# Anotando documentos
{: #user-guide}

As informações nesta seção ajudam os especialistas no assunto que foram solicitados a anotar documentos da indústria a usarem o editor de verdade absoluta para concluir a tarefa.
{: shortdesc}

## Acesso à área de trabalho
{: #wks_access_for_annotator}

Não é possível ver nenhuma área de trabalho até que alguém crie uma área de trabalho e forneça acesso a ela.

Quando um administrador inclui você em uma instância do {{site.data.keyword.knowledgestudioshort}}, você é incluído na função de anotador humano. Com essa função, não é possível criar uma área de trabalho. Para obter acesso a uma área de trabalho, o administrador deve criar uma área de trabalho. Em seguida, o administrador ou um gerente de projeto que o administrador associa com a área de trabalho deve executar as etapas a seguir:

1. Criar um conjunto de anotações e associar você com ele.
1. Criar uma tarefa que designa você para anotar os documentos no conjunto.

É possível ver a área de trabalho somente depois que uma tarefa de anotação é designada a você.

Se você foi convidado para participar de uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}, mas não vê nenhuma área de trabalho na página Áreas de trabalho, entre em contato com a pessoa que fez o convite e peça para executar as etapas necessárias.

## Melhores práticas de anotação
{: #wks_anno_bp}

Estas melhores práticas de anotação fornecem alguma orientação e exemplos conforme você começa a anotar documentos.

- Anote todos os documentos completamente.

    O aprendizado de máquina aprende de exemplos negativos -- o que não é anotado -- não apenas do que é anotado. Então, seja criterioso no que você anota, mas execute uma tarefa completa. Se você anotar cuidadosamente somente os primeiros 5 de 10 documentos em um conjunto, as anotações que não capturar nos últimos 5 documentos ensinarão o modelo a ignorar quaisquer menções de entidade ou relação que foram perdidas nesses documentos. Você pode acabar revertendo quaisquer ganhos que fez executando uma tarefa minuciosa com os primeiros 5 documentos.

- A anotação consistente é pelo menos tão importante quanto a anotação correta.

    Algumas decisões sobre diretrizes de anotação são arbitrárias, como se as linhas de corte do carro devem ser consideradas parte dos nomes dos modelos, como *Camry* ou *Camry LX*. Qual das políticas será escolhida é muito menos importante do que a equipe do projeto concordar com um ou outro e anotar de acordo com essa política de forma consistente.

- Rotule menções de entidade somente em limites de token de palavra, porque a procura de detecção de menção funciona no nível de token de palavra de granularidade.
- Rotule menções de entidade que estão limitadas a uma ou duas palavras adjacentes sempre que possível.

    Fazer isso nem sempre é possível ou fácil. Considere estes exemplos:
    - O documento de origem contém uma sentença da qual, para os propósitos do aplicativo que usará o sistema de tipos, desejamos anotar o problema e sua causa.

        ```
        O módulo eletrônico foi queimado porque a voltagem errado foi aplicada.
        ```
        {: screen}

        Alguém pode ser levado a anotar o problema e a causa assim:

        ```
                    [PROBLEM][CAUSE]
        ```
        {: screen}

        ```
        [ O módulo eletrônico foi queimado ][because the wrong voltage was applied].
        ```
        {: screen}

        Entretanto, não é uma boa prática anotar essas frases longas como tipos de entidade. Em vez disso, localize as entidades de importância e identifique como elas são associadas umas com as outras definindo uma menção de relação.

        ```
               [LOCATION][SYMPTOM]                [CAUSE]
        ```
        {: screen}

        ```
        O [módulo eletrônico] foi [queimado] porque a [voltagem errada] foi aplicada.
        ```
        {: screen}

        ```
                      ^---isStatusOf--| |------causedBy-------^
        ```
        {: screen}

    - O documento de origem contém um verbo de divisão que você deseja anotar. Como você anota texto não contíguo como um único tipo de entidade? É possível anotar cada menção de entidade e identificá-las como estando relacionadas umas com as outras usando uma menção de relação.

        ```
                  [EVENT_ANSWER][EVENT_ANSWER]
        ```
        {: screen}

        ```
        Todos os telefones estavam tocando, mas ele sabia que o telefone vermelho [deveria] ser [atendido] primeiro.
        ```
        {: screen}

        ```
                            ^----splitType-----^
        ```
        {: screen}

- Evite menções de sobreposição, que são dois rótulos de tipo de entidade diferentes que são aplicados a uma única frase em um documento. Por exemplo, dada a sentença *She donated her father's journals to the JFK Library.*, você sobreporia menções se anotasse `JFK`=`PERSON` e `JFK Library`=`LOCATION` para a frase única *JFK Library*. O uso do termo é mais sobre a biblioteca que a pessoa nesta sentença, então somente a última anotação deve ser aplicada.

    A decodificação de tais estruturas requer múltiplas chamadas paralelas de um modelo de aprendizado de máquina porque a detecção de menção procura somente um único rótulo ou nenhum rótulo em cada token de palavra.

- Determine como a equipe manipulará as listas e os plurais no texto em execução. Por exemplo, o sistema de tipos KLUE tem os tipos de entidade `PERSON` e `PEOPLE` que distinguem o singular do plural. É possível escolher anotar a lista *Barack, Michelle, Malia e Sasha Obama* de uma das maneiras a seguir:

    - Anote cada item na lista como uma menção de entidade singular (*Barack*, *Michelle*, *Malia* e *Sasha Obama* são cada um deles uma menção `PERSON`)
    - Anote a frase inteira como uma menção de entidade plural (*Barack, Michelle, Malia e Sasha Obama* é uma única menção `PEOPLE`).

    Nenhuma abordagem é necessariamente melhor que a outra. Apenas certifique-se de que sua equipe escolha uma delas e a aplique de forma consistente a qualquer lista que ocorra nos documentos.

- Uma correferência é usada quando menções se referem à mesma entidade do mundo real. As relações são usadas entre entidades distintas. Então, duas menções não devem ser conectadas por ambas, uma correferência e uma relação.

## Anotação com o editor de verdade absoluta
{: #wks_hagte}

Quando um anotador humano anota um documento, o documento é aberto no *editor de verdade absoluta*. O editor de verdade absoluta é uma ferramenta visual que os anotadores humanos usam para aplicar rótulos ao texto.

O objetivo da anotação humana é rotular menções, relações e menções correferenciadas para que o modelo de aprendizado de máquina possa ser treinado para detectar esses padrões em texto invisível. No mínimo, use a ferramenta para anotar menções de entidade. Se o aplicativo que usará o modelo resultante não precisar localizar e extrair correferências e menções de relação, você não precisará anotar correferências e menções de relação.

A Concordância é uma ferramenta opcional que pode ser usada por anotadores humanos para expedir a anotação de menções repetitivas.

Escolha um modo para usar quando anotar manualmente os documentos:

- Modo ** Menção **

    Nesse modo, o anotador humano associa tipos de entidade, conforme definido no sistema de tipos, com palavras ou frases significativas no texto. Por exemplo, todas as menções de nomes de pessoa podem ser associadas a um tipo de entidade denominado PERSON. A anotação de menções é necessária e deve ocorrer antes de você anotar tipos de relação e menções como correferências.

    O anotador humano pode usar opcionalmente a ferramenta de concordância para assegurar que o mesmo texto seja anotado com o mesmo tipo de entidade em um documento e em conjuntos de anotações.

- Modo ** Relação **

    Nesse modo, o anotador humano conecta menções associando um tipo de relação, conforme definido no sistema de tipos. Por exemplo, a menção `John Smith` pode estar conectada à menção `{{site.data.keyword.IBM_notm}}` pelo tipo de relação `employedBy`. A anotação de tipos de relação é opcional e pode ocorrer antes ou depois de você anotar menções como correferências.

- Modo ** Coreferência **

    Nesse modo, o anotador humano identifica menções que significam a mesma coisa, portanto, ajudando a assegurar a consistência nas anotações quando palavras não são idênticas. Por exemplo, a menção de `{{site.data.keyword.IBM_notm}}` na primeira frase, a menção de `International Business Machines` e a menção de `{{site.data.keyword.IBM_notm}}` em uma sentença posterior se referem à mesma coisa e seriam todas rotuladas pelo mesmo tipo de entidade, como `ORGANIZATION`. A anotação de menções como correferências é opcional e pode ocorrer antes ou depois de você anotar tipos de relação.

### Dicas para usar o editor
{: #wks_hagte_tips}

- Salve seu trabalho conforme você avança.
- Se você cometer um erro, será possível pressionar Ctrl+Z para desfazer a ação anterior. Para refazer a ação depois de desfazê-la, pressione Ctrl+Y. É possível desfazer as 10 ações anteriores que foram executadas ao editar o documento atual. As ações são perdidas assim que você fecha o documento. As ações devem ser desfeitas em ordem inversa e deve-se alternar para o modo em que estava quando executou a ação para desfazê-la. Não é possível desfazer e refazer ações da ferramenta de concordância.

## Anotando menções de entidade
{: #wks_haentity}

Para anotar menções de entidade, um anotador humano seleciona uma sequência de texto em um documento e, em seguida, aplica um rótulo que descreva mais adequadamente o que a sequência de texto representa. Os rótulos que podem ser aplicados são tipos de entidade definidos no sistema de tipos da área de trabalho.

### Sobre essa Tarefa
{: #wks_haentity_about}

Antes de começar a anotar menções de entidade em um documento, é uma boa prática ler o documento inteiro. Fazer isso pode ajudar a manter o contexto inteiro em mente enquanto anota e pode ajudar a fornecer insights sobre como as menções de entidade podem se relacionar umas com as outras e quais menções podem precisar ser correferenciadas em passagens futuras pelo documento.

Ao abrir um documento para anotá-lo, você pode desejar usar a ferramenta de concordância para anotar as menções de entidade de repetição primeiro e, então, anotar menções de entidade individuais. É possível então anotar as menções de relação e as correferências em qualquer ordem que você desejar ou não anotar de forma alguma. A anotação de menção de entidade é obrigatória. Se você também anota menções de relação e correferências depende do propósito de seu modelo e das necessidades de seu domínio. No entanto, até e a menos que você identifique correferências, cada menção de entidade é considerada para representar uma entidade distinta.

#### Dicas
{: #wks_haentity_tips}

- Tenha em mente que menções de entidade mais curtas são melhores para treinar porque é mais fácil para o modelo de aprendizado de máquina reconhecer os padrões mais curtos e incluir os tokens de anotação corretos.
- Se você escolheu usar um tokenizer baseado em dicionário com a área de trabalho e deseja manipular termos compostos e pontuação em seus dados de treinamento, é possível incluir os termos em um dicionário e criar um anotador de dicionário para pré-anotar as ocorrências. Por exemplo, para evitar que o limite de sentença quebre termos que incluem pontuação, inclua termos como Yahoo! e Dr. em um dicionário. Da mesma forma, se seus dados de treinamento incluem palavras hifenizadas ou acrônimos alfanuméricos, como `Hi-C` ou `MS-60-70`, inclua esses termos no dicionário. Para anotar ocorrências independentemente de maiúsculas e minúsculas, inclua os termos em minúsculas (como `hi-c`). Para anotar variações, inclua as variações como formas superficiais (`MS-60-70` e `MS 60 70`).

   **Importante**: não use essa abordagem se você estiver usando o tokenizer padrão.

### Procedimento
{: #wks_haentity_procedure}

Para anotar menções de entidade em um documento:

1. Efetue login como um anotador humano (ou como um administrador que foi designado para anotar documentos). As áreas de trabalho que contêm tarefas que são designadas a você são exibidas.
1. Abra uma área de trabalho e, em seguida, clique em **Modelo de aprendizado de máquina** > **Tarefas de anotação**. As tarefas de anotação que estão designadas a você são exibidas.
1. Abra a tarefa de anotação na qual deseja trabalhar. Os conjuntos de anotações que são designados a você são exibidos.
1. Clique em **Anotar** para abrir o conjunto de anotação no qual deseja trabalhar. Os documentos no conjunto de anotação são exibidos.
1. Abra o documento que deseja anotar. Por padrão, o documento é aberto no modo **Menção**, que é o modo que você usa para anotar menções de entidade.
1. Comece a anotar as menções da entidade.

    1. Clique em uma palavra no texto que você reconheça como uma menção de um tipo de entidade específico do sistema de tipos. Para menções de entidade que consistem em mais de uma palavra, clique em outra palavra ou arraste as bordas da caixa de seleção para selecionar múltiplas palavras ou palavras compostas.
    1. Selecione o tipo de entidade que você deseja aplicar na área de janela à direita ou insira o atalho de teclado para o tipo de entidade.

        Se as diretrizes de anotação eram anteriormente conectadas à área de trabalho e se você quiser ajuda com a escolha da anotação correta a ser aplicada, clique em **Visualizar diretrizes**. Dependendo das permissões de acesso configuradas no site em que as diretrizes são hospedadas, você pode ser capaz de atualizar as diretrizes após abri-las, por exemplo, para incluir esclarecimentos e exemplos.
        {: tip}

    1. Evite criar menções de sobreposição. Mas se uma menção de sobreposição válida for necessária, clique em **Substituir** para incluí-la mais facilmente. Uma sobreposição ocorre quando você aplica mais de um rótulo a uma menção de entidade. Revise estas sugestões:

        - Anote *Sub-Saharan* como uma única menção, não apenas *Saharan* ou apenas *Sub*.
        - Não crie uma anotação `PERSON` de sobreposição para a referência *JFK* em *JFK International Airport*. A menção inteira *JFK International Airport* deve ser rotulada somente como `FACILITY`.
        - Para o texto *CEOs*, não crie uma anotação `PERSON` para *CEO* e uma anotação `PEOPLE` para *CEOs*. Anote *CEOs* somente como um tipo de entidade `PEOPLE`.

        Geralmente, a existência de muitas menções de sobreposição significa que as diretrizes de anotação são ambíguas e precisam ser melhorada para fornecer exemplos melhores de como manipular palavras compostas em sua origem de dados.

    1. Para remover uma anotação que você acabou de incluir, pressione Ctrl+Z para desfazer a ação. Para remover uma menção de entidade posteriormente, é possível clicar com o botão esquerdo do mouse em uma menção e pressionar a tecla Excluir ou clicar em **Visualizar detalhes** e, em seguida, clicar no **X** ao lado do tipo de entidade designado à menção.

1. Dependendo do sistema de tipos, você pode ser capaz de configurar atributos para uma menção de entidade, como designar uma função ou um subtipo de entidade ou uma classe ou tipo de menção. Neste caso, selecione uma menção e clique em **Visualização de atributo**.

1. Clique em **Salvar** a qualquer momento para salvar o seu trabalho.

### O que fazer em seguida
{: #wks_haentity_next}

Após você concluir a anotação de todas as menções de entidade, menções de relação e correferências no documento, conforme aplicável, mude o status do documento de **Em andamento** para **Concluído**, clique em **Salvar** e, em seguida, feche o documento.

Após você concluir a anotação de todos os documentos e marcá-los como **Concluídos**, o status do conjunto de anotações mudará para **Enviado**. É assim que os gerentes de projeto sabem que podem começar a avaliar os documentos para o contrato entre anotadores, rejeitar ou aceitar documentos, e promovê-los para a verdade absoluta.

## Anotando menções de repetição
{: #wks_haconcordance}

É possível usar opcionalmente a ferramenta de concordância para rotular múltiplas ocorrências de uma menção de uma vez. A ferramenta permite que você anote o mesmo texto com o mesmo tipo de entidade em um documento e em conjuntos de anotações. Usar a ferramenta ajuda a assegurar a consistência na anotação em múltiplos documentos. Por exemplo, é possível rotular cada ocorrência da menção *criptografia* individualmente no modo de menção ou rotular todas as ocorrências da menção *criptografia* usando a ferramenta de concordância. De qualquer forma, o modelo aprende por meio do tipo de entidade que você aplica à menção.

### Sobre essa Tarefa
{: #wks_haconcordance_about}

Embora a ferramenta de concordância seja opcional, uma boa prática é usar a ferramenta de concordância para anotar menções dentro de um documento ou entre documentos antes de começar a anotar menções em documentos individuais. Quando você aplica um tipo de entidade a uma menção com a ferramenta de concordância, o sistema aplica o tipo de entidade a todas as menções correspondentes, substituindo quaisquer tipos de entidade existentes que estão designados a uma menção correspondente. Para evitar conflitos, os atributos (como funções ou subtipos) são removidos dos tipos de entidade existentes quando um novo tipo de entidade é aplicado pela ferramenta de concordância.

### Procedimento
{: #wks_haconcordance_procedure}

Para anotar menções de repetição:

1. Efetue login como um anotador humano (ou como um administrador ou gerente de projeto que foi designado para anotar documentos). As áreas de trabalho que contêm tarefas que são designadas a você são exibidas.
1. Abra uma área de trabalho e, em seguida, clique em **Modelo de aprendizado de máquina** > **Tarefas de anotação**. As tarefas de anotação que estão designadas a você são exibidas.
1. Abra a tarefa de anotação na qual deseja trabalhar. Os conjuntos de anotações que são designados a você são exibidos.
1. Clique em **Anotar** para abrir o conjunto de anotação no qual deseja trabalhar. Os documentos no conjunto de anotação são exibidos.
1. Abra o documento que deseja anotar. Por padrão, o documento é aberto no modo **Menção**, que é o modo que você usa para anotar menções de entidade.
1. Se você ainda não tiver incluído nenhuma anotação, inclua pelo menos uma. Selecione uma palavra ou frase de palavra que representa uma menção de um tipo de entidade do seu sistema de tipos e designe o tipo apropriado para ela. Clique em **Salvar** para salvar sua anotação.
1. Selecione uma única ocorrência de texto de repetição que você deseja anotar e, em seguida, clique em **Concordância**.
1. Selecione os documentos aos quais você deseja aplicar o tipo de entidade selecionado. É possível criar as anotações em todos os documentos que você foi designado para anotar, todos os documentos que você começou a anotar ou todos os documentos que ainda não começou a anotar.
1. Clique em **Visualização** para ver as anotações que serão incluídas.

  Se você deseja visualizar as anotações em contexto maior, clique nos ícones para visualizar o conteúdo do documento ou abra o documento em uma nova janela.

1. Clique em **Aplicar e revisar** para aplicar os tipos de entidade selecionados a menções nos documentos selecionados. Você ainda tem uma chance de revisar as anotações que serão incluídas. Se uma anotação é imprecisa em um contexto específico, é possível remover essa ocorrência clicando no ícone Editar e, em seguida, remover a designação de tipo de entidade para a menção.
1. Quando estiver satisfeito com a lista de anotações, clique em **Voltar para o editor de verdade absoluta**.

### Resultados
{: #wks_haconcordance_results}

As menções estão anotadas no documento. Não há nenhuma maneira de remover o conjunto de menções que você incluiu por meio de concordância de uma vez. Deve-se remover cada menção, uma de cada vez.

## Anotando menções como correferências
{: #wks_hacoref}

Para anotar menções como correferências para a mesma entidade, um anotador humano seleciona cada ocorrência de uma menção que se refere à mesma coisa. A correferência ajuda um modelo a reconhecer que as entidades que são referidas de diferentes maneiras devem ser associadas à mesma entidade, como o nome de um estado dos EUA e sua abreviação, o nome de uma empresa e seu acrônimo ou o nome de uma pessoa e um pronome que se refira novamente a essa pessoa.

### Antes de Começar
{: #wks_hacoref_prereqs}

Deve-se anotar menções no documento antes de poder identificar correferências.

### Sobre essa Tarefa
{: #wks_hacoref_about}

Quando você anota as menções como correferências, o sistema cria uma cadeia de correferências. A cadeia fornece uma maneira para você visualizar todas as menções no contexto e verificar se todas as ocorrências pertencem juntas sob a mesma entidade. Por exemplo, "Barack", "Michelle", "ele" e "ela" são todos do mesmo tipo de entidade, `PERSON`, mas "Barack" e "ele" são uma entidade e "Michelle" e "ela" são outra entidade. Neste exemplo, você cria duas cadeias de correferência.

Ao criar uma cadeia de correferência, deve-se selecionar menções que foram marcadas pelo mesmo tipo de entidade. Em alguns casos, no entanto, você pode desejar incluir menções de tipos diferentes na mesma cadeia de correferência. Para fazer isso, deve-se criar múltiplas cadeias e, então, mesclá-las. Por exemplo, pense sobre como as pessoas usam progressivamente as abreviações para evitar repetir coisas no texto. Em um relatório de incidente de tráfego, a primeira referência a um veículo pode ser "2004 Honda Accord Sedan". Posteriormente, o autor pode se referir ao veículo como "Accord" e depois referir-se ao veículo simplesmente como "veículo". Se o sistema de tipos inclui entradas para fabricante do veículo, modelo e tipo, você pode criar múltiplas cadeias de correferência por tipo de entidade e, em seguida, mesclá-las para criar uma cadeia consolidada. A cadeia mesclada ajuda a treinar o modelo de aprendizado de máquina para reconhecer que todas essas menções se referem à mesma coisa.

Outra maneira de combinar menções de diferentes tipos de entidade é criar uma cadeia com menções de um tipo de entidade. É possível então clicar em uma menção de outro tipo de entidade e, em seguida, clicar na cadeia que você criou para incluir a menção nessa cadeia.

Dependendo de suas diretrizes de anotação, você pode desejar criar cadeias de correferência para verbos, assim como substantivos se os verbos mencionarem a mesma instância de uma ação. Por exemplo, se duas menções do verbo "criptografa" referem-se à mesma ocorrência de criptografia, você pode correferenciar as menções. Mas se uma referência a "criptografa" é uma referência geral ou se as duas ocorrências se referem a dois atos diferentes de criptografia, você não as correferencia. Se dois verbos diferentes referem-se à mesma ocorrência de uma ação, você pode desejar correferenciar as menções. Por exemplo, na instrução, "Ele criptografou o documento e depois do processamento ele enviou o arquivo... ", as menções "criptografou" e "processamento" poderiam ser correferenciadas porque elas se referem à mesma instância de uma ação.

O mais importante é a consistência. Decida como você deseja anotar a correferência e especifique as regras, com exemplos, claramente em suas diretrizes de anotação.

### Procedimento
{: #wks_hacoref_procedure}

Para anotar menções como correferências:

1. Efetue login como um anotador humano (ou como um administrador ou gerente de projeto que foi designado para anotar documentos). As áreas de trabalho que contêm tarefas que são designadas a você são exibidas.
1. Abra uma área de trabalho e, em seguida, clique em **Modelo de aprendizado de máquina** > **Tarefas de anotação**. As tarefas de anotação que estão designadas a você são exibidas.
1. Abra a tarefa de anotação na qual deseja trabalhar. Os conjuntos de anotações que são designados a você são exibidos.
1. Clique em **Anotar** para abrir o conjunto de anotação no qual deseja trabalhar. Os documentos no conjunto de anotação são exibidos.
1. Abra o documento que deseja anotar. Por padrão, o documento é aberto no modo **Menção**, que é o modo que você usa para anotar menções de entidade.
1. Clique em  ** Coreferences **.
1. Crie uma cadeia de coreferência:

    1. Mova-se pelo documento e clique em cada menção que significa a mesma coisa e é rotulada pelo mesmo tipo de entidade. Por exemplo, clique em cada ocorrência de `{{site.data.keyword.IBM_notm}}`, `International Business Machines` e `{{site.data.keyword.IBM_notm}} Corp.`, supondo que todas essas menções tenham o tipo de entidade `ORGANIZATION`.
    1. Clique duas vezes na última menção que você deseja incluir na cadeia. Uma cadeia de correferência é criada no painel lateral. O nome da cadeia corresponde à primeira menção que você selecionou.
    1. Para destacar todas as menções em uma cadeia para revisá-las no contexto, passe o mouse sobre o nome da cadeia na área de janela lateral.

1. A **Lista de menções únicas** exibe termos no documento que foram anotados, mas que não foram incluídos em uma cadeia. Se você observar uma menção na lista que pertence a uma cadeia, será possível incluí-la na cadeia daqui.

    1. Na **Lista de menções únicas** no painel lateral, clique na menção.
    1. Na lista suspensa abaixo da descrição da menção, escolha o número que representa a cadeia na qual você deseja incluir a menção.
    1. Clique em **Mesclar** para incluir a menção na cadeia e, em seguida, clique em **OK**.

    A menção é removida da **Lista de menções únicas** e o número da cadeia à qual ela agora pertence é exibido abaixo da menção no documento.

1. É possível desfazer seu trabalho usando os métodos a seguir:

    - Para remover uma cadeia de correferência que você acabou de incluir, pressione Ctrl+Z para desfazer a ação.
    - Para remover uma cadeia de correferência posteriormente, no painel lateral **Cadeias de correferência**, clique no **X** ao lado da cadeia que você deseja remover.
    - Para remover uma única menção da cadeia, clique no ID correferência para abrir uma janela que exibe uma lista das menções na cadeia e, em seguida, clique no **X** próximo à menção que você deseja remover.

1. Clique em **Salvar** a qualquer momento para salvar o seu trabalho.

### O que fazer em seguida
{: #wks_hacoref_next}

Após você concluir a anotação de todas as menções de entidade, menções de relação e correferências no documento, conforme aplicável, mude o status do documento de **Em andamento** para **Concluído**, clique em **Salvar** e, em seguida, feche o documento.

Após você concluir a anotação de todos os documentos e marcá-los como **Concluídos**, o status do conjunto de anotações mudará para **Enviado**. Esse status é como os gerentes de projeto sabem que podem começar a avaliar os documentos para o contrato entre anotadores, rejeitá-los ou aceitá-los e promovê-los para a verdade absoluta.

## Anotando relações
{: #wks_harelation}

Para anotar menções de relação, um anotador humano localiza evidência textual de uma relação entre duas menções de entidade em uma sentença e então aplica um rótulo que descreva mais apropriadamente o tipo de relação. Os rótulos que podem ser aplicados são tipos de relação definidos no sistema de tipos da área de trabalho.

### Antes de Começar

Deve-se anotar as menções de entidade no documento antes de poder definir os tipos de relação entre elas.

### Sobre essa Tarefa

A menção de relação pode ser definida somente se o texto descreve explicitamente o relacionamento entre as duas menções de entidade. A evidência textual explícita pode incluir possessivos, estruturas sujeito-verbo-objeto ou apostos. Por exemplo, na sentença a seguir, não é válido incluir a menção de relação `ownedBy` entre `cão` e `proprietário`.

<pre><code>NÃO VÁLIDO: o <u>cão</u> recebeu uma guloseima de seu <u>proprietário</u>.</code></pre>

A menção de relação válida é entre `seu` e `proprietário`, porque isso faz parte da sentença na qual o texto define explicitamente o relacionamento entre o cão e seu proprietário. `Proprietário` pode ser um proprietário da casa ou o proprietário de um outro cão, mas esse texto deixa claro que o mesmo cachorro que é mencionado no início da sentença é de propriedade dessa pessoa.

<pre><code>VÁLIDO: o cão recebeu uma guloseima de <u>seu</u> <u>proprietário</u>.</code></pre>

<pre><code>                                |ownedBy^</code></pre>

O requisito de que ambas as menções de entidade e o texto que define o tipo de relação entre elas devem existir em uma única sentença pode parecer rigoroso. No entanto, tenha em mente que, como no exemplo acima, contanto que você também identifique correferências no documento, é possível identificar menções de relação em sentenças que contêm palavras que servem mais como menções de entidade informais, como pronomes. Por exemplo, a segunda sentença em `Mary is a scientist. She works for {{site.data.keyword.IBM_notm}}.` contém evidência textual válida de um relacionamento `employedBy` entre Mary e {{site.data.keyword.IBM_notm}}. A correferência, `She`, é entendida como uma referência para o tipo de entidade `PERSON` `Mary`. É a identificação de um correferência entre `Mary` e `Ela` mais a identificação de uma menção de relação entre `Ela` e `{{site.data.keyword.IBM_notm}}` que captura totalmente esse relacionamento. A maneira correta de anotar a menção de relação é assim:

<pre><code>Mary[<i>#1</i>] é uma cientista. <u>Ela</u>[<i>#1</i>] trabalha para a <u>IBM</u>.</code></pre>

<pre><code>                         |----employedBy----^</code></pre>

em que o subscrito [<i>#1</i>] indica que `Mary` e `Ela` são ambos membros da primeira cadeia de correferência no documento.

### Procedimento

Para anotar menções de relação entre menções de entidade em um documento:

1. Efetue login como um anotador humano (ou como um administrador ou gerente de projeto que foi designado para anotar documentos). As áreas de trabalho que contêm tarefas que são designadas a você são exibidas.
1. Abra uma área de trabalho e, em seguida, clique em **Modelo de aprendizado de máquina** > **Tarefas de anotação**. As tarefas de anotação que estão designadas a você são exibidas.
1. Abra a tarefa de anotação na qual deseja trabalhar. Os conjuntos de anotações que são designados a você são exibidos.
1. Clique em **Anotar** para abrir o conjunto de anotação no qual deseja trabalhar. Os documentos no conjunto de anotação são exibidos.
1. Abra o documento que deseja anotar. Por padrão, o documento é aberto no modo **Menção**, que é o modo que você usa para anotar menções de entidade.
1. Clique em **Relações**.
1. Para anotar uma relação:

    1. Clique em uma menção de entidade no texto; em seguida, clique em uma segunda menção de entidade na mesma sentença que você deseja conectar à primeira menção.
    1. Selecione o tipo de relação que você deseja aplicar na área de janela à direita ou insira o atalho de teclado para o tipo de relação. A lista de tipos de relação disponíveis é restrita pela primeira menção de entidade que você seleciona e mais restrita pela segunda menção de entidade. Em alguns casos, somente um tipo de relação permanece; você ainda deve selecionar explicitamente o tipo de relação para aplicá-lo.

        Se as diretrizes de anotação eram anteriormente conectadas à área de trabalho e se você quiser ajuda com a escolha da anotação correta a ser aplicada, clique em **Visualizar diretrizes**. Dependendo das permissões de acesso configuradas no site em que as diretrizes são hospedadas, você pode ser capaz de atualizar as diretrizes após abri-las, por exemplo, para incluir esclarecimentos e exemplos.
        {: tip}

1. Para remover uma relação que você acabou de incluir, pressione Ctrl+Z para desfazer a ação. Para remover uma menção de relação posteriormente, é possível clicar com o botão esquerdo do mouse no tipo de relação e, em seguida, pressionar a tecla **Delete** ou clicar no **X** ao lado do tipo de relação.
1. Dependendo do sistema de tipos, você pode ser capaz de configurar atributos para uma relação, como designar uma relação tempo, modalidade ou classe. Se sim, selecione um rótulo de relação e clique em **Visualização de atributo**.
1. Clique em **Salvar** a qualquer momento para salvar o seu trabalho.

### O que fazer em seguida

Após você concluir a anotação de todas as menções de entidade, menções de relação e correferências no documento, conforme aplicável, mude o status do documento de **Em andamento** para **Concluído**, clique em **Salvar** e, em seguida, feche o documento.

Após você concluir a anotação de todos os documentos e marcá-los como **Concluídos**, o status do conjunto de anotações mudará para **Enviado**. É assim que os gerentes de projeto sabem que podem começar a avaliar os documentos para um contrato interanotador e a rejeitá-los ou aceitá-los e promovê-los para verdade absoluta.

## Informações relacionadas

[Criando dicionários](/docs/services/watson-knowledge-studio/dictionaries.html)

[Resolução de problemas do editor de verdade absoluta](/docs/services/watson-knowledge-studio/user-guide-help.html)

[Estabelecer um sistema de tipos](/docs/services/watson-knowledge-studio/typesystem.html)
