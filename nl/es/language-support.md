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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/language-support.html){: new_window}.
{: tip}

# Soporte de idioma
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} proporciona soporte para entrenar un modelo en varios idiomas.

El soporte para varios idiomas no significa que el propio producto esté traducido. Las interfaces de usuario, los mensajes y la documentación de {{site.data.keyword.knowledgestudioshort}} están disponibles solo en inglés.
{: shortdesc}

Puede entrenar un modelo en los idiomas siguientes:

- Inglés (el idioma predeterminado)
- Árabe
- Portugués de Brasil
- Chino (simplificado)
- Neerlandés
- Francés
- Alemán
- Italiano
- Japonés
- Coreano
- Español

El soporte incluye la capacidad de añadir documentos en estos idiomas a un espacio de trabajo, añadir diccionarios, ejecutar la preanotación, utilizar el editor de datos de campo para anotar documentos, y entrenar un modelo de aprendizaje automático. Cuando seleccione un idioma, el sistema aplica plantillas específicas del idioma para manejar entradas de diccionario, señalización de texto y segmentación de frases. Para obtener información sobre cómo maneja el sistema diccionarios en distintos idiomas, consulte [Diccionarios](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries).

> **Nota:** El editor de reglas y el modelo basado en reglas no pueden manejar texto bidireccional, por lo que no puede utilizarlos con documentos en árabe.

> **Restricciones:**
>
> Debido a restricciones de caracteres en la tecnología de aprendizaje automático subyacente, las entradas del sistema de tipos no pueden contener espacios y solo pueden incluir los siguientes caracteres ASCII:
>
> - De A a Z y de a a z
> - De 0 a 9
> - El carácter de subrayado: _
>
> También se aplican las reglas siguientes:
>
> - El primer carácter del nombre debe ser alfabético.
> - La longitud del nombre de tipo de entidad no puede superar los 64 caracteres.
> - La longitud del nombre del tipo de relación no puede superar los 128 caracteres.
>
> Así, por ejemplo, cuando un anotador humano anota texto en japonés en el editor de datos de campo, los nombres de tipo de entidad y de tipo de relación que se pueden aplicar no estarán en japonés.

### Tareas relacionadas

[Configuración de soporte para árabe](/docs/services/watson-knowledge-studio/language-support-arabic.html)
