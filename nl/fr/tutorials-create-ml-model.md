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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window}.
{: tip}

# Créer un modèle d'apprentissage automatique
{: #wks_tutml_intro}

Ce tutoriel vous aide à comprendre le processus de construction d'un modèle d'apprentissage automatique que vous pourrez déployer et utiliser avec d'autres services {{site.data.keyword.watson}}.
{: shortdesc}

## Objectifs pédagogiques

Après avoir terminé les leçons de ce tutoriel, vous saurez comment effectuer les tâches suivantes :

- Créer des jeux de documents
- Pré-annoter des documents
- Créer des tâches pour les annotateurs humains
- Analyser la convergence entre annotateurs et arbitrer les conflits dans les documents annotés
- Créer des annotateurs d'apprentissage automatique

Ce tutoriel devrait prendre environ 60 minutes. Comptez plus de temps si vous explorez d'autres concepts relatifs aux sujets qui y sont traités.

## Avant de commencer

- Vérifiez que vous utilisez un navigateur pris en charge. Consultez à cet effet [Navigateur nécessaire](/docs/services/watson-knowledge-studio/system-requirements.html).
- Assurez-vous d'avoir suivi le tutoriel [Créer un espace de travail](/docs/services/watson-knowledge-studio/tutorials-create-project.html).
- Vous devez avoir au moins un ID utilisateur dans le rôle Admin ou ProjectManager.

    > **Remarque :** Dans la mesure du possible, utilisez plusieurs ID utilisateur pour effectuer les tâches décrites dans ce tutoriel (un ID utilisateur avec le rôle Admin ou ProjectManager et au moins deux autres avec le rôle HumanAnnotator). Vous aurez ainsi une simulation plus réaliste d'un véritable espace de travail {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}™ {{site.data.keyword.knowledgestudioshort}}, dans lequel un chef de projet doit coordonner et arbitrer le travail de plusieurs annotateurs humains. Si vous n'avez accès qu'à un seul ID utilisateur, vous pourrez quand même simuler la plus grande part du processus.

    Pour des informations sur les rôles d'utilisateur, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

## Résultats

Au terme de ce tutoriel, vous serez en possession d'un modèle d'apprentissage automatique personnalisé que vous pourrez utiliser avec d'autres services {{site.data.keyword.watson}}.

## Leçon 1 : ajouter des documents pour l'annotation
{: #tut_lessml1}

Au cours de cette leçon, vous allez apprendre comment ajouter des documents à un espace de travail dans {{site.data.keyword.knowledgestudioshort}} qui pourront ensuite passer entre les mains d'annotateurs humains.

### A propos de cette tâche

Pour plus d'informations sur l'ajout de documents, consultez [Ajouter des documents à un espace de travail](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

### Procédure

1. Téléchargez le fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv`<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> sur votre ordinateur. Ce fichier contient des exemples de documents qui se prêtent au transfert.
1. Dans votre espace de travail, dans la barre latérale, cliquez sur **Documents**.
1. Dans la page Documents, cliquez sur **Transférer des jeux de documents**.
1. Sélectionnez le fichier `documents-new.csv` que vous avez téléchargé sur votre ordinateur et cliquez sur **Transférer**. Le fichier transféré apparaît dans le tableau.

### Que faire ensuite

Vous pouvez maintenant diviser le corpus en plusieurs jeux de documents et affecter ces derniers à des annotateurs humains.

## Leçon 2 : créer des jeux d'annotations
{: #wks_tutless_ml2}

Au cours de cette leçon, vous allez apprendre comment créer des jeux d'annotations dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Un jeu d'annotations est une partie d'un jeu de documents transféré que vous affectez à un annotateur humain. Ce dernier annote les documents du jeu d'annotations qui lui est affecté. Pour pouvoir comparer ultérieurement les annotations ajoutées par différents annotateurs humains en utilisant leurs scores de convergence, vous devez affecter au moins deux annotateurs humains à des jeux d'annotations différents. Vous devez aussi spécifier quel pourcentage de documents se chevauchent entre les jeux.

> **Remarque :** Dans un véritable espace de travail, vous auriez créé autant de jeux d'annotations que nécessaire, compte tenu du nombre d'annotateurs humains travaillant dans cet espace. Dans ce tutoriel, vous allez créer deux jeux d'annotations. Si vous n'avez pas accès à plusieurs ID utilisateur, vous pouvez affecter les deux jeux au même utilisateur.

Pour plus d'informations sur les d'annotations, consultez [Créer et affecter des jeux d'annotations](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).

### Procédure

1. Dans votre espace de travail, dans la barre latérale, cliquez sur **Documents**.
1. Cliquez sur **Créer des jeux d'annotations**.

    La fenêtre Créer des jeux d'annotations s'ouvre. Par défaut, cette fenêtre montre le jeu de base (contenant tous les documents) ainsi que des champs permettant de spécifier les détails d'un nouveau jeu d'annotations.

1. Cliquez sur **Ajouter un jeu et un annotateur humain supplémentaires** pour ajouter les champs d'un nouveau jeu d'annotations. Vous pouvez cliquer sur cette option autant de fois qu'il le faut pour créer le nombre de jeux d'annotations nécessaire. Pour ce tutoriel, vous n'en avez besoin que de deux.

    ![Capture d'écran de la page Créer des jeux d'annotations.](images/wks_tutdocset2.jpg)

1. Dans le champ **Chevauchement**, spécifiez `100`. Ce faisant, vous indiquez votre souhait de voir 100 pour cent des documents du jeu de base inclus dans chacun des nouveaux jeux d'annotations afin qu'ils soient annotés par tous les annotateurs humains.
1. Spécifiez les informations requises pour chaque nouveau jeu d'annotations que vous créez.

    - Dans la liste **Annotateur**, sélectionnez l'ID utilisateur d'un annotateur humain à affecter au nouveau jeu d'annotations. Chaque jeu d'annotations doit être affecté à un annotateur humain différent.

        > **Remarque :** Si vous n'avez qu'un seul ID d'administrateur utilisable pour le tutoriel, affectez-lui tous les jeux d'annotations. Dans un véritable espace de travail, il y aurait plusieurs annotateurs humains et chacun recevrait son propre jeu d'annotations, mais pour ce tutoriel, l'administrateur peut agir en tant qu'annotateur humain.

    - Dans le champ **Nom du jeu**, entrez un nom descriptif (tel que `Jeu 1` ou `JeuDavid`) pour le jeu d'annotations.

1. Cliquez sur **Générer**.

### Résultats

Les nouveaux jeux d'annotations sont créés et apparaissent maintenant dans l'onglet **Jeux d'annotations** de la page Documents.

## Leçon 3 : pré-annoter avec un annotateur à base de dictionnaire
{: #wks_tutless_ml3}

Au cours de cette leçon, vous allez voir comment utiliser un annotateur à base de dictionnaire pour pré-annoter des documents dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

La pré-annotation de documents est une étape optionnelle. Cependant, c'est une étape intéressante dans la mesure où elle facilite ensuite le travail des annotateurs humains.

Pour plus d'informations sur la pré-annotation avec des annotateurs à base de dictionnaire, consultez [Pré-annoter des documents avec le pré-annotateur à base de dictionnaire](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot).

### Procédure

1. Dans la barre latérale **Actifs & Outils** > **Pré-annotateurs** de votre espace de travail, cliquez sur **Gérer les dictionnaires**.

  Le dictionnaire `Dictionnaire test` s'ouvre.

1. Dans la liste **Type d'entité**, sélectionnez **ORGANIZATION** pour associer le type d'entité ORGANIZATION au dictionnaire `Dictionnaire test` que vous avez créé dans la leçon [Ajouter un dictionnaire](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) du tutoriel *Créer un espace de travail*.
1. Cliquez sur la flèche arrière en haut à gauche pour retourner à la page Pré-annotateurs, puis cliquez sur **Appliquer ce pré-annotateur**.
1. Sur la page Exécuter un annotateur, cochez les cases des deux jeux d'annotations que vous avez créés plus tôt dans ce tutoriel (sans inclure le jeu de base).
1. Cliquez sur **Exécuter**.

    ![Capture d'écran montrant la page Exécuter un annotateur. Le bouton Exécuter est mis en évidence.](images/wks_tutanno3.jpg)

### Résultats

Les documents des jeux sélectionnés sont pré-annotés avec l'annotateur à base de dictionnaire que vous avez créé. Plus tard, vous pourrez utiliser le même annotateur pour pré-annoter d'autres jeux de documents en cliquant sur **Appliquer ce pré-annotateur**.

## Leçon 4 : créer une tâche d'annotation
{: #wks_tutless_ml4}

Au cours de cette leçon, vous allez découvrir comment utiliser des tâches d'annotation pour suivre le travail des annotateurs humains dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Pour plus d'informations sur les tâches d'annotation, consultez [Créer une tâche d'annotation](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask).

### Procédure

1. Dans la barre latérale **Actifs & Outils** > **Documents** de votre espace de travail, sélectionnez l'onglet **Tâches**.
1. Sur la page Tâches, cliquez sur **Ajouter une tâche**.
1. Spécifiez les détails de la tâche :

    - Dans le champ **Nom de la tâche**, tapez `Test`.
    - Dans le champ **Echéance**, sélectionnez une date future.

1. Cliquez sur **Créer**.
1. Dans la fenêtre Ajouter des jeux d'annotations à la tâche, cochez les cases des deux jeux d'annotations que vous avez créés dans la [Leçon 3 : pré-annoter avec un annotateur à base de dictionnaire](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3). Ce faisant, vous indiquez que les deux jeux d'annotations seront à annoter par leurs annotateurs humains respectifs dans le cadre de cette tâche.
1. Cliquez sur **Créer une tâche**.
1. Plus tard, pour voir où en est le travail d'annotation humaine, vous pourrez revenir à cet écran et cliquer sur la tâche afin de l'ouvrir.

## Leçon 5 : annoter des documents
{: #wks_tutless_ml5}

Au cours de cette leçon, vous allez apprendre à utiliser l'éditeur de données de référence pour annoter des documents dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Pour plus d'informations sur l'annotation humaine, consultez [Annotation avec l'éditeur de données de référence](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte).

### Procédure

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant qu'annotateur humain affecté à la tâche d'annotation que vous avez créée dans la [Leçon 4: créer une tâche d'annotation](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).

    > **Remarque :** si vous n'avez accès qu'à un seul ID d'administrateur pour suivre ce tutoriel, vous pouvez l'utiliser pour effectuer l'annotation humaine. N'oubliez pas cependant que dans un véritable espace de travail, l'annotation humaine est réalisée par plusieurs utilisateurs ayant le rôle HumanAnnotator.

1. Ouvrez l'espace de travail `Mon espace de travail`.
1. Dans la barre latérale, cliquez sur **Annotation de document** > **Relations**.
1. Ouvrez la tâche d'annotation `Test` que vous avez créée dans la [Leçon 4: créer une tâche d'annotation](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).
1. Faites défiler l'écran pour atteindre le document *Technology - gmanews.tv* et cliquez dessus pour l'ouvrir en vue de son annotation. Notez que le terme `IBM` est déjà annoté avec le type d'entité ORGANIZATION ; cette annotation a été ajoutée par le pré-annotateur à base de dictionnaire, dans la [Leçon 2 : créer des jeux d'annotations](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2). Cette pré-annotation étant correcte, nul besoin de la modifier.

    ![Capture d'écran montrant un document ouvert, avec une pré-annotation existante du mot IBM.](images/wks_tut_preannotation.png)

1. Annotez une mention :

    1. Cliquez sur l'icône **Mentions** pour commencer à annoter les mentions.
    1. Dans le corps du document, sélectionnez le texte `Thomas Watson`.
    1. Dans la liste des types d'entités, cliquez sur **PERSON**. Le type d'entité PERSON est appliqué à la mention sélectionnée.

        ![Capture d'écran montrant le type d'entité PERSON appliqué à la mention Thomas Watson.](images/wks_tut_annotatemention3.png)

1. Cliquez sur **Annotation de document** > **Relations** dans la barre latérale pour commencer à annoter les relations.
1. Sélectionnez les mentions `Thomas Watson` et `IBM` (dans cet ordre). Pour sélectionner une mention, cliquez sur son étiquette de type d'entité, au-dessus de son texte.
1. Dans la liste des types de relations, cliquez sur **founderOf** (fondateur de). Les deux mentions sont connectées par une relation founderOf.

    ![Capture d'écran montrant deux mentions connectées l'une à l'autre par le type de relation founderOf.](images/wks_tut_annotaterelation.png)

1. Dans le menu de statut, sélectionnez **Terminé**, puis cliquez sur le bouton **Sauvegarder**.
1. Retournez à la liste des documents et cliquez sur **Soumettre tous les documents** pour soumettre les documents en vue de leur approbation.

    > **Remarque :** Dans une situation de la vie réelle, vous auriez à créer beaucoup plus d'annotations, et ce n'est qu'une fois tous les documents terminés qu'ils seraient soumis pour approbation. 

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant que l'annotateur humain auquel est affecté un autre jeu de documents dans la tâche d'annotation.
1. Reproduisez les mêmes annotations dans le document *Technology - gmanews.tv*, à un détail près : utilisez la relation employedBy (employé par) à la place de la relation founderOf.

  Vous connecter en tant qu'un autre utilisateur aidera à illustrer la notion de convergence entre annotateurs dans la prochaine leçon. Terminez les annotations et cliquez sur **Soumettre tous les documents**.

## Leçon 6 : analyser la convergence entre annotateurs
{: #wks_tutless_ml6}

Au cours de cette leçon, vous allez apprendre à comparer le travail de plusieurs annotateurs humains dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Pour déterminer dans quelle mesure différents annotateurs humains annote de manière cohérente des documents chevauchants, examinez les scores de convergence entre annotateurs (`IAA`, de l'anglais "Inter-Annotator Agreement").

Pour calculer les scores IAA, {{site.data.keyword.knowledgestudioshort}} examine tous les documents qui se chevauchent dans tous les jeux de documents de la tâche, quel que soit le statut de ces jeux. Les scores IAA indiquent dans quelle mesure les annotateurs humains ont annoté différemment les mentions, relations et chaînes de coréférences. Il est bon de les contrôler périodiquement et de vérifier que les annotateurs humains sont cohérents entre eux.

Dans ce tutoriel, les annotateurs humains ont soumis tous les jeux de documents pour approbation. Si les scores de convergence entre annotateurs sont acceptables, vous pouvez approuver les jeux de documents. Si vous rejetez un jeu de documents, il est retourné à l'annotateur humain pour qu'il l'améliore.

### Procédure

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant qu'administrateur, sélectionnez **Actifs & Outils** > **Documents** et cliquez sur la tâche `Test`.

  Dans la colonne **Statut**, vous pouvez constater que les jeux de documents sont soumis.

1. Cliquez sur **Calculer les scores de convergence entre annotateurs (IAA)**.
1. Examinez les scores IAA des mentions, relations et chaînes de coréférences en cliquant dans le premier menu. Vous pouvez aussi consulter la convergence par paire d'annotateurs humains. Par exemple, vous pouvez comparer toutes les annotations de David avec toutes celles de Philippe. Il est aussi possible d'obtenir le score de convergence par document spécifique. Par exemple, vous pouvez comparer les annotations de David dans un document à celles de Philippe dans le même document. En général, visez un score de 0,8 sur 1, le score 1 signifiant une convergence parfaite. Comme vous avez annoté seulement deux types d'entités dans ce tutoriel, la plupart des scores sont N/A (non applicable), ce qui signifie qu'il n'y a pas d'informations pour donner un score.

    *Figure 1. Scores de convergence entre annotateurs avec les utilisateurs David et Philippe*

    ![Capture d'écran montrant les scores de convergence entre annotateurs pour une tâche.](images/wks_tutiaa2.gif)

1. Après avoir examiné les scores, vous pouvez décider s'il faut approuver ou rejeter les jeux de documents dont le statut est `Soumis`. Lorsqu'un jeu de documents a été soumis, une case à cocher apparaît à côté de son nom. Effectuez l'une des opérations suivantes :

    - Si les scores sont acceptables pour un jeu de documents, cochez la case et cliquez sur **Accepter**. Les documents qui ne figurent pas également dans les autres jeux de documents sont promus au rang de données de référence. En revanche, les documents qui se chevauchent avec d'autres jeux doivent être passés en revue par le biais d'un arbitrage visant à résoudre les conflits. Pour ce tutoriel, acceptez les deux jeux de documents.
    - Si les scores ne sont pas acceptables pour un jeu de documents, cochez la case et cliquez sur **Rejeter**. Ce jeu de documents devra être revu par l'annotateur humain afin qu'il en améliore les annotations.

### Résultats

En évaluant les scores de convergence entre annotateurs, vous avez vu comment différentes paires d'annotateurs humains peuvent annoter plus ou moins différemment un même document. Si le score était acceptable, vous avez accepté le jeu de documents.

## Leçon 7 : arbitrer les conflits dans les documents annotés
{: #wks_tutless_ml7}

Au cours de cette leçon, vous allez apprendre comment arbitrer les conflits d'annotations dans les documents qui se chevauchent entre différents jeux de documents dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Lorsque vous approuvez un jeu de documents, seuls les documents de ce jeu qui ne figurent pas également dans les autres jeux de documents sont promus au rang de données de référence. Si un document fait partie du chevauchement entre plusieurs jeux de documents, avant de le promouvoir au rang de données de référence, vous devez arbitrer les éventuels conflits d'annotations.

### Procédure

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant qu'administrateur, sélectionnez **Actifs & Outils** > **Documents** et cliquez sur la tâche `Test`.
1. Vérifiez que les deux jeux de documents sont dans un état approuvé.
1. Cliquez sur **Rechercher les conflits dans les documents qui se chevauchent**.

    Vous pouvez voir les documents chevauchants, c'est-à-dire ceux qui ont été annotés par plusieurs annotateurs humains.

1. Pour déterminer s'il y a des conflits dans la manière dont les documents ont été annotés, cliquez sur **Rechercher les conflits**.
1. En mode arbitrage, vous pouvez voir combien d'annotations sont en conflit et supprimer ou remplacer celles qui ne conviennent pas avant de promouvoir les documents au rand de données de référence.
1. Pour ce tutoriel, partons du principe que vous avez corrigé toutes les annotations en conflit et accepté les changements. Cliquez sur **Promouvoir comme données de référence**. Répétez ces étapes pour résoudre les conflits dans le second jeu de documents.

    Vous pouvez aussi promouvoir un document au rang de données de référence en cliquant sur **Accepter** dans la page Documents.

### Résultats

Ayant résolu les conflits d'annotations et promu les documents au rang de données de référence, vous pouvez les utiliser pour entraîner le modèle d'apprentissage automatique.

## Leçon 8 : créer un modèle d'apprentissage automatique
{: #wks_tutless_ml8}

Au cours de cette leçon, vous allez apprendre à créer un modèle d'apprentissage automatique dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Lorsque vous créez un modèle d'apprentissage automatique, vous devez sélectionner les jeux de documents à utiliser pour l'entraîner. Vous spécifiez également les pourcentages de documents à utiliser comme données d'apprentissage, données de test et données aveugles. Seuls les documents qui sont devenus données de référence par le biais d'une approbation ou d'un arbitrage peuvent servir à entraîner le modèle d'apprentissage automatique.

### Procédure

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant qu'administrateur.
1. Dans la barre latérale **Gestion des modèles** > **Performances**, cliquez sur **Entraîner et évaluer**.
1. Sélectionnez les jeux de documents que vous voulez utiliser pour créer un modèle d'apprentissage automatique. Cochez la case en regard du nom de chaque jeu voulu.
1. Sélectionnez les deux jeux d'annotations pour créer vos données de test, d'entraînement et aveugles. Cliquez ensuite sur **Entraîner &amp; Evaluer**.

    > **Remarque :** L'entraînement peut prendre plus de dix minutes. Il peut même prendre des heures. Tout dépend du nombre d'annotations humaines et du nombre total de mots, tous documents confondus.

1. Une fois le modèle d'apprentissage automatique entraîné, vous pouvez l'exporter ou consulter ses performances en détail en cliquant sur les liens **Statistiques détaillées** au-dessus de chaque graphe.
1. Pour voir la page Jeu d'entraînement / Jeu de test / Jeu aveugle, cliquez sur le bouton **Entraîner et évaluer**.
1. Pour les documents sur lesquels les annotateurs humains ont travaillé, cliquez sur **Afficher les données de référence**.
1. Pour voir les annotations que le modèle entraîné a créées sur ce même jeu de documents, cliquez sur **Afficher les résultats de décodage**.
1. Pour obtenir les scores détaillés de précision, de rappel et F1 du modèle d'apprentissage automatique, sélectionnez la page Performances.
1. Cliquez sur les liens **Statistiques détaillées** au-dessus de chaque graphe. Sur ces pages de statistiques, utilisez les boutons radio pour voir les scores des mentions, des relations et des chaînes de coréférences.

    Vous pouvez analyser les performances en consultant une synthèse de statistiques relatives aux types d'entités, types de relations et chaînes de coréférences. Vous pouvez aussi analyser les statistiques présentées dans une matrice de confusion en sélectionnant **Matrice de confusion** dans le menu qui, par défaut, s'intitule **Récapitulatif**. La *matrice de confusion* vous aide à comparer annotations ajoutées par le modèle d'apprentissage automatique et annotations des données de référence.

    > **Remarque :** Dans ce tutoriel, vous n'avez annotés les documents qu'avec un seul dictionnaire d'organisations. C'est la raison pour laquelle les scores que vous voyez sont `0` ou `N/A` pour la plupart des types d'entités excepté `ORGANIZATION`. Les scores sont faibles, mais cela n'a rien d'étonnant, car vous n'avez pas effectué d'annotations humaines ni de corrections.

    *Figure 2. Options de la page Statistiques pour un modèle d'apprentissage automatique*

    ![Capture d'écran montrant la page Statistiques.](images/wks_tutanno9.gif)

1. Dans la barre latérale, sélectionnez **Gestion des modèles** > **Versions**. La page Versions vous permet de prendre un instantané du modèle et des ressources qui ont servi à le créer (excepté les dictionnaires et les tâches d'annotation). Par exemple, vous avez peut-être envie de prendre un instantané du modèle avant de le réentraîner. De cette manière, si après le prochain entraînement les statistiques sont moins bonnes, vous pourrez rétablir l'ancienne version et supprimer celle qui a donné de mauvais résultats.

### Résultats

Vous avez créé un modèle d'apprentissage automatique, vous l'avez entraîné et vous avez évalué ses performances d'annotation de données de test et de données aveugles. En explorant les métriques de performances, vous avez identifié différents moyens d'améliorer l'exactitude du modèle d'apprentissage automatique.

## Résumé du tutoriel
{: #wks_tutml_sum}

Tout en découvrant {{site.data.keyword.knowledgestudioshort}}, vous avez créé un modèle d'apprentissage automatique.

### Ce que vous avez appris

En suivant ce tutoriel, vous avez appris les concepts suivants :

- Jeux de documents
- Modèles d'apprentissage automatique
- Tâches d'annotation humaine
- Convergence entre annotateurs et arbitrage
