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
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/artifacts.html){: new_window}.
{: tip}

# Types d'artefacts

{: #artifacts}

Commencez par créer ou transférer les artefacts que vous comptez utiliser pour entraîner les annotateurs.
{: shortdesc}

Les annotateurs apprennent les types d'artefacts suivants que vous ajoutez à l'espace de travail :


- **Système de types**

    Un système de types définit les entités et les relations entre entités qui vous importent.
Consultez [Etablir un système de types](/docs/services/watson-knowledge-studio/typesystem.html).

- **Dictionnaires**

    Un dictionnaire regroupe des mots et des syntagmes qui doivent être traités de façon équivalente par un modèle.
Consultez [Créer des dictionnaires](/docs/services/watson-knowledge-studio/dictionaries.html).

- **Documents**

    Les documents ont une finalité différente selon que vous créez un modèle
d'apprentissage automatique ou un modèle à base de règles.
Pour plus d'informations, reportez-vous aux rubriques suivantes :
    - Documents pour un modèle d'apprentissage automatique : [Ajouter des documents pour l'annotation](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)
    - Documents pour un modèle à base de règles : [Ajouter des documents pour définir des règles](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)

Nombre de ces artefacts peuvent être transférés à partir de ressources externes, y compris lorsqu'il
s'agit d'artefacts que vous avez précédemment téléchargés d'autres espaces de travail {{site.data.keyword.knowledgestudioshort}}.
Pour des informations sur le transfert d'artefacts provenant d'autres espaces de travail,
consultez [Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

Consultez [Synthèse des entrées, des sorties et des limites](/docs/services/watson-knowledge-studio/create-project.html#wks_formats)
pour l'essentiel de ce qu'il faut savoir à propos des artefacts, notamment les tailles limites et les types de fichier acceptés à l'importation.


