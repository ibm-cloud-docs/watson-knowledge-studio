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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}.
{: tip}

# Transférer des ressources d'un autre espace de travail
{: #exportimport}

Pour accélérer la création d'un modèle, vous pouvez transférer des ressources telles que des documents (avec ou sans annotations de référence), un système de types et des dictionnaires que vous avez téléchargés d'un autre espace de travail.
{: shortdesc}

La possibilité de télécharger et transférer séparément différentes ressources vous donne plus souplesse lorsque vous concevez et créez un modèle. Par exemple, vous pourriez créer un espace de travail pour y concevoir le système de types et effectuer l'annotation humaine, puis créer un espace de travail à part, peut-être même dans une instance séparée de {{site.data.keyword.knowledgestudioshort}} avec des utilisateurs différents, pour entraîner le modèle d'apprentissage automatique. Comme vous êtes en mesure de transférer les ressources, y compris les données de référence créées par les annotateurs humains, ce scénario est tout à fait possible.

Vous ne pouvez pas télécharger ni transférer un modèle d'apprentissage automatique. A la place, vous pouvez télécharger d'un espace de travail tous les artefacts qui ont été utilisés pour créer le modèle et les transférer vers un nouvel espace de travail. A partir du nouvel espace de travail, vous pouvez relancer l'entraînement afin de recréer le modèle. Le nouveau modèle devrait produire des résultats similaires à ceux du modèle d'origine, car l'un et l'autre ont été entraînés avec le même jeu d'artefacts.

Les fichiers que vous téléchargez sont indépendants du système d'exploitation. Les instances de {{site.data.keyword.knowledgestudioshort}} où vous téléchargez et transférez les fichiers n'ont pas besoin de fonctionner avec la même version de Linux.

## Systèmes de types
{: #wks_exportimport_expimp_type}

Pour télécharger un système de types, ouvrez la page **Actifs & Outils** > **Types d'entité** et cliquez sur **Télécharger des types**. Le système crée un fichier nommé `types-ID.json` et vous invite à le télécharger sur votre système local. Pour utiliser le système de types dans un nouvel espace de travail, ouvrez la page **Types d'entité** et transférez le fichier `JSON` que vous avez téléchargé.

## Dictionnaires
{: #wks_exportimport_expimp_dict}

Pour télécharger un ou plusieurs dictionnaires, sélectionnez l'onglet **Actifs & Outils** > **Pré-annotateurs** > **Dictionnaires** et cliquez sur **Télécharger des dictionnaires**. Pour chacun des dictionnaires que vous téléchargez, le système crée un fichier nommé `dictionary name_timestamp.csv` et combine les fichiers dans un fichier `ZIP` ayant un nom de la forme `nom de l'espace de travail_dictionnaire_horodatage.zip`, puis vous invite à télécharger ce fichier vers votre système local. Vous pouvez aussi télécharger un dictionnaire individuel en ouvrant celui-ci et en cliquant sur **Télécharger**. Les dictionnaires en aperçu seul que vous avez transférés sous forme de fichiers CSV ne peuvent pas être téléchargés.

Avant de transférer un dictionnaire téléchargé dans un nouvel espace de travail, vous devez télécharger le système de types de l'ancien espace de travail et le transférer dans le nouvel espace. Le système de types et les dictionnaires doivent provenir du même espace de travail {{site.data.keyword.knowledgestudioshort}}. En outre, le système de types doit exister dans le nouvel espace de travail avant que les dictionnaires n'y soient transférés.

Pour transférer des dictionnaires, ouvrez l'onglet **Dictionnaires** et ajoutez un fichier `CSV` que vous avez téléchargé ou transférez le fichier `ZIP`.

## Documents
{: #wks_exportimport_expimp_doc}

Pour télécharger des documents que vous avez ajoutés au corpus, ouvrez l'onglet **Actifs & Outils** > **Documents** > **Jeux de documents** et cliquez sur **Télécharger des jeux de documents**. Le système crée un fichier nommé `corpus-ID.zip` et vous invite à le télécharger sur votre système local. Le fichier `ZIP` contient tous les documents du corpus. Les annotations qui ont été ajoutées à des jeux d'annotations sont incluses dans le fichier ZIP, mais seulement une fois que ces jeux d'annotations ont été approuvés et promus au rang de données de référence.

> **Restriction :** Tous les documents qui ont été pré-annotés sont obscurcis de manière à être rendus illisibles lorsqu'ils sont téléchargés. Même les annotations qui y ont été ajoutées par des humains sont illisibles.

Avant de transférer des documents incluant des données de référence dans un nouvel espace de travail, vous devez télécharger le système de types de l'ancien espace de travail et le transférer dans le nouvel espace. Le système de types et les documents doivent provenir du même espace de travail {{site.data.keyword.knowledgestudioshort}}. En outre, le système de types doit exister dans le nouvel espace de travail avant que les annotations de référence n'y soient transférées.

Pour transférer les documents, ouvrez l'onglet **Jeux de documents** dans le nouvel espace de travail, cliquez sur **Transférer des jeux de documents** et sélectionnez le fichier `ZIP` du corpus que vous avez téléchargé. Avant de cliquer sur **Transférer**, indiquez si vous voulez que les documents transférés incluent ou excluent les annotations de référence. Seules les annotations ayant été promues au rang de données de référence avant que les documents ne soient téléchargés seront transférées.

**Concepts connexes** :

[Systèmes de types](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[Dictionnaires](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[Documents pour les annotateurs d'apprentissage automatique](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[Documents pour les annotateurs à base de règles](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
