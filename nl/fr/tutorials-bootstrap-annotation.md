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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}.
{: tip}

# Amorcer le processus d'annotation
{: #wks_tutboot_intro}

Ce tutoriel vous aide à comprendre comment pré-annoter des documents afin de simplifier le travail d'annotation incombant ensuite aux annotateurs humains.
{: shortdesc}

## Objectifs pédagogiques

Après avoir suivi ce tutoriel, vous saurez comment pré-annoter des documents avec un modèle d'apprentissage automatique.

Ce tutoriel devrait prendre environ 5 minutes. Comptez plus de temps si vous explorez d'autres concepts relatifs aux sujets qui y sont traités.

## Avant de commencer

- Vérifiez que vous utilisez un navigateur pris en charge. Consultez à cet effet [Navigateur nécessaire](/docs/services/watson-knowledge-studio/system-requirements.html).
- Assurez-vous d'avoir suivi les tutoriels [Créer un espace de travail](/docs/services/watson-knowledge-studio/tutorials-create-project.html) et [Créer un modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Vous devez avoir au moins un ID utilisateur dans le rôle Admin ou ProjectManager. Pour des informations sur les rôles d'utilisateur, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).

## Résultats

Au terme de ce tutoriel, vous serez en possession d'un jeu de documents partiellement annotés. Vous pourrez ensuite les affecter à des annotateurs humains pour qu'ils terminent le travail d'annotation.

## Leçon 1 : pré-annoter de nouveaux documents avec un modèle d'apprentissage automatique
{: #wks_tutboot_ml}

Au cours de cette leçon, vous allez découvrir comment utiliser un modèle d'apprentissage automatique pour pré-annoter des documents dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche

Après avoir entraîné un modèle d'apprentissage automatique, vous pouvez utiliser celui-ci pour pré-annoter de nouveaux documents que vous ajoutez au corpus.

> **Attention :** Ne lancez pas de pré-annotateur sur des documents qui ont été annotés par des humains mais qui n'ont pas encore été ajoutés aux données de référence. Toutes les annotations humaines déjà présentes seraient sinon supprimées de ces documents.

Dans ce tutoriel, vous pouvez ajouter un second jeu de documents en utilisant le fichier `documents-ml.csv`. Faites attention de ne pas ajouter à nouveau le fichier `documents-new.csv`, car cela entraînerait une duplication des documents dans les données de référence, avec les problèmes suivants :

- Si les annotations des deux exemplaires d'un même document ne concordent pas, elles font baisser la qualité du modèle d'apprentissage automatique.
- Si les annotations des deux exemplaires d'un même document concordent, il y a surentraînement du modèle d'apprentissage automatique sur ces deux fichiers.

### Procédure

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant qu'administrateur.
1. Transférez davantage de documents dans l'espace de travail. Vous pouvez utiliser le fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv`<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.

    Pour savoir comment transférer des documents, consultez [Créer un modèle d'apprentissage automatique > Ajouter des documents pour annotation](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1).

1. Créez un jeu d'annotations avec le fichier `documents-ml.csv`.

    Pour ce tutoriel, attribuez le jeu d'annotations à vous-même, l'administrateur. Après avoir exécuté le modèle d'apprentissage automatique pour pré-annoter les nouveaux documents, vous pouvez consulter le jeu d'annotations pour voir comment le modèle les a pré-annotés. Généralement, vous affectez les jeux d'annotations à un ou plusieurs annotateurs humains. Pour plus d'informations sur la création de jeux d'annotations, consultez [Créer un modèle d'apprentissage automatique > Créer des jeux d'annotations](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2).

1. Dans la barre latérale **Gestion des modèles** > **Versions**, sélectionnez l'onglet **Apprentissage automatique** et cliquez sur **Exécuter ce modèle**.
1. Sélectionnez le jeu de documents que vous avez ajouté au corpus, `documents-ml.csv`, et cliquez sur **Exécuter**.
1. Une fois la pré-annotation achevée, vous pouvez créer une tâche d'annotation humaine et annoter les nouveaux documents pré-annotés.

    Pour des détails sur la création d'une tâche et l'annotation de documents, consultez [Créer un modèle d'apprentissage automatique > Créer une tâche d'annotation](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4) et [Créer un modèle d'apprentissage automatique > Annoter des documents](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5).

    Dans le cas présent, l'annotation humaine nécessite moins de temps, car vous avez utilisé le modèle d'apprentissage automatique pour pré-annoter les documents.

### Résultats

En utilisant votre modèle d'apprentissage automatique pour pré-annoter les nouveaux jeux de documents, vous pouvez accélérer les tâches d'annotation humaine de ces documents.
