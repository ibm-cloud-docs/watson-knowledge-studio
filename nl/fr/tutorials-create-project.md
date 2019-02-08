---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}.
{: tip}

# Initiation à {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

Ce tutoriel {{site.data.keyword.knowledgestudiofull}} vous aide à accomplir certaines tâches préalables sans lesquelles vous ne pouvez pas commencer les autres tutoriels.
{: shortdesc}

## Avant de commencer
{: #prereq}

- Vérifiez que vous utilisez un navigateur pris en charge. Consultez à cet effet [Navigateur nécessaire](/docs/services/watson-knowledge-studio/system-requirements.html).
-  Pour suivre ce tutoriel, vous devez avoir au moins un ID utilisateur qui soit utilisable dans {{site.data.keyword.knowledgestudioshort}}. Cet ID utilisateur doit avoir le rôle Admin. Si vous vous inscrivez à un plan Lite, en tant que seul utilisateur, vous aurez le rôle Admin. Pour des informations sur les rôles d'utilisateur, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

## Créer une instance de service
{: #instance}

1. Si ce n'est déjà fait, [inscrivez-vous pour obtenir un {{site.data.keyword.ibmid}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window} et connectez-vous à {{site.data.keyword.cloud_notm}}.
1. A partir de la [page des services {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/watson/services){: new_window}, cliquez sur la vignette {{site.data.keyword.knowledgestudioshort}} et inscrivez-vous à un plan.
1. Après vous être inscrit à un plan, à partir de la liste des services existants, lancez {{site.data.keyword.knowledgestudioshort}}.

## Leçon 1 : attribuer des rôles aux utilisateurs
{: #wks_tutless1}

Au cours de cette leçon, vous allez découvrir les différents rôles qu'il est possible d'attribuer aux utilisateurs dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche
{: #wks_tutless1_about}

La création d'un modèle d'apprentissage automatique nécessite le concours d'experts du domaine, de chefs de projet et d'utilisateurs capables de comprendre et d'interpréter les modèles statistiques. Les administrateurs attribuent un rôle à chaque utilisateur afin que celui-ci ait les autorisations nécessaires pour accomplir les tâches qui lui incombent. Pour plus d'informations sur les rôles d'utilisateur, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

### Procédure
{: #wks_tutless1_procedure}

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} avec votre ID d'administrateur. Si vous avez une instance existante de {{site.data.keyword.knowledgestudioshort}}, vous pouvez la localiser à partir de la [page des services {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/watson/services){: new_window}.
1. Cliquez sur l'icône Paramètres pour ouvrir la page Détails du service. Celle-ci contient la liste de tous les ID utilisateur enregistrés comme utilisateurs de {{site.data.keyword.knowledgestudioshort}}. Chaque ID utilisateur a l'un des rôles suivants (par ordre décroissant de pouvoirs) :

    - Admin
    - Chef de projet
    - Annotateur humain

    Pour des informations sur les rôles d'utilisateur, consultez [Rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Vérifiez qu'au moins un utilisateur a le rôle Admin. Tout ID utilisateur ayant ce rôle peut créer des espaces de travail et agir en tant que chef de projet ou annotateur humain.
1. Si vous avez accès à d'autres ID utilisateur, vérifiez qu'au moins deux d'entre eux ont le rôle Annotateur humain.

    > **Remarque :** La création d'un modèle de la vie réelle fait généralement intervenir plusieurs annotateurs humains en plus d'un administrateur ou d'un chef de projet. Cependant, pour les besoins de ce tutoriel, vous pouvez continuer avec un seul ID utilisateur.

1. Au besoin, changez le rôle attribué à un ID utilisateur. Dans la colonne **Action** de la table, cliquez sur le lien **Editer** et changez le rôle attribué à l'utilisateur.

    > **Remarque :** Vous pouvez faire passer un ID utilisateur à un rôle ayant plus d'autorisations, mais vous ne pouvez pas déclasser un utilisateur ayant le rôle Admin ou Chef de projet vers le rôle Annotateur humain.

## Leçon 2 : créer un espace de travail
{: #wks_tutless2}

Au cours de cette leçon, vous allez apprendre comment créer un espace de travail dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche
{: #wks_tutless2_about}

Un espace de travail définit toutes les ressources nécessaires à la création d'un modèle d'apprentissage automatique : documents d'entraînement, système de types, dictionnaires et annotations ajoutées par les annotateurs humains. Pour plus d'informations sur la création d'un espace de travail, consultez [Créer un espace de travail](/docs/services/watson-knowledge-studio/create-project.html).

### Procédure
{: #wks_tutless2_procedure}

1. En tant qu'administrateur {{site.data.keyword.knowledgestudioshort}}, à partir de votre [tableau de bord ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){:new_window} {{site.data.keyword.cloud_notm}}, lancez le service {{site.data.keyword.knowledgestudioshort}}.
1. Cliquez sur **Créer un espace de travail**.
1. Spécifiez les détails du nouvel espace de travail :

    - Dans le champ **Nom de l'espace de travail**, tapez `Mon espace de travail`.
    - Dans le champ **Description de l'espace de travail**, tapez `Espace de travail des tutoriels de Watson Knowledge Studio`.
    - Dans le champ **Langue des documents**, utilisez la valeur par défaut, soit l'**anglais**. Les fichiers d'exemple que vous utiliserez pour ce tutoriel sont en anglais.

1. Cliquez sur **Créer**.

### Résultats
{: #wks_tutless2_results}

L'espace de travail est créé et s'ouvre automatiquement.

### Que faire ensuite
{: #wks_tutless2_next}

Vous pouvez maintenant commencer à configurer les ressources de l'espace de travail, telles que le système de types.

## Leçon 3 : créer un système de types
{: #wks_tutless3}

Au cours de cette leçon, vous allez apprendre comment transférer et modifier un système de types dans {{site.data.keyword.knowledgestudioshort}}. Avant de commencer toute tâche d'annotation, vous devez créer un système de types ou en transférer un.

### A propos de cette tâche
{: #wks_tutless3_about}

Pour plus d'informations sur les systèmes de types, consultez [Systèmes de types](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem).

### Procédure
{: #wks_tutless3_procedure}

1. Téléchargez le fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> sur votre ordinateur. Ce fichier contient un exemple de système de types KLUE.
1. Cliquez sur **Actifs** > **Types d'entité**.
1. Dans la page Types d'entité, cliquez sur **Transférer**.
1. Transférez le fichier `en-klue2-types.json` de votre ordinateur. Le système de types transféré apparaît dans le tableau.
1. Parcourez le système de types pour voir quelles données ont été transférées.
1. Editez un type d'entité :

    1. Localisez le type d'entité MONEY.
    1. Double-cliquez n'importe où dans la ligne du tableau pour éditer le type d'entité.
    1. Dans la colonne **Rôles**, cliquez sur l'icône **Supprimer un rôle** ![Icône "Supprimer un rôle".](images/wks_delete.jpg "Icône Supprimer un rôle") à côté du rôle AWARD.

        ![Capture d'écran montrant la suppression d'un rôle d'un type d'entité.](images/wks_tut_delete_role.jpg "Capture d'écran montrant le survol avec le curseur ")

    1. Cliquer sur **Sauvegarder**.

### Que faire ensuite
{: #wks_tutless3_next}

Lorsque vous avez fini de modifier le système de types, vous pouvez commencer à ajouter des documents à votre espace de travail.

## Leçon 4 : ajouter un dictionnaire
{: #wks_tutless4}

Au cours de cette leçon, vous allez apprendre comment ajouter un dictionnaire à un espace de travail dans {{site.data.keyword.knowledgestudioshort}}. Les dictionnaires sont utilisés pour pré-annoter le texte lors de la création d'un modèle d'apprentissage automatique.

### A propos de cette tâche
{: #wks_tutless4_about}

Pour plus d'informations sur les dictionnaires, consultez [Ajouter des dictionnaires à un espace de travail](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Procédure
{: #wks_tutless4_procedure}

1. Téléchargez le fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> sur votre ordinateur. Ce fichier contient des termes de dictionnaire au format CSV, lequel est adapté à un transfert dans un dictionnaire {{site.data.keyword.knowledgestudioshort}}.
1. Cliquez sur **Actifs** > **Dictionnaires**.
1. Cliquez sur **Créer un dictionnaire** pour ajouter un dictionnaire.

    > **Remarque :** Ne cliquez pas sur **Transférer un dictionnaire**, cette fonction servant à transférer un dictionnaire que vous voulez utiliser tel quel. Pour le tutoriel, vous allez créer un nouveau dictionnaire éditable, puis vous y transférerez des termes.

1. Dans le champ **Nom**, tapez `Dictionnaire test` et cliquez sur **Sauvegarder** pour créer le dictionnaire (vide).

    Le dictionnaire est créé et s'ouvre automatiquement en vue de son édition.

1. Dans le panneau du dictionnaire, cliquez sur **Transférer**.
1. Transférez le fichier `dictionary-items-organization.csv` de votre ordinateur. Les termes du fichier sont transférés dans le dictionnaire.
1. Cliquez sur **Ajouter une entrée** pour créer un nouveau terme. Une ligne éditable est ajoutée en haut du tableau.
1. Dans la colonne **Formes de surface**, tapez `IBM` et `International Business Machines Corporation` sur deux lignes séparées. (Dès que vous commencez à taper une nouvelle forme de surface, un espace est ajouté en dessous pour une forme de surface supplémentaire.) Le bouton radio `IBM` est sélectionné. Laissez-le ainsi. Cette sélection indique que le lemme est `IBM`.
1. Dans la colonne **Partie du discours**, sélectionnez **Nom** (nom commun).
1. Cliquer sur **Sauvegarder**.

    ![Capture d'écran de la page Dictionnaires. L'entrée "IBM" du dictionnaire est sélectionnée et ses formes de surface et partie du discours sont mises en évidence.](images/wks_tutdict4.jpg "Capture d'écran de la page Dictionnaires. ")

### Que faire ensuite
{: #wks_tutless4_next}

Après avoir créé un dictionnaire, vous pouvez l'utiliser pour accélérer les tâches d'annotation humaine en pré-annotant les documents.

## Résumé du tutoriel
{: #wks_tutsum}

Tout en découvrant {{site.data.keyword.knowledgestudioshort}}, vous avez créé un espace de travail et y avez ajouté des artefacts.

### Ce que vous avez appris
{: #lessons_learned}

En suivant ce tutoriel, vous avez appris les concepts suivants :

- Espaces de travail
- Systèmes de types
- Dictionnaires
