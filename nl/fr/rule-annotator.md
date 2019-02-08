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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator.html){: new_window}.
{: tip}

# Règles
{: #rule-annotator}

Créez un modèle à base de règles qui puisse reconnaître des motifs caractéristiques dans vos documents. Utilisez des règles pour repérer et capturer des motifs apparaissant dans les documents et faire ressortir des informations à propos des types d'entités sous-jacents.
{: shortdesc}

## Les classes

Lorsque vous construisez une règle, vous utilisez des classes pour représenter les différents types d'informations. Ces classes sont similaires aux types d'entités. Alors pourquoi ne pas simplement utiliser des types d'entités pour définir les règles ? Parce qu'en utilisant des classes, il est possible de définir des classes intermédiaires qui ne servent qu'à construire d'autres classes plus complexes. Ces classes intermédiaires sont purement utilitaires. Elles ne sont pas utiles en soi. Elles coopèrent avec d'autres classes intermédiaires pour définir une classe plus utile et plus complète. Une classe intermédiaire est une nécessité, mais pas quelque chose que vous exposez en tant que partie d'un système de types. Pour que le modèle à base de règles puisse avoir une fonction utile, comme pré-annoter des documents avec des mentions d'entités, vous devez associer les classes complexes que vous utilisez pour créer vos règles à leurs types d'entités équivalents dans le système de types.

Supposons, par exemple, que vous vouliez obtenir un modèle qui puisse reconnaître des noms de personnes. Il faut pour cela étiqueter avec le type d'entité `PERSON` de nombreux noms différents, écrits sous des formes diverses, dans les documents d'un jeu d'annotations, puis utiliser ce dernier pour entraîner un modèle d'apprentissage automatique. Pour créer un modèle à base de règles capable de reconnaître les noms de personnes, vous devez définir une règle décrivant les motifs de texte couramment employés pour écrire les noms de personnes. Vous pourriez donc créer une classe `FirstName` (prénom) et une classe `LastName` (nom de famille) et les utiliser comme classes intermédiaires pour définir une classe `FullName` (nom complet). Vous pourriez ensuite définir des conditions qui détermine la position de la classe `FullName` par rapport à des préfixes courants tels que `Dr.` et des suffixes courants tels que `Jr.`. Lors de l'utilisation du modèle à base de règles, la classe `FullName` serait associée au type d'entité `PERSON`.

Une autre raison pour laquelle il n'est pas souhaitable d'associer directement les classes intermédiaires à des types d'entités dans le système de types est que si vous pré-annotez des documents avec votre modèle à base de règles et que vous les ajoutez ensuite à vos données de référence pour entraîner un modèle d'apprentissage automatique, vous ne voulez pas que les règles produisent des mentions d'entités chevauchantes. Par exemple, si vous deviez associer à la fois la classe intermédiaire `FirstName` et la classe complexe `FullName` au type d'entité `PERSON`, une occurrence de `Dr. John Doe` produirait une mention chevauchante.

## Outils de l'éditeur de règle

L'éditeur de règle fournit plusieurs outils d'aide à la définition de règles.

- Dictionnaire

    Ajoutez un dictionnaire et associez-lui un nom de classe. Tous les mots figurant dans un texte qui correspondent à des entrées du dictionnaire seront automatiquement annotés avec la classe associée.

- Expression régulière

    Une expression régulière (regex) est une séquence de caractères qui composent un motif de recherche. L'outil regex inclus dans l'éditeur de règle reconnaît les expressions qui obéissent à la syntaxe définie par la classe Java standard `java.util.regex.Pattern`. Par exemple, l'expression `[A-Z][a-z]*` trouve les mots commençant par une majuscule.

    `[A-Z]` trouve n'importe quelle lettre majuscule (A à Z) tandis que `[a-z]*` trouve un nombre quelconque (y compris zéro) d'occurrences de lettres minuscules (a à z). Ici, l'astérisque (*) dicte la condition de répétition et signifie zéro, une ou plusieurs fois.

    Pour composer l'expression qui vous permettra de capturer le motif voulu, vous pouvez vous aider d'un utilitaire d'aide à la syntaxe regex. Beaucoup sont disponibles gratuitement sur le web.

    Par exemple, vos documents pourraient contenir plusieurs références similaires aux syntagmes suivants :

    ```
    conducteur de 35 ans
    élève conducteur de 16 ans
    ```
    {: screen}

    La syntaxe `x de n ans` est un motif qui représente typiquement une personne. Vous pouvez donc définir une règle à base d'expression régulière pour trouver les syntagmes qui correspondent au motif `x de n ans` et les annoter en tant que mentions du type d'entité `PERSON`.
