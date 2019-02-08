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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}.
{: tip}

# Incluindo documentos para definir regras
{: #wks_rule_anno_add}

Inclua documentos com padrões linguísticos que ilustram os tipos de regras você deseja definir.
{: shortdesc}

Os documentos que você inclui para definir regras são mantidos separados dos documentos incluídos para anotação. Seu único propósito é ser usado para obter exemplos de padrões. Eles não são usados para treinamento, nem mesmo transferidos por download.

## Maneiras pelas quais é possível incluir documentos no editor de regras

- **Criar um documento de texto no formato UTF-8**

    É possível incluir texto que ilustra um padrão diretamente no editor de regras. O nome que você especifica para o documento não pode ser maior que 256 caracteres.

- **Fazer upload de um arquivo CSV**

    Faça upload de um arquivo no formato CSV que contém o texto do documento.

- **Copiar um documento que foi importado para anotação**

    Se um documento que faz parte de um conjunto que foi importado para propósitos de anotação contém exemplos de padrões que você deseja capturar como regras, é possível copiar o documento no editor de regras. Nenhuma mudança feita no documento afeta a versão original do documento que está sendo usado para anotação. Veja [Incluindo documentos em uma área de trabalho](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd) para obter informações sobre o upload de documentos.

Para documentos que você copia ou faz upload, escolha aqueles que contêm padrões distintos que ajudam a identificar tipos de entidade em documentos.
