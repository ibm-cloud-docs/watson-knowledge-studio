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

Cette documentation concerne
{{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}.
Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace,
[cliquez sur
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/dictionaries.html){: new_window}.
{: tip}

# Créer des dictionnaires
{: #dictionaries}

Les dictionnaires aident les annotateurs automatiques de {{site.data.keyword.knowledgestudioshort}} à comprendre
le langage du domaine ou du métier concerné.
{: shortdesc}

## Dictionnaires
{: #wks_dictionaries}

En apprentissage automatique, un dictionnaire regroupe des mots et des syntagmes qui ont un point commun.

Une entrée du dictionnaire ne signifie pas que tous les mots qui la composent signifient la même chose, mais qu'ils doivent être traités de façon équivalente
par un modèle.


Un dictionnaire est une liste de mots ou de syntagmes équivalents en termes
d'extraction d'informations, ce qui signifie qu'ils sont interchangeables pour identifier
les mentions d'entités et de relations.

Prenons cet exemple : une entrée de dictionnaire contient les sept jours de la semaine.
Pour annoter un document, un annotateur humain associe le type d'entité DAY_OF_WEEK (ou JOUR_SEMAINE) aux mentions
de lundi et vendredi dans le texte.
Comme le dictionnaire traite sur un même plan les sept jours de la semaine, il contribue à ce que
le modèle d'apprentissage automatique, lors de son exécution, annote correctement les occurrences de mardi, mercredi et des autres jours
de la semaine dans des documents jamais vus auparavant.
Le fait de mettre ces mots sur un même pied d'égalité profite aussi
à l'extraction de l'information figurant dans le texte environnant.
En effet, comme le dictionnaire stipule qu'ils sont équivalents en termes d'extraction de l'information,
lors de son entraînement avec des exemples, tout ce que le modèle d'apprentissage automatique a retenu à propos des textes à proximité
de lundi et vendredi, il le réapplique aux textes qu'il voit à proximité des mentions des autres jours de la semaine dans les nouveaux documents qui lui sont ensuite soumis.


> **Remarque :** Inutile de créer un dictionnaire contenant les jours de la semaine ; plusieurs dictionnaires généralistes contenant
ces types d'informations sont déjà intégrés dans l'application.
D'autres contiennent les noms de pays et de lieux, les noms des nombres (adjectifs numéraux cardinaux), les noms d'animaux,
de plantes et de maladies, les noms d'unités de mesure (tels que once et mètre) et les titres de civilité (tels que M. et Mme). Les
dictionnaires intégrés ne peuvent pas être désactivés ni édités.


Evitez d'ajouter des entrées ayant plusieurs significations.
Par exemple, dans un domaine traitant de l'automobile, il peut être logique d'inclure le terme *batterie*, qui fait référence
à l'organe mécanique, mais à condition qu'il ne soit pas également question de musique dans le texte.
Si le mot apparaît souvent avec les deux sens dans les documents source, mieux vaut le laisser en dehors des deux types de dictionnaires,
celui qui est associé à la mécanique automobile et celui qui est associé à la musique et à ses instruments.


Vous pouvez créer des dictionnaires dans {{site.data.keyword.knowledgestudioshort}} en ajoutant
vous-même des entrées une à une.
{{site.data.keyword.knowledgestudioshort}} vous donne aussi la possibilité de transférer plusieurs types de fichiers de dictionnaire.


### Comment les dictionnaires sont-ils utilisés ?

Les dictionnaires s'utilisent de deux manières, toutes optionnelles.
Ils sont utilisés d'une part par le modèle d'apprentissage automatique pour fournir les mots ou les syntagmes qui sont
équivalents en termes d'extraction de l'information, d'autre part au cours de la pré-annotation pour
amorcer le travail d'annotation.


- **Utilisation pour l'apprentissage automatique**

    Le type d'entité que vous associez à un dictionnaire ne sert pas à définir de règles pour
le modèle d'apprentissage automatique.
Ce dernier évalue les mentions dans les documents indépendamment.
Il ne part pas du principe qu'une mention a un type d'entité spécifique juste parce qu'elle correspond à une entrée d'un dictionnaire qui est associé à
ce type d'entité.
Il prend note de l'information, mais il la traite comme une information parmi d'autres qu'il recueille à travers son analyse linguistique.
En fait, si aucun des termes d'un dictionnaire ne figure dans les documents de référence, ce dictionnaire n'est pas utilisé du tout par le modèle d'apprentissage automatique.


- **Utilisation pour la pré-annotation**

    Les dictionnaires sont importants pour les processus de pré-annotation suivants.
    - Pré-annotateur à base de dictionnaire : lorsque vous exécutez ce pré-annotateur, vous associez un dictionnaire à un type d'entité du
système de types.

    - Modèle à base de règles : au besoin, vous pouvez associer un dictionnaire à une classe de règle.
Ce type de classe est ensuite associé à un type d'entité du système de types lorsque vous exécutez le modèle à base de règles
pour pré-annoter des documents.
Par conséquent, les termes des dictionnaires sont, bien que de manière indirecte, également associés à des types d'entités pour le modèle à base de règles.

    Dans les deux cas, les dictionnaires servent à fourni des termes que le système peut trouver
et annoter en tant que mentions.
Lorsqu'il trouve une mention d'un terme, il lui attribue le type d'entité qui est associé au dictionnaire qui contient
ce terme.
De cette manière, lorsqu'un annotateur humain commence à travailler sur de nouveaux documents qui ont été pré-annotés de la sorte,
nombre de mentions sont déjà annotées en fonction d'entrées du ou des dictionnaires utilisés.
Il peut donc passer plus de temps à attribuer des types d'entités aux mentions qui requièrent une analyse plus approfondie.


### Langue

- Pour le portugais du Brésil, l'anglais, le français, l'allemand, l'italien et l'espagnol,
{{site.data.keyword.knowledgestudioshort}} ne prévoit pas actuellement d'option pour spécifier
que les recherches dans les dictionnaires doivent être indifférentes à la casse des caractères. Néanmoins, il y a correspondance entre une
entrée d'un dictionnaire et un texte dès lors que la casse du texte est égale ou plus haute que celle de l'entrée du dictionnaire.
Par exemple, l'entrée "voiture" dans un dictionnaire concorde avec "voiture", "Voiture" ou "VOITURE" dans le texte, tandis que
l'entrée "Samedi" dans le dictionnaire concorde avec "Samedi" ou "SAMEDI" dans le texte, mais pas avec "samedi".

- Pour le japonais et le coréen, la correspondance avec les entrées des dictionnaires pendant la pré-annotation est
sensible à la casse.

- Pour l'arabe, {{site.data.keyword.knowledgestudioshort}} considère que les textes en arabe sont stockés
dans leur forme non formée et il traite le formage des nombres comme une propriété au niveau du stockage.
Pour des détails sur la manière dont {{site.data.keyword.knowledgestudioshort}} gère le formage des caractères et
des chiffres arabes, consultez [Configurer le support de l'arabe](/docs/services/watson-knowledge-studio/language-support.html#wks_langsupp_ar).


### Dictionnaire au format de fichier CSV
{: #wks_dictionaries__cvsdict}

Un dictionnaire au format `CSV` (valeurs séparées par des virgules), également appelé format de dictionnaire standard,
est un fichier que vous pouvez éditer après l'avoir transféré.
La taille maximum d'un fichier `CSV` que vous pouvez transférer est de 1 Mo.
Si vous avez fichier de dictionnaire dépassant cette limite, décomposez-le en plusieurs
fichiers plus petits et transférez-les ensemble vers un unique dictionnaire de votre espace de travail
{{site.data.keyword.knowledgestudioshort}}.


Les conditions à satisfaire sont pour l'essentiel les suivantes : pour créer le fichier `CSV`, vous
devez utiliser un éditeur de texte, et non un logiciel tel
que Microsoft Excel. Le fichier doit utiliser un encodage UTF-8 qui n'inclut pas la marque d'ordre d'octet (BOM)
au début du flot de texte.
La première ligne du fichier doit comporter les en-têtes de colonnes suivants :


```
lemma,poscode,surface
```
{: screen}

Les lignes restantes du fichier spécifient les entrées du dictionnaire, avec :


- **`lemma`**

    Spécifie la forme de mot la plus représentative pour l'entrée.

- **`poscode (arabe, portugais du Brésil, anglais, français, allemand, italien et espagnol)`**

    Spécifie un code qui identifie la partie du discours.
Cette information est utilisée par l'annotateur à base de dictionnaire pour aider à l'analyse lexicale de la phrase.
    - 0 - Inconnu

        > **Remarque :** Ce code est prévu pour le cas où vous voulez transférer un gros dictionnaire généré automatiquement
qui n'inclut pas l'information de partie du discours dans chaque entrée.
Vous pouvez appliquer la valeur Inconnu à toutes les entrées, par défaut.
Evitez si possible d'utiliser ce code.


    - 1 - Pronom
    - 2 - Verbe
    - 3 - Nom commun
    - 4 - Adjectif
    - 5 - Adverbe
    - 6 - Apposition
    - 7 - Interjection
    - 8 - Conjonction
    - 9 - Déterminant
    - 10 - Quantificateur

    En anglais, les parties du discours les plus couramment employées pour les entrées des dictionnaires sont
nom commun (3), verbe (2) et adjectif (4).


    > **Remarque :** La partie du discours ne détermine pas automatiquement
le type d'une mention.
Ne partez pas du principe que tous les noms sont assimilables à des mentions de types d'entités et que
tous les verbes sont assimilables à des mentions de types de relations.
Par exemple, *américain* est un adjectif, mais il gagnerait à être annoté en tant que
type d'entité GPE (entité géopolitique) ou PERSON.
*Rencontre* est un verbe, mais une annotation comme type d'entité EVENT_MEETING (événement rencontre) lui conviendrait certainement mieux.


    Dans d'autres langues, comme l'allemand, qui utilise des mots composés, la
précision de l'information de partie du discours est encore plus importante pour aider à
déterminer les limites des mots.


- **`poscode (japonais)`**

    Spécifie un code qui identifie la partie du discours.
Cette information est importante pour l'analyse lexicale du texte et la pré-annotation dans les langues telles
que le japonais, qui n'utilisent pas l'espace pour indiquer les limites des mots.

    - 19 - Nom commun
    - 23 - Préfixe commun
    - 24 - Préfixe commun
    - 140 - Nom propre (Nom)
    - 141 - Nom propre (Prénom)
    - 146 - Nom propre (Nom de personne)
    - 142 - Nom propre (Organisation)
    - 144 - Nom propre (Nom de lieu)
    - 143 - Nom propre (Région)
    - 145 - Nom propre (Autre)

- **`poscode (coréen)`**

    Spécifie un code qui identifie la partie du discours.
Cette information est importante pour l'analyse lexicale du texte et la pré-annotation dans les langues telles
que le coréen, qui n'utilisent pas l'espace pour indiquer les limites des mots.

    - 10010 - Nom commun
    - 10300 - Nom propre (Nom)
    - 10310 - Nom propre (Prénom)
    - 110360 - Nom propre (Nom de personne)
    - 10320 - Nom propre (Organisation)
    - 10340 - Nom propre (Nom de lieu)
    - 10330 - Nom propre (Région)
    - 10350 - Nom propre (Autre)

- **`surface`**

    Spécifie des termes équivalents, que l'on appelle aussi formes de surface.
Répétez le lemme comme première forme de surface et, si vous en spécifiez d'autres, séparez-les par une virgule.
Mettez la forme de surface entre guillemets si elle inclut elle-même une virgule.


Par exemple :

```
lemma,poscode,surface
IBM,3,IBM Corp.,IBM,"International Business Machines, Inc."
Department of Energy,3,DOE,Department of Energy
premium,4,premium,premium-grade
```
{: screen}

**Concepts connexes** :

[Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html)

**Tâches connexes** :

[Pré-annoter des documents avec le pré-annotateur à base de dictionnaire](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

## Ajouter des dictionnaires à un espace de travail
{: #wks_projdictionaries}

L'ajout de dictionnaires n'est pas obligatoire lorsque vous créez
un modèle.
Ils sont cependant utiles dans la mesure où ils permettent d'accélérer le processus d'annotation.


### A propos de cette tâche

Si vous fournissez un dictionnaire, vous pouvez annoter des documents à l'aide
du pré-annotateur à base de dictionnaire.
Celui-ci trouve dans les documents les termes représentés dans votre dictionnaire et les annote automatiquement.
Cette passe initiale sur les documents simplifie le travail des annotateurs humains qui interviennent ensuite, leur tâche consistant
à passer en revue les annotations qui ont été ajoutées par le pré-annotateur, à les corriger si besoin est et à les compléter.
Cela leur évite de partir de zéro.


Les restrictions suivantes s'appliquent aux dictionnaires :


- Maximum 15 000 entrées par dictionnaire

    > **Remarque :** Cette limite ne s'applique pas aux dictionnaires que vous transférez sous forme
de fichiers CSV.
Les dictionnaires en lecture seule peuvent contenir davantage d'entrées.

- Maximum 64 dictionnaires par espace de travail

### Procédure

Pour ajouter un dictionnaire à votre espace de travail :

1. Connectez-vous en tant qu'administrateur
ou chef de projet {{site.data.keyword.knowledgestudioshort}} et ouvrez
l'onglet **Actifs & Outils** > **Pré-annotateurs** > **Dictionnaires**.

1. Effectuez l'une des opérations suivantes :

    - Cliquez sur **Transférer un dictionnaire**, sélectionnez un dictionnaire, puis cliquez
sur **Transférer**.
Une fois le dictionnaire transféré, pour le voir et l'associer à un type d'entité,
cliquez sur **Gérer les dictionnaires**.


        - Vous pouvez transférer un fichier ZIP contenant un dictionnaire que vous avez précédemment
téléchargé d'un autre espace de travail {{site.data.keyword.knowledgestudioshort}}.
Vous devez transférer le système de types qui a été téléchargé de l'autre espace de travail au format JSON avant de pouvoir transférer
le fichier du dictionnaire correspondant.
Vous pouvez éditer et compléter les entrées d'un dictionnaire que vous réutilisez d'un
autre espace de travail {{site.data.keyword.knowledgestudioshort}}.
Pour plus de détails,
consultez [Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

        Le transfert d'un fichier CSV est également possible, mais le
transférer directement comme dictionnaire a pour effet de créer un
dictionnaire en aperçu seul que vous ne pouvez pas éditer ni utiliser pour pré-annoter des
documents.
Pour transférer un fichier CSV qui puisse être édité et utilisé pour la pré-annotation,
cliquez sur **Gérer les dictionnaires**, puis sur
**Créer un dictionnaire** afin de d'abord créer un dictionnaire. Après quoi,
transférez le contenu CSV en tant qu'entrées dans ce dictionnaire nouvellement créé.


    - Cliquez sur le bouton **Gérer les dictionnaires** pour créer un nouveau dictionnaire auquel vous pourrez ensuite
ajouter des entrées.


        Cliquez sur le bouton **Créer un dictionnaire** et spécifiez un
nom descriptif pour le nouveau dictionnaire.
Sélectionnez le type d'entité qui décrit le mieux la finalité du dictionnaire, puis cliquez sur **Sauvegarder**.

1. Pour ajouter des entrées au dictionnaire, effectuez l'une des opérations suivantes :

    - Cliquez sur **Ajouter une entrée** pour ajouter une entrée au dictionnaire.
Spécifiez le lemme (la forme de mot la plus représentative pour le terme).

    - Pour transférer un fichier `CSV` contenant des
entrées de dictionnaire, cliquez sur **Transférer**, puis recherchez et
sélectionnez le fichier CSV,
dont la taille ne doit pas excéder 1 Mo.


1. Vous pouvez éditer les entrées d'un dictionnaire après les avoir ajoutées ou après avoir transféré le dictionnaire.


    Ouvrez une entrée pour spécifier des termes équivalents, appelés
formes de surface.
Chaque forme de surface doit être limitée à 256 caractères.
Vous pouvez changer laquelle des formes de surface est utilisée comme lemme. 

    Par exemple, le lemme *{{site.data.keyword.IBM_notm}}* pourrait avoir des formes de surface
telles que *{{site.data.keyword.IBM_notm}} Corp.* et *International Business Machines, Inc.*.

1. Sélectionnez la partie du discours appropriée pour chaque lemme et forme de surface dans le dictionnaire.


    L'information de partie du discours est utilisée par l'analyseur lexical (tokenizer) ainsi que pendant la pré-annotation.


1. Cliquez sur **Sauvegarder** pour stocker vos changements.


### Que faire ensuite

Exécutez le pré-annotateur, qui utilise les dictionnaires que vous avez créés pour effectuer une passe préliminaire sur les documents
source et y ajouter des annotations.


**Tâches connexes** :

[Pré-annoter des documents avec le pré-annotateur à base de dictionnaire](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

**Référence associée** :

[Support multilingue](/docs/services/watson-knowledge-studio/language-support.html)
