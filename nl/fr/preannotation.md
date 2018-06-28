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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/preannotation.html){: new_window}.
{: tip}

# Amorcer le processus d'annotation
{: #preannotation}

Simplifiez le travail de l'annotateur humain en pré-annotant les documents dans un espace de travail. Un pré-annotateur est un dictionnaire, modèle à base de règles ou modèle d'apprentissage automatique {{site.data.keyword.knowledgestudioshort}} que vous pouvez exécuter pour trouver et annoter automatiquement les mentions.
{: shortdesc}

La pré-annotation facilite le travail des annotateurs humains parce qu'elle couvre les annotations simples et permet de mettre en route le travail d'annotation des documents.

La méthode utilisée pour pré-annoter les documents ne restreint en aucune manière la façon dont vous pouvez utiliser le modèle résultant. Par exemple, ce n'est pas parce que vous utilisez le service {{site.data.keyword.nlushort}} pour pré-annoter les documents que vous devrez ensuite déployer sur ce même service le modèle d'apprentissage automatique que vous aurez construit à partir de ces documents. La pré-annotation ne sert qu'à mettre en route le processus d'annotation humaine.

## Remarques importantes

- Ne lancez jamais un pré-annotateur sur des documents que les annotateurs humains ont commencé à annoter, car tout ce qu'ils ont fait jusqu'ici serait supprimé.
- Vous ne pouvez exécuter qu'un seul pré-annotateur sur les documents. Si vous en exécutez deux l'un derrière l'autre, le second supprimera les annotations ajoutées par le premier. Choisissez la méthode de pré-annotation qui convient le mieux à votre cas d'utilisation, et n'utilisez que cette méthode.

## Méthodes de pré-annotation

Les pré-annotateurs suivants sont disponibles :
>**Remarque **: Le service {{site.data.keyword.alchemylanguageshort}} a été déprécié. Pour plus d'informations, consultez [Retirement of {{site.data.keyword.alchemyapishort}} service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}.

- **{{site.data.keyword.nlushort}}**

    Pré-annotateur que vous pouvez utiliser pour trouver automatiquement les mentions d'entités dans vos documents. C'est un bon choix de pré-annotateur si vos documents source contiennent des connaissances générales dans le domaine concerné. Si vous travaillez avec des documents hautement spécialisés qui se concentrent sur un domaine spécifique, tel que la recherche en droit des brevets, le pré-annotateur à base de dictionnaire ou un modèle à base de règles pourraient être de meilleurs choix.

- **Dictionnaire**

    Utilise un dictionnaire de termes que vous fournissez et associez à un type d'entité pour trouver les mentions de ce type d'entité dans les documents. C'est le meilleur choix de pré-annotateur pour les domaines utilisant une terminologie unique ou spécialisée, car contrairement au pré-annotateur à base de modèle d'apprentissage automatique, il n'analyse pas le contexte dans lequel le terme est utilisé. Il repose plutôt sur le fait que le terme est suffisamment distinct pour avoir un sens déchiffrable quel que soit le contexte dans lequel il apparaît. Par exemple, il est plus facile de reconnaître *amiante* comme un type d'entité minéral que de déterminer le type d'entité de *voile*, qui peut faire référence à l'étoffe servant à cacher, au moyen de propulsion d'un navire ou à la forme conjuguée du verbe voiler.

- **Apprentissage automatique**

    Utilise un modèle d'apprentissage automatique pour annoter automatiquement les documents. Cette option ne vous est proposée que dans la mesure où un modèle d'apprentissage automatique a déjà été créé avec {{site.data.keyword.knowledgestudioshort}}. Dans ce cas, vous pouvez utiliser ce modèle existant pour pré-annoter un nouveau jeu de documents. Si le nouveau jeu de documents est similaire aux documents qui ont servi à entraîner le modèle, celui-ci est certainement votre meilleur choix de pré-annotateur.

- **Règle**

    Utilise un modèle à base de règles pour annoter automatiquement les documents. Cette option ne vous est proposée que dans la mesure où un modèle à base de règles a déjà été créé avec {{site.data.keyword.knowledgestudioshort}}. Si vos documents contiennent des motifs communs d'unités lexicales à partir desquels il est possible de dériver un sens, ce modèle pourrait être un bon choix de pré-annotateur. Il peut incorporer une partie de la fonction du pré-annotateur à base de dictionnaire (si vous l'activez) en identifiant par leur type de classe les termes du dictionnaire qu'il trouve dans les documents.

Vous pouvez également transférer des documents déjà annotés et les utiliser pour démarrer l'entraînement du modèle d'apprentissage automatique. Vous ne pouvez pas exécuter un pré-annotateur sur des documents annotés que vous transférez, sous peine de supprimer toutes les annotations existantes de ces documents et de les remplacer exclusivement par celles du pré-annotateur.

> **Remarque :** Il est *possible* d'exécuter un pré-annotateur sur des documents qui ont été ajoutés aux données de référence de l'espace de travail en cours. Cela ne supprimera pas les annotations qui, après avoir été ajoutées à ces documents, ont été révisées, acceptées et promues au rang de données de référence dans l'espace de travail en cours.

## Pré-annoter des documents avec {{site.data.keyword.nlushort}}
{: #wks_preannotnlu}

Vous pouvez utiliser le service {{site.data.keyword.nlushort}} pour pré-annoter les documents que vous ajoutez à votre corpus.

### Avant de commencer

Déterminez si le pré-annotateur {{site.data.keyword.nlushort}} est susceptible d'ajouter de la valeur à votre cas d'utilisation. Passez en revue la liste des types et sous-types d'entités pris en charge par le service [{{site.data.keyword.nlushort}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/natural-language-understanding/entity-types.html){: new_window} afin de déterminer s'il existe un recoupement naturel entre eux et les types de votre système de types. Dans l'affirmative, continuez avec cette procédure. Sinon, choisissez un pré-annotateur différent.

### A propos de cette tâche

{{site.data.keyword.nlushort}} est un service d'analyse de texte utilisant le traitement automatique du langage naturel. Lorsque vous utilisez le pré-annotateur {{site.data.keyword.nlushort}}, celui-ci appelle le service {{site.data.keyword.nlushort}} pour trouver et annoter les entités dans vos documents.

Vous devez spécifier quels types d'entités le service doit rechercher en associant des types d'entités {{site.data.keyword.nlushort}} aux types d'entités {{site.data.keyword.knowledgestudioshort}} correspondants que vous avez ajoutés au système de types {{site.data.keyword.knowledgestudioshort}}. Seules les mentions des types d'entités que vous associez de cette manière seront trouvées et annotées.

### Procédure

Pour pré-annoter des documents à l'aide du service {{site.data.keyword.nlushort}}, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez l'onglet **Actifs & Outils** > **Pré-annotateurs** > **Natural Language Understanding**.
1. Cliquez sur **Editer** pour associer chaque type d'entité défini sur la page **Types d'entités** au type d'entité qui lui correspond dans {{site.data.keyword.nlushort}}.

    - La liste déroulante des types d'entités {{site.data.keyword.nlushort}} est préremplie avec les types d'entités reconnus par le service {{site.data.keyword.nlushort}}.
    - Vous devez associer au moins un type d'entité.
    - Un type d'entité {{site.data.keyword.nlushort}} ne peut être associé qu'à un ou plusieurs types d'entités {{site.data.keyword.knowledgestudioshort}}, et non à un rôle d'entité {{site.data.keyword.knowledgestudioshort}}.
    - Il est possible d'associer plusieurs types d'entités {{site.data.keyword.nlushort}} à un seul type d'entité {{site.data.keyword.knowledgestudioshort}}, ou l'inverse. Par exemple, les association suivantes sont possibles :

    <table cellpadding="4" cellspacing="0" summary="Exemples d'associations de types d'entités" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d20428e292" class="stentry thleft thbot">Type d'entité Watson Knowledge Studio</th>
        <th valign="bottom" align="left" id="d20428e298" class="stentry thleft thbot">Type d'entité {{site.data.keyword.nlushort}}</th>
      </tr>
      <tr class="strow"><td valign="top" headers="d20428e292" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ENGINEER</p></li>
            <li class="li"><p class="p wrapper">SCIENTIST</p></li>
          </ul>
        </td>
        <td valign="top" headers="d20428e298" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Person</p></li>
          </ul></td>
      </tr>
      <tr class="strow"><td valign="top" headers="d20428e292" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">LOCATION</p></li></td>
        <td valign="top" headers="d20428e298" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">CityTown</p></li>
            <li class="li"><p class="p wrapper">Country</p></li>
          </ul>
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. Après avoir créé toutes les associations de types d'entités voulues, cliquez sur **Appliquer ce pré-annotateur**.

    Le bouton **Appliquer ce pré-annotateur** n'est disponible qu'à compter du moment où vous associez au moins un type d'entité.

1. Cochez la case de chaque jeu de documents que vous voulez pré-annoter.

    Si vous exécutez ce pré-annotateur pour la première fois, vérifiez d'abord qu'il trouve comme prévu les mentions des entités associées. Créez un jeu de documents contenant un ou plusieurs documents représentatifs de chaque source de données distincte.
    {: tip}

1. Cliquez sur **Exécuter**.

    Si vous êtes en train de valider le fonctionnement du pré-annotateur, ouvrez les documents annotés et examinez les annotations qui viennent d'être ajoutées. Assurez-vous qu'un nombre suffisant d'annotations exactes ont été créées. Si c'est le cas, vous pouvez exécuter l'annotateur sur des jeux de documents à la fois plus gros et plus nombreux. Si un trop grand nombre d'annotations sont inexactes, il faut peut-être revoir les associations entre vos propres types d'entités et ceux de {{site.data.keyword.nlushort}}. S'il n'y a pas de chevauchement naturel entre les types des deux environnements, c'est que le pré-annotateur {{site.data.keyword.nlushort}} n'est pas le plus adapté à votre cas d'utilisation.

    La pré-annotation est appliquée individuellement à chaque document, sans qu'il soit tenu compte des jeux de documents auxquels il appartient. Un document constituant un chevauchement entre un jeu sélectionné et un jeu non sélectionné sera pré-annoté dans les deux jeux.

1. Après avoir exécuté le pré-annotateur une première fois, vous pouvez cliquer à nouveau sur **Appliquer ce pré-annotateur** chaque fois que vous voulez l'utiliser pour pré-annoter d'autres jeux de documents que vous ajoutez au corpus.

    > **Restriction :** Si vous modifiez la définition des associations de types du pré-annotateur {{site.data.keyword.nlushort}}, vous devrez recréer toutes les tâches d'annotation qui incluaient des jeux de documents pré-annotés avec ce pré-annotateur. En effet, il n'est pas possible d'appliquer à des jeux de documents déjà affectés à une tâche d'annotation une pré-annotation fondée sur les changements que vous apportez à la définition des associations.

### Résultats
{: #wks_preannotnlu__export-warning}

Les données de référence produites par les documents qui ont été pré-annotés par le service {{site.data.keyword.nlushort}} ne peuvent pas être utilisées directement en dehors de {{site.data.keyword.knowledgestudioshort}}. Vous pouvez les télécharger (sous une forme non lisible) pour les déplacer d'un espace de travail {{site.data.keyword.knowledgestudioshort}} vers un autre. Vous pouvez aussi continuer à les développer et les utiliser pour construire un modèle d'apprentissage automatique ou un modèle à base de règles qui puisse être déployé pour être utilisé dans des services extérieurs à {{site.data.keyword.knowledgestudioshort}}.

> **Restriction :** Les documents qui ont été pré-annotés avec {{site.data.keyword.nlushort}} sont obscurcis de manière à être rendus illisibles lorsqu'ils sont téléchargés. Toutes les annotations sont obscurcies, y compris celles qui ont été ajoutées aux documents par des annotateurs humains.

**Informations associées** :

[{{site.data.keyword.nlushort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## Pré-annoter des documents avec un dictionnaire
{: #wks_preannot}

Pour aider les annotateurs humains à commencer les tâches d'annotation qui leur sont attribuées, vous pouvez créer un dictionnaire et l'utiliser pour pré-annoter les documents que vous ajoutez au corpus.

### A propos de cette tâche

Lorsqu'un annotateur humain commence à travailler sur des documents qui ont été pré-annotés, un certain nombre de mentions sont probablement déjà annotées avec des types d'entités fondés sur les entrées du ou des dictionnaires utilisés. L'annotateur humain est libre de changer ou de supprimer les types d'entités affectés aux mentions et d'en affecter aux mentions qui n'ont pas été annotées. La pré-annotation au moyen d'un dictionnaire n'annote pas les relations ni les coréférences. C'est donc aux annotateurs humains de les annoter.

**Remarque **: Cette tâche vous montre comment créer un dictionnaire qui puisse être édité. Si vous voulez transférer et pré-annoter vos documents avec un dictionnaire en lecture seule, cliquez sur le bouton **Transférer un dictionnaire**, sous l'onglet **Actifs & Outils** > **Pré-annotateurs** > **Dictionnaires**.

### Procédure

Pour créer un dictionnaire éditable et pré-annoter des documents avec lui :

1. Connectez-vous en tant qu'administrateur {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez l'onglet **Actifs & Outils** > **Pré-annotateurs** > **Dictionnaires**.
1. Cliquez sur **Gérer les dictionnaires**, puis sur **Créer un dictionnaire**.
1. Dans la liste **Type d'entité**, sélectionnez un type d'entité à associer au dictionnaire.
1. Ajoutez des entrées au dictionnaire ou transférez un fichier contenant les termes du dictionnaire.
1. Retournez à la page **Pré-annotateurs** et, sous l'onglet **Dictionnaires**, cliquez sur **Appliquer ce pré-annotateur**.
1. Cochez la case de chaque jeu de documents que vous voulez pré-annoter, puis cliquez sur **Exécuter**.

    La pré-annotation est appliquée individuellement à chaque document, sans qu'il soit tenu compte des jeux de documents auxquels il appartient. Un document constituant un chevauchement entre un jeu sélectionné et un jeu non sélectionné sera pré-annoté dans les deux jeux.

1. Une fois le dictionnaire créé, après l'avoir exécuté comme pré-annotateur une première fois, vous pouvez cliquer à nouveau sur **Exécuter** chaque fois que vous voulez l'utiliser pour pré-annoter d'autres jeux de documents que vous ajoutez au corpus.

    > **Restriction :** Si vous modifiez le dictionnaire pour y ajouter ou en supprimer des entrées, vous devrez recréer toutes les tâches d'annotation qui incluaient des jeux de documents ayant été pré-annotés avec ce pré-annotateur. En effet, il n'est pas possible d'appliquer à des jeux d'annotations déjà affectés à une tâche d'annotation une pré-annotation fondée sur les changements que vous apportez à l'annotateur à base de dictionnaire.

**Informations associées** :

[Dictionnaires](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries)

[Initiation > Ajouter un dictionnaire](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## Pré-annoter des documents avec le modèle d'apprentissage automatique
{: #wks_preannotsire}

Vous pouvez utiliser un modèle d'apprentissage automatique existant pour pré-annoter les documents que vous ajoutez à votre corpus.

### A propos de cette tâche

Lorsque de 10 à 30 documents ont été annotés, les données de référence correspondantes peuvent servir à entraîner un modèle d'apprentissage automatique. Un modèle si peu entraîné ne doit pas être utilisé en production, mais il est possible de l'exploiter comme modèle de pré-annotation pour accélérer l'annotation humaine des documents subséquents. Par exemple, si vous ajoutez des documents au corpus après avoir entraîné un modèle d'apprentissage automatique, vous pouvez utiliser celui-ci pour pré-annoter les nouveaux jeux de documents que vous ajoutez. N'exécutez jamais un pré-annotateur sur des documents qui ont été annotés par une personne. Les pré-annotateurs suppriment toutes les annotations humaines.

### Procédure

Pour utiliser un modèle d'apprentissage automatique existant afin de pré-annoter des documents :

1. Connectez-vous en tant qu'administrateur {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez l'onglet **Gestion des modèles** > **Versions** > **Apprentissage automatique**.
1. Cliquez sur **Exécuter ce modèle**.
1. Cochez la case de chaque jeu de documents que vous voulez pré-annoter, puis cliquez sur **Exécuter**.

    La pré-annotation est appliquée individuellement à chaque document, sans qu'il soit tenu compte des jeux de documents auxquels il appartient. Un document constituant un chevauchement entre un jeu sélectionné et un jeu non sélectionné sera pré-annoté dans les deux jeux.

1. Après avoir exécuté le modèle une première fois pour pré-annoter les premiers jeux de documents, vous pouvez cliquer à nouveau sur **Exécuter ce modèle** chaque fois que vous voulez l'utiliser pour pré-annoter d'autres jeux de documents que vous ajoutez au corpus.

## Pré-annoter des documents avec le modèle à base de règles
{: #wks_preannotrule}

Vous pouvez utiliser un modèle à base de règles existant pour pré-annoter les documents que vous ajoutez à votre corpus.

### Procédure

Pour pré-annoter des documents à l'aide du modèle à base de règles, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez l'onglet **Gestion des modèles** > **Versions** > **A base de règles**.
1. Si ce n'est déjà fait, cliquez sur **Mapper les types d'entité et les classes** pour associer les types d'entités que vous avez définis dans votre système de types {{site.data.keyword.knowledgestudioshort}} à une ou plusieurs classes du modèle à base de règles.

    - La liste déroulante de la colonne **Nom de la classe** est préremplie avec les noms des classes associées au modèle à base de règles.
    - Vous devez associer au moins un type d'entité à une classe.

1. Sous l'onglet **A base de règles**, cliquez sur **Exécuter ce modèle**, puis sélectionnez les jeux de documents ou jeux d'annotations que vous voulez pré-annoter. Assurez-vous que les jeux choisis ne contiennent pas de documents avec des annotations humaines. Les pré-annotateurs suppriment toutes les annotations humaines.

    Le bouton **Exécuter ce modèle** n'est disponible qu'à compter du moment où vous associez au moins un type d'entité à une classe.

1. Cochez la case de chaque jeu de documents que vous voulez pré-annoter.
1. Cliquez sur **Exécuter**.

    La pré-annotation est appliquée individuellement à chaque document, sans qu'il soit tenu compte des jeux de documents auxquels il appartient. Un document constituant un chevauchement entre un jeu sélectionné et un jeu non sélectionné apparaîtra pré-annoté dans les deux jeux.

1. Après avoir exécuté le modèle une première fois pour pré-annoter les premiers jeux de documents, vous pouvez cliquer à nouveau sur **Exécuter ce modèle** chaque fois que vous voulez l'utiliser pour pré-annoter d'autres jeux de documents que vous ajoutez au corpus.

    > **Restriction :** Si vous modifiez les associations entre types d'entités et classes du modèle à base de règles, vous devrez recréer toutes les tâches d'annotation qui incluaient des jeux de documents pré-annotés avec ce pré-annotateur. En effet, il n'est pas possible d'appliquer à des jeux de documents déjà affectés à une tâche d'annotation une pré-annotation fondée sur les changements que vous apportez à la définition des associations.

## Transférer des documents pré-annotés
{: #wks_uima}

Vous pouvez accélérer l'entraînement de votre modèle en transférant des documents ayant été pré-annotés par un moteur d'analyse UIMA (Unstructured Information Management Architecture).

Les documents ainsi pré-annotés doivent être dans la forme de sérialisation XMI de la structure CAS (Common Analysis Structure) UIMA. Le fichier ZIP que vous transférez doit inclure le fichier descripteur du système de types UIMA ainsi qu'un fichier associant les types UIMA aux types d'entités de votre système de types {{site.data.keyword.knowledgestudioshort}}.

UIMA CAS XMI est un format standard d'Apache UIMA. Des consignes sont fournies sur la manière de créer des fichiers dans le format correct à partir de collections analysées dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer. Si vous utilisez une autre implémentation d'Apache UIMA, adaptez ces consignes à votre cas. Peu importe de quelle manière vous créez les fichiers XMI : les conditions à remplir pour créer le fichier d'association des systèmes de types et le fichier ZIP sont les mêmes pour tous.

Si vous affectez les documents importés à des annotateurs humains, ils apparaîtront pré-annotés dans l'éditeur de données de référence et un certain nombre de mentions seront peut-être déjà annotées. Les annotateurs humains peuvent ainsi consacrer plus de temps à appliquer les directives d'annotation aux mentions qui ne sont pas encore annotées. Vous pouvez aussi passer outre l'étape d'annotation humaine et utiliser les documents pré-annotés pour commencer immédiatement l'entraînement et l'évaluation d'un modèle d'apprentissage automatique.

### Exporter des documents analysés de Watson Explorer Content Analytics
{: #wks_uimawexca}

Vous pouvez exporter des documents qui ont été explorés et analysés dans {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics et les transférer sous forme de fichiers XMI dans un espace de travail {{site.data.keyword.knowledgestudioshort}}.

#### Procédure

Pour récupérer des documents analysés d'une collection {{site.data.keyword.watson}} Explorer Content Analytics :

1. Ouvrez la console d'administration de Content Analytics dans un navigateur web.
1. Dans la vue Collections, développez la collection dont vous souhaitez exporter des documents. Dans le panneau Analyse syntaxique et index, vérifiez que le processus d'analyse syntaxique et d'indexation est en cours d'exécution, puis cliquez sur l'icône fléchée de l'option **Exporter les métadonnées et les contenus des documents analysés**.
1. Dans la section **Options d'exportation des documents analysés**, sélectionnez **Exporter les documents en tant que fichiers XML**, cochez la case **Activer CAS comme exportation au format XMI**, spécifiez le chemin de sortie, c'est-à-dire l'endroit où les données exportées devront être écrites, puis cliquez sur **OK**.
1. Arrêtez puis redémarrez les services d'analyse syntaxique et d'indexation, puis effectuez l'une des étapes suivantes :

    - Si la collection contient déjà dans son cache des documents indexés que vous voulez utiliser pour entraîner le modèle d'apprentissage automatique, redémarrez une construction complète de l'index.
    - Si la collection ne contient pas de documents indexés parmi ceux que vous voulez utiliser pour entraîner le modèle d'apprentissage automatique, transférez les documents, configurez au moins un moteur d'exploration (crawler) pour explorer les documents, puis démarrez-le.

1. Dans la section **Exporter**, vérifiez le statut de la demande d'exportation. Le nombre de documents exportés est indiqué.
1. Allez dans le dossier de sortie que vous avez spécifié lors de la configuration des options d'exportation. Lorsque les documents sont exportés comme fichiers XML, le nom du dossier de sortie contient l'horodatage du moment où a eu lieu l'exportation. Le dossier de sortie contient les fichiers XMI (`*.xmi`) et le fichier descripteur du système de types UIMA (`exported_typesystem.xml`).

#### Que faire ensuite
{: #wks_uimawexca__preUIMAimport}

Vous devez définir une association (mappage) entre les types UIMA et les types d'entités {{site.data.keyword.knowledgestudioshort}}. Vous devez aussi créer un fichier ZIP contenant tous les fichiers nécessaires au transfert des données analysées dans un espace de travail {{site.data.keyword.knowledgestudioshort}}.

**Informations associées** :

[Exporting crawled or analyzed documents ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[Output paths for exported documents ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### Exporter une collection analysée de Content Analytics Studio
{: #wks_uimawexstudio}

Vous pouvez exporter une collection de documents analysés de {{site.data.keyword.watson}} Explorer Content Analytics Studio et transférer ces documents sous forme de fichiers XMI dans un projet {{site.data.keyword.knowledgestudioshort}}.

#### Procédure

Pour récupérer des documents analysés d'une collection Content Analytics Studio :

1. Lancez Content Analytics Studio et ouvrez le projet Studio.
1. Faites un clic droit sur le dossier contenant les documents que vous voulez utiliser pour entraîner un modèle d'apprentissage automatique, puis choisissez **Analyze Collection**.
1. Sélectionnez un fichier de configuration de pipeline UIMA.
1. Allez dans la vue Collection Analysis et cliquez sur son icône **Save**. Spécifiez le dossier dans lequel doivent être écrits les résultats sauvegardés, ainsi que le nom de fichier.
1. Ouvrez le dossier que vous avez spécifié. L'extension de fichier du fichier sauvegardé est `.annotations`.
1. Copiez le fichier `.annotations` dans votre système de fichiers local en le renommant de `.annotations` en `.zip`.
1. Extrayez tous les fichiers du fichier ZIP. Le contenu extrait inclut les fichiers XMI (`*.xmi`), le fichier descripteur du système de types UIMA (`TypeSystem.xml`) et d'autres fichiers.

#### Que faire ensuite

Vous devez définir une association (mappage) entre les types UIMA et les types d'entités {{site.data.keyword.knowledgestudioshort}}. Vous devez aussi créer un fichier ZIP contenant tous les fichiers nécessaires au transfert des données analysées dans un espace de travail {{site.data.keyword.knowledgestudioshort}}.

### Associer les types UIMA aux types d'entités
{: #wks_uimawexmap}

Avant de transférer des fichiers XMI dans un espace de travail {{site.data.keyword.knowledgestudioshort}}, vous devez définir les associations (mappages) entre types UIMA types et types d'entités {{site.data.keyword.knowledgestudioshort}}.

#### Avant de commencer

Dans votre espace de travail {{site.data.keyword.knowledgestudioshort}}, le système de types doit inclure les types d'entités auxquels vous souhaitez associer les types UIMA.

#### Procédure

Pour associer des types UIMA aux types d'entités {{site.data.keyword.knowledgestudioshort}} :

1. Créez un fichier nommé `cas2di.tsv` dans le dossier qui contient le fichier descripteur du système de types UIMA, tel que `exported_typesystem.xml` ou `TypeSystem.xml`.
1. Ouvrez le fichier `cas2di.tsv` dans un éditeur de texte. Chaque ligne du fichier doit spécifier une unique association. Le format de l'association à créer dépend de la nature de l'annotateur dont vous souhaitez associer les types d'entités :

    - Vous pouvez créer des associations en utilisant le format de base :

        `nom_type_UIMA[TABULATION]type_entité_WKS`

        L'exemple suivant définit des associations entre certains types UIMA produits par l'annotateur Named Entity Recognition dans {{site.data.keyword.watson}} Explorer Content Analytics et des types d'entités faisant partie d'un système de types {{site.data.keyword.knowledgestudioshort}} :

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        Voici un autre exemple définissant cette fois l'association entre des types UIMA produits par l'annotateur personnalisé ayant été créé dans {{site.data.keyword.watson}} Explorer Content Analytics Studio et des types d'entités {{site.data.keyword.knowledgestudioshort}} :

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - Les associations que vous créez peuvent être basées sur les facettes utilisées dans les annotateurs Pattern Matcher ou Dictionary Lookup de {{site.data.keyword.watson}} Explorer Content Analytics. Dans les fichiers de règles d'analyse de texte (`*.pat`), la facette est représentée par l'attribut 'category'. Pour définir un association, utilisez la syntaxe suivante :

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={CHEMIN_FACETTE}[TABULATION]{TYPE_ENTITE_WKS}
        ```
        {: screen}

        Dans l'exemple suivant, valable pour les annotateurs Pattern Matcher et Dictionary Lookup, on définit une association entre la catégorie $.mykeyword.product et le type d'entité PRODUCT du système de types {{site.data.keyword.knowledgestudioshort}} :

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### Que faire ensuite

Vous devez créer un fichier ZIP contenant tous les fichiers nécessaires au transfert des données analysées dans un espace de travail {{site.data.keyword.knowledgestudioshort}}.

**Informations associées** :

[Annotateur Pattern Matcher ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[Annotateur Dictionary Lookup ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[Annotateur Named Entity Recognition ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### Transférer des fichiers XMI au format UIMA CAS dans un espace de travail
{: #wks_uimaweximport}

Pour entraîner un modèle avec les documents pré-annotés que vous avez téléchargés, vous devez créer un fichier ZIP contenant tous les fichiers nécessaires au transfert des fichiers XMI, puis transférer ce fichier ZIP dans un espace de travail {{site.data.keyword.knowledgestudioshort}}.

#### Avant de commencer

Avant de transférer le fichier ZIP, assurez-vous que le système de types dans votre espace de travail {{site.data.keyword.knowledgestudioshort}} inclut bien les types d'entités auxquels vous avez associé les types UIMA.

> **Avertissement :** Les moteurs d'analyse UIMA permettent aux annotations de s'étendre sur plusieurs phrases. Or, dans {{site.data.keyword.knowledgestudioshort}}, chaque annotation doit être confinée dans une même phrase. Si les fichiers XMI que vous transférez incluent des annotations qui franchissent les limites d'une phrase, celles-ci n'apparaîtront pas dans l'éditeur de données de référence.

#### Procédure

Pour transférer des documents pré-annotés dans un espace de travail {{site.data.keyword.knowledgestudioshort}} :

1. Créez un fichier ZIP contenant tous les fichiers nécessaires à {{site.data.keyword.knowledgestudioshort}}.

    1. Sélectionnez le dossier contenant les fichiers XMI, le fichier descripteur du système de types UIMA et le fichier `cas2di.tsv`, ou bien sélectionnez tous les fichiers de ce dossier.
    1. Créez un fichier ZIP incluant tous les fichiers. Veillez à ce que le fichier `cas2di.tsv` et le fichier descripteur du système de types UIMA soient stockés à la racine du fichier ZIP. S'ils sont stockés dans un sous-dossier du fichier ZIP, {{site.data.keyword.knowledgestudioshort}} ne pourra pas les lire et rien ne sera importé.

        Sous Windows, vous pouvez faire un clic droit et sélectionner **Envoyer vers** > **Dossier compressé**.

1. Transférez le fichier ZIP dans un espace de travail {{site.data.keyword.knowledgestudioshort}}.

    1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}}, ouvrez l'espace de travail auquel vous souhaitez ajouter les documents, puis ouvrez la page **Actifs & Outils** > **Documents**.
    1. Cliquez sur **Transférer des jeux de documents**.
    1. Faites glisser le fichier ZIP que vous avez créé ou cliquez pour le localiser et le sélectionner.
    1. Cochez la case pour indiquer que le fichier ZIP contient des fichiers au format UIMA CAS XMI.
    1. Cliquez sur **Transférer**.
