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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}.
{: tip}

# Ajouter des documents pour définir des règles
{: #wks_rule_anno_add}

Ajoutez des documents avec des motifs linguistiques illustrant les types de règles que vous voulez définir.
{: shortdesc}

Les documents que vous ajoutez pour définir des règles sont conservés à part des documents que vous ajoutez pour l'annotation. Leur seul but est d'être utilisés pour l'extraction d'exemples de motifs. Ils ne servent pas à l'entraînement et ne sont jamais téléchargés.

## Les différents moyens d'ajouter des documents à l'éditeur de règle

- **Créer un document texte au format UTF-8**

    Vous pouvez ajouter un texte illustrant un motif directement dans l'éditeur de règle. Le nom que vous spécifiez pour le document ne doit pas dépasser 256 caractères.

- **Transférer un fichier CSV**

    Transférez un fichier au format CSV contenant le texte du document.

- **Copier un document ayant été importé pour l'annotation**

    Si un document d'un jeu ayant été importé pour les tâches d'annotation contient des exemples des motifs que vous voulez capturer sous forme de règles, vous pouvez le copier dans l'éditeur de règle. S'agissant d'une copie, vous pouvez la modifier librement, cela n'aura pas d'incidence sur la version d'origine du document qui sert à l'annotation. Pour plus d'informations sur le transfert de documents, consultez [Ajouter des documents à un espace de travail](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

Concernant les documents que vous copiez ou transférez, choisissez-en qui contiennent des motifs distincts, aidant à identifier les types d'entités dans les documents qui seront annotés.
