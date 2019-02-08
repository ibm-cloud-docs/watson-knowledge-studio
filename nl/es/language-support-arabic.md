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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/language-support-arabic.html){: new_window}.
{: tip}

# Configuración de soporte para árabe
{: #wks_langsupp_ar}

Lea estas directrices para comprender cómo maneja {{site.data.keyword.knowledgestudioshort}} el formato de caracteres y el formato numérico en árabe en documentos en árabe.

## Acerca de esta tarea

Con respecto al formato de caracteres, el alfabeto árabe no tiene letras en mayúscula, sino que letras pueden cambiar de forma dependiendo de su posición en la serie de texto y de las letras circundantes. Distintos sistemas operativos y programas de conversión de la página de códigos manejan el formato de las letras de formas distintas. El almacenamiento sin formato es un estándar para los sistemas Windows, y {{site.data.keyword.knowledgestudioshort}} presupone que el texto en árabe se almacena sin formato. Si desea cargar texto con formato en {{site.data.keyword.knowledgestudioshort}}, primero debe convertir el texto a formato sin formato utilizando las herramientas estándares, como la API de ICU (International Components for Unicode) (consulte la ArabicShaping Class en [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}).

> **Importante:** En algunos casos, la falta de formato de caracteres en árabe correctos puede hacer que el contenido se muestre incorrectamente en el editor de datos de campo.

En cuanto al formato numérico, {{site.data.keyword.knowledgestudioshort}} trata el formato numérico como una propiedad de nivel de almacenamiento, similar a cómo se maneja el contenido en árabe en la plataforma iOS. Dado que mucho contenido en árabe se crea en plataformas como Windows, que tratan el formato numérico como una propiedad a nivel de visualización, debe convertir el contenido para que una propiedad de nivel de almacenamiento tenga formato numérico o utilizar un navegador Firefox al utilizar {{site.data.keyword.knowledgestudioshort}}. Firefox permite establecer preferencias de forma numérica explícitamente en el nivel del navegador y aplicar la visualización adecuada para todo el contenido mostrado en el navegador.

## Procedimiento

Para configurar el formato numérico en el navegador Firefox:

1. En el campo URL del navegador, escriba **about:config**. Si se muestra un aviso de Firefox, pulse la acción para descartar el aviso y continúe. Para obtener información sobre cómo editar las propiedades **about:config**, consulte [http://kb.mozillazine.org/About:config_entries ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://kb.mozillazine.org/About:config_entries){: new_window}.
1. Escriba `bidi` en el campo de filtro de búsqueda.
1. Seleccione la propiedad **bidi.numeral**, que controla cómo se visualizan los numerales, y pulse Intro.
1. Cambie el valor de esta propiedad según sea necesario. Por ejemplo, escriba `3` y, a continuación, pulse **Aceptar**.

    - **0**: Números nominales (el valor predeterminado)
    - **1**: Números de contexto regular
    - **2**: Números de contexto hindi
    - **3**: Números arábigos
    - **4**: Números hindis

    > **Importante:** Cuando se utiliza la propiedad **bidi.numeral**, Firefox ignora completamente el punto de código de caracteres de dígitos específicos en el contenido de una página web.

### Referencia relacionada

[Soporte de idioma](/docs/services/watson-knowledge-studio/language-support.html)
