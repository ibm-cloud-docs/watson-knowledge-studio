---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-26"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}.
{: tip}

# Criando o modelo baseado em regra
{: #wks_rule_train}

Depois de definir regras, é possível criar um modelo baseado em regra.
{: shortdesc}

## Procedimento

Para criar um modelo baseado em regra. Conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Baseado em regra**.
1. Mapeie os tipos de entidade de seu sistema de tipos para uma ou mais classes que você usou para definir regras.

  Após os tipos de entidade serem mapeados, é possível [implementar o modelo baseado em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html) ou usá-lo para [pré-anotar documentos](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) no processo de criação de um modelo de aprendizado de máquina.

## Excluindo um modelo baseado em regra
{: #wks_rule_delete_model}

Não é possível excluir um modelo baseado em regra.

É possível excluir a área de trabalho que foi usada para desenvolver o modelo baseado em regra, mas não é possível excluir o modelo em si. Excluir um modelo não é a melhor abordagem. Em vez disso, recrie as regras definidas para ele. Editar as regras diretamente muda o comportamento do modelo baseado em regra.
