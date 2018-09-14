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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/user-guide.html){: new_window}.
{: tip}

# Annoter des documents
{: #user-guide}

Les informations de cette section aideront les experts d'un domaine particulier, à qui on a demandé d'annoter des documents traitant de ce domaine, d'utiliser l'éditeur de données de référence pour accomplir cette tâche.
{: shortdesc}

## Accès aux espaces de travail
{: #wks_access_for_annotator}

Vous ne pouvez voir aucun espace de travail tant que quelqu'un d'autre n'en a pas créé un et ne vous y a pas donné accès.

Lorsqu'un administrateur vous ajoute à une instance de {{site.data.keyword.knowledgestudioshort}}, le rôle d'annotateur humain vous est attribué d'office. Ce rôle ne vous autorise pas à créer un espace de travail. C'est à l'administrateur de le créer et de vous y donner accès. Ensuite, l'administrateur ou un chef de projet que l'administrateur associe à l'espace de travail doit effectuer les étapes suivantes :

1. Créer un jeu d'annotations et vous y associer.
1. Créer une tâche qui vous affecte à l'annotation des documents du jeu.

Ce n'est qu'à compter du moment où une tâche d'annotation vous est affectée que vous pouvez voir l'espace de travail.

Si vous avez été invité à participer à un espace de travail {{site.data.keyword.knowledgestudioshort}} mais que vous ne voyez aucun espace de travail sur la page Espaces de travail, contactez la personne qui vous a invité et demandez-lui d'effectuer les étapes requises.

## Les bonnes pratiques d'annotation
{: #wks_anno_bp}

Ces quelques conseils et exemples vous aideront à commencer votre travail d'annotation de documents dans les meilleures conditions.

- Annotez tous les documents complètement.

    Un système à apprentissage automatique apprend autant des exemples négatifs (ce qui n'est pas annoté) de ce qui est annoté. Par conséquent, soyez judicieux dans ce que vous annotez, mais faites un travail complet. Si vous annotez soigneusement les 5 ou 10 premiers documents d'un jeu, mais moins bien les 5 derniers, le modèle apprendra à ignorer les mentions d'entités ou de relations que vous avez omis d'annoter dans la dernière série de documents. Cela pourrait vous faire perdre le bénéfice du travail soigné accompli sur les premières séries de documents.

- Une annotation cohérente est au moins aussi importante qu'une annotation correcte.

    Certaines décisions concernant les directives d'annotation sont arbitraires. Par exemple, doit-on ou non considérer le code de finition ou de motorisation comme partie du nom d'un modèle de voiture, comme dans *Camry* ou *Camry LX* ? Le choix entre les deux politiques est beaucoup moins important que le fait que tous les membres de l'équipe s'entendent sur l'une ou l'autre et annotent ensuite les documents conformément à ce qui a été convenu.

- Etiquetez les mentions d'entités en vous alignant toujours sur les limites des unités lexicales ou des mots (et non sur une partie d'une unité ou d'un mot), car c'est le niveau de granularité avec lequel fonctionne la recherche des mentions.
- Etiquetez les mentions d'entités limitées à un ou deux mots adjacents, dans la mesure du possible.

    Cela n'est pas toujours possible ni facile. Prenons ces exemples :
    - Le document source contient une phrase à partir de laquelle, pour les besoins de l'application qui utilisera le système de types, nous voulons annoter le problème et sa cause.

        ```
        Le module électronique a grillé car la mauvaise tension lui a été appliquée.
        ```
        {: screen}

        On pourrait être tenté d'annoter le problème et sa cause comme ceci :

        ```
                    [PROBLEME][CAUSE]
        ```
        {: screen}

        ```
        [Le module électronique a grillé] [car la mauvaise tension lui a été appliquée].
        ```
        {: screen}

        Toutefois, il n'est pas très judicieux d'annoter des syntagmes aussi longs comme types d'entités. Mieux vaut repérer les entités importantes et identifier comment elles sont associées l'une à l'autre en définissant une mention de relation.

        ```
               [EMPLACEMENT][SYMPTOM]                [CAUSE]
        ```
        {: screen}

        ```
        Le [module électronique] a [grillé] car la [mauvaise tension] lui a été appliquée.
        ```
        {: screen}

        ```
                      ^---isStatusOf--| |------causedBy-------^
        ```
        {: screen}

    - Dans cet autre exemple (en anglais), le document source contient un verbe à particule que l'on souhaite annoter. La base verbale (pick) et la postposition (up) ne sont pas contiguës. Comment annoter deux éléments de texte non contigus en tant que type d'entité unique ? Vous pouvez annoter chaque mention d'entité et identifier les deux mentions comme étant liées l'une à l'autre au moyen d'une mention de relation.

        ```
                  [EVENT_ANSWER][EVENT_ANSWER]
        ```
        {: screen}

        ```
        All of the phones were ringing, but he knew he should [pick] the red phone [up] first.
        ```
        {: screen}

        ```
                            ^----splitType-----^
        ```
        {: screen}

- Evitez les mentions chevauchantes, c'est-à-dire deux étiquettes de types d'entités différentes appliquées à un même syntagme dans un document. Par exemple, dans la phrase *Elle a fait don des journaux intimes de son père à la Bibliothèque JFK.*, il y aurait chevauchement de deux mentions si vous annotiez `JFK`=`PERSON` et `Bibliothèque JFK`=`LOCATION` dans le syntagme *Bibliothèque JFK*. Dans cette phrase, il est plus question de la bibliothèque que de la personne. Seule la dernière annotation devrait donc être appliquée.

    Le décodage de telles structures nécessite plusieurs invocations en parallèle du modèle d'apprentissage automatique, car le mécanisme de détection des mentions recherche seulement une unique étiquette ou l'absence d'étiquette sur chaque unité lexicale (mot).

- Déterminez comment l'équipe traitera les listes et les pluriels dans le corps d'un texte. Par exemple, le système de types KLUE comprend les types d'entités `PERSON` et `PEOPLE` qui, en anglais, distinguent le singulier du pluriel. Vous pouvez choisir d'annoter l'énumération *Barack, Michelle, Malia et Sasha Obama* de l'une des façons suivantes :

    - Annoter chaque élément de la liste comme une mention d'entité singulière (*Barack*, *Michelle*, *Malia* et *Sasha Obama* sont chacun une mention du type `PERSON`)
    - Annoter le syntagme entier comme une seule mention d'entité plurielle (*Barack, Michelle, Malia et Sasha Obama* est une unique mention du type `PEOPLE`).

    Aucune approche n'est nécessairement meilleure que l'autre. L'essentiel est que votre équipe choisisse l'une d'elles et l'applique uniformément à toutes les énumérations qui apparaissent dans les documents.

- Une coréférence est utilisée lorsque plusieurs mentions se réfèrent à la même entité du monde réel. Les relations sont utilisées entre des entités distinctes. Deux mentions ne doivent donc jamais être reliées à la fois par une coréférence et par une relation.

## Annotation avec l'éditeur de données de référence
{: #wks_hagte}

Lorsqu'un annotateur humain travaille sur un document, celui-ci est ouvert dans l'*éditeur de données de référence*. Il s'agit d'un outil visuel dont se servent les annotateurs humains pour appliquer des étiquettes au texte.

Le but de l'annotation humaine est d'étiqueter les mentions, les relations et les mentions coréférencées de sorte que le modèle d'apprentissage automatique puisse être entraîné à détecter des motifs analogues dans un texte qu'il n'a jamais vu auparavant. Vous devez au minimum utiliser l'outil pour annoter les mentions d'entités. Vous pouvez éventuellement omettre d'annoter les coréférences et les mentions de relations s'il n'est pas prévu qu'elles soient extraites par l'application qui utilisera le modèle résultant.

L'outil de concordance est utilisable en option par les annotateurs humains désireux d'accélérer l'annotation des mentions répétitives.

Choisissez le mode à utiliser lorsque vous annotez manuellement des documents :

- Mode **mention**

    Dans ce mode, l'annotateur humain associe des types d'entités, choisis parmi ceux que définit le système de types, à des mots ou syntagmes qu'il considère significatifs dans le texte. Par exemple, toutes les mentions de noms de personnes pourraient être associées à un type d'entité nommé PERSONNE (ou PERSON dans le système de types anglophone KLUE). L'annotation des mentions est indispensable et doit intervenir avant celle des types de relations et des mentions en tant que coréférences.

    L'annotateur humain peut, en option, utiliser l'outil de concordance de façon à annoter rapidement un même texte avec le même type d'entité partout dans un même document ainsi qu'entre différents jeux d'annotations.

- Mode **relation**

    Dans ce mode, l'annotateur humain relie des mentions l'une à l'autre en leur associant un type de relation qu'il choisit parmi ceux que définit le système de types. Par exemple, la mention `Jean Martin` pourrait être reliée à la mention `{{site.data.keyword.IBM_notm}}` par le type de relation `employedBy` (employé par). L'annotation des relations est optionnelle et peut intervenir avant ou après celle des mentions en tant que coréférences.

- Mode **coréférence**

    Dans ce mode, l'annotateur humain identifie les mentions qui signifient la même chose, contribuant ainsi à maintenir la cohérence des annotations lorsque les mots ne sont pas identiques. Par exemple, la mention d'`{{site.data.keyword.IBM_notm}}` dans une première phrase, puis la mention d'`International Business Machines` dans une autre phrase et enfin une autre mention d'`{{site.data.keyword.IBM_notm}}` dans une dernière phrase désignent toutes la même chose et pourraient donc être étiquetées avec le même type d'entité, tel que `ORGANIZATION`. L'annotation des mentions en tant que coréférences est optionnelle et peut intervenir avant ou après celle des types de relations.

### Astuces et conseils d'utilisation de l'éditeur
{: #wks_hagte_tips}

- Sauvegardez votre travail au fur et à mesure de son avancement.
- Si vous faites une erreur, vous pouvez appuyer sur Ctrl+Z pour annuler l'action précédente. Pour rétablir l'action après l'avoir annulée, appuyez sur Ctrl+Y. Vous pouvez annuler les 10 dernières actions effectuées pendant l'édition du document en cours. En revanche, dès que vous fermez le document, vous ne pouvez plus revenir en arrière. Les actions doivent être annulées dans l'ordre inverse. Lorsque vous souhaitez annuler une action, vous devez repasser dans le mode qui était actif au moment où vous l'avez effectuée. Les actions effectuées avec l'outil de concordance ne peuvent pas être annulées ni rétablies.

## Annoter les mentions d'entités
{: #wks_haentity}

Pour annoter les mentions d'entités, l'annotateur humain sélectionne une chaîne de texte dans le document, puis il applique une étiquette qui décrit le mieux ce que la chaîne de texte représente. Les étiquettes qui peuvent être appliquées sont les types d'entités définis dans le système de types de l'espace de travail.

### A propos de cette tâche
{: #wks_haentity_about}

Avant de commencer à annoter les mentions d'entités dans un document, il est conseillé à l'annotateur de lire celui-ci en entier. Cela peut l'aider à s'imprégner du contexte dans son ensemble et à le mémoriser. Il pourra aussi déterminer plus facilement comment les mentions d'entités peuvent être reliées les unes aux autres et prévoir celles qui devront être coréférencées dans les prochaines passes d'annotation du document.

Lorsque vous ouvrez un document pour l'annoter, vous pouvez commencer par annoter les mentions d'entités répétitives à l'aide de l'outil de concordance, puis annoter les mentions d'entités individuelles. Passez ensuite à l'annotation des mentions de relations puis à celle des coréférences, ou inversement. Vous pouvez aussi ne pas annoter les relations ni les coréférences. Seule l'annotation des mentions est obligatoire. La nécessité d'annoter également les mentions de relations et les coréférences dépendra de l'objectif de votre modèle et des besoins de votre domaine. Chaque mention d'entité est censée représenter une entité distincte tant que vous n'identifiez pas des coréférences.

#### Bon à savoir
{: #wks_haentity_tips}

- Les mentions d'entités courtes sont meilleures pour l'entraînement du modèle d'apprentissage automatique, car celui-ci a plus de facilité à reconnaître les motifs de texte courts et à leur associer les bonnes annotations.
- Si vous choisissez d'utiliser un analyseur lexical à base de dictionnaires avec l'espace de travail et que vous prévoyez d'inclure des termes composés et des signes de ponctuation dans vos données d'apprentissage, vous pouvez les ajouter à un dictionnaire, puis créer un annotateur à base de dictionnaire pour pré-annoter les occurrences de ces termes et signes. Par exemple, pour éviter que des termes incluant des signes de ponctuation, tels que Yahoo! et Dr., ne soient interprétés à tort comme la fin d'une phrase, ajoutez-les à un dictionnaire. De même, si vos données d'apprentissage comprennent des mots à traits d'union ou des acronymes alphanumériques, tels que `Hi-C` ou `MS-60-70`, ajoutez ceux-ci au dictionnaire. Pour annoter les occurrences de ces termes sans considération de leur casse, ajoutez-les en minuscules (par exemple, `hi-c`). Pour annoter des variantes graphiques, ajoutez-les en tant que formes de surface (`MS-60-70` et `MS 60 70`). 

   **Important **: cette approche est à proscrire si vous utilisez l'analyseur lexical par défaut.

### Procédure
{: #wks_haentity_procedure}

Pour annoter les mentions d'entités dans un document :

1. Connectez-vous en tant qu'annotateur humain (ou en tant qu'administrateur ayant reçu des documents à annoter). La liste des espaces de travail contenant des tâches qui vous ont été affectées s'affiche.
1. Ouvrez un espace de travail, puis cliquez sur **Modèle d'apprentissage automatique** > **Tâches d'annotation**. Les tâches d'annotation qui vous ont été affectées apparaissent.
1. Ouvrez la tâche sur laquelle vous souhaitez travailler. Les jeux d'annotations qui vous ont été affectés apparaissent.
1. Cliquez sur **Annoter** pour ouvrir le jeu d'annotations sur lequel vous voulez travailler. Les documents du jeu d'annotations sont affichés.
1. Ouvrez le document que vous voulez annoter. Par défaut, le document s'ouvre en mode **Mention**. Il s'agit du mode à utiliser pour annoter les mentions d'entités.
1. Commencez à annoter les mentions d'entités.

    1. Cliquez sur un mot du texte que vous reconnaissez comme mention d'un type d'entité particulier (parmi les types définis dans le système de types). Si la mention d'entité est composée de plusieurs mots, cliquez sur les autres mots ou faites glisser les bords du cadre de sélection pour englober tous les mots voulus.
    1. Appliquez le type d'entité souhaité en le sélectionnant dans le panneau de droite ou en utilisant le raccourci clavier correspondant.

        Si des directives d'annotation ont été préalablement connectées à l'espace de travail et que vous avez besoin d'aide pour choisir l'annotation correcte à appliquer, cliquez sur **Afficher les directives**. Il est possible que vous soyez autorisé à mettre à jour les directives d'annotation après les avoir ouvertes,
par exemple, pour ajouter des clarifications et des exemples. Cela dépend si des autorisations d'accès ont été mises en place
et vous ont été accordées sur le site où sont hébergées les directives.
        {: tip}

    1. Evitez de créer des annotations de mentions chevauchantes. Si toutefois une mention chevauchante est nécessaire, cliquez sur **Remplacer** pour l'ajouter plus facilement. Il y a chevauchement lorsque vous appliquez plusieurs étiquettes à une mention d'entité. Voici quelques suggestions :

        - Annotez *sous-développé* comme une seule mention, et non *développé* seul ou *sous* seul.
        - Ne créez pas d'annotation `PERSON` chevauchante pour la référence à *JFK* dans *JFK International Airport*. La mention *JFK International Airport* doit être considérée dans sa globalité et doit être étiquetée comme type `FACILITY` (établissement ou installation).
        - Dans un texte en anglais contenant la mention *CEOs* (PDG au pluriel), ne créez pas d'annotation `PERSON` (singulier) pour *CEO* et d'annotation `PEOPLE` (pluriel) pour *CEOs*. Annotez uniquement *CEOs* comme type d'entité `PEOPLE`.

        La présence d'un trop grand nombre de mentions chevauchantes est généralement le signe que les directives d'annotation sont ambiguës et doivent être améliorées afin de fournir de meilleurs exemples d'annotation des mots composés dans vos données source.

    1. Pour retirer une annotation que vous venez d'ajouter, appuyez sur Ctrl+Z afin d'annuler l'action. Pour retirer une annotation plus tard (lorsque l'action sera trop ancienne pour pouvoir être annulée), cliquez sur la mention et appuyez sur la touche Suppr, ou cliquez sur **Afficher les détails**, puis sur le **X** à côté du type d'entité associé à cette mention.

1. Selon le système de types, il est possible que vous puissiez configurer les attributs d'une mention d'entité, par exemple lui associer un rôle ou un sous-type d'entité ou encore une classe de mention ou un type de mention. Dans ce cas, sélectionnez la mention concernée et cliquez sur **Vue d'attributs**.

1. Cliquez sur **Sauvegarder** à tout moment pour sauvegarder votre travail.

### Que faire ensuite
{: #wks_haentity_next}

Lorsque vous avez fini d'annoter toutes les mentions d'entités et, accessoirement, toutes les mentions de relations et toutes les coréférences dans un document, faites passer celui-ci du statut **En cours** au statut **Terminé**, cliquez sur **Sauvegarder**, puis fermez le document.

Lorsque vous avez fini d'annoter tous les documents d'un jeu d'annotations et que vous les avez tous fait passer au statut **Terminé**, le statut du jeu d'annotations passe à **SOUMIS**. C'est ainsi que les chefs de projet savent qu'ils peuvent commencer à évaluer les documents sur le plan de la convergence entre annotateurs et les rejeter ou les accepter et les promouvoir au rang de données de référence.

## Annoter les mentions répétitives
{: #wks_haconcordance}

Au besoin, vous pouvez utiliser l'outil de concordance pour étiqueter plusieurs occurrences d'une mention à la fois. Cet outil vous permet d'annoter le même texte avec le même type d'entité partout dans un même document ainsi qu'entre différents jeux d'annotations. Il contribue à l'uniformité des annotations entre plusieurs documents. Par exemple, vous pouvez étiqueter individuellement chaque occurrence de la mention *chiffrement* en mode mention, ou bien vous pouvez utiliser l'outil de concordance et étiqueter d'un coup toutes les occurrences de cette mention. Dans les deux cas, le modèle apprendra du type d'entité que vous appliquez à la mention.

### A propos de cette tâche
{: #wks_haconcordance_about}

Même si l'outil de concordance est optionnel, il est conseillé de l'utiliser pour annoter les mentions qui se répètent au sein d'un document ou de plusieurs documents avant de commencer à annoter les mentions uniques document par document. Lorsque vous appliquez un type d'entité à une mention avec l'outil de concordance, le système applique ce même type d'entité à toutes les mentions identiques, remplaçant s'il le faut les types qui leur sont déjà appliqués. Pour éviter tout conflit, les attributs (tels que les rôles ou les sous-types) sont retirés des types d'entités existants lorsqu'un nouveau type d'entité est appliqué par l'outil de concordance.

### Procédure
{: #wks_haconcordance_procedure}

Pour annoter les mentions répétitives :

1. Connectez-vous en tant qu'annotateur humain (ou en tant qu'administrateur ou chef de projet ayant reçu des documents à annoter). La liste des espaces de travail contenant des tâches qui vous ont été affectées s'affiche.
1. Ouvrez un espace de travail, puis cliquez sur **Modèle d'apprentissage automatique** > **Tâches d'annotation**. Les tâches d'annotation qui vous ont été affectées apparaissent.
1. Ouvrez la tâche sur laquelle vous souhaitez travailler. Les jeux d'annotations qui vous ont été affectés apparaissent.
1. Cliquez sur **Annoter** pour ouvrir le jeu d'annotations sur lequel vous voulez travailler. Les documents du jeu d'annotations sont affichés.
1. Ouvrez le document que vous voulez annoter. Par défaut, le document s'ouvre en mode **Mention**. Il s'agit du mode à utiliser pour annoter les mentions d'entités.
1. Si vous n'avez pas encore ajouté d'annotations, ajoutez-en au moins une. Sélectionnez un mot ou un syntagme représentant une mention d'un type d'entité existant dans votre système de types et affectez-lui le type approprié. Cliquez sur **Sauvegarder** pour sauvegarder votre annotation.
1. Sélectionnez une occurrence particulière d'un texte qui se répète et que vous voulez annoter, puis cliquez sur **Concordance**.
1. Sélectionnez les documents auxquels vous souhaitez appliquer le type d'entité sélectionné. Vous pouvez créer les annotations dans tous les documents que vous avez été chargé d'annoter, dans tous les documents que vous avez commencé à annoter ou dans tous les documents que vous n'avez pas encore commencé à annoter.
1. Cliquez sur **Prévisualiser** pour voir les annotations qui seront ajoutées.

  Si vous voulez voir les annotations dans un contexte plus large, cliquez sur les icônes pour prévisualiser le contenu du document ou ouvrir celui-ci dans une nouvelle fenêtre.

1. Cliquez sur **Appliquer & Réviser** pour appliquer les types d'entités sélectionnés aux mentions dans les documents sélectionnés. Une dernière occasion vous est donnée de passer en revue les annotations qui seront ajoutées. Si une annotation ne convient pas dans un contexte particulier, vous pouvez retirer cette occurrence en cliquant sur l'icône Editer, puis en supprimant l'affectation du type d'entité à cette mention.
1. Lorsque vous êtes satisfait de la liste des annotations, cliquez sur **Revenir à Ground Truth Editor**.

### Résultats
{: #wks_haconcordance_results}

Les mentions sont annotées dans le document. Il n'existe aucun moyen de supprimer d'un coup l'ensemble des annotations que vous avez ajoutées via l'outil de concordance. Le cas échéant, vous devez les retirer une à une.

## Annoter les mentions en tant que coréférences
{: #wks_hacoref}

Pour annoter des mentions en tant que coréférences à une même entité, l'annotateur humain doit sélectionner chaque occurrence d'une mention de cette entité. Les coréférences aident un modèle à reconnaître que les entités auxquelles il est fait référence de différentes manières doivent être associées à la même entité, par exemple, le nom d'un état des Etats-Unis et son abréviation, le nom d'une société et son acronyme ou le nom d'une personne et un pronom qui se réfère à cette même personne.

### Avant de commencer
{: #wks_hacoref_prereqs}

Avant de pouvoir identifier des coréférences, vous devez annoter les mentions dans le document.

### A propos de cette tâche
{: #wks_hacoref_about}

Lorsque vous annotez des mentions en tant que coréférences, le système crée une chaîne de coréférences. La chaîne vous permet de voir toutes les mentions dans leur contexte et de vérifier que toutes les occurrences relèvent de la même entité. Par exemple, "Barack", "Michelle", "il" et "elle" sont toutes des mentions du même type d'entité, `PERSON`, mais "Barack" et "il" sont une même entité et "Michelle" et "elle" sont une autre entité. Dans cet exemple, il faudrait créer deux chaînes de coréférences.

Lorsque vous créez une chaîne de coréférences, vous devez sélectionner des mentions qui ont été étiquetées avec le même type d'entité. Il existe cependant des cas où des mentions de types différents doivent être incluses dans une même chaîne de coréférences. Pour ce faire, vous  devez créer plusieurs chaînes, puis les fusionner. Par exemple, pensez à la façon dont les gens utilisent progressivement des raccourcis pour éviter les répétitions dans le texte. Dans un rapport d'accident de la circulation, la première référence à un véhicule pourrait être "berline Honda Accord de 2004". Plus loin, l'auteur pourrait faire référence à ce même véhicule en citant seulement "Accord", puis, plus loin encore, en l'appelant simplement "véhicule". Si le système de types incluait des entrées spécifiques pour les types constructeur (ou marque), modèle et catégorie de véhicule, vous pourriez créer plusieurs chaînes de coréférences par type d'entité, puis les fusionner pour former une chaîne unifiée. La chaîne fusionnée aiderait le modèle d'apprentissage automatique à reconnaître que toutes ces mentions font référence à la même chose.

Un autre moyen de combiner les mentions de différents types d'entités est de créer une chaîne avec les mentions d'un premier type d'entité. Vous pouvez ensuite cliquer sur une mention d'un autre type d'entité, puis sur la chaîne que vous venez de créer afin d'y ajouter cette mention.

Si les directives d'annotation le préconise, vous pouvez créer des chaînes de coréférences pour les verbes ainsi que pour les noms communs si les verbes mentionnent la même instance d'une action. Par exemple, si deux mentions du verbe "chiffre" font référence à la même occurrence de chiffrement, vous pouvez coréférencer ces mentions. Mais si une mention du verbe "chiffre" est une référence générale, ou si les deux occurrences se réfèrent à deux actions de chiffrement distinctes, vous ne devez pas les coréférencer. Si deux verbes différents se réfèrent à la même occurrence d'une action, vous pouvez coréférencer les mentions de ces verbes. Par exemple, dans le passage "Il a chiffré le document et, après ce traitement, il a envoyé le fichier ... ", les mentions "chiffré" et "traitement" pourraient être coréférencées, car elles se réfèrent à la même instance d'une action.

L'essentiel est de rester cohérent. Décidez de la manière dont vous voulez que les coréférences soient annotées et indiquez-le clairement, avec des exemples, dans vos directives d'annotation.

### Procédure
{: #wks_hacoref_procedure}

Pour annoter des mentions en tant que coréférences :

1. Connectez-vous en tant qu'annotateur humain (ou en tant qu'administrateur ou chef de projet ayant reçu des documents à annoter). La liste des espaces de travail contenant des tâches qui vous ont été affectées s'affiche.
1. Ouvrez un espace de travail, puis cliquez sur **Modèle d'apprentissage automatique** > **Tâches d'annotation**. Les tâches d'annotation qui vous ont été affectées apparaissent.
1. Ouvrez la tâche sur laquelle vous souhaitez travailler. Les jeux d'annotations qui vous ont été affectés apparaissent.
1. Cliquez sur **Annoter** pour ouvrir le jeu d'annotations sur lequel vous voulez travailler. Les documents du jeu d'annotations sont affichés.
1. Ouvrez le document que vous voulez annoter. Par défaut, le document s'ouvre en mode **Mention**. Il s'agit du mode à utiliser pour annoter les mentions d'entités.
1. Cliquez sur **Coréférences**.
1. Créez une chaîne de coréférences :

    1. Déplacez-vous dans le document et cliquez sur chaque mention qui signifie la même chose et qui est étiquetée avec le même type d'entité. Par exemple, cliquez sur chaque occurrence des mentions `{{site.data.keyword.IBM_notm}}`, `International Business Machines` et `{{site.data.keyword.IBM_notm}} Corp.`, en supposant que toutes sont des mentions de la même entité du type `ORGANIZATION`.
    1. Double-cliquez sur la dernière mention que vous voulez ajouter à la chaîne. Une chaîne de coréférences est créée dans le panneau latéral. Son nom reprend la première des mentions que vous avez sélectionnées.
    1. Pour mettre en évidence toutes les mentions faisant partie d'une même chaîne afin de les examiner dans leur contexte, passez le pointeur sur le nom de cette chaîne dans le panneau latéral.

1. La **Liste de mentions uniques** affiche les termes qui ont été annotés dans le document mais qui n'ont pas été ajoutés à une chaîne. Si, parmi ces mentions, vous en repérez une qui devrait être rattachée à une chaîne, vous pouvez l'y ajouter à partir de cette liste.

    1. Dans la **Liste de mentions uniques**, dans le panneau latéral, cliquez sur la mention.
    1. Dans la liste déroulante, en dessous de la description de la mention, choisissez le numéro qui représente la chaîne à laquelle vous voulez ajouter la mention.
    1. Cliquez sur **Fusionner** pour ajouter la mention à la chaîne, puis cliquez sur **OK**.

    La mention disparaît de la **Liste de mentions uniques** et le numéro de la chaîne dont elle fait maintenant partie est affiché en dessous d'elle dans le document.

1. Vous pouvez annuler votre travail par différents moyens :

    - Pour retirer une chaîne de coréférences que vous venez d'ajouter, appuyez sur Ctrl+Z afin d'annuler l'action. 
    - Pour retirer une chaîne de coréférences plus tard (lorsque l'action sera trop ancienne pour pouvoir être annulée), dans le panneau latéral **Chaînes de coréférences**, cliquez sur le **X** en regard de la chaîne que vous voulez supprimer. 
    - Pour retirer une mention particulière de la chaîne, cliquez sur l'ID de coréférence afin d'ouvrir une fenêtre contenant la liste des mentions membres de la chaîne, puis cliquez sur le **X** en regard de la mention que vous voulez supprimer.

1. Cliquez sur **Sauvegarder** à tout moment pour sauvegarder votre travail.

### Que faire ensuite
{: #wks_hacoref_next}

Lorsque vous avez fini d'annoter toutes les mentions d'entités et, accessoirement, toutes les mentions de relations et toutes les coréférences dans un document, faites passer celui-ci du statut **En cours** au statut **Terminé**, cliquez sur **Sauvegarder**, puis fermez le document.

Lorsque vous avez fini d'annoter tous les documents d'un jeu d'annotations et que vous les avez tous fait passer au statut **Terminé**, le statut du jeu d'annotations passe à **SOUMIS**. C'est ainsi que les chefs de projet savent qu'ils peuvent commencer à évaluer les documents sur le plan de la convergence entre annotateurs et les rejeter ou les accepter et les promouvoir au rang de données de référence.

## Annoter les relations
{: #wks_harelation}

Pour annoter une mention de relation, l'annotateur humain identifie la preuve textuelle d'une relation entre deux mentions d'entités dans une phrase, puis il applique une étiquette qui décrit le mieux le type de la relation. Les étiquettes qui peuvent être appliquées sont les types de relations définis dans le système de types de l'espace de travail.

### Avant de commencer

Avant de pouvoir identifier et annoter des relations entre entités, vous devez annoter les mentions d'entités dans le document.

### A propos de cette tâche

Une mention de relation ne peut être définie que si le texte décrit explicitement la relation entre les deux mentions d'entités. Les preuves textuelles explicites peuvent être des pronoms possessifs, des constructions sujet-verbe-complément ou des appositions. Par exemple, dans la phrase suivante, la mention de relation `ownedBy` (appartient à) ne doit pas être ajoutée entre `chien` et `propriétaire`.

<pre><code>NON VALIDE : Le <u>chien</u> a reçu une récompense de son <u>propriétaire</u>.</code></pre>

La mention de relation valide se situe entre `son` et `propriétaire`, car c'est cette partie de la phrase qui définit explicitement la relation (d'appartenance) entre le chien et son propriétaire. Le mot `propriétaire` pourrait très bien désigner le propriétaire d'une maison, ou même le propriétaire d'un autre chien, mais ce texte indique clairement que le chien mentionné au début de la phrase appartient à cette personne.

<pre><code>VALIDE : Le chien a reçu une récompense de <u>son</u> <u>propriétaire</u>.</code></pre>

<pre><code>                                |ownedBy^</code></pre>

Le fait que les deux mentions d'entités et le texte définissant le type de relation entre elles doivent obligatoirement figurer dans la même phrase peut vous sembler strict. Sachez cependant que, comme dans l'exemple ci-dessus, tant que vous identifiez également les coréférences dans le document, vous pouvez identifier des mentions de relations dans les phrases où apparaissent des mots qui servent de mentions d'entités plus informelles, tels que des pronoms. Par exemple, la seconde phrase du passage `Marie est une scientifique. Elle travaille pour {{site.data.keyword.IBM_notm}}.` contient la preuve textuelle valide d'une relation `employedBy` (employée par) entre Marie et {{site.data.keyword.IBM_notm}}. La coréférence `Elle` est perçue comme une référence à l'entité `Marie` du type `PERSON`. C'est l'identification d'une coréférence entre `Marie` et `Elle` combinée à l'identification d'une mention de relation entre `Elle` et `{{site.data.keyword.IBM_notm}}` qui reflète pleinement cette relation. La façon correcte d'annoter la mention de relation est donc :

<pre><code>Marie[<i>#1</i>] est une scientifique. <u>Elle</u>[<i>#1</i>] travaille pour <u>IBM</u>.</code></pre>

<pre><code>                                |----employedBy----^</code></pre>

l'indice [<i>#1</i>] indiquant que `Marie` et `Elle` sont tous deux membres de la première chaîne de coréférences dans le document.

### Procédure

Pour annoter les mentions de relations entre mentions d'entités dans un document :

1. Connectez-vous en tant qu'annotateur humain (ou en tant qu'administrateur ou chef de projet ayant reçu des documents à annoter). La liste des espaces de travail contenant des tâches qui vous ont été affectées s'affiche.
1. Ouvrez un espace de travail, puis cliquez sur **Modèle d'apprentissage automatique** > **Tâches d'annotation**. Les tâches d'annotation qui vous ont été affectées apparaissent.
1. Ouvrez la tâche sur laquelle vous souhaitez travailler. Les jeux d'annotations qui vous ont été affectés apparaissent.
1. Cliquez sur **Annoter** pour ouvrir le jeu d'annotations sur lequel vous voulez travailler. Les documents du jeu d'annotations sont affichés.
1. Ouvrez le document que vous voulez annoter. Par défaut, le document s'ouvre en mode **Mention**. Il s'agit du mode à utiliser pour annoter les mentions d'entités.
1. Cliquez sur **Relations**.
1. Pour annoter une relation :

    1. Cliquez sur une mention d'entité dans le texte, puis, dans la même phrase, cliquez sur une seconde mention d'entité que vous voulez relier à la première mention.
    1. Appliquez le type de relation souhaité en le sélectionnant dans le panneau de droite ou en utilisant le raccourci clavier correspondant. La liste des types de relations disponibles est contrainte par la première mention d'entité que vous sélectionnez ; elle l'est encore plus par la deuxième mention d'entité sélectionnée. Dans certains cas, une fois les deux mentions d'entités sélectionnées, il ne reste plus qu'un seul choix de type de relation dans la liste. Vous devez quand même le sélectionner explicitement pour l'appliquer.

        Si des directives d'annotation ont été préalablement connectées à l'espace de travail et que vous avez besoin d'aide pour choisir l'annotation correcte à appliquer, cliquez sur **Afficher les directives**. Il est possible que vous soyez autorisé à mettre à jour les directives d'annotation après les avoir ouvertes,
par exemple, pour ajouter des clarifications et des exemples. Cela dépend si des autorisations d'accès ont été mises en place
et vous ont été accordées sur le site où sont hébergées les directives.
        {: tip}

1. Pour retirer une mention de relation que vous venez d'ajouter, appuyez sur Ctrl+Z afin d'annuler l'action. Pour retirer une mention de relation plus tard (lorsque l'action sera trop ancienne pour pouvoir être annulée), cliquez sur le type de relation et appuyez sur la touche **Suppr**, ou cliquez sur le **X** à côté du type de relation.
1. Selon le système de types, il est possible que vous puissiez configurer les attributs d'une relation, par exemple un temps, une modalité ou une classe. Dans ce cas, sélectionnez l'étiquette de relation concernée et cliquez sur **Vue d'attributs**.
1. Cliquez sur **Sauvegarder** à tout moment pour sauvegarder votre travail.

### Que faire ensuite

Lorsque vous avez fini d'annoter toutes les mentions d'entités et, accessoirement, toutes les mentions de relations et toutes les coréférences dans un document, faites passer celui-ci du statut **En cours** au statut **Terminé**, cliquez sur **Sauvegarder**, puis fermez le document.

Lorsque vous avez fini d'annoter tous les documents d'un jeu d'annotations et que vous les avez tous fait passer au statut **Terminé**, le statut du jeu d'annotations passe à **SOUMIS**. C'est ainsi que les chefs de projet savent qu'ils peuvent commencer à évaluer les documents sur le plan de la convergence entre annotateurs et les rejeter ou les accepter et les promouvoir au rang de données de référence.

## Informations connexes

[Créer des dictionnaires](/docs/services/watson-knowledge-studio/dictionaries.html)

[Remédier aux problèmes d'utilisation de l'éditeur de données de référence](/docs/services/watson-knowledge-studio/user-guide-help.html)

[Etablir un système de types](/docs/services/watson-knowledge-studio/typesystem.html)
