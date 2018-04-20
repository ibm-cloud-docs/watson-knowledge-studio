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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window}.
{: tip}

# Definindo uma regra
{: #wks_rule_creation}

Use o editor de regras para definir regras.
{: shortdesc}

## Sobre essa Tarefa

Evite a edição simultânea de regras, classes e expressões regulares por múltiplos usuários porque isso pode resultar em sobrescrições inesperadas ou duplicação.

## Procedimento

Para definir uma regra, conclua as etapas a seguir:

1. Efetue login como administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e abra a página **Regras**.
1. Clique no sinal de mais (+) ao lado de Documentos para incluir um documento.

    Veja [Incluindo documentos para definir regras](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html) para obter detalhes.

    Por exemplo, você pode incluir um documento denominado `Meu documento` que contém esta única linha de texto:

    ```
    Um motorista de 50 anos estava dirigindo o Horizon Exemplo 2017.
    ```
    {: screen}

1. Se você planeja definir uma expressão regular ou incluir um dicionário, crie uma classe para associar com isso.

    1. No painel **Classe**, clique no sinal de mais (+) próximo à Classe.
    1. Inclua um nome de classe.

        Se você associará a classe com uma expressão regular ou dicionário, considere nomear a classe de forma que seja possível identificar sua origem. Por exemplo, se você planeja usar uma expressão regular para definir um padrão para o número na sentença, é possível criar uma classe chamada AGE_REGEX. E se você planeja usar um dicionário para anotar o fabricante do carro na sentença, é possível incluir uma classe chamada MANUFACTURER_DICT.

        Mantenha estas regras de nomenclatura em mente:
        - O primeiro caractere em um nome de classe deve ser alfabético.
        - Use somente os caracteres ASCII alfanuméricos a seguir e o caractere de sublinhado em valores que você inclui nas classes: A-Z, a-z, 0-9.
        - Os nomes não podem conter espaços.
        - Os nomes não podem ter mais que 64 caracteres.

1. Opcional: para anotar rapidamente as classes no documento, é possível associar um dicionário com o editor de regras. Os termos no documento que correspondem a entradas no dicionário são anotados automaticamente com a classe apropriada.

    1. Clique na guia **Dicionários** no painel.

        Os dicionários que você criou são exibidos.

        Se você não tiver incluído um dicionário, abra a guia **Dicionários** na barra de navegação principal para incluir um. Veja [Criando dicionários](/docs/services/watson-knowledge-studio/dictionaries.html) para obter mais informações.

    1. Clique em um dicionário e defina uma associação de classe para ele e, em seguida, clique em **Salvar**.

        Por exemplo, se você tem um dicionário que contém nomes de organização, é possível associá-lo à regra e designar a classe ORGANIZATION_DICT a ele. Quaisquer nomes de organização que ocorrem em seus documentos de amostra serão anotados como instâncias da classe ORGANIZATION_DICT.

    Se você desejar remover a associação de dicionário do editor de regras mais tarde, será possível remover o mapeamento de classe. Para fazer isso, escolha a opção vazia na parte superior da lista suspensa.

1. Opcional: para definir uma expressão regular para ajudá-lo a construir uma regra, clique em **Regex** na navegação.

    1. Clique no sinal de mais (+) próximo a Expressões regulares para incluir uma expressão regular.
    1. Nomeie a expressão regular. Por exemplo, MyAgeRegex.

        O nome não pode ter mais de 64 caracteres.

    1. Associe a expressão com uma classe. Por exemplo, AGE_REGEX.
    1. Clique em **Incluir entrada**.
    1. Inclua a expressão.

        Por exemplo, para capturar um número que representa uma idade (até 99 anos), é possível especificar `[0-9]{1,2}`. Para capturar expressões de tempo, como *00:30*, você pode especificar esta expressão regular:

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        É possível mudar opcionalmente os números mínimo e máximo de tokens de palavra. Em inglês, os tokens são frequentemente comparados a palavras como delimitados por espaços em branco em uma sentença. No entanto, eles nem sempre correspondem um a um com palavras; outros elementos textuais são considerados tokens em algumas situações. Por exemplo, cada hífen no termo *50-anos-idade* conta como um token, o que significa que o número total de tokens usados nesse termo é 5. E o texto *12:30* contém 4 tokens. (`12 | : | 30 | PM`)

        Clique em ** Adicionar**.

    1. Repita as duas etapas anteriores se desejar incluir mais expressões.
    1. Clique em **Salvar**.

    O editor regex é fechado e o documento é exibido. Você deverá ver a classe que definiu para a expressão regular aplicada ao texto ao qual pretendia que ela correspondesse. Se não, verifique sua expressão. Ela pode precisar ser revisada para que corresponda ao texto que você pretendia que ela localizasse.

    ![O editor de regras mostrando a guia "Regex" selecionada, uma expressão regular chamada "Age" que está associada à classe "AGE_REGEX" e um documento que mostra o texto "50" destacado em amarelo. O texto destacado corresponde à expressão regular que foi criada.](images/rule_step3.jpg)

1. Para definir uma regra, clique em **Regras** na navegação.
1. Abra o documento com o padrão que você deseja capturar como uma regra. Por exemplo, se você tiver criado um documento intitulado `My Document` com o texto de amostra que contém a frase `50-year-old`, abra esse documento.
1. No texto no documento, selecione os caracteres que ilustram o padrão que você deseja capturar. Por exemplo, é possível selecionar as palavras e os hifens (-) a seguir:

    ```
    50-anos-idade
    ```
    {: screen}

    Depois de selecionar caracteres, é possível incluir uma regra.

1. Clique no sinal de mais (+) no painel **Regras**.

    O editor de regras representa o texto que você selecionou como duas camadas de células. As células na camada superior são onde você anota as classes dos tokens subjacentes. A camada inferior é onde você define as condições pelas quais os tokens participarem no padrão.

    ![O editor de regras que mostra como o painel "Criar uma regra" se parece depois que você seleciona texto de seu documento e clica no sinal de mais no painel "Regras". Os elementos gráficos a seguir são mostrados: o campo "Nome da regra" com o termo "IDADE" inserido, o painel "Criar uma regra" e o painel "Classe". No painel "Criar uma regra", as células com linhas pontilhadas são mostradas na parte superior. Uma célula é mostrada para cada token do texto que foi selecionado. Nessas células, você anota as classes dos tokens. Na parte inferior do painel "Criar uma regra", as células com linhas sólidas são mostradas. Cada célula contém um token do texto selecionado, "50-anos-idade". Os tokens são "50", "-" (hífen), "anos", "-" e "idade". Cada célula de linha sólida tem dois ícones ao lado dela que é possível usar para ajustar a condição da palavra ou anotação.](images/rule_step4.jpg)

1. Defina as condições pelas quais cada token participa no padrão.

    Na camada inferior de células, clique no primeiro token para revisar suas condições. Se você deseja indicar que qualquer token pode ser usado na posição atual no padrão, clique em **Abrir propriedades** e selecione **Permitir qualquer token**. Clique em **Fechar propriedades**. Se um token é um regex, como `AGE_REGEX` no exemplo, **Permitir qualquer token** não está disponível.

    > **Nota:** o número máximo de células do grupo que podem participar de um padrão é 15 quando cada célula tem uma configuração de repetição de 1 ou menos. As células do grupo incluem tokens únicos, anotações ou tokens em que qualquer token é permitido. O número máximo de total de tokens permitido em um padrão é 20. Considere a configuração de repetição de cada célula enquanto você define o padrão. Por exemplo, é possível definir um padrão que inclui 15 tokens quando cada célula tem uma configuração de repetição de 1 ou menos. Mas é possível definir no máximo 4 tokens no padrão se cada um tem uma configuração de repetição de 1 ou mais, pois para cada um, o token pode repetir até 5 vezes. Quatro tokens que são repetidos 5 vezes traz você para o máximo permitido de 20.

    Para indicar que um tipo particular de token é necessário, é possível definir os tipos de configurações de condições a seguir:
    - **Configuração de repetição**: especifica quantas vezes o token atual deve ser incluído no padrão. É possível mudar a configuração de repetição, mas somente uma configuração de repetição pode ser especificada por token. As opções são descritas na tabela a seguir.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e471" class="stentry thleft thbot">Opção de configuração</th>
        <th valign="bottom" align="left" id="d27028e473" class="stentry thleft thbot">Descrição</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Necessário (exatamente 1)</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esse token deve existir no padrão
            uma vez. Essa opção é aplicada por padrão, mas é
            possível mudá-la.</p></td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Repetindo 1 ou mais vezes</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esse token deve existir no padrão
            pelo menos uma vez e pode repetir mais vezes.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Repetindo 0 ou mais vezes</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esse token pode opcionalmente repetir no
            padrão muitas vezes, mas não precisa repetir.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Ocorrendo 0 ou 1 vez</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esse token é opcional.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Avançado: _customizado_</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esse token deve repetir no padrão
            o número de vezes que é especificado aqui. Para definir
            uma configuração de repetição customizada, clique
            em <b>Abrir propriedades</b>,
            selecione **Avançado** e, em seguida, selecione o número exato de repetições ou intervalo de repetições que você deseja definir.</p>
          <p class="note">
            O número máximo de repetições que são permitidas para um token
            é 5.</p>
        </td>
      </tr>
    </table>

    - **Configuração de recurso**: pelo menos uma das configurações de recurso deve ser definida. É possível incluir mais recursos para incluir no número de condições que devem ser atendidas para que o texto corresponda a esse padrão. As opções são descritas na tabela a seguir.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e512" class="stentry thleft thbot">Opção de configuração</th>
        <th valign="bottom" align="left" id="d27028e514" class="stentry thleft thbot">Condição que ela inclui</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">Texto</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">Deve corresponder ao texto exato nesse
            token. Essa opção é aplicada por padrão. É possível removê-la,
            mas somente se você incluir uma configuração diferente como uma condição
            ou aplicar a configuração Qualquer token.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">Comprimento</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">Deve corresponder ao comprimento de caracteres
            desse token. O comprimento é contado iniciando em 0 na
            frente do primeiro caractere.</p>
        </td>
      </tr>
    </table>

    O resto das opções diferem dependendo do tipo do token.

    - **O token não anotado não corresponde a um regex ou termo de dicionário**: essas configurações estão disponíveis para tokens que não são anotados e não correspondem a um regex ou termo de dicionário.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e535" class="stentry thleft thbot">Opção de configuração</th>
        <th valign="bottom" align="left" id="d27028e537" class="stentry thleft thbot">Descrição</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Parte do discurso</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Deve ser a mesma parte do discurso
       que esse token. Os tipos a seguir são suportados:</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">adjetivo</p>
            </li>
            <li class="li">
              <p class="p wrapper">adposição</p>
            </li>
            <li class="li">
              <p class="p wrapper">advérbio</p>
            </li>
            <li class="li">
              <p class="p wrapper">conjunção</p>
            </li>
            <li class="li">
              <p class="p wrapper">determinador</p>
            </li>
            <li class="li">
              <p class="p wrapper">interjeição</p>
            </li>
            <li class="li">
              <p class="p wrapper">substantivo</p>
            </li>
            <li class="li">
              <p class="p wrapper">numeral</p>
            </li>
            <li class="li">
              <p class="p wrapper">pronome</p>
            </li>
            <li class="li">
              <p class="p wrapper">residual</p>
            </li>
            <li class="li">
              <p class="p wrapper">verbo </p>
            </li>
          </ul>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Lema</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Deve ter o mesmo lema que esse
       token.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Tipo de caractere</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Deve ter o mesmo tipo de caractere
       que esse token. Os tipos a seguir são suportados:</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">Árabe: contém uma sequência
       de caracteres árabes</p>
            </li>
            <li class="li">
              <p class="p wrapper">ChineseNumeral: contém somente
                numerais chineses</p>
            </li>
            <li class="li">
              <p class="p wrapper">ClauseEndingPunctuation:
                Caracteres de pontuação que separam uma cláusula
                ou sentença da próxima</p>
            </li>
            <li class="li">
              <p class="p wrapper">Han: contém caracteres Han</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hangul: contém caracteres silábicos
       coreano Hangul</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hebraico: contém uma sequência de
       caracteres hebraicos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hiragana: contém caracteres silábicos
       japoneses Hiragana</p>
            </li>
            <li class="li">
              <p class="p wrapper">Ideográfico: contém um
       ideograma ou símbolo que representa uma ideia ou
       coisa</p>
            </li>
            <li class="li">
              <p class="p wrapper">Katakana: contém caracteres silábicos
       japoneses Katakana</p>
            </li>
            <li class="li">
              <p class="p wrapper">Minúscula: contém somente caracteres alfabéticos
       minúsculos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Numérico: contém somente caracteres
       numéricos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Pontuação: um ou mais
       caracteres que fornecem a pontuação no
       texto</p>
            </li>
            <li class="li">
              <p class="p wrapper">Silábico: contém caracteres
                silábicos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Tailandês: contém caracteres
                tailandeses</p>
            </li>
            <li class="li">
              <p class="p wrapper">Iniciais: inicia com um
       único caractere alfabético maiúsculo, seguido
       por um ou mais caracteres alfabéticos minúsculos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Maiúscula: um token contendo
       somente caracteres alfabéticos maiúsculos</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **Correspondência de regra:**

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e617" class="stentry thleft thbot">Opção de configuração</th>
        <th valign="bottom" align="left" id="d27028e619" class="stentry thleft thbot">Descrição</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e617" class="stentry">
          <p class="p wrapper">Correspondência de regra</p>
        </td>
        <td valign="top" headers="d27028e619" class="stentry">
          <p class="p wrapper">Deve corresponder à classe nomeada.
            Lembre-se, uma classe pode ser derivada de um regex,
            um dicionário ou uma regra. Se a classe especificada
            aqui é derivada de uma expressão regular, por
            exemplo, esse token deve corresponder ao padrão
            de procura da expressão.</p>
        </td>
      </tr>
    </table>

1. Para tokens que possuem anotações que foram incluídas indiretamente de uma anotação de dicionário ou correspondência de expressão regular, é possível escolher se o padrão deve requerer qualquer palavra com o mesmo tipo de anotação ou as palavras reais subjacentes que foram anotadas.

    Na camada inferior de células, é possível ver quais células são incluídas no padrão porque uma linha horizontal as conecta entre si. Quando uma anotação tiver sido aplicada, há uma divisão. As células com as palavras originais são exibidas abaixo de uma célula com o rótulo de anotação. É possível clicar em um conjunto de células ou no outro para mudar o caminho da linha e, assim, mudar as células que são incluídas no padrão.

    Por exemplo, você poderia escolher permitir que o padrão use 50 em vez de permitir que ele corresponda à expressão regular de idade.

    ![O painel "Criar uma regra" que mostra uma edição do token, "50", que usa a anotação, "AGE_REGEX", na regra. Por padrão, a anotação "AGE_REGEX" é usada, mas é possível editar o padrão para que a palavra subjacente, "50", seja usada em seu lugar.](images/rule_step5.jpg)

1. Depois de configurar a ordem padrão, é possível anotar tokens no texto.

    Na camada superior de células, clique nas células que representam os tokens que você deseja anotar e, em seguida, aplique um rótulo de classe a elas. Para selecionar múltiplas células, clique em uma, pressione a tecla **Shift** e clique em células adicionais.

    Designe uma classe às células selecionadas. Se a classe que você deseja designar não existe, é possível incluí-la. Digite o nome de classe no campo **Designar classe** e pressione **Enter**.

    > **Nota:** não é possível incluir mais de 10 classes para a regra.

    ![A seção "Criar uma regra" mostrando a janela "Designar classe" que é aberta quando você clica em um token. A janela mostra um campo no qual é possível inserir o nome de uma nova classe ou selecionar uma classe existente da lista.](images/rule_step6.jpg)

1. Nomeie a regra.

    O nome da regra não pode ter mais que 64 caracteres.

1. Clique em **Salvar** no painel Regras para salvar a regra.
