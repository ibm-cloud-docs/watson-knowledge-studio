---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrer sur IBM Cloud
{: #migrate}

Le 18 décembre 2017, IBM a lancé {{site.data.keyword.knowledgestudiofull}} sur {{site.data.keyword.cloud_notm}}, marquant ainsi le début du processus de migration de toutes les instances de {{site.data.keyword.knowledgestudioshort}} d'{{site.data.keyword.IBM_notm}} Marketplace vers la plateforme [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}.
{: shortdesc}

**Remarque **: Le terme _espace de travail_ est utilisé dans {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}, alors que dans {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace, on parle de _projet_. La fonctionnalité est la même. Seule la terminologie est différente.

**Attention** : Si vous devez vous conformer au RGPD, vous devez migrer sur la plateforme {{site.data.keyword.cloud_notm}}. {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace a été retiré du service et ne convient pas aux clients qui doivent se conformer au Règlement général sur la protection des données (RGPD) de l'Union Européenne (UE) 2016/679.

## Processus 
{: #process}

Le processus de migration de vos projets {{site.data.keyword.knowledgestudioshort}} dépend de votre abonnement à {{site.data.keyword.IBM_notm}} Marketplace, comme le montre le tableau suivant :

| Abonnement | Processus de migration |Détails |
|------|-------------------|--------------------|
| Plan Standard avec abonnement libre-service | Le client fait migrer l'instance et les données | Migrez dès que possible pour obtenir l'accès à la version la plus à jour de {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}.
| Plan Standard avec contrat d'abonnement | {{site.data.keyword.IBM_notm}} fait migrer le contrat d'abonnement. Le client fait migrer l'instance et les données. | Contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Plan Premium avec contrat d'abonnement | {{site.data.keyword.IBM_notm}} fait migrer le contrat d'abonnement. {{site.data.keyword.IBM_notm}} fait migrer l'instance et les données. | Contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tableau 1. Processus et calendrier de migration de {{site.data.keyword.knowledgestudioshort}} d'{{site.data.keyword.IBM_notm}} vers {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Automigration des instances de plan standard
{: migratestandard}

Si vous avez un plan Standard, effectuez les étapes suivantes pour faire migrer votre instance d'{{site.data.keyword.IBM_notm}} Marketplace vers {{site.data.keyword.cloud_notm}} :

1. Si vous n'avez pas de compte {{site.data.keyword.cloud_notm}}, inscrivez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/registration/){: new_window} en utilisant votre {{site.data.keyword.ibmid}} d'{{site.data.keyword.IBM_notm}} Marketplace.

   Votre {{site.data.keyword.ibmid}} est l'ID que vous utilisez pour vous connecter à {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace.

2. Connectez-vous à [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}.
3. Si votre compte {{site.data.keyword.cloud_notm}} est un compte Lite, passez à un compte payant. Pour plus d'informations sur les comptes payants, consultez [Types de comptes ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/account/index.html){: new_window}.
4. A partir de la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/knowledge-studio){: new_window}, créez un plan Standard {{site.data.keyword.knowledgestudioshort}}.
5. Suivez les instructions à l'écran, en indiquant que vous voulez faire migrer une instance d'{{site.data.keyword.IBM_notm}} Marketplace sur {{site.data.keyword.cloud_notm}}.
6. Si vous avez plusieurs instances à faire migrer, répétez le processus.

## Migration d'instances de plan Premium
{: migratesubscription}

Si vous avez un plan Premium {{site.data.keyword.knowledgestudioshort}}, contactez votre représentant de compte désigné {{site.data.keyword.IBM_notm}} ou envoyez un e-mail au service [{{site.data.keyword.cloud_notm}} Sales ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Une fois l'abonnement migré sur {{site.data.keyword.cloud_notm}}, IBM se chargera de faire migrer vos données conformément à un calendrier négocié entre vous et {{site.data.keyword.IBM_notm}}.
