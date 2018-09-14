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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migración a IBM Cloud
{: #migrate}

El 18 de diciembre de 2017, IBM lanzó {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud_notm}}, lo que marca el inicio del proceso para migrar todas las instancias de {{site.data.keyword.knowledgestudioshort}} de {{site.data.keyword.IBM_notm}} Marketplace a la plataforma [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}.
{: shortdesc}

**Nota**: {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}} utiliza el término _espacio de trabajo_, mientras que {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace utiliza el término _proyecto_. La funcionalidad es la misma. Solo la terminología es distinta.

**Atención**: si tiene que cumplir con el GDPR, debe migrar a la plataforma {{site.data.keyword.cloud_notm}}. {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace se ha retirado y no es adecuado para clientes que necesiten cumplir con el Reglamento General de Protección de Datos de la Unión Europea (GDPR) (EU) 2016/679.

## Proceso
{: #process}

El proceso de migración para los proyectos de {{site.data.keyword.knowledgestudioshort}} depende de la suscripción de {{site.data.keyword.IBM_notm}} Marketplace, como se muestra en la tabla siguiente.

| Suscripción | Proceso de migración | Detalles |
|------|-------------------|--------------------|
| Plan estándar con una suscripción de autoservicio | El cliente migra instancias y datos | Migre lo antes posible para acceder a la versión más actualizada de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}}.
| Plan estándar con un contrato de suscripción | {{site.data.keyword.IBM_notm}} migra el contrato de suscripción. El cliente migra la instancia y los datos. | Póngase en contacto con su representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Plan premium con contrato de suscripción | {{site.data.keyword.IBM_notm}} migra el contrato de suscripción. {{site.data.keyword.IBM_notm}} migra la instancia y los datos. | Póngase en contacto con su representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabla 1. Proceso y planificación para migrar {{site.data.keyword.knowledgestudioshort}} de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migración automática de instancias de plan estándar
{: migratestandard}

Si tiene un plan estándar, complete los pasos siguientes para migrar la instancia de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Si no tiene una cuenta de {{site.data.keyword.cloud_notm}}, regístrese en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/registration/){: new_window} utilizando el {{site.data.keyword.ibmid}} de {{site.data.keyword.IBM_notm}} Marketplace.

   Su {{site.data.keyword.ibmid}} es el ID que utiliza para iniciar sesión en {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace.

2. Inicie sesión en [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net){: new_window}.
3. Si su cuenta de {{site.data.keyword.cloud_notm}} es una cuenta Lite, actualice a una cuenta de pago. Para obtener más información sobre los tipos de cuentas de pago, consulte [Tipos de cuenta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/account/index.html){: new_window}.
4. En la consola de [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}, cree un plan estándar de {{site.data.keyword.knowledgestudioshort}}.
5. Siga las instrucciones de la pantalla, indicando que desea migrar una instancia de {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}.
6. Si tiene más de una instancia para migrar, repita el proceso.

## Migración de instancias del plan premium
{: migratesubscription}

Si tiene un Plan premium de {{site.data.keyword.knowledgestudioshort}}, póngase en contacto con el representante de cuenta designado de {{site.data.keyword.IBM_notm}} o póngase en contacto con [Ventas de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Una vez que se haya migrado la suscripción a {{site.data.keyword.cloud_notm}}, IBM migrará sus datos en una planificación negociada entre usted e {{site.data.keyword.IBM_notm}}.
