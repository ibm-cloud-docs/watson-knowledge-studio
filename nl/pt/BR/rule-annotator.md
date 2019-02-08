---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator.html){: new_window}.
{: tip}

# Regras
{: #rule-annotator}

Crie um modelo baseado em regra que possa reconhecer padrões em seus documentos. Use regras para capturar padrões que ocorrem em documentos e transmitir informações sobre os tipos de entidade subjacentes.
{: shortdesc}

## Visão geral de classe

Ao construir uma regra, você usa as classes para representar tipos de informações. Essas classes são semelhantes aos tipos de entidade. Então, por que não apenas usamos tipos de entidade ao definir regras? Como você constrói regras, é possível definir classes intermediárias que são usadas somente para construir outras classes mais complexas. Essas classes intermediárias são exclusivamente utilitárias. Elas não são úteis sozinhas. As classes intermediárias trabalham com outras classes intermediárias para definir uma classe mais útil e completa. Uma classe intermediária é necessária, mas não algo que você expõe como parte de um sistema de tipos. Para permitir que o modelo baseado em regra execute coisas úteis como pré-anotar documentos com menções de entidade, deve-se mapear as classes complexas que você usa durante a criação de regras para seus tipos de entidade equivalentes do sistema de tipos.

Por exemplo, você deseja um modelo que possa reconhecer nomes de pessoas. Para treinar um modelo de aprendizado de máquina para reconhecer nomes de pessoas, você anotaria muitos nomes diferentes que são gravados em uma variedade de formatos de documentos em um conjunto de anotações com o tipo de entidade `PERSON` e treinaria um modelo para reconhecer os nomes de pessoas. Para criar um modelo baseado em regra para reconhecer nomes de pessoas, você define uma regra que descreve os padrões de texto usados para escrever os nomes de pessoas. Então, você pode criar uma classe `FirstName` e uma classe `LastName` e usar essas classes intermediárias para definir uma classe `FullName`. Você pode definir condições que determinam o posicionamento da classe `FullName` em relação a prefixos comuns como `Dr.` e sufixos comuns como `Jr.`. Quando o modelo baseado em regra é usado, a classe `FullName` é mapeada para o tipo de entidade `PERSON`.

Outra razão para evitar mapear classes intermediárias para entidades em seu sistema de tipos é que se você pré-anotar documentos com o modelo baseado em regra e, em seguida, incluí-los em sua verdade absoluta para treinar um modelo de aprendizado de máquina, você não desejará definir regras de tal forma que elas produzam menções de entidade de sobreposição. Por exemplo, se você fosse mapear a classe intermediária `FirstName` e a classe complexa `FullName` para a entidade `PERSON`, uma ocorrência de `John Doe, Jr.` resultaria em uma menção de sobreposição.

## Ferramentas do editor de regras

O editor de regras fornece algumas ferramentas que ajudam a definir regras.

- Dicionário

    Inclua um dicionário e designe a ele um nome de classe. Quaisquer palavras localizadas que correspondem a entradas no dicionário são automaticamente anotadas com a classe designada.

- Expressão regular

    Uma expressão regular (regex) é uma sequência de caracteres que definem um padrão de procura. A ferramenta regex que está incluída no editor de regras reconhece expressões que seguem a sintaxe `java.util.regex.Pattern`. Aqui está um exemplo básico:
    `[A-Z][a-z]*`: localiza palavras em letras maiúsculas.

    `[A-Z]` corresponde qualquer letra alfabética maiúscula (A-Z) e `[a-z]*` corresponde qualquer letra alfabética minúscula (a-z) zero ou mais vezes. O asterisco (*) é o caractere que define a configuração de repetição (zero ou mais vezes).

    Considere usar um utilitário regex baseado na web grátis para ajudá-lo a determinar a expressão certa a ser usada para capturar o padrão que você deseja localizar.

    Por exemplo, seus documentos podem ter várias referências que são semelhantes às frases a seguir:

    ```
    35-year-old driver
    16-year-old learner
    ```
    {: screen}

    A sintaxe `n-year-old x` é um padrão que geralmente representa uma pessoa. É possível definir uma regra de expressão regular para localizar frases que correspondem ao padrão `n-year-old x` e anotá-las como menções de entidade `PERSON`.
