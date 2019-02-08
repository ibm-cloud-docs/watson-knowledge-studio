---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}.
{: tip}

# Pré-annoter des documents
{: #wks_tutboot_intro}

Ce tutoriel vous aide à comprendre comment pré-annoter des documents, opération qui permet de jeter les bases du processus d'annotation humaine.
{: shortdesc}

## Objectifs pédagogiques
{: #objectives}

Après avoir suivi ce tutoriel, vous saurez comment pré-annoter des documents avec un modèle d'apprentissage automatique.

Ce tutoriel devrait prendre environ 5 minutes. Comptez plus de temps si vous explorez d'autres concepts relatifs aux sujets qui y sont traités.

## Avant de commencer
{: #prereqs}

- Vérifiez que vous utilisez un navigateur pris en charge. Consultez à cet effet [Navigateur nécessaire](/docs/services/watson-knowledge-studio/system-requirements.html).
- Vous avez suivi et effectué correctement la procédure [Initiation à {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html), qui couvre la création d'un espace de travail, la création d'un système de types et l'ajout d'un dictionnaire.
- Vous avez suivi et effectué correctement la procédure [Créer un modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Vous devez avoir au moins un ID utilisateur dans le rôle Admin ou Chef de projet. Pour des informations sur les rôles d'utilisateur, consultez [Rôles d'utilisateur dans {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Résultats
{: #results}

Au terme de ce tutoriel, vous serez en possession d'un jeu de documents partiellement annotés. Vous pourrez ensuite les affecter à des annotateurs humains pour qu'ils terminent le travail d'annotation.

## Leçon 1 : pré-annoter de nouveaux documents avec un modèle d'apprentissage automatique
{: #wks_tutboot_ml}

Au cours de cette leçon, vous allez découvrir comment utiliser un modèle d'apprentissage automatique pour pré-annoter des documents dans {{site.data.keyword.knowledgestudioshort}}.

### A propos de cette tâche
{: #wks_tutboot_ml_about}

Après avoir entraîné un modèle d'apprentissage automatique, vous pouvez utiliser celui-ci pour pré-annoter de nouveaux documents que vous ajoutez au corpus.

> **Attention :** Ne lancez pas de pré-annotateur sur des documents qui ont été annotés par des humains mais qui n'ont pas encore été ajoutés aux données de référence. Toutes les annotations humaines déjà présentes seraient sinon supprimées de ces documents.

Dans ce tutoriel, vous pouvez ajouter un second jeu de documents en utilisant le fichier `documents-ml.csv`. Faites attention de ne pas ajouter à nouveau le fichier `documents-new.csv`, car cela entraînerait une duplication des documents dans les données de référence, avec les problèmes suivants :

- Si les annotations des deux exemplaires d'un même document ne concordent pas, elles font baisser la qualité du modèle d'apprentissage automatique.
- Si les annotations des deux exemplaires d'un même document concordent, il y a surentraînement du modèle d'apprentissage automatique sur ces deux fichiers.

Pour plus d'informations sur la pré-annotation des documents, consultez [Amorcer le processus d'annotation](/docs/services/watson-knowledge-studio/preannotation.html), qui traite d'autres méthodes de pré-annotation.

### Procédure
{: #wks_tutboot_ml_procedure}

1. Connectez-vous à {{site.data.keyword.knowledgestudioshort}} en tant qu'administrateur.
1. Transférez davantage de documents dans l'espace de travail. Vous pouvez utiliser le fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.

    Pour plus d'informations sur l'ajout de documents à un espace de travail, consultez [Ajouter des documents pour l'annotation](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Créez un jeu d'annotations qui utilise le fichier `documents-ml.csv` comme jeu de base et attribuez-le à vous-même, l'administrateur. 

    Après avoir effectué les étapes suivantes pour pré-annoter les nouveaux documents, vous pouvez consulter le jeu d'annotations pour voir comment le modèle a annoté les documents. Généralement, vous affectez les jeux d'annotations à un ou plusieurs annotateurs humains. Pour plus d'informations sur la création et l'affectation de jeux d'annotations, consultez [Ajouter des documents pour l'annotation](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Pour pré-annoter les nouveaux documents, cliquez sur **Modèle d'apprentissage automatique** > **Versions**, puis sur **Exécuter ce modèle**. 
1. Sélectionnez le jeu de documents que vous avez ajouté au corpus, `documents-ml.csv`, et cliquez sur **Exécuter**.
1. Une fois la pré-annotation achevée, créez une tâche d'annotation humaine incluant le jeu d'annotations que vous avez créé.

    Pour plus d'informations sur la création d'une tâche d'annotation, consultez [Configuration d'annotation](/docs/services/watson-knowledge-studio/annotate-documents.html).

1. Pour voir les annotations qui ont été appliquées aux nouveaux documents par le modèle d'apprentissage automatique, ouvrez la tâche d'annotation.

    Comme les nouveaux documents ont été pré-annotés avec le modèle d'apprentissage automatique, l'annotation humaine demande moins de temps. Pour plus d'informations sur l'ajout d'annotations par les annotateurs humains, consultez [Annoter des documents](/docs/services/watson-knowledge-studio/user-guide.html).

### Résultats
{: #wks_tutboot_ml_results}

En utilisant votre modèle d'apprentissage automatique pour pré-annoter les nouveaux jeux de documents, vous pouvez accélérer les tâches d'annotation humaine de ces documents.
