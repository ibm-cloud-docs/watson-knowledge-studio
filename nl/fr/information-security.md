---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-27"

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

# Sécurité de l'information
{: #information-security}

IBM se donne pour mission de fournir à ses clients et partenaires des solutions innovantes de confidentialité, de sécurité et de gouvernance des données.
{: shortdesc}

**Remarque :**
Il appartient à chaque entreprise de se conformer aux lois et réglementations, notamment relatives à la protection des données personnelles. Il relève de la seule responsabilité du client de consulter les services juridiques compétents aussi bien pour identifier et interpréter les lois et règlements susceptibles d’affecter son activité, que pour toute action à entreprendre pour se mettre en conformité avec ces lois et réglementations.

Les produits, services et autres fonctionnalités décrits ici ne sont pas adaptés à toutes les situations client et ne pourront être proposés que sous réserve de disponibilité. IBM ne donne aucun avis juridique, comptable ou d'audit et ne garantit pas que ses produits ou services permettent aux clients de se conformer aux lois ou réglementations applicables.

Si vous avez besoin d'une assistance RGPD pour les ressources {{site.data.keyword.cloud}} {{site.data.keyword.watson}} qui sont créées

- Dans l'Union Européenne, consultez [Requesting support for IBM Cloud Watson resources created in the European Union ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/watson/getting-started-gdpr-sar.html#request-EU){: new_window}.
- En dehors de l'Union Européenne, consultez [Requesting support for resources outside the European Union ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU){: new_window}.

## Règlement général sur la protection des données (RGPD) de l'Union Européenne
{: #gdpr}

IBM se donne pour mission de fournir à ses clients et partenaires des solutions innovantes de confidentialité, de sécurité et de gouvernance des données pour les accompagner dans leur mise en conformité au RGPD.

Pour en savoir plus sur la mise en conformité d'IBM avec le RGPD, ainsi que sur nos offres et fonctionnalités liées au RGPD, visitez [cette page ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/gdpr){: new_window}.

## RGPD dans {{site.data.keyword.knowledgestudioshort}}
{: #gdpr-wks}

{{site.data.keyword.knowledgestudiofull}} fournit une interface graphique à travers laquelle vous pouvez accéder à et supprimer des artefacts transférés qui contiennent des données. Les artefacts suivants peuvent être transférés vers {{site.data.keyword.knowledgestudioshort}} :
- Systèmes de types
- Dictionnaires
- Documents

Si vous recevez une demande de suppression de données, effectuez les étapes suivantes :
1. [Supprimez l'artefact concerné](/docs/services/watson-knowledge-studio/artifacts.html).
2. [Réentraînez et redéployez le modèle](/docs/services/watson-knowledge-studio/train-ml.html).
3. [Supprimez les précédentes versions du modèle qui utilisaient les données supprimées](/docs/services/watson-knowledge-studio/improve-ml.html#wks_maversions).
