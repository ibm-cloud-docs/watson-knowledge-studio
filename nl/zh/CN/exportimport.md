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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}。
{: tip}

# 从其他工作空间上传资源
{: #exportimport}

要加速模型的创建，可以上传从其他工作空间下载的资源，如文档（包含或不包含参考标准注释）、类型系统以及字典。
{: shortdesc}

通过单独下载和上传不同资源的功能，您可灵活地设计和创建模型。例如，您可以创建一个工作空间来设计类型系统并执行人工注释，然后再创建一个单独的工作空间（可能位于带有不同用户的单独 {{site.data.keyword.knowledgestudioshort}} 实例中）来培训机器学习模型。通过上传资源（包括由人类注释者创建的参考标准）的功能，可以实现此场景。

无法下载和上传机器学习模型。但可以从一个工作空间下载用于创建模型的所有工件，然后将其上传到新的工作空间。在新的工作空间中，可以再次运行培训来重新创建模型。新模型应该会生成与原始模型类似的结果，因为这两个模型都是使用同一组工件培训的。

下载的文件与操作系统无关。在其中下载和上传文件的 {{site.data.keyword.knowledgestudioshort}} 实例不必运行相同的 Linux 版本。

## 类型系统
{: #wks_exportimport_expimp_type}

要下载类型系统，请打开**资产和工具** > **实体类型**页面，然后单击**下载类型**。系统将创建名为 `type-ID.json` 的文件，并提示您将该文件下载到本地系统。要在新工作空间中使用此类型系统，请打开**实体类型**页面，并上传已下载的 `JSON` 文件。

## 字典
{: #wks_exportimport_expimp_dict}

要下载一个或多个字典，请选择**资产和工具** > **预注释器** > **字典**选项卡，然后单击**下载字典**。对于下载的每个字典，系统都将创建名为 `dictionary name_timestamp.csv` 的文件，然后系统会将这些文件组合到名为 `workspace name_dictionary_timestamp.zip` 的 `ZIP` 文件中，并提示您将该文件下载到本地系统。您还可以通过打开字典并单击**下载**来下载单个字典。但无法下载上传为字典 CSV 文件的仅预览字典。

将已下载的字典上传到新工作空间之前，必须先从旧工作空间下载类型系统，并将其上传到新工作空间中。类型系统和字典必须源自同一个 {{site.data.keyword.knowledgestudioshort}} 工作空间，并且上传字典之前，该类型系统必须在新的工作空间中存在。

要上传字典，请打开**字典**选项卡，然后添加已下载的 `CSV` 文件或上传 `ZIP` 文件。

## 文档
{: #wks_exportimport_expimp_doc}

要下载已添加到语料库的文档，请打开**资产和工具** > **文档** > **文档集**选项卡，然后单击**下载文档集**。系统将创建名为 `corpus-ID.zip` 的文件，并提示您将该文件下载到本地系统。该 `ZIP` 文件包含语料库中的所有文档。添加到注释集的注释将包含在该 ZIP 文件中，但仅在这些注释集得到核准并升级为参考标准后才会包含在内。

> **限制**：下载任何预注释的文档时，这些文档都会隐藏为不可读格式。即使这些文档中通过人工注释添加的注释也是不可读的。

将包含参考标准的文档上传到新工作空间之前，必须先从旧工作空间下载类型系统，并将其上传到新工作空间中。类型系统和文档必须源自同一个 {{site.data.keyword.knowledgestudioshort}} 工作空间，并且上传参考标准注释之前，该类型系统必须在新的工作空间中存在。

要上传文档，请在新工作空间中打开**文档集**选项卡，单击**上传文档集**，然后选择已下载的语料库 `ZIP` 文件。在单击**上传**之前，请指定是希望上传的文档包含还是排除参考标准注释。系统只会上传在下载文档之前升级为参考标准的注释。

**相关概念**：

[类型系统](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[字典](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[机器学习注释器的文档](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[基于规则的注释器的文档](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
