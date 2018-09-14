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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}.
{: tip}

# Créer le modèle à base de règles
{: #wks_rule_train}

Après avoir défini des règles, vous pouvez créer un modèle basé sur celles-ci.
{: shortdesc}

## Procédure
{: #wks_rule_train_procedure}

Pour créer un à base de règles, effectuez les étapes suivantes :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez l'onglet **Modèle à base de règles** > **Versions** > **Modèle à base de règles**.
2. Cliquez sur **Mapper les types d'entité et les classes**.
3. Associez les types d'entités du système de types à une ou plusieurs des classes que vous avez utilisées pour définir les règles.

  Une fois les associations créées entre les types d'entités et les classes, vous pouvez [déployer le modèle à base de règles](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html) ou l'utiliser pour [pré-annoter des documents](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) dans le processus de création d'un modèle d'apprentissage automatique.

## Supprimer un modèle à base de règles
{: #wks_rule_delete_model}

Vous ne pouvez pas supprimer un modèle à base de règles.

Vous pouvez supprimer l'espace de travail ayant servi au développement du modèle à base de règles, mais vous ne pouvez pas supprimer le modèle lui-même. Ce ne serait pas la meilleure approche. Mieux vaut en effet recréer les règles qui ont été définies pour lui. En éditant les règles directement, vous changez le comportement du modèle à base de règles.
