---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-14"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrer sur IBM Cloud
{: #migrate}

Le 18 décembre 2017, IBM a lancé {{site.data.keyword.knowledgestudiofull}} sur {{site.data.keyword.cloud_notm}}, marquant ainsi le début du processus de migration de toutes les instances de {{site.data.keyword.knowledgestudioshort}} d'{{site.data.keyword.IBM_notm}} Marketplace vers {{site.data.keyword.cloud_notm}}.
{: shortdesc}

**Remarque **: Le terme _espace de travail_ est utilisé dans {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}, alors que dans {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace, on parle de _projet_. La fonctionnalité est la même. Seule la terminologie est différente.

## Processus et calendrier
{: #process}

Le processus et le calendrier de migration de vos projets {{site.data.keyword.knowledgestudioshort}} dépendent du [plan de tarification que vous possédez actuellement sur {{site.data.keyword.IBM_notm}} Marketplace ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} et de votre type de compte, comme le montre le tableau suivant :

| Plan et compte | Processus de migration | Calendrier de migration |
|------|-------------------|--------------------|
| Plan gratuit | Le client fait migrer l'instance et les données | Toutes les migrations doivent être achevées d'ici le 1er février 2018. Le 2 février 2018, tous les plans gratuits sur {{site.data.keyword.IBM_notm}} Marketplace, ainsi que les données des projets associés, seront purgés. |
| Plan Standard avec compte Paiement à la carte | Le client fait migrer l'instance et les données | Toutes les migrations doivent être achevées d'ici le 29 juin 2018. Le 30 juin 2018, tous les plans Standard avec compte Paiement à la carte sur {{site.data.keyword.IBM_notm}} Marketplace, ainsi que les données des projets associés, seront purgés.
| Plan Standard contractuel | Le client fait migrer l'instance et les données. {{site.data.keyword.IBM_notm}} renouvelle son contrat. | Toutes les migrations doivent être achevées d'ici le 29 juin 2018. Contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Plan Premium contractuel | {{site.data.keyword.IBM_notm}} fait migrer l'instance et les données. {{site.data.keyword.IBM_notm}} renouvelle son contrat. | Toutes les migrations doivent être achevées d'ici le 29 juin 2018. Contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tableau 1. Processus et calendrier de migration de {{site.data.keyword.knowledgestudioshort}} d'{{site.data.keyword.IBM_notm}} vers {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migration des plans gratuits
{: migratefree}

Si vous avez un plan gratuit {{site.data.keyword.knowledgestudioshort}}, effectuez les étapes suivantes pour faire migrer votre instance et les projets associés d'{{site.data.keyword.IBM_notm}} Marketplace vers {{site.data.keyword.cloud_notm}} :

1. Si vous n'avez pas de compte {{site.data.keyword.cloud_notm}}, inscrivez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/wks_cloud){: new_window} en utilisant votre {{site.data.keyword.ibmid}} d'{{site.data.keyword.IBM_notm}} Marketplace.

   Votre {{site.data.keyword.ibmid}} est l'ID que vous utilisez pour vous connecter à {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace.

1. Connectez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Si vous n'avez pas d'instance {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}, créez-en une sur la [page {{site.data.keyword.knowledgestudioshort}} du catalogue {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Suivez la procédure de [sauvegarde et restauration](/docs/services/watson-knowledge-studio/backup-restore.html) pour faire migrer manuellement vos projets de l'instance sur {{site.data.keyword.IBM_notm}} Marketplace vers votre instance sur {{site.data.keyword.cloud_notm}}.

  **Remarque **: Si vous avez un modèle qui est déjà déployé et que vous comptez supprimer l'espace de travail après l'avoir sauvegardé, retirez ce modèle du déploiement. Vous pourrez reconstruire et redéployer le modèle après avoir restauré l'espace de travail à partir de la sauvegarde. Pour des informations sur le retrait de modèles du déploiement, consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migration des plans Standard pour les comptes Paiement à la carte
{: migratepaygo}

Si vous avez un plan Standard et un compte [Paiement à la carte ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/pricing/billable.html){: new_window}, effectuez les étapes suivantes pour faire migrer votre instance et les projets associés d'{{site.data.keyword.IBM_notm}} Marketplace vers {{site.data.keyword.cloud_notm}} :

1. Si vous n'avez pas de compte {{site.data.keyword.cloud_notm}}, inscrivez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/){: new_window} en utilisant votre {{site.data.keyword.ibmid}} d'{{site.data.keyword.IBM_notm}} Marketplace.

   Votre {{site.data.keyword.ibmid}} est l'ID que vous utilisez pour vous connecter à {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace.

1. Connectez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Si vous n'avez pas d'instance {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}, créez-en une sur la [page {{site.data.keyword.knowledgestudioshort}} du catalogue {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Suivez la procédure de [sauvegarde et restauration](/docs/services/watson-knowledge-studio/backup-restore.html) pour faire migrer manuellement vos projets de l'instance sur {{site.data.keyword.IBM_notm}} Marketplace vers votre instance sur {{site.data.keyword.cloud_notm}}.

  **Remarque **: Si vous avez un modèle qui est déjà déployé et que vous comptez supprimer l'espace de travail après l'avoir sauvegardé, retirez ce modèle du déploiement. Vous pourrez reconstruire et redéployer le modèle après avoir restauré l'espace de travail à partir de la sauvegarde. Pour des informations sur le retrait de modèles du déploiement, consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migration des plans Standard pour les comptes contractuels
{: migratecontract}

Si vous avez un plan Standard contractuel {{site.data.keyword.knowledgestudioshort}}, effectuez les étapes suivantes pour renouveler votre contrat et faire migrer votre instance et les projets associés d'{{site.data.keyword.IBM_notm}} Marketplace vers {{site.data.keyword.cloud_notm}} :

1. Pour renouveler votre contrat, contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration).
1. Une fois votre contrat renouvelé sur {{site.data.keyword.cloud_notm}}, connectez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Si vous n'avez pas d'instance {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}, créez-en une sur la [page {{site.data.keyword.knowledgestudioshort}} du catalogue {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Suivez la procédure de [sauvegarde et restauration](/docs/services/watson-knowledge-studio/backup-restore.html) pour faire migrer manuellement vos projets de l'instance sur {{site.data.keyword.IBM_notm}} Marketplace vers votre instance sur {{site.data.keyword.cloud_notm}}.

  **Remarque **: Si vous avez un modèle qui est déjà déployé et que vous comptez supprimer l'espace de travail après l'avoir sauvegardé, retirez ce modèle du déploiement. Vous pourrez reconstruire et redéployer le modèle après avoir restauré l'espace de travail à partir de la sauvegarde. Pour des informations sur le retrait de modèles du déploiement, consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migration des plans Premium pour les comptes contractuels
{: migratecontract}

Si vous avez un plan Premium contractuel {{site.data.keyword.knowledgestudioshort}}, contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Une fois le contrat renouvelé sur {{site.data.keyword.cloud_notm}}, IBM se chargera de faire migrer vos données conformément à un calendrier négocié entre vous et {{site.data.keyword.cloud_notm}}.
