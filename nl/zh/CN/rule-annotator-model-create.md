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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}。
{: tip}

# 创建基于规则的模型
{: #wks_rule_train}

定义规则后，可以创建基于规则的模型。
{: shortdesc}

## 过程

要创建基于规则的模型，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **基于规则**选项卡。
1. 将类型系统中的实体类型映射到用于定义规则的一个或多个类。

  映射实体类型后，可以[部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)，或者在创建机器学习模型的过程中，使用该模型来[对文档进行预注释](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)。

## 删除基于规则的模型
{: #wks_rule_delete_model}

无法删除基于规则的模型。

可以删除用于开发基于规则的模型的工作空间，但无法删除该模型本身。删除模型并不是最佳方法。请改为重新创建为模型定义的规则。编辑规则会直接更改基于规则的模型的行为。
