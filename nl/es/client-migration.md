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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migración a IBM Cloud
{: #migrate}

El 18 de diciembre de 2017, IBM lanzó {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud_notm}}, lo que marca el inicio del proceso para migrar todas las instancias de {{site.data.keyword.knowledgestudioshort}} de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}.
{: shortdesc}

**Nota**: {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}} utiliza el término _espacio de trabajo_, mientras que {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace utiliza el término _proyecto_. La funcionalidad es la misma. Solo la terminología es distinta.

## Proceso y planificación
{: #process}

El proceso y la planificación de migración para los proyectos de {{site.data.keyword.knowledgestudioshort}} depende del [plan de precios de {{site.data.keyword.IBM_notm}} Marketplace actual ![Icono de plan de precios](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} y del tipo de cuenta, como se muestra en la tabla siguiente:

| Plan y cuenta | Proceso de migración | Planificación de migración |
|------|-------------------|--------------------|
| Plan gratuito | El cliente migra instancias y datos | Las migraciones deben completarse el o antes del 1 de febrero de 2018. El 2 de febrero de 2018, todos los Planes gratuitos de {{site.data.keyword.IBM_notm}} Marketplace se depurarán, incluidos los datos de proyecto asociados. |
| Plan estándar con cuenta de pago según uso | El cliente migra instancias y datos | Las migraciones deben completarse el o antes del 29 de junio de 2018. El 30 de junio de 2018, todos los Planes estándares con cuentas de pago según uso de {{site.data.keyword.IBM_notm}} Marketplace se depurarán, incluidos los datos de proyecto asociados.
| Plan estándar en contrato | El cliente migra la instancia y los datos. {{site.data.keyword.IBM_notm}} renueva el contrato. | Las migraciones deben completarse el o antes del 29 de junio de 2018. Póngase en contacto con su representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Plan premium en contrato | {{site.data.keyword.IBM_notm}} migra la instancia y los datos. {{site.data.keyword.IBM_notm}} renueva el contrato. | Las migraciones deben completarse el o antes del 29 de junio de 2018. Póngase en contacto con su representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabla 1. Proceso y planificación para migrar {{site.data.keyword.knowledgestudioshort}} de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migración de planes gratuitos
{: migratefree}

Si tiene un plan gratuito de {{site.data.keyword.knowledgestudioshort}}, siga los pasos siguientes para migrar su instancia y proyectos de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Si no tiene una cuenta de {{site.data.keyword.cloud_notm}}, regístrese en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/wks_cloud){: new_window} utilizando el {{site.data.keyword.ibmid}} de {{site.data.keyword.IBM_notm}} Marketplace.

   Su {{site.data.keyword.ibmid}} es el ID que utiliza para iniciar sesión en {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace.

1. Inicie sesión en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Si no tiene una instancia de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}}, cree una en la página {{site.data.keyword.knowledgestudioshort}} del catálogo de [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Siga el proceso de [copia de seguridad y restauración](/docs/services/watson-knowledge-studio/backup-restore.html) para migrar manualmente los proyectos desde la instancia de {{site.data.keyword.IBM_notm}} Marketplace a su instancia de {{site.data.keyword.cloud_notm}}.

  **Nota**: Si tiene un modelo que ya está desplegado y piensa suprimir el espacio de trabajo después de realizar su copia de seguridad, retire el modelo del despliegue. Puede volver a crear y a desplegar el modelo después de restaurar el espacio de trabajo desde la copia de seguridad. Para obtener información sobre la retirada de modelos, consulte [Retirada de modelos de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) y [Retirada de modelos basados en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migración de Planes estándares para las cuentas de pago según uso
{: migratepaygo}

Si tiene un Plan estándar y una cuenta de [pago según uso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/pricing/billable.html){: new_window}, siga estos pasos para migrar su instancia y proyectos de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Si no tiene una cuenta de {{site.data.keyword.cloud_notm}}, regístrese en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/){: new_window} utilizando el {{site.data.keyword.ibmid}} de {{site.data.keyword.IBM_notm}} Marketplace.

   Su {{site.data.keyword.ibmid}} es el ID que utiliza para iniciar sesión en {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace.

1. Inicie sesión en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Si no tiene una instancia de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}}, cree una en la página {{site.data.keyword.knowledgestudioshort}} del catálogo de [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Siga el proceso de [copia de seguridad y restauración](/docs/services/watson-knowledge-studio/backup-restore.html) para migrar manualmente los proyectos desde la instancia de {{site.data.keyword.IBM_notm}} Marketplace a su instancia de {{site.data.keyword.cloud_notm}}.

  **Nota**: Si tiene un modelo que ya está desplegado y piensa suprimir el espacio de trabajo después de realizar su copia de seguridad, retire el modelo del despliegue. Puede volver a crear y a desplegar el modelo después de restaurar el espacio de trabajo desde la copia de seguridad. Para obtener información sobre la retirada de modelos, consulte [Retirada de modelos de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) y [Retirada de modelos basados en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migración de Planes estándares para las cuentas de contrato
{: migratecontract}

Si tiene un Plan estándar de {{site.data.keyword.knowledgestudioshort}} en contrato, siga estos pasos para renovar el contrato y migrar su instancia y proyectos de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Para renovar el contrato, póngase en contacto con el representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration).
1. Después de renovar su contrato en {{site.data.keyword.cloud_notm}}, inicie sesión en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Si no tiene una instancia de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}}, cree una en la página {{site.data.keyword.knowledgestudioshort}} del catálogo de [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Siga el proceso de [copia de seguridad y restauración](/docs/services/watson-knowledge-studio/backup-restore.html) para migrar manualmente los proyectos desde la instancia de {{site.data.keyword.IBM_notm}} Marketplace a su instancia de {{site.data.keyword.cloud_notm}}.

  **Nota**: Si tiene un modelo que ya está desplegado y piensa suprimir el espacio de trabajo después de realizar su copia de seguridad, retire el modelo del despliegue. Puede volver a crear y a desplegar el modelo después de restaurar el espacio de trabajo desde la copia de seguridad. Para obtener información sobre la retirada de modelos, consulte [Retirada de modelos de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) y [Retirada de modelos basados en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migración de Planes premium para las cuentas de contrato
{: migratecontract}

Si tiene un Plan premium de {{site.data.keyword.knowledgestudioshort}} en contrato, póngase en contacto con el representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Una vez renovado el contrato en {{site.data.keyword.cloud_notm}}, IBM migrará sus datos en una planificación negociada entre usted y {{site.data.keyword.cloud_notm}}.
