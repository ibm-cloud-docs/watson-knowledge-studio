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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window}.
{: tip}

# Estabelecer um sistema de tipos
{: #typesystem}

O sistema de tipos controla como o conteúdo pode ser anotado.
{: shortdesc}

## Sistemas de tipos
{: #wks_typesystem}

Um sistema de tipos define coisas que são interessantes em seu conteúdo de domínio que você deseja rotular com uma anotação. O sistema de tipos controla como o conteúdo pode ser anotado, definindo os tipos de entidades que podem ser rotulados e como os relacionamentos entre diferentes entidades podem ser rotulados. O gerenciador de processos de modelagem normalmente trabalha com especialistas no assunto para o seu domínio para definir o sistema de tipos.

No {{site.data.keyword.knowledgestudioshort}}, é possível criar um sistema de tipos do zero ou fazer upload de um sistema de tipos existente. Para iniciar uma área de trabalho, você pode desejar fazer upload de um sistema de tipos que foi criado para um domínio semelhante. É possível então editar o sistema de tipos para incluir ou remover tipos de entidade ou redefinir os tipos de relacionamento.

Um sistema de tipos de amostra baseado no sistema de tipos *KLUE* é fornecido para você usar com os tutoriais do {{site.data.keyword.knowledgestudioshort}}. KLUE representa Knowledge from Language Understanding and Extraction e foi derivado pelo {{site.data.keyword.IBM_notm}} Research com base na análise de coleções de artigos de notícias. É possível fazer download de um sistema de tipos KLUE de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>aqui<img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.

Muitas indústrias, como em domínios como a metalurgia, geologia, market intelligence, ciências biológicas, registros eletrônicos de saúde e dicionários de publicação de oncologia ou ontologias de terminologia de domínio específico. Considere referenciar esse tipo de recurso para obter uma ideia dos tipos de entidades que você pode desejar definir em seu próprio sistema de tipos.

### Menções
{: #wks_typesystem__wks_typesystemS2}

Uma menção é qualquer período de texto que você considera relevante em seus dados de domínio. Por exemplo, em um sistema de tipos sobre veículos automotivos, as ocorrências de termos como `airbag`, `Ford Explorer` e `child restraint system` podem ser menções relevantes.

### Tipos de entidade
{: #wks_typesystem__wks_typesystemS3}

Um tipo de entidade é como você categorizar uma coisa real. Uma menção de entidade é um exemplo de uma coisa desse tipo. Por exemplo, a menção `President Obama` pode ser anotada como um tipo de entidade `PERSON`. A menção `{{site.data.keyword.IBM_notm}}` pode ser anotada como um tipo de entidade `ORGANIZATION`. As entidades são frequentemente substantivos, mas também podem ser verbos, contanto que o verbo seja importante capturar para propósitos do aplicativo que usará o sistema de tipos. Por exemplo, `EVENT_CRASH` pode ser um tipo de entidade válido para um sistema de tipos sobre veículos automotivos, de modo que a palavra `hit` na sentença `The car hit the barrier.` possa ser anotada.

O objetivo de sua área de trabalho de anotação é anotar cada menção em um documento com o tipo de coisa que é. Depois que uma menção é classificada por tipo de entidade, o período rotulado de texto é referido como uma entidade.

Um sistema de tipos que você constrói com o {{site.data.keyword.knowledgestudioshort}} pode incluir os atributos de tipo de entidade a seguir. Os atributos ajudam a qualificar menções no texto, mas eles não são marcados como tipos de entidade por um modelo de aprendizado de máquina. Por exemplo, se o tipo de entidade `ORGANIZATION` tiver um subtipo de entidade chamado `COMMERCIAL`, `COMMERCIAL` não será marcado como um tipo de entidade por conta própria.

- **Função**

    Qualifica a menção pelo contexto no qual a menção ocorre. Por exemplo, a menção `France` na instrução `the students went to France` é marcada com o tipo de entidade `GPE` porque `France` é uma entidade geopolítica. Mas, como `France` neste contexto também é um destino para os estudantes viajantes, o tipo de entidade é qualificado incluindo um atributo, neste caso, a função `LOCATION`. Para outro exemplo, a menção `Lawyers` pode ser marcada com o tipo de entidade `PEOPLE` e também pela função `OCCUPATION`.

- **Subtipo de entidade                 **

    Classifica ainda mais o tipo de entidade. Por exemplo, o tipo de entidade `ORGANIZATION` pode incluir os subtipos `COMMERCIAL`, `GOVERNMENT`, `MILITARY` e `EDUCATION`.

- **Tipo de menção**

    Qualifica a menção por certas partes do discurso:
    - **NAM**: a menção é um nome adequado, como o nome de uma pessoa ou o nome de uma organização.
    - **NOM**: a menção é nominal (um substantivo comum), tal como *company* ou *president*.
    - **PRO**: a menção é um pronome, como *ele*, *nós* ou *isso*.
    - **NONE**: nenhum dos outros três tipos de menção é aplicável.

- **Classe de menção**

    Qualifica a menção indicando se a menção é específica, genérica ou negada:
    - **SPC**: a menção é específica, muitas vezes incluindo a palavra *the* em inglês, como *the book* ou *the hurricane occurred in September*. Nesses exemplos, as menções *book* e *hurricane* seriam anotadas com o atributo **SPC**.
    - **GEN**: a menção é genérica, tal como *a book* ou *hurricanes usually occur in the fall*. Nesses exemplos, as menções *book* e *hurricanes* seriam anotadas com o atributo **GEN**.
    - **NEG**: a menção é negada, como referências a *no book*. Quando você treina um modelo, o algoritmo pode aprender com os exemplos negativos e positivos, então é importante marcar menções de ambos os tipos.

### Tipos de relação
{: #wks_typesystem__wks_typesystemS4}

Um tipo de relação define um relacionamento ordenado e binário entre duas entidades. Para que uma menção de relação exista, o texto deve definir explicitamente as menções de relação e ligação de duas entidades juntas e deve fazer isso em uma única sentença. Por exemplo, a sentença `Mary trabalha para a {{site.data.keyword.IBM_notm}}` é evidência textual do tipo de relação `employedBy`.

Para alguns tipos de relação, a ordem de entidade menciona questões. Por exemplo, o tipo de relação `employedBy` permite que o tipo de entidade `PERSON` ou `PEOPLE` como a primeira menção no relacionamento e `ORGANIZATION` ou **GPE** como a segunda menção, mas não o contrário. `Mary` `employedBy` `{{site.data.keyword.IBM_notm}}` é um relacionamento válido. `{{site.data.keyword.IBM_notm}}` `employedBy` `Mary` não é. Para alguns tipos de relação, como `spouseOf`, `colleague` ou `sibling`, a ordem não importa. Quando você define um tipo de relação em que a ordem não é importante, a melhor prática é incluir informações nas diretrizes de anotação para regularizar como o tipo de relação é usado. Uma convenção para observar tais relações simétricas é dizer que a menção de entidade que ocorre primeiro no texto deve ser a primeira na relação.

**Conceitos relacionados**:

[Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html)

## Incluindo um sistema de tipos na área de trabalho
{: #wks_projtypesys}

Deve-se criar ou fazer upload de um sistema de tipos antes de começar qualquer tarefa de anotação.

### Sobre essa Tarefa

As regras de nomenclatura a seguir se aplicam às entradas de sistema de tipos:

- Os nomes não podem conter espaços.
- Use somente os caracteres ASCII alfanuméricos a seguir e o caractere de sublinhado em valores que você inclui no sistema de tipos: `A` a `Z`, `a` a `z`, `0` a `9`.
- O primeiro caractere em um nome do tipo de entidade ou relação deve ser alfabético.
- Os nomes do tipo de entidade não podem ter mais que 64 caracteres.
- Os nomes do tipo de relação não podem ter mais que 128 caracteres.

Por convenção, os nomes de tipo de entidade são especificados em caracteres maiúsculos (`ORGANIZATION`) e os nomes de tipo de relação são especificados em camel case (`employedBy`). Mas essa convenção é opcional.

### Procedimento

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e abra a página **Ativos** > **Tipos de entidades**.
1. Escolha um dos métodos a seguir para criar um sistema de tipos:

    - Faça upload de um sistema de tipos existente:

        1. Na guia **Tipos de entidade**, clique em **Fazer upload**.

            Se você fez download anteriormente de um sistema de tipos de uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}, o sistema de tipos é transferido por download no formato `JSON`. É possível fazer upload desse sistema de tipos para iniciar a criação de uma área de trabalho. Para obter detalhes, veja [Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html).

            > **Nota:** independentemente da origem do sistema de tipos, as entradas devem atender às regras de nomenclatura listadas anteriormente.

        1. Inclua, edita e exclua tipos de entidade e tipos de relação da mesma maneira que você faz quando cria um sistema de tipos do zero.

    - Crie um sistema de tipos a partir do zero:

        1. Na guia **Tipos de entidade**, clique em **Incluir tipo de entidade**.
        1. Especifique um nome de tipo de entidade descritivo, tendo em mente que o tipo de entidade é um rótulo para anotar períodos importantes de texto (menções) em seu conteúdo de domínio. Mantenha o nome abreviado e representante, assim os anotadores humanos podem se lembrar dele facilmente.

            Também é possível opcionalmente definir funções e subtipos para o tipo de entidade:
            - Uma função ajuda a qualificar o tipo de entidade no contexto em que a menção ocorre. Por exemplo, a menção `Software Engineer` pode ser rotulada com o tipo de entidade `PEOPLE` e, nesse contexto, pela função `OCCUPATION`. Veja [Quando definir funções](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles) para obter mais informações.
            - Um subtipo ajuda a classificar ainda mais o tipo de entidade. Por exemplo, o tipo de entidade `GOVERNMENT` pode ter os subtipos de `MILITARY` e `CIVILIAN`.

            > **Nota:** ao definir uma função ou um subtipo para uma entidade, você está dando mais opções para a pessoa associará informações de tipo com menções no tempo de anotação. O anotador humano pode aplicar uma anotação que especifica somente o tipo de entidade ou o tipo de entidade mais a função ou subtipo que você está definindo agora.

            Tente definir tipos de entidade suficientes para capturar os conceitos chave que você deseja anotar, mas não muitos tipos de entidade, que se torna cansativo para os anotadores humanos aplicarem os rótulos com precisão.

        1. Clique em **Classes de menção** e **Tipos de menção** para visualizar as classes de menção e os tipos de menção padrão. Não é possível editar esses valores.

            O propósito de um atributo é ajudar a rotular cada menção pelo tipo de coisa que ela é. Um tipo de menção indica se a menção é um nome, nominal ou pronome e uma classe menção indica se a menção é específica, genérica ou negada.

        1. Abra a página **Ativos** > **Tipos de relação** e especifique como duas menções podem se relacionar umas com as outras.

            A ordem entre a primeira e segunda entidades em um tipo de relação é geralmente relevante. Por exemplo, uma entidade `PERSON` pode ser um funcionário de uma entidade `ORGANIZATION` ou uma entidade geopolítica (**GPE**), como `Mary` `employedBy` `{{site.data.keyword.IBM_notm}}`, mas as organizações e as entidades geopolíticas não podem ser empregadas por uma pessoa. Quando um anotador humano clica em uma entidade no editor de verdade absoluta, a lista de tipos de relação disponíveis é controlada pelo que está definido no sistema de tipos.

            Não defina atributos de relação. Eles não são usados pelo modelo de aprendizado de máquina. O modelo usa somente o tipo de relação e a ordem e ignora os atributos de relação.

        1. Use os ícones **Editar** e **Excluir** para modificar tipos de entidade e seus tipos de relação associados ou para excluir um tipo de entidade ou tipo de relação do sistema de tipos.

            Se você exclui uma entidade que é usada em uma definição de tipo de relação, a definição de tipo de relação também é excluída.

**Tarefas relacionadas**:

[Modificando um sistema de tipos sem perder as anotações humanas](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Diretrizes de criação do sistema de tipos
{: #wks_typesys_guidelines}

O objetivo de qualquer sistema de tipos no {{site.data.keyword.knowledgestudioshort}} é definir como períodos de texto podem ser anotados. Se você escolher criar um sistema de tipos do zero, siga estas diretrizes.

Foque na criação de um inventário de tipos de entidade e tipos de relação que cobrem as informações que são necessárias pelo aplicativo no qual o sistema de tipos será usado. Não cubra coisas que não são necessárias. Não divida tipos ou faça distinções que não sejam necessárias ao aplicativo. Por exemplo, se o documento de origem contém a sentença `Assassinato no Expresso do Oriente fez manchetes`, então o modo como você define os tipos de entidade para capturar as informações chave na sentença difere dependendo do tipo de aplicativo que usará o modelo construído com o sistema de tipos.

- Para um aplicativo literário, você pode criar tipos que capturam estas informações:

    ```
               [NOVEL][CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Assassinato no Expresso do Oriente ][made headlines]
    ```
    {: screen}

- Para um aplicativo de segurança pública, você pode criar estes tipos:

    ```
    [EVENT_CRIME][LOCATION]
    ```
    {: screen}

    ```
      [Assassinato] no [Orient Express] fez manchetes
    ```
    {: screen}

A estrutura é geralmente acionada por características dos documentos dos quais as informações serão extraídas, mas deve ser sempre temperada por quais informações o aplicativo realmente usará desses documentos. Por exemplo, você pode estar criando um aplicativo que ganha insights de registros médicos. Para construir o sistema de tipos, você começar a olhar os registros de pacientes para ver quais tipos de informações devem ser capturados. Os registros de pacientes podem todos conter um campo que descreve o que o paciente comeu no almoço. No entanto, se o aplicativo não usará essas informações, não inclua no sistema de tipos. E ao tomar a decisão de fazer essa omissão, reconheça que isso significa que as seções de seus documentos de registro de paciente serão deixadas sem anotação. Isso é correto e até esperado.

As menções anotam um período de texto; elas não substituem o texto. Um sistema de tipos não é uma ontologia para um domínio. Espere ter tipos de entidade gerais, como `MEDICATION_NAME`, em vez de ter um tipo de entidade para cada tipo de medicamento. O texto do documento continuará a conter o nome do medicamento específico. Ele apenas será aprimorado com uma anotação que identifica seu tipo, que torna as informações mais fáceis de localizar e extrair programaticamente.

Quando você começar, defina de 10 a 40 tipos de entidade e tipos de relação. Fique na extremidade inferior do intervalo se os anotadores humanos que trabalharão na área de trabalho não forem altamente especializados no campo. Não defina mais que 50.

Planeje gastar uma boa quantia de tempo definindo o sistema de tipos antes que sua equipe inicie quaisquer tarefas de anotação humana. Quando a equipe inicia a anotação dos documentos, ela inicia com um conjunto pequeno, talvez não mais que 50. Anote somente menções inicialmente, examine os resultados e refina suas diretrizes de anotação e o sistema de tipos conforme necessário. Quando você estiver satisfeito com os resultados de anotação de menção, avance para anotar relações e correferências.

Embora o trabalho fundamental esteja em andamento para definir um conjunto de tipos de entidade e diretrizes de anotação de menção, evite colocar muito esforço para anotar menções de relação. As mudanças de relação desfazem o trabalho de anotação de relação. Reserve algum tempo para definir um conjunto de tipos de relação e seus pares de tipo de entidade permitidos para que as necessidades de tipo de relação sejam levadas em consideração antes que o inventário de tipo de entidade seja finalizado.

Espere que o sistema de tipos se desenvolva com a experiência de pessoas que tentam anotar nele. Se você revisa o sistema de tipos depois de criar tarefas de anotação humana, deve decidir se aplica as mudanças para cada tarefa. Se você aplicar as mudanças, os anotadores humanos terão que revisitar os documentos que eles anotaram anteriormente.

Ao testar o modelo, é possível revisar as estatísticas que mostram a frequência com que os tipos de entidade e tipos de relação ocorrem em seus documentos de amostra. Certifique-se de revisar essas estatísticas. Para assegurar que seu aplicativo receba contexto suficiente para anotar com precisão grandes coleções de documentos, seus dados de teste devem incluir uma grande amostragem dos tipos de entidade e tipos de relação mais importantes.

> **Importante:** depois de treinar seu primeiro modelo, você provavelmente precisará fazer modificações com base nas estatísticas de desempenho. No entanto, para criar um modelo estatístico confiável para anotação de máquina, você deseja que o sistema esteja o mais perto possível do final antes de iniciar as tarefas de anotação em larga escala.

## Quando definir funções
{: #wks_typesystem_roles}

O uso de funções permite que você defina tipos de entidade mais precisos.

Cada entidade que você inclui tem uma função. A menos que mude, o nome da função é o mesmo que o nome da entidade. É possível escolher definir uma função diferente para uma entidade para capturar um uso mais flexível da menção. A palavra ou frase à qual a função se aplica é literalmente um exemplo de um tipo de entidade, mas na sentença ela desempenha a função de outro tipo de entidade. Por exemplo, na frase `the White House vetoed the bill`, podemos capturar mais precisamente o significado de `the White House` se anotamos o tipo de entidade de `FACILITY` e uma função de `ORGANIZATION` ou `PERSON`. A Casa Branca é um prédio (`FACILITY`), mas representa o governo (`ORGANIZATION`) ou o Presidente dos Estados Unidos (`PERSON`) nessa construção. O tipo de entidade mais o rótulo de função cria uma classificação mais precisa da menção no texto.

As funções também podem fornecer a você uma maneira de capturar informações de relação sem depender do uso de menções de sobreposição. Por exemplo, você pode desejar anotar o texto `31 anos masculino` de forma que ele capture a ideia de que esta é uma referência a uma pessoa com o atributo idade de 31 anos e o atributo sexo de masculino. Ao examinar o texto, nós determinamos que `31 anos` é uma idade, `masculino` é um gênero e, juntos, eles significam uma pessoa. Você está lidando com 3 tipos de entidade, basicamente: `AGE`, `GENDER` e `PERSON`. Uma abordagem para a representação disso seria anotar `31-year-old` como `AGE`, `male` como `GENDER` e, como a menção distinta de um `PERSON` está ausente, mas `male` vem para representar a pessoa, a palavra `male` pode ter uma função de `PERSON`. É possível, então, capturar as relações entre a função `PERSON` e todos os atributos de uma pessoa que você deseja capturar. Por exemplo, é possível definir uma relação `hasAttribute` entre a função `PERSON` e a menção `AGE`. Como você aplicou um tipo de entidade `GENDER` e um rótulo de tipo de função `PERSON` para a mesma palavra `male`, não é possível definir uma relação `hasAttribute` entre os dois. No entanto, o fato de que os dois rótulos são aplicados à mesma menção os associa entre si. Essa associação é considerada pelo modelo de aprendizado de máquina sem precisar definir um tipo de relação hasAttribute para chamar explicitamente o relacionamento.

Um exemplo semelhante é quando a frase `2008 Ford F-150` é usado como abreviação para `caminhão 2008 Ford F-150`. Aqui, `2008` é anotado como um tipo de entidade `MODEL_YEAR`, `Ford` é anotado como um tipo de entidade `MANUFACTURER` e `F-150` recebe um tipo de entidade `MODEL`. Mas com a palavra `truck` ausente, `F-150` também representa um veículo. Dizer `F-150` é como dizer `o caminhão`. É possível capturar esse uso incluindo uma função `VEHICLE` na menção além de seu tipo de entidade `MODEL`. Em seguida, é possível definir as relações `hasAttribute` entre a função `VEHICLE` e as menções de entidade `MANUFACTURER` e `MODEL_YEAR`.

### Como as funções são diferentes de subtipos?

Os subtipos de entidade são para estratificar um inventário de tipos de entidade em uma hierarquia. Por exemplo, se você deseja distinguir 40 coisas, mas elas se agrupam logicamente em 10 conjuntos de 4 (`VITALSIGN_BLOODPRESSURE`, `VITALSIGN_HEARTRATE`, `MEDICATION_DOSAGE`, `MEDICATION_FREQUENCY`), é possível estruturá-las em tipos e subtipos, o que rende menus mais compactos, mas inclui um nível de profundidade e incômodo para o processo de rotulagem. Para os propósitos de extração de informações, uma combinação de tipos e subtipos é intercambiável com muitos tipos sem subtipos. Em contraste, a palavra ou frase à qual você aplica uma função é um exemplo de um tipo de entidade, mas desempenha a função de outro tipo de entidade, e um que não é um subtipo do outro.

### Como as funções são tratadas?

O modelo de aprendizado de máquina do {{site.data.keyword.knowledgestudioshort}} define rótulos do classificador para cada menção de uma entidade que ele localiza nos documentos de origem, concatenando o tipo de entidade e os valores de função. Ao fornecer valores de função, você cria rótulos mais precisos. Cada grupo de instâncias de um tipo de rótulo que são localizadas nos dados de treinamento forma um conjunto mais uniforme de menções. O desafio é que, ao escolher ser mais preciso, você também deve aderir ao fornecimento de mais dados de treinamento para assegurar que o modelo seja bem executado. Mas quanto mais dados de treinamento você fornece, melhor o modelo se torna. Então, se você não se importa em executar anotação adicional, o uso de funções leva a melhores resultados.

Como um exemplo, suponhamos que as sentenças a seguir ocorram em um documento de origem e nós desejamos capturar o `Acme` (em que `Acme` é um fabricante de caminhão bem conhecido), `sedan` e `truck` como entidades semelhantes, porque todas elas se referem a um veículo físico:

- a) `The Acme crashed into the concrete barrier.`
- b) `The sedan crashed into the concrete barrier.`
- c) `The Acme A-160 truck crashed into the concrete barrier.`

É possível manipular o design do sistema de tipos de duas maneiras:

1. Defina dois tipos de entidade: `MANUFACTURER` e `VEHICLE`. Para a entidade `MANUFACTURER`, defina uma função `VEHICLE` que pode ser usada além da função `MANUFACTURER` padrão.

    Usando esse sistema de tipos, as sentenças são anotadas como segue:
    - a) O `Acme` é anotado como uma entidade `MANUFACTURER`, mas com uma função de `VEHICLE`, uma vez que se refere a um veículo real. Então, seu rótulo interno é `MANUFACTURER-VEHICLE`.
    - b) O `sedan` é anotado como o tipo de entidade `VEHICLE`. Ele é designado automaticamente à função `VEHICLE`, pois nenhuma outra função está definida.
    - c) O `Acme` é anotado como o tipo de entidade `MANUFACTURER` e `truck` é anotado como o tipo de entidade `VEHICLE`. Nenhuma função está designada, então as funções padrão são usadas.

1. Defina somente dois tipos de entidade sem funções: `MANUFACTURER` e `VEHICLE`.

    Usando esse sistema de tipos, as sentenças são anotadas como segue:
    - a) O `Acme` é anotado como o tipo de entidade `VEHICLE`.
    - b) O `sedan` é anotado como o tipo de entidade `VEHICLE`.
    - c) O `Acme` é anotado como o tipo de entidade `MANUFACTURER` e `truck` é anotado como o tipo de entidade `VEHICLE`.

Como os dois sistemas de tipos diferentes são executados? Vamos supor que um conjunto de documentos foi anotado por anotadores humanos. Após a passagem de anotação, os eventos de treinamento a seguir, que são entidades rotuladas manualmente, são identificados no corpus de treinamento:

- **Sistema de tipos 1**

    ```
    MANUFACTURER-MANUFACTURER 800 events
    MANUFACTURER-VEHICLE 200 events
    VEHICLE-VEHICLE 400 events
    ```
    {: screen}

- **Sistema de tipos 2**

    ```
    MANUFACTURER 800 events
    VEHICLE 200 + 400 = 600 events
    ```
    {: screen}

Quando o modelo processa novos documentos, é provável que `Acme` seja rotulado como um `MANUFACTURER` a maior parte do tempo porque a ortografia de uma palavra é um recurso forte e a palavra `Acme` provavelmente será definida no dicionário `MANUFACTURER`. Levaria muito contexto para rotulá-lo de forma diferente. Se usarmos o sistema de tipos 1, haverá somente 200 eventos de treinamento `MANUFACTURER-VEHICLE`, o que é uma desvantagem quando comparado com os 600 eventos de `VEHICLE` no sistema de tipos 2. No entanto, os clusters de eventos de treinamento no sistema de tipos 1 são todos muito uniformes, o que leva a um melhor desempenho. Para o sistema de tipos 2, o conjunto de 600 eventos de treinamento para `VEHICLE` é, na verdade, composto de dois clusters um pouco desconectados: um contém nomes de fabricantes que se referem a veículos reais, como `Acme` e `Ford`, e o outro contém tipos de veículo, como `sedan`, `SUV` e `truck`. Intuitivamente, cada um desses dois clusters em si são uniformes, mas combinando-os, isso dilui o cluster de treinamento e apresenta um problema difícil de resolver. Se você continua fazendo anotação e incluindo mais eventos de treinamento, o desempenho no sistema de tipos 1 continua melhorando, enquanto o problema de resolver dois clusters separados que você obtém com o sistema de tipos 2 não melhora com mais treinamento.
