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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window}.
{: tip}

# Definindo uma regra
{: #wks_rule_creation}

Use o editor de regras para definir regras.
{: shortdesc}

## Sobre essa Tarefa

Evite a edição simultânea de regras, classes e expressões regulares por múltiplos usuários porque isso pode resultar em sobrescrições inesperadas ou duplicação.

## Procedimento

Para definir uma regra, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e clique em **Modelo baseado em regra** > **Regras**.
1. Clique no sinal de mais (+) ao lado do título Documentos para incluir um documento.

    Para obter mais informações, veja [Incluindo documentos para definir regras](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html).

    Por exemplo, você pode incluir um documento denominado `Meu documento` que contém esta única linha de texto:

    ```
    Um motorista de 50 anos estava dirigindo o Horizon Exemplo 2017.
    ```
    {: screen}

1. Se você planeja definir uma expressão regular ou incluir um dicionário, crie uma classe para associar com isso.

    1. No painel **Classe**, clique no sinal de mais (+) próximo à Classe.
    1. Inclua um nome de classe.

        Se você associará a classe com uma expressão regular ou dicionário, considere nomear a classe de forma que seja possível identificar sua origem. Por exemplo, se você planeja usar uma expressão regular para definir um padrão para a idade na sentença de exemplo, é possível criar uma classe denominada `AGE_REGEX`. Se você planeja usar um dicionário para anotar o fabricante do carro na sentença, é possível incluir uma classe denominada `MANUFACTURER_DICT`.

        Mantenha estas regras de nomenclatura em mente:
        - O primeiro caractere em um nome de classe deve ser alfabético.
        - Use somente os caracteres ASCII alfanuméricos a seguir e o caractere de sublinhado em valores que você incluir nas classes: `A` a `Z`, `a` a `z`, `0` a `9`.
        - Os nomes não podem conter espaços.
        - Os nomes não podem ter mais que 64 caracteres.

1. Opcional: para anotar rapidamente as classes em um documento, é possível associar um dicionário ao editor de regras. Os termos em um documento que correspondem a entradas no dicionário são anotados automaticamente com a classe que você seleciona para o dicionário.

    1. Clique na guia **Dicionários**.

        Os dicionários que você criou são exibidos.

        Se você não tiver incluído um dicionário, abra a página **Ativo** > **Dicionários** na barra de navegação principal para incluir um. Veja [Criando dicionários](/docs/services/watson-knowledge-studio/dictionaries.html) para obter mais informações.

    1. Clique em um dicionário, associe uma classe ao dicionário e, em seguida, clique em **Salvar**.

        Por exemplo, se você tiver um dicionário que contenha nomes de organização, será possível criar uma classe de regra chamada `ORGANIZATION` e associar a classe ao dicionário. Quaisquer nomes de organização que ocorrerem em seus documentos de amostra serão anotados como instâncias da classe `ORGANIZATION`.

    Se você desejar remover a associação de dicionário do editor de regras mais tarde, será possível remover o mapeamento de classe. Para fazer isso, escolha a opção vazia na parte superior da lista suspensa.

2. Opcional: para definir uma expressão regular para ajudar a construir uma regra, clique na guia **Regex**.

    1. Clique no sinal de mais (+) ao lado do título Expressões regulares.
    2. Nomeie a expressão regular. Por exemplo,  ` MyAgeRegex `.

        O nome não pode ter mais de 64 caracteres.

    3. Associe a expressão com uma classe. Por exemplo,  ` AGE_REGEX `.
    4. Clique em **Incluir entrada**.
    5. Inclua a expressão.

        Por exemplo, para capturar um número que representa uma idade (até 99 anos), é possível especificar `[0-9]{1,2}`. Para capturar expressões de tempo, como *00:30*, você pode especificar esta expressão regular:

        ```
        (1[0-2]|0?[1-9 ]): ([ 0-5 ][0-9]) (\s + [ AaPp ][Mm])?
        ```
        {: screen}

        É possível mudar opcionalmente os números mínimo e máximo de tokens de palavra. Em inglês, os tokens são frequentemente comparados a palavras como delimitados por espaços em branco em uma sentença. No entanto, eles nem sempre correspondem um a um com palavras. Outros elementos textuais são considerados tokens em algumas situações. Por exemplo, cada hífen no termo *50-anos-idade* conta como um token, o que significa que o número total de tokens usados nesse termo é 5. E o texto *12:30* contém 4 tokens. (`12 | : | 30 | PM`)

        Clique em ** Adicionar**.

    6. Repita as duas etapas anteriores se desejar incluir mais expressões.
    7. Clique em **Salvar**.

    O editor regex é fechado e o documento é exibido. Você deverá ver a classe que definiu para a expressão regular aplicada ao texto ao qual pretendia que ela correspondesse. Se você não vir a anotação, verifique sua expressão. Ela pode precisar ser revisada para que corresponda ao texto que você pretendia que ela localizasse.

    ![O editor de regras mostrando a guia "Regex" selecionada, uma expressão regular chamada "Age" que está associada à classe "AGE_REGEX" e um documento que mostra o texto "50" destacado em amarelo. O texto destacado corresponde à expressão regular que foi criada.](images/rule_step3.jpg "O editor de regras mostrando a ")

3. Para definir uma regra, clique em **Regras** na navegação.
4. Abra o documento com o padrão que você deseja capturar como uma regra. Por exemplo, se você tiver criado um documento intitulado `My Document` com o texto de amostra que contém a frase `50-year-old`, abra esse documento.
5. No texto no documento, selecione os caracteres que ilustram o padrão que você deseja capturar. Por exemplo, é possível selecionar as palavras e os hifens (-) a seguir:

    ```
    50-anos-idade
    ```
    {: screen}

    Depois de selecionar caracteres, é possível incluir uma regra.

6. Clique no sinal de mais (+) no painel **Regras**.

    O editor de regras representa o texto que você selecionou como duas camadas de células. As células na camada superior são onde você anota as classes dos tokens subjacentes. A camada inferior é onde você define as condições pelas quais os tokens participarem no padrão.

    ![O editor de regras que mostra o painel "Criar uma regra".](images/rule_step4.jpg "O editor de regras que mostra o que o ")

7. Defina as condições pelas quais cada token participa no padrão.

    Na camada inferior de células, clique no primeiro token para revisar suas condições. Se você deseja indicar que qualquer token pode ser usado na posição atual no padrão, clique em **Abrir propriedades** e selecione **Permitir qualquer token**. Clique em **Fechar propriedades**. Se um token é um regex, como `AGE_REGEX` no exemplo, **Permitir qualquer token** não está disponível.

    > **Nota:** o número máximo de células do grupo que podem participar de um padrão é 15 quando cada célula tem uma configuração de repetição de 1 ou menos. As células do grupo incluem tokens únicos, anotações ou tokens em que qualquer token é permitido. O número máximo de total de tokens permitido em um padrão é 20. Considere a configuração de repetição de cada célula enquanto você define o padrão. Por exemplo, é possível definir um padrão que inclui 15 tokens quando cada célula tem uma configuração de repetição de 1 ou menos. Mas é possível definir no máximo 4 tokens no padrão se cada um tem uma configuração de repetição de 1 ou mais, pois para cada um, o token pode repetir até 5 vezes. Quatro tokens que são repetidos 5 vezes traz você para o máximo permitido de 20.

    Para indicar que um tipo particular de token é necessário, é possível definir os tipos de configurações de condições a seguir:
    - **Configuração de repetição**: especifica quantas vezes o token atual deve ser incluído no padrão. É possível mudar a configuração de repetição, mas somente uma configuração de repetição pode ser especificada por token. As opções são descritas na tabela a seguir.

    <table summary="">
      <caption>Tabela 1. Configurações de repetição</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e471">
          Opção de configuração
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e473">
          Descrição
        </th>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Necessário (exatamente 1)</p>
        </td>
        <td headers="d27028e473">
          <p>Esse token deve existir no padrão
            uma vez. Essa opção é aplicada por padrão, mas é
            possível mudá-la.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Repetindo 1 ou mais vezes</p>
        </td>
        <td headers="d27028e473">
          <p>Esse token deve existir no padrão
            pelo menos uma vez e pode repetir mais vezes.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Repetindo 0 ou mais vezes</p>
        </td>
        <td headers="d27028e473">
          <p>Esse token pode opcionalmente repetir no
            padrão muitas vezes, mas não precisa repetir.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Ocorrendo 0 ou 1 vez</p>
        </td>
        <td headers="d27028e473">
          <p>Esse token é opcional.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Avançado: _customizado_</p>
        </td>
        <td headers="d27028e473">
          <p>Esse token deve repetir no padrão
            o número de vezes que é especificado aqui. Para definir
            uma configuração de repetição customizada, clique
            em <b>Abrir propriedades</b>,
            selecione **Avançado** e, em seguida, selecione o número exato de repetições ou intervalo de repetições que você deseja definir.</p>
          <p>
            O número máximo de repetições que são permitidas para um token
            é 5.</p>
        </td>
      </tr>
    </table>

    - **Configuração de recurso**: pelo menos uma das configurações de recurso deve ser definida. É possível incluir mais recursos para incluir no número de condições que devem ser atendidas para que o texto corresponda a esse padrão. As opções são descritas na tabela a seguir.

    <table summary="">
      <caption>Tabela 2. Configurações de Recursos</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e512">
          Opção de configuração
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e514">
          Condição que ela inclui
        </th>
      </tr>
      <tr>
        <td headers="d27028e512">
          <p>Texto</p>
        </td>
        <td headers="d27028e514">
          <p>Deve corresponder ao texto exato nesse
            token. Essa opção é aplicada por padrão. É possível removê-la,
            mas somente se você incluir uma configuração diferente como uma condição
            ou aplicar a configuração Qualquer token.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e512">
          <p>Comprimento</p>
        </td>
        <td headers="d27028e514">
          <p>Deve corresponder ao comprimento de caracteres
            desse token. O comprimento é contado iniciando em 0 na
            frente do primeiro caractere.</p>
        </td>
      </tr>
    </table>

    O resto das opções diferem dependendo do tipo do token.

    - **O token não anotado não corresponde a um regex ou termo de dicionário**: essas configurações estão disponíveis para tokens que não são anotados e não correspondem a um regex ou termo de dicionário.

    <table summary="">
      <caption>Tabela 3. Configurações de Token Não Anotado</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e535">Opção de configuração</th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e537">Descrição</th>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Parte do discurso</p>
        </td>
        <td headers="d27028e537">
          <p>Deve ser a mesma parte do discurso
       que esse token. Os tipos a seguir são suportados:</p>
          <ul>
            <li>
              adjetivo
            </li>
            <li>
              adposição
            </li>
            <li>
              advérbio
            </li>
            <li>
              conjunção
            </li>
            <li>
              determinador
            </li>
            <li>
              interjeição
            </li>
            <li>
              substantivo
            </li>
            <li>
              numeral
            </li>
            <li>
              pronome
            </li>
            <li>
              residual
            </li>
            <li>
              verbo
            </li>
          </ul>
        </td>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Lema</p>
        </td>
        <td headers="d27028e537">
          <p>Deve ter o mesmo lema que esse
       token.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Tipo de caractere</p>
        </td>
        <td headers="d27028e537">
          <p>Deve ter o mesmo tipo de caractere
       que esse token. Os tipos a seguir são suportados:</p>
          <ul>
            <li>
              <p>Árabe: contém uma sequência
       de caracteres árabes</p>
            </li>
            <li>
              <p>ChineseNumeral: contém somente
                numerais chineses</p>
            </li>
            <li>
              <p>ClauseEndingPunctuation:
                Caracteres de pontuação que separam uma cláusula
                ou sentença da próxima</p>
            </li>
            <li>
              <p>Han: contém caracteres Han</p>
            </li>
            <li>
              <p>Hangul: contém caracteres silábicos
       coreano Hangul</p>
            </li>
            <li>
              <p>Hebraico: contém uma sequência de
       caracteres hebraicos</p>
            </li>
            <li>
              <p>Hiragana: contém caracteres silábicos
       japoneses Hiragana</p>
            </li>
            <li>
              <p>Ideográfico: contém um
       ideograma ou símbolo que representa uma ideia ou
       coisa</p>
            </li>
            <li>
              <p>Katakana: contém caracteres silábicos
       japoneses Katakana</p>
            </li>
            <li>
              <p>Minúscula: contém somente caracteres alfabéticos
       minúsculos</p>
            </li>
            <li>
              <p>Numérico: contém somente caracteres
       numéricos</p>
            </li>
            <li>
              <p>Pontuação: um ou mais
       caracteres que fornecem a pontuação no
       texto</p>
            </li>
            <li>
              <p>Silábico: contém caracteres
                silábicos</p>
            </li>
            <li>
              <p>Tailandês: contém caracteres
                tailandeses</p>
            </li>
            <li>
              <p>Iniciais: inicia com um
       único caractere alfabético maiúsculo, seguido
       por um ou mais caracteres alfabéticos minúsculos</p>
            </li>
            <li>
              <p>Maiúscula: um token contendo
       somente caracteres alfabéticos maiúsculos</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **Correspondência de regra:**

    <table summary="">
      <caption>Tabela 4. Correspondência de</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e617">
          Opção de configuração</th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e619">
          Descrição</th>
      </tr>
      <tr>
        <td headers="d27028e617">
          <p>Correspondência de regra</p>
        </td>
        <td headers="d27028e619">
          <p>Deve corresponder à classe nomeada. Lembre-se, uma classe pode ser derivada de um regex,
            um dicionário ou uma regra. Se a classe especificada
            aqui é derivada de uma expressão regular, por
            exemplo, esse token deve corresponder ao padrão
            de procura da expressão.</p>
        </td>
      </tr>
    </table>

8. Para tokens que possuem anotações que foram incluídas indiretamente de uma anotação de dicionário ou correspondência de expressão regular, é possível escolher se o padrão deve requerer qualquer palavra com o mesmo tipo de anotação ou as palavras reais subjacentes que foram anotadas.

    Na camada inferior de células, é possível ver quais células são incluídas no padrão porque uma linha horizontal as conecta entre si. Quando uma anotação tiver sido aplicada, há uma divisão. As células com as palavras originais são exibidas abaixo de uma célula com o rótulo de anotação. É possível clicar em um conjunto de células ou no outro para mudar o caminho da linha e, assim, mudar as células que são incluídas no padrão.

    Por exemplo, você poderia escolher permitir que o padrão use 50 em vez de permitir que ele corresponda à expressão regular de idade.

    ![O painel "Criar uma regra" que mostra uma edição do token, "50", que usa a anotação, "AGE_REGEX", na regra. Por padrão, a anotação "AGE_REGEX" é usada, mas é possível editar o padrão para que a palavra subjacente, "50", seja usada em seu lugar.](images/rule_step5.jpg)

9. Depois de configurar a ordem padrão, é possível anotar tokens no texto.

    Na camada superior de células, clique nas células que representam os tokens que você deseja anotar e, em seguida, aplique um rótulo de classe a elas. Para selecionar múltiplas células, clique em uma, pressione a tecla **Shift** e clique em células adicionais.

    Designe uma classe às células selecionadas. Se a classe que você deseja designar não existe, é possível incluí-la. Digite o nome de classe no campo **Designar classe** e pressione **Enter**.

    > **Nota:** não é possível incluir mais de 10 classes para a regra.

    ![A seção "Criar uma regra" mostrando a janela "Designar classe" que é aberta quando você clica em um token. A janela mostra um campo no qual é possível inserir o nome de uma nova classe ou selecionar uma classe existente da lista.](images/rule_step6.jpg)

10. Nomeie a regra.

    O nome da regra não pode ter mais que 64 caracteres.

11. Clique em **Salvar** no painel Regras para salvar a regra.
