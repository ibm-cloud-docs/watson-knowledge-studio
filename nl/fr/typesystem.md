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
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window}.
{: tip}

# Etablir un système de types
{: #typesystem}

Le système de types contrôle de quelle manière le contenu peut être annoté.
{: shortdesc}

## Systèmes de types
{: #wks_typesystem}

Un système de types définit tout ce qui est intéressant dans les contenus relatifs à votre domaine et que vous voulez étiqueter avec une annotation.
Le système de types contrôle de quelle manière le contenu peut être annoté en définissant les types des entités qui peuvent être étiquetées et comment
les relations entre les différentes entités peuvent elles-mêmes être étiquetées.
Il est généralement défini par le gestionnaire des processus de modélisation en collaboration avec
les experts de votre domaine.


Dans {{site.data.keyword.knowledgestudioshort}}, vous pouvez créer un système de types en partant de
zéro ou en transférant un système existant si vous en possédez un.
Pour démarrer un espace de travail, vous pouvez aussi transférer un système de types ayant été créé pour un
domaine similaire.
Vous pouvez ensuite l'éditer pour y ajouter des types d'entités ou en retirer, ou encore pour redéfinir
les types de relations.


Un exemple de système de types basé sur le système de types
KLUE vous est fourni en vue de son utilisation avec les
tutoriels de {{site.data.keyword.knowledgestudioshort}}.
Le système de types KLUE, qui signifie Knowledge from Language Understanding and Extraction, est le résultat de l'analyse de collections d'articles de presse
par {{site.data.keyword.IBM_notm}} Research.
Vous pouvez télécharger un spécimen de système de types
KLUE <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>ici<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.

De nombreuses industries, notamment dans des domaines
comme la métallurgie, la géologie, l'intelligence marketing,
les sciences de la vie, les dossiers médicaux informatisés
et l'oncologie, publient des dictionnaires ou des ontologies de
terminologie propre à leur domaine.
Pensez à vous référer à ce type de ressource pour vous faire une idée des types d'entités à définir dans votre propre système.


### Mentions
{: #wks_typesystem__wks_typesystemS2}

Une mention est une étendue de texte que vous considérez pertinente dans les données de votre
domaine.
Par exemple, dans un système de types du secteur automobile, des
occurrences de termes tels que *airbag*, *Ford Explorer* et
*siège enfant* pourraient être des mentions pertinentes.


### Types d'entités
{: #wks_typesystem__wks_typesystemS3}

Un type d'entité est la manière de catégoriser une chose du monde réel.
Une mention d'entité est un exemple d'une chose de ce type.
Par exemple, la mention "Président Obama" peut être annotée comme un type d'entité PERSON.
La mention "{{site.data.keyword.IBM_notm}}" peut être annotée comme un type d'entité ORGANIZATION.
Les entités sont souvent des noms, mais il peut aussi s'agir de verbes s'il est important de les capturer pour les besoins
de l'application qui utilisera le système de types.
Par exemple, dans un système de types du secteur automobile,
EVENT_CRASH pourrait être un type d'entité valide, qui
permettrait d'annoter le mot *heurté* dans la phrase "La voiture a heurté la barrière.".


L'objectif de votre espace de travail d'annotation est d'annoter chaque mention dans un document
avec le type de la chose mentionnée.
Lorsqu'une mention a été classée par type d'entité, l'étendue de texte étiquetée devient une entité.


Un système de types que vous construisez avec {{site.data.keyword.knowledgestudioshort}} peut inclure
les attributs de type d'entité suivants.
Le but des attributs est d'aider à qualifier les mentions dans le texte, mais ils ne sont pas
repérés comme des types d'entités par un modèle d'apprentissage automatique.
Par exemple, si le type d'entité ORGANIZATION a un sous-type d'entité nommé COMMERCIAL, celui-ci n'est
pas considéré à part entière comme un type d'entité.


- **Rôle**

    Qualifie la mention par le contexte dans lequel elle apparaît.
Par exemple, la mention "France" dans la phrase "les étudiants sont allés en France" est
repérée avec le type d'entité GPE (geo-political entity), car France est une entité géopolitique.
Mais comme, dans ce contexte, France est aussi une destination pour les étudiants en voyage,
le type d'entité est qualifié davantage par l'ajout d'un attribut qui, dans le cas présent, est le rôle LOCATION (lieu).
Autre exemple, la mention "Avocats" pourrait être repérée avec le type d'entité PEOPLE et qualifiée davantage avec
le rôle OCCUPATION (profession).

- **Sous-type d'entité**

    Complète la classification du type d'entité.
Par exemple, le type d'entité ORGANIZATION pourrait inclure les sous-types COMMERCIAL, GOVERNMENT, MILITARY et EDUCATION.

- **Type de mention**

    Qualifie la mention par certaines parties du discours :
    - NAM : la mention est un nom propre, comme celui d'une personne ou d'une organisation.
    - NOM : la mention est nominale (un nom commun), par exemple "société" ou "président".
    - PRO : la mention est un pronom tel que "il", "elle" ou "nous".
    - NONE : aucun des trois autres types de mentions n'est applicable.

- **Classe de mention**

    Qualifie la mention en indiquant si celle-ci est spécifique, générique ou niée :

    - SPC : la mention est spécifique et inclut souvent l'article (le, la, les, l'), comme dans "le livre" ou "l'ouragan s'est produit en septembre".
Dans ces exemples, les mentions "livre" et "ouragan" seraient annotées avec l'attribut SPC.
    - GEN : la mention est générique. Par exemple, "un livre" ou "les ouragans se produisent souvent à l'automne".
Dans ces exemples, les mentions "livre" et "ouragans" seraient annotées avec l'attribut GEN. 
    - NEG : la mention est une négation. Ce peut être, par exemple, une référence à "pas de livre" ou "aucun livre".
Lorsque vous entraînez un modèle, l'algorithme peut apprendre tant des formulations positives que des formulations négatives. Il est
donc important de marquer les mentions des deux types.


### Types de relations
{: #wks_typesystem__wks_typesystemS4}

Un type de relation définit une relation binaire et ordonnée entre deux
entités.
Pour qu'une mention de relation puisse exister, le texte doit définir explicitement la relation et relier entre elles les mentions
des deux entités, le tout dans une même phrase.
Par exemple, la phrase *Marie travaille pour {{site.data.keyword.IBM_notm}}* est une
preuve textuelle du type de relation **employedBy** (employé par).


Pour certains types de relations, l'ordre des mentions d'entités est important.
Par exemple, le type de relation employedBy admet le type d'entité PERSON ou PEOPLE comme
première mention dans la relation, et ORGANIZATION ou GPE comme deuxième mention, mais
pas l'inverse.
Marie employedBy {{site.data.keyword.IBM_notm}} est une relation valide, mais
pas {{site.data.keyword.IBM_notm}} employedBy Marie.
Pour certains types de relations tels que spouseOf (conjoint de) ou colleague (collègue de),
l'ordre n'a pas d'importance.
Lorsque vous définissez un type de relation dans lequel l'ordre n'a pas d'importance, il est recommandé d'ajouter
des informations aux directives d'annotation afin de réglementer la façon dont ce type de relation est utilisé.
La convention, pour ce type de relation symétrique, est de stipuler que la mention d'entité qui apparaît en premier dans le texte doit être la première dans la relation.

**Concepts connexes** :

[Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html)

## Ajouter un système de types à l'espace de travail
{: #wks_projtypesys}

Avant de commencer toute tâche d'annotation, vous devez créer un système de types ou en transférer un.

### A propos de cette tâche

Les règles de nommage suivantes s'appliquent aux entrées du système de types :


- Les noms ne peuvent pas contenir d'espaces. 
- Utilisez seulement les caractères ASCII alphanumériques suivants et le trait de soulignement (touche 8) dans les
valeurs que vous ajoutez au système de types : A à Z, a à z, 0 à 9.
- Le premier caractère d'un nom d'entité ou de type de relation doit être une lettre.
- Un nom d'entité ne peut pas comporter plus de 64 caractères.
- Un nom de type de relation ne peut pas comporter plus de 128 caractères.

Par convention, les noms de type d'entité sont spécifiés en majuscules (ORGANIZATION) et
les noms de type de relation sont en casse mixte (employedBy).
Il n'est cependant pas obligatoire d'obéir à cette convention.


### Procédure

1. Connectez-vous en tant qu'administrateur
ou chef de projet {{site.data.keyword.knowledgestudioshort}} et ouvrez
la page **Actifs & Outils** > **Types d'entité**.

1. Choisissez l'une des méthodes suivantes pour créer le système de types :


    - Pour transférer un système de types existant :


        1. Cliquez sur **Transférer** pour transférer un système de types existant.

            Si vous avez précédemment téléchargé un système de types d'un espace
de travail {{site.data.keyword.knowledgestudioshort}}, vous l'avez reçu au format
`JSON`.
Vous pouvez le transférer pour accélérer la création d'un nouvel espace de travail.
Pour les détails, consultez [Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

            > **Remarque :** Quelle que soit l'origine du système de types, ses entrées doivent obéir aux règles de nommage listées plus haut.

        1. Ajoutez, éditez et supprimez des types d'entités et des types de relations en procédant comme pour
créer un système de types en partant de zéro.


    - Pour créer un système de types en partant de zéro :

        1. Cliquez sur **Ajouter un type d'entité**.
        1. Spécifiez un nom de type d'entité descriptif, en gardant à l'esprit que
le type d'entité est une étiquette qui servira à annoter des étendues de texte
(mentions) importantes dans les contenus relatifs à votre domaine.
Utilisez un nom court et représentatif pour que les annotateurs humains puissent le retenir facilement.

            Au besoin, vous pouvez aussi définir des rôles et des sous-types pour le type d'entité :

            - Un rôle aide à qualifier le type d'entité dans le contexte où la mention apparaît.
Par exemple, la mention "Ingénieur logiciel" pourrait être étiquetée avec le type d'entité PEOPLE et, dans ce contexte, avec
le rôle OCCUPATION (profession).
Pour plus d'informations, consultez [Quand définir des rôles](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles).

            - Un sous-type aide à compléter la classification du type d'entité.
Par exemple, le type d'entité GOVERNMENT pourrait comporter les sous-types MILITARY et CIVILIAN.

            > **Remarque :** En définissant un rôle ou un sous-type pour une entité,
vous donnez plus de possibilités à la personne qui, au moment d'annoter le document, devra associer des informations de typage aux mentions.
Cette personne (l'annotateur humain) pourra en effet choisir d'appliquer une annotation spécifiant uniquement
le type d'entité ou d'en appliquer une qui spécifie le type d'entité plus le rôle ou un sous-type que vous définissez maintenant.


            Essayez de définir suffisamment de types d'entités pour capturer les concepts clés que vous voulez annoter,
mais pas au point qu'il deviendrait fastidieux pour les annotateurs humains d'appliquer les étiquettes avec précision.


        1. Cliquez sur **Classes de mention** et
**Types de mention** pour voir les classes et types de mentions par
défaut (vous ne pouvez pas éditer ces valeurs).

            Le but d'un attribut est d'aider à étiqueter chaque mention par le type de chose qu'elle est.
Un type de mention indique si la mention est un nom propre, un nom commun ou un pronom, tandis qu'une classe
de mention précise si la mention est spécifique (définie), générique (indéfinie) ou niée.


        1. Ouvrez la page **Actifs & Outils** > **Types de relation** et spécifiez comment
deux mentions peuvent être reliées l'une à l'autre.

            Dans un type de relation, l'ordre entre les première et deuxième entités
a généralement son importance.
Par exemple,
une entité PERSON peut être un employé d'une entité ORGANIZATION ou d'une entité géopolitique (GPE), comme
dans la relation "Marie employedBy {{site.data.keyword.IBM_notm}}", mais l'inverse n'est pas possible : les organisations et les
entités géopolitiques ne peuvent pas être employées par une personne.
Lorsqu'un annotateur humain clique sur une entité dans l'éditeur de données de référence, la liste
des types de relations disponibles est contrôlée par ce qui est défini dans le système de types.


            Ne définissez pas d'attributs de relation.
Ils ne sont pas utilisés par le modèle d'apprentissage automatique.
Celui-ci utilise seulement le type de relation et l'ordre des entités. Il ignore les attributs de relation.


        1. Utilisez les icônes **Editer** et **Supprimer** pour modifier
des types d'entités et les types de relations qui leur sont associés, ou pour supprimer un type d'entité ou un type de relation
du système de types.


            Si vous supprimez une entité qui est utilisée dans la définition d'un type de relation,
cette définition est également supprimée.


**Tâches connexes** :

[Modifier un système de types sans perdre les annotations humaines](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Consignes de création d'un système de type
{: #wks_typesys_guidelines}

Dans {{site.data.keyword.knowledgestudioshort}}, l'objectif d'un système de types est
de définir comment les étendues de texte peuvent être annotées.
Si vous choisissez de créer un système de types en partant de zéro, suivez ces consignes :


Mettez l'accent sur la création d'un inventaire des types d'entités et des types de
relations couvrant toutes les informations nécessaires à l'application dans laquelle le
système de types sera utilisé.
Ne couvrez pas d'informations qui sont pas nécessaires.
Ne divisez pas les types et ne créez pas de distinctions qui ne sont pas
utiles à l'application.
Par exemple, si le document source contient la phrase *Le Crime de l'Orient-Express fait les gros titres*,
la manière de définir les types d'entités pour capturer les informations clés de cette phrase peut varier en fonction
du type d'application qui utilisera le modèle que vous construisez avec le système de types.


- Pour une application littéraire, vous pourriez créer des types qui capturent ces informations :


    ```
               [NOVEL]           [CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Le Crime de l'Orient-Express] [fait les gros titres]
    ```
    {: screen}

- Pour une application de sécurité publique, les types à créer pourraient être les suivants :


    ```
    [EVENT_CRIME]      [LOCATION]
    ```
    {: screen}

    ```
      Le [Crime] de l'[Orient-Express] fait les gros titres
    ```
    {: screen}

La structure est souvent dictée par les caractéristiques des documents à partir
desquels les informations seront extraites, mais elle doit toujours être tempérée par la
nature des informations qui seront effectivement exploitées par l'application.
Supposons, par exemple, que vous vouliez créer une application recueillant des informations à partir de dossiers médicaux.
Pour construire le système de types, vous commencez par étudier quelques dossiers de patients
pour identifier les types d'informations à capturer.
Il est possible que ces dossiers contiennent tous un champ décrivant ce qu'a mangé le patient au déjeuner.
Si toutefois il n'est pas prévu que l'application utilise cette information, ne l'ajoutez pas au
système de types.
Et en choisissant de faire cette omission, prenez acte du fait que, dans les dossiers des patients, certaines parties ne seront pas annotées.
C'est tout à fait normal et même attendu.

Les mentions annotent une partie du texte, elles ne le remplacent pas.
Un système de types n'est pas une ontologie d'un domaine.
Attendez-vous à avoir des types d'entités généraux, tels que
MEDICATION_NAME (nom de médicament) plutôt qu'un type d'entité pour chaque type de médicament.
Une fois annoté, le texte du document contiendra toujours le nom spécifique du médicament.
Il sera juste complété d'une annotation identifiant son type, et c'est cette annotation qui facilitera la localisation et l'extraction programmées de l'information.


Pour commencer, définissez de 10 à 40 types d'entités et types de relations.
Restez dans le bas de la fourchette si les annotateurs humains qui travailleront sur l'espace de travail ne sont pas très spécialisés dans le domaine.
N'en définissez pas plus de 50.

Prévoyez de passer pas mal de temps à définir le système de types avant que votre équipe ne puisse commencer des
tâches d'annotation.
Lorsque l'équipe est prête à annoter les documents, commencez avec un petit ensemble,
peut-être pas plus de 50.
Au départ, annotez seulement les mentions, examinez les résultats et, selon les besoins,
redéfinissez vos directives d'annotation ainsi que le système de types.
Lorsque vous êtes satisfait de l'annotation des mentions, passez à l'annotation des relations et
des coréférences.


Pendant qu'un travail fondamental est en cours pour définir un ensemble de
types d'entités et de directives d'annotation des mentions, évitez de consacrer trop
d'efforts à l'annotation des mentions de relations.
Les changements de mentions invalident le travail d'annotation des relations.
Prenez en revanche le temps de définir un ensemble de types de relations ainsi que leurs paires de types d'entités
autorisées afin que les besoins en la matière soient pris en considération avant la finalisation de l'inventaire des types d'entités.


Attendez-vous à voir le système de types évoluer à mesure que les personnes qui tentent de l'utiliser pour annoter acquièrent de
l'expérience.
Si vous révisez le système de types après avoir créé des tâches d'annotation humaine, vous devez décider dans quelle mesure
il convient d'appliquer les changements à chaque tâche.
Si vous optez pour l'application des changements, les annotateurs humains devront revoir les documents qu'ils ont déjà annotés.


Lorsque vous testez le modèle, des statistiques sont produites, qui montrent avec quelle régularité les types d'entités et les
types de relations apparaissent dans votre échantillon de documents.
Pensez à les passer en revue.
Pour que votre application reçoive suffisamment de contexte pour annoter avec précision
de grandes collections de documents, vos données de test doivent inclure un large
échantillon des types d'entités et des types de relations les plus importants.


> **Important :** Après avoir entraîné votre premier modèle, vous aurez certainement besoin d'entreprendre
des modifications en fonction des statistiques de performances.
Cependant, pour créer un modèle statistique fiable et répondant aux besoins de l'annotation automatique,
avant de commencer les tâches d'annotation à grande échelle, vous avez tout intérêt à
ce que le système de types soit aussi proche que possible de sa version définitive.


## Quand définir des rôles
{: #wks_typesystem_roles}

L'utilisation de rôles vous permet de définir des types d'entités plus précis.


Chaque entité que vous ajoutez a un rôle.
Sauf si vous le changez, le nom du rôle est le même que celui de l'entité.
Vous pouvez choisir de définir un rôle différent pour une entité particulière afin de capturer
un usage plus nuancé de la mention.
Le mot ou le syntagme auquel s'applique le rôle est littéralement un exemple d'un type d'entité, mais
dans la phrase, il joue le rôle d'un autre type d'entité.
Par exemple, dans le syntagme *la Maison Blanche a opposé son veto au projet de loi*, il est possible
de capturer plus précisément le sens de *Maison Blanche* si nous l'annotons à la fois
avec le type d'entité FACILITY et le rôle ORGANIZATION ou PERSON.
En effet, le terme Maison Blanche désigne un bâtiment (FACILITY), mais dans cette
construction, il représente le Gouvernement (ORGANIZATION) ou le Président des Etats-Unis
(PERSON).
Ainsi, l'étiquette type d'entité + rôle crée une classification plus précise de la mention dans le texte.

Les rôles peuvent aussi fournir un moyen de capturer des informations relationnelles sans
dépendre de l'utilisation de mentions chevauchantes.
Imaginons, par exemple, que vous vouliez annoter le texte
*homme de 31 ans* de manière à capturer l'idée qu'il s'agit d'une référence à une personne avec l'attribut âge = 31 ans
et l'attribut genre = masculin.
En examinant le texte, nous déterminons que *31 ans* est un âge, que *homme* est
un genre et qu'ensemble, ils signifient une personne.
En gros, vous manipulez trois types d'entités : AGE, GENDER et PERSON.
Pour représenter l'ensemble, vous pourriez annoter *31 ans* comme type d'entité AGE et *homme* comme type d'entité GENDER.
Comme il manque la mention distincte d'une entité PERSON, mais que *homme* représente une personne, le mot *homme* peut avoir
le rôle PERSON.
Vous pouvez dès lors capturer les relations entre le rôle PERSON et tous les attributs d'une personne que vous voulez
capturer.
Par exemple, vous pouvez définir une
relation hasAttribute entre le rôle PERSON et la mention d'une entité AGE.
En revanche, comme vous avez appliqué un type d'entité GENDER et une étiquette de rôle PERSON au même mot *homme*,
vous ne pouvez pas définir de relation hasAttribute entre les deux.
Cependant, le fait que les deux étiquettes soient appliquées à la même mention les associe l'une à l'autre.
Cette association est prise en compte par le modèle d'apprentissage automatique sans que vous ayez à la définir explicitement par un
type de relation hasAttribute.


Un exemple similaire est celui où le syntagme *Ford F-150 2008* est utilisé comme
forme abrégée de *pick-up Ford F-150 de 2008*.
Ici, *Ford* est annoté comme type d'entité MANUFACTURER (constructeur),
*F-150* comme type d'entité MODEL (modèle)
et *2008* comme type d'entité MODEL_YEAR (année modèle ou millésime).
Mais avec l'omission du mot "pick-up", *F-150* représente aussi un véhicule.
Dire *le F-150*, c'est comme dire *le pick-up*.
Vous pouvez capturer cet usage en ajoutant un rôle VEHICLE à la mention en complément de son type d'entité MODEL.
Il devient dès lors possible de définir des relations hasAttribute entre le rôle VEHICLE et les mentions d'entités MANUFACTURER et
MODEL_YEAR.


### En quoi les rôles diffèrent-ils des sous-types ?

Les sous-types d'entités servent à stratifier un inventaire de types d'entités en une hiérarchie.
Par exemple, si vous teniez à distinguer 40 choses, mais qu'elles se regroupaient logiquement en 10 ensembles de 4
(SIGNES_VITAUX_TENSION, SIGNES_VITAUX_RYTHME_CARDIAQUE, MEDICAMENTS_DOSE, MEDICAMENTS_FREQUENCE_ADMIN),
vous pourriez les structurer en types et sous-types. Les menus de sélection seraient alors plus compacts, mais
cela ajouterait un niveau de profondeur et de nuisance au processus d'étiquetage.
Pour les besoins de l'extraction d'informations, une combinaison de types et de sous-types est interchangeable avec de nombreux types sans sous-types.
Par opposition, le mot ou le syntagme auquel vous appliquez un rôle est un exemple d'un type d'entité, mais
il joue le rôle d'un autre type d'entité, qui n'est pas un sous-type de l'autre.


### Comment les rôles sont-ils traités ?

Le modèle d'apprentissage automatique {{site.data.keyword.knowledgestudioshort}} définit
des étiquettes de classification pour chaque mention d'une entité qu'il trouve dans les documents source en concaténant les valeurs
type d'entité + rôle.
Lorsque vous fournissez des valeurs pour les rôles, vous créez des
étiquettes plus précises.
Chaque groupe d'instances d'un type d'étiquette trouvées dans les données d'apprentissage forme
un ensemble plus uniforme de mentions.
Mais en choisissant d'être plus précis, vous devez aussi accepter de fournir plus de données d'apprentissage
pour assurer le bon fonctionnement du modèle.
Plus vous fournirez de données d'apprentissage, meilleur sera votre modèle.
Par conséquent, si le travail d'annotation supplémentaire n'est pas un inconvénient pour vous,
l'utilisation de rôles vous permettra d'obtenir de meilleurs résultats.


Par exemple, supposons que les phrases suivantes apparaissent dans un
document source et que nous voulions capturer les mots
"Acme" (qu'on imagine être une marque d'automobile bien connue), "berline" et "pick-up" comme entités
similaires, car elles se réfèrent toutes à un véhicule physique :


- a) L'Acme a heurté le mur de béton.
- b) La berline a heurté le mur de béton.
- c) Le pick-up Acme 1-160 a heurté le mur de béton.

Vous pouvez concevoir le système de types de deux manières :


1. Définissez deux types d'entités : **MANUFACTURER** et **VEHICLE**.
Pour l'entité **MANUFACTURER**, définissez un rôle **VEHICLE** qui puisse être
utilisé en plus du rôle **MANUFACTURER** par défaut.


    Avec ce système de types, les phrases sont annotées comme ceci : 
    - a) La mention "Acme" est annotée comme entité **MANUFACTURER**, mais avec un rôle **VEHICLE**, puisqu'elle se
réfère justement à un véhicule.
Son étiquette interne est donc **MANUFACTURER-VEHICLE**.
    - b) La mention "berline" est annotée comme type d'entité **VEHICLE**. Le rôle **VEHICLE** lui est automatiquement
associé, puisqu'il n'y a aucun autre rôle de défini.

    - c) La mention "Acme" est annotée comme type d'entité **MANUFACTURER** et la mention "pick-up", comme type d'entité **VEHICLE**.
Aucun rôle spécifique ne leur est associé, et ce sont donc les rôles par défaut qui sont appliqués.


1. Définissez deux types d'entités seuls, sans rôles : **MANUFACTURER** et **VEHICLE**.


    Avec ce système de types, les phrases sont annotées comme ceci : 
    - a) La mention "Acme" est annotée comme type d'entité **VEHICLE**. 
    - b) La mention "berline" est annotée comme type d'entité **VEHICLE**. 
    - c) La mention "Acme" est annotée comme type d'entité **MANUFACTURER** et la mention "pick-up", comme type d'entité **VEHICLE**.


Alors quelles sont les performances obtenues avec les deux système de types ?
Supposons qu'un jeu de documents ait été annoté par des annotateurs humains.
Après la passe d'annotation, les événements d'entraînement suivants, qui sont des entités étiquetées manuellement, sont
identifiés dans le corpus d'entraînement :

- **Système de types 1**

    ```
    MANUFACTURER-MANUFACTURER 800 événements
    MANUFACTURER-VEHICLE 200 événements
    VEHICLE-VEHICLE 400 événements
    ```
    {: screen}

- **Système de types 2**

    ```
    MANUFACTURER 800 événements
    VEHICLE 200 + 400 = 600 événements
    ```
    {: screen}

Lorsque le modèle traitera de nouveaux documents, il est probable que "Acme" sera étiqueté
comme MANUFACTURER dans la plupart des cas, car l'orthographe d'un mot est une
caractéristique forte et le mot "Acme" sera certainement défini
dans le dictionnaire MANUFACTURER.
Il faudrait beaucoup de contexte pour l'étiqueter différemment.
Le système de types 1 contient seulement 200 événements d'entraînement
MANUFACTURER-VEHICLE ; c'est un désavantage comparé aux 600 événements de VEHICLE dans le
système de types 2. En revanche, les groupes d'événements d'entraînement
dans le système de types 1 étant tous relativement uniformes, ce système est celui qui fournira
les meilleures performances.
Dans le système de types 2, l'ensemble de 600 événements d'entraînement pour VEHICLE est en réalité
composé de deux groupes plutôt disjoints : l'un contient des noms de constructeurs automobile,
tels que "Acme" et "Ford", qui font référence à des véhicules, tandis que
l'autre contient des types de véhicules, tels que "berline", "SUV" et "pick-up".
Intuitivement, on voit que ces deux groupes pris séparément sont uniformes, mais dès qu'on les mélange, le groupe résultant est dilué et
présente un problème plus dur à résoudre.
Si vous poursuivez l'annotation et ajoutez davantage d'événements d'entraînement, les performances du système de types 1 continuent à s'améliorer,
tandis qu'avec le système de types 2,
le problème de résolution des deux groupes disjoints reste un frein à l'amélioration, même avec plus d'entraînement.

