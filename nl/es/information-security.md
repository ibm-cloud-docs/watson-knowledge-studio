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

# Seguridad de la información
{: #information-security}

IBM se ha comprometido a proporcionar a nuestros clientes y socios soluciones innovadoras de privacidad, seguridad y gobierno de datos.
{: shortdesc}

**Aviso:**
Los clientes son responsables de garantizar su propio cumplimiento con diversas leyes y reglamentos, incluido el Reglamento General de Protección de Datos de la Unión Europea. Los clientes son los únicos responsables de obtener asesoramiento legal competente referente a la identificación y la interpretación de cualquier ley relevante que pudiera afectar a su negocio, así como cualquier medida que debieran tomar para cumplir con dichas leyes y normativas.

Los productos, los servicios y otras prestaciones descritas en este documento no son adecuados para todas las situaciones de los clientes y su disponibilidad puede estar restringida. IBM no proporciona recomendaciones legales, contables o de auditoría ni garantiza que sus servicios o productos garantizarán que los clientes cumplan ninguna legislación o normativa.

Si tiene que solicitar soporte de GDPR para los recursos de {{site.data.keyword.cloud}} {{site.data.keyword.watson}} que se crean

- En la Unión Europea, consulte [Solicitud de soporte para recursos de IBM Cloud Watson creados en la Unión Europea ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/watson/getting-started-gdpr-sar.html#request-EU){: new_window}.
- Fuera de la Unión Europea, consulte [Solicitud de soporte para recursos fuera de la Unión Europea ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU){: new_window}.

## Reglamento General de Protección de Datos de la Unión Europea (GDPR)
{: #gdpr}

IBM se ha comprometido a proporcionar a nuestros clientes y socios soluciones innovadoras de privacidad, seguridad y gobierno de datos para ayudarles a cumplir con el GDPR.

Obtenga más información sobre la implantación del GDPR en IBM y las prestaciones y las ofertas de GDPR para ayudarle a cumplirlo [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/gdpr){: new_window}.

## GDPR en {{site.data.keyword.knowledgestudioshort}}
{: #gdpr-wks}

{{site.data.keyword.knowledgestudiofull}} proporciona una interfaz gráfica a través de la cual puede acceder y suprimir los artefactos cargados que contienen datos. Los siguientes artefactos se pueden cargar en {{site.data.keyword.knowledgestudioshort}}:
- Sistemas de tipos
- Diccionarios
- Documentos

Si recibe una solicitud para suprimir datos, complete los pasos siguientes:
1. [Suprima el artefacto correspondiente](/docs/services/watson-knowledge-studio/artifacts.html).
2. [Vuelva a entrenar y vuelva a desplegar el modelo](/docs/services/watson-knowledge-studio/train-ml.html).
3. [Suprima las versiones anteriores del modelo que utilizaba los datos suprimidos](/docs/services/watson-knowledge-studio/improve-ml.html#wks_maversions).
