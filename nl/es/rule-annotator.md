---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator.html){: new_window}.
{: tip}

# Reglas
{: #rule-annotator}

Cree un modelo basado en reglas que pueda reconocer patrones en los documentos. Utilice reglas para capturar patrones que se produzcan en documentos y transmita información sobre tipos de entidades subyacentes.
{: shortdesc}

## Visión general de la clase

Al construir una regla, utilice clases para representar tipos de información. Estas clases son similares a los tipos de entidades. Entonces, ¿por qué no utilizamos simplemente los tipos de entidades al definir reglas? Porque al crear reglas, puede definir clases intermedias que se utilicen solo para crear otras clases más complejas. Estas clases intermedias son exclusivamente utilitarias. No son útiles por sí solas. Las clases intermedias funcionan con otras clases intermedias para definir una clase más útil y completa. Una clase intermedia es necesaria, pero no algo que exponga como parte de un sistema de tipos. Para habilitar el modelo basado en reglas para hacer cosas útiles como preanotar documentos con menciones de entidades, debe correlacionar las clases complejas que utilice durante la creación de reglas con sus tipos de entidades equivalentes del sistema de tipos.

Por ejemplo, desea un modelo que pueda reconocer nombres de personas. Para entrenar un modelo de aprendizaje automático para que reconozca nombres de personas, debe anotar muchos nombres distintos escritos en una variedad de formatos en documentos en un conjunto de anotaciones con el tipo de entidad `PERSON`, y entrenar un modelo para que reconozca nombres de personas. Para crear un modelo basado en reglas para que reconozca nombres de personas, defina una regla que describa los patrones de texto utilizados para escribir los nombres de personas. Así, podría crear una clase `FirstName` y una clase `LastName` y utilizar estas clases intermedias para definir una clase `FullName`. Puede definir condiciones que determinen la colocación de la clase `FullName` en relación con prefijos comunes, como `Dr.` y sufijos comunes, como `Jr.`. Cuando se utiliza el modelo basado en reglas, la clase `FullName` se correlaciona con el tipo de entidad `PERSON`.

Otro motivo para evitar correlacionar clases intermedias a entidades del sistema de tipos es que si preanota documentos con el modelo basado en reglas, y a continuación los añade a los datos de campo para entrenar un modelo de aprendizaje automático, no deseará definir reglas de tal forma que haga que se solapen las menciones de entidades. Por ejemplo, si fuera a correlacionar la clase intermedia `FirstName` y la clase compleja `FullName` con la entidad `PERSON`, se podría dar lugar a una aparición de `Juan Pérez, Jr.` en una mención que se solape.

## Herramientas del editor de reglas

El editor de reglas proporciona algunas herramientas que le ayudan a definir reglas.

- Diccionario

    Añada un diccionario y asígnele un nombre de clase. Las palabras que se encuentren que coincidan con las entradas del diccionario se anotarán automáticamente con la clase asignada.

- Expresión regular

    Una expresión regular (regex) es una secuencia de caracteres que define un patrón de búsqueda. La herramienta regex incluida en el editor de reglas reconoce expresiones que siguen la sintaxis `java.util.regex.Pattern`. Aquí hay un ejemplo básico:
    `[A-Z][a-z]*`: Busca palabras en mayúscula.

    `[A-Z]` coincide con cualquier letra alfabética en mayúscula (de la A a la Z) y `[a-z]*` coincide con cualquier letra alfabética en minúscula (de la a a la z) cero o más veces. El asterisco (*) es el carácter que define el valor de repetición (cero o más veces).

    Considere la posibilidad de utilizar un programa de utilidad regex basado en web gratuito para ayudarle a determinar la expresión correcta que se utilizará para capturar el patrón que desea encontrar.

    Por ejemplo, sus documentos pueden tener muchas referencias similares a las siguientes frases:

    ```
    35-year-old driver
    16-year-old learner
    ```
    {: screen}

    La sintaxis `n-year-old x` es un patrón que normalmente representa a una persona. Puede definir una regla de expresión regular para buscar frases que coincidan con el patrón `n-year-old x`, y anotarlas como menciones de entidad `PERSON`.
