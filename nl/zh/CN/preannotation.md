---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/preannotation.html){: new_window}。
{: tip}

# 引导注释
{: #preannotation}

通过对工作空间中的文档进行预注释，可简化人工注释者的工作。预注释器是 {{site.data.keyword.knowledgestudioshort}} 字典、基于规则的模型或机器学习模型，您可以运行预注释器来自动查找并注释提及项。
{: shortdesc}

预注释使人工注释者的工作更轻松，因为它涵盖简单明了的注释，并开始开展对文档进行注释的作业。

用于对文档进行预注释的方法绝不会限制您可以使用所生成模型的方式。例如，仅仅因为使用 {{site.data.keyword.nlushort}} 服务来对文档进行预注释，并不意味着您必须将构建的最终机器学习模型部署到 {{site.data.keyword.nlushort}} 服务。预注释仅用于引导人工注释过程。

## 重要注意事项
{: #preannotation_notes}

- 切勿对人工注释者已注释的文档运行预注释器，因为这将除去人工注释者添加的注释。
- 只能对文档运行一个预注释器。如果运行了一个预注释器，然后运行第二个预注释器，那么第二个预注释器将除去第一个预注释器添加的注释。选取最适合您的用例的预注释方法，并仅使用这一个预注释器。

## 预注释方法
{: #preannotation_methods}

以下预注释器可用：

- **{{site.data.keyword.nlushort}}**

    一种预注释器，可用于在文档中自动查找实体的提及项。如果源文档有一般知识主题，那么此预注释器是不错的选择。如果要处理侧重于特定领域（如专利法研究）的高度专业化文档，那么字典预注释器或基于规则的模型可能是更好的选择。

- **字典**

    使用您提供的术语字典，并与实体类型相关联，以在文档中查找该实体类型的提及项。此选项最适用于具有独特或专业化术语的领域，因为此预注释器不会以机器学习预注释器的分析方式来分析使用了术语的上下文，而是依赖于该术语足够清楚明确而具有可解释的含义，与使用该术语的上下文无关。例如，将 *asbestos* 识别为矿物实体类型，要比确定 *squash*（可以指蔬菜、运动或有挤压某物的含义的动词）的实体类型更容易。

- **机器学习**

    使用机器学习模型自动对文档进行注释。仅当已使用 {{site.data.keyword.knowledgestudioshort}} 创建了机器学习模型时，此选项才可用。如果添加新文档集，那么可以运行先前创建的机器学习注释器来对新文档进行预注释。如果新文档集类似于最初培训机器学习注释器时使用的文档，那么这可能是进行预注释的最佳选择。

- **规则**

    使用基于规则的模型自动对文档进行注释。仅当已使用 {{site.data.keyword.knowledgestudioshort}} 创建了基于规则的模型时，此选项才可用。如果文档包含可以从中派生意义的记号的常用模式，那么此模型可能是不错的选择。它可以通过标识同时在文档中找到的字典术语的类类型，包含字典预注释器的某个功能（如果启用）。

或者，可以上传已注释的文档，并使用这些文档开始培训机器学习模型。不能对上传的已注释文档运行预注释器，否则将从这些文档中除去现有注释，并替换为仅由预注释器生成的注释。

> **注**：*可以*对已作为当前工作空间的一部分添加到参考标准的文档运行预注释器。这不会除去当前工作空间内已添加到文档且已复查、接受并升级为参考标准的注释。

## 使用 {{site.data.keyword.nlushort}} 对文档进行预注释
{: #wks_preannotnlu}

可以使用 {{site.data.keyword.nlushort}} 服务对添加到语料库的文档进行预注释。

### 开始之前
{: #wks_preannotnlu_prereqs}

确定 {{site.data.keyword.nlushort}} 预注释器是否有可能为您的用例增加价值。查看支持的 [{{site.data.keyword.nlushort}} 服务实体类型和子类型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/natural-language-understanding/entity-types.html){: new_window} 的列表，以确定它们与类型系统中的类型之间是否存在自然重叠。如果是，请继续执行此过程。否则，请选择其他预注释器来使用。

### 关于本任务
{: #wks_preannotnlu_about}

{{site.data.keyword.nlushort}} 是通过自然语言处理来提供文本分析的服务。使用 {{site.data.keyword.nlushort}} 预注释器时，它会调用 {{site.data.keyword.nlushort}} 服务以在文档中查找和注释实体。

必须通过将 {{site.data.keyword.nlushort}} 实体类型映射到已添加到 {{site.data.keyword.knowledgestudioshort}} 类型系统的相应 {{site.data.keyword.knowledgestudioshort}} 实体类型，指定希望服务查找的实体类型。仅会查找并注释映射的实体类型的提及项。

### 过程
{: #wks_preannotnlu_procedure}

要使用 {{site.data.keyword.nlushort}} 服务对文档进行预注释，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录，然后选择工作空间。
1. 选择**机器学习模型** > **预注释** > **Natural Language Understanding** 选项卡。
1. 单击**编辑**以将**实体类型**页面上定义的每个实体类型映射到相应的 {{site.data.keyword.nlushort}} 实体类型。

    - {{site.data.keyword.nlushort}} 实体类型的下拉列表会使用 {{site.data.keyword.nlushort}} 服务识别到的实体类型进行预填充。
    - 必须至少映射一种实体类型。
    - 不能将 {{site.data.keyword.nlushort}} 实体类型映射到 {{site.data.keyword.knowledgestudioshort}} 实体角色，而只能映射到 {{site.data.keyword.knowledgestudioshort}} 实体类型。
    - 可以将多个 {{site.data.keyword.nlushort}} 实体类型映射到一个 {{site.data.keyword.knowledgestudioshort}} 实体类型，反之亦然。例如，允许以下映射：

    <table summary="样本实体类型映射">
    <caption>表 1. 样本实体类型映射</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">{{site.data.keyword.nlushort}} 实体类型</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENGINEER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Person
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          LOCATION
        </td>
        <td headers="d20428e298">
          CityTown<br/>
          Country
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. 在映射了要应用的所有实体类型后，单击**应用此预注释器**。

    至少映射一个实体类型后，**应用此预注释器**按钮才可用。

1. 选中要对其进行预注释的每个文档集的对应复选框。

    如果是第一次运行此预注释器，请先验证该预注释器是否可以按预期查找所映射实体的提及项。创建一个文档集，其中包含来自每个不同数据源的一个或多个代表性文档。
    {: tip}

1. 单击**运行**。

    如果要对预注释器执行验证检查，那么打开已注释的文档并复查已添加的注释。确保创建了足够数量的准确注释。如果注释准确，那么可以对更多和更大的文档集再次运行该注释器。如果注释不准确，那么考虑将不同的 {{site.data.keyword.nlushort}} 实体类型映射到您的类型。如果这些类型不自然重叠，说明 {{site.data.keyword.nlushort}} 预注释器并不是最适合您使用的预注释器。

    预注释会应用于单个文档，而不考虑文档可能属于的各种文档集。在所选文档集和未选文档集之间重叠的文档将在这两个文档集内进行预注释。

1. 运行一次预注释器后，如果要使用此预注释器对添加到语料库的其他文档集进行预注释，可以随时单击**应用此预注释器**。

    > **限制**：如果编辑了 {{site.data.keyword.nlushort}} 预注释器的类型映射定义，那么必须重新创建包含已预注释文档集的注释任务。对于基于对预注释器映射定义所做更改的预注释，无法将这些预注释应用于已分配给注释任务的文档集。

### 结果
{: #wks_preannotnlu__export-warning}

由 {{site.data.keyword.nlushort}} 服务预注释的文档所生成的参考标准不能直接在 {{site.data.keyword.knowledgestudioshort}} 外部使用。您可以下载参考标准（不可读格式）以将其从一个 {{site.data.keyword.knowledgestudioshort}} 工作空间移至另一个工作空间。您可以继续开发参考标准，并使用它来构建机器学习模型或基于规则的模型，这些模型可以部署用于 {{site.data.keyword.knowledgestudioshort}} 外部的服务。

> **限制**：下载使用 {{site.data.keyword.nlushort}} 预注释的文档时，这些文档都会隐藏为不可读格式。而且，这些文档中的所有注释也都会隐藏，包括人工注释者添加到文档的注释。

**相关信息**：

[{{site.data.keyword.nlushort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## 使用字典对文档进行预注释
{: #wks_preannot}

为了帮助人工注释者开始处理其注释任务，您可以创建字典，并使用该字典对添加到语料库的文档进行预注释。

### 关于本任务
{: #wks_preannot_about}

当人工注释者开始处理已预注释的文档时，可能有若干提及项已经基于字典条目由实体类型进行了标记。人工注释者可以更改或除去预注释的实体类型，也可以将实体类型分配给未注释的提及项。通过字典进行的预注释不会对关系和指代进行注释。关系和指代必须由人工注释者进行注释。

**注**：此任务显示如何创建可编辑的字典。如果要上传文档并使用只读字典对其进行预注释，请单击**创建字典**按钮旁边的**菜单**图标。选择**上传字典**。

### 过程
{: #wks_preannot_procedure}

要创建可编辑的字典并对文档进行预注释，请执行以下操作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录，然后选择工作空间。
1. 选择**资产** > **字典**页面。
1. 单击**创建字典**，输入名称，然后单击**保存**。
1. 从**实体类型**列表中，选择要与字典关联的实体类型。
3. 为字典添加条目或上传包含字典术语的文件。
4. 单击**机器学习模型** > **预注释**。
5. 在**字典**选项卡上，单击**应用此预注释器**。
6. 选中要对其进行预注释的每个文档集的对应复选框，然后单击**运行**。

    预注释会应用于单个文档，而不考虑文档可能属于的各种文档集或注释集。在所选文档集和未选文档集之间重叠的文档将在这两个文档集内进行预注释。

7. 创建字典后，如果要使用此字典对添加到语料库的其他文档集进行预注释，请随时单击**运行**。

    > **限制**：如果编辑字典以添加或除去条目，那么必须重新创建包含已预注释的文档集的注释任务。对于基于对字典注释器所做更改的预注释，无法将这些预注释应用于已分配给注释任务的注释集。

**相关信息**：

[创建字典](/docs/services/watson-knowledge-studio/dictionaries.html)

[入门 > 添加字典](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## 使用机器学习模型对文档进行预注释
{: #wks_preannotsire}

可以使用现有机器学习模型对添加到语料库的文档进行预注释。

### 关于本任务
{: #wks_preannotsire_about}

注释了 10 到 30 个文档后，可以基于这些数据来培训机器学习模型。此类最低限度培训的模型不应在生产中使用，但可用于对文档进行预注释，以帮助加快对后续文档的人工注释。例如，如果在培训机器学习模型后向语料库添加了文档，那么可以使用该模型对新的文档集进行预注释。切勿对已由人员注释的文档运行预注释器。预注释器会除去人工注释。

### 过程
{: #wks_preannotsire_procedure}

要使用现有机器学习模型对文档进行预注释，请执行以下操作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录，然后选择工作空间。
2. 选择**机器学习模型** > **版本**。
3. 要对新文档进行预注释，请单击**运行此模型**。
4. 选中要对其进行预注释的每个文档集的对应复选框，然后单击**运行**。

    预注释会应用于单个文档，而不考虑文档可能属于的各种文档集或注释集。在所选文档集和未选文档集之间重叠的文档将在这两个文档集内进行预注释。

5. 如果要使用机器模型对添加到语料库的其他文档集进行预注释，可以随时单击**运行此模型**。

## 使用基于规则的模型对文档进行预注释
{: #wks_preannotrule}

可以使用现有基于规则的模型对添加到语料库的文档进行预注释。

### 过程
{: #wks_preannotrule_procedure}

要使用基于规则的模型对文档进行预注释，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录，然后选择工作空间。
1. 选择**基于规则的模型** > **版本** > **基于规则的模型**选项卡。
1. 请单击**映射实体类型和类**以将 {{site.data.keyword.knowledgestudioshort}} 类型系统中定义的实体类型映射到一个或多个基于规则的模型类（如果尚未完成此操作）。
2. 对于要映射的每个实体类型，单击**编辑**。

    - **类名**列的下拉列表会使用与基于规则的模型关联的类进行预填充。
    - 必须至少将一个实体类型映射到类。

3. 在**基于规则的模型**选项卡上，单击**运行此模型**。

    至少将一个实体类型映射到类后，**应用此模型**按钮才可用。

4. 选择要对其进行预注释的文档集或注释集。请确保选择的集不包含具有人工注释的文档。预注释器会除去人工注释。
5. 单击**运行**。

    预注释会应用于单个文档，而不考虑文档可能属于的各种文档集。在所选文档集和未选文档集之间重叠的文档将在这两个文档集内显示为已预注释。

6. 如果要使用基于规则的模型对添加到语料库的其他文档集进行预注释，可以随时单击**运行此模型**。

    > **限制**：如果编辑了基于规则的模型的实体类型到类映射，那么必须重新创建包含已预注释的文档集的注释任务。对于基于对预注释器映射定义所做更改的预注释，无法将这些预注释应用于已分配给注释任务的文档集。

## 上传预注释的文档
{: #wks_uima}

可以通过上传通过非结构化信息管理体系结构 (UIMA) 分析引擎预注释的文档来快速启动模型培训。

预注释的文档必须为 UIMA 公共分析结构的 XMI 序列化格式 (UIMA CAS XMI)。上传的 ZIP 文件必须包含 UIMA TypeSystem 描述符文件以及用于将 UIMA 类型映射到 {{site.data.keyword.knowledgestudioshort}} 类型系统中实体类型的文件。

UIMA CAS XMI 是一种标准格式的 Apache UIMA。提供了有关如何通过 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中已分析集合来创建正确格式的文件的准则。如果使用其他 Apache UIMA 实现，请针对您的用途调整这些准则。无论以何种方式创建 XMI 文件，针对创建类型系统映射文件和 ZIP 文件的需求对于所有人都是相同的。

如果将导入的文档分配给人工注释者，那么这些文档会在参考标准编辑器中显示为已预注释，并且可能已对若干提及项进行注释。因此，人工注释者有更多时间专注于将注释准则应用于未标记的提及项。或者，可以绕过人工注释步骤，而使用预注释的文档来立即开始培训和评估机器学习模型。

### 从 Watson Explorer Content Analytics 导出已分析的文档
{: #wks_uimawexca}

可以导出在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics 中已搜寻并分析的文档，然后将已分析的文档作为 XMI 文件上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间。

#### 过程
{: #wks_uima_procedure}

要从 {{site.data.keyword.watson}} Explorer Content Analytics 集合中获取已分析的文档，请执行以下操作：

1. 在 Web 浏览器中打开 Content Analytics 管理控制台。
1. 在“集合”视图上，展开要从中导出文档的集合。在“解析和索引”窗格中，确保解析和索引过程正在运行，然后单击**导出已分析文档的内容和元数据**的箭头图标。
1. 在**已分析文档导出选项**区域中，选择**将文档导出为 XML 文件**，选中**启用 CAS 作为 XMI 格式导出**复选框，指定要写入所导出数据的输出路径，然后单击**确定**。
1. 停止并重新启动集合的解析和索引服务，然后执行下列其中一个步骤：

    - 如果集合已在文档高速缓存中包含要用于培训机器学习模型的建立索引的文档，请重新启动完全索引构建。
    - 如果集合未包含要用于培训机器学习模型的建立索引的文档，请上传文档，至少配置一个搜寻器来搜寻这些文档，然后启动该搜寻器。

1. 在**导出**区域中，检查导出请求的状态。进度会指示导出的文档数。
1. 转至在配置导出选项时指定的输出文件夹。将文档导出为 XML 文件时，输出文件夹名称基于执行导出时的时间戳记。输出文件夹包含 XMI 文件 (`*.xmi`) 和 UIMA TypeSystem 描述符文件 (`exported_typesystem.xml`)。

#### 后续步骤
{: #wks_uimawexca__preUIMAimport}

必须定义 UIMA 类型和 {{site.data.keyword.knowledgestudioshort}} 实体类型之间的映射。此外，还必须创建一个 ZIP 文件，其中包含将已分析的数据上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间所需的所有文件。

**相关信息**：

[导出已搜寻或已分析的文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[已导出文档的输出路径 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### 从 Content Analytics Studio 导出已分析的集合
{: #wks_uimawexstudio}

可以从 {{site.data.keyword.watson}} Explorer Content Analytics Studio 导出已分析文档的集合，并将已分析的文档作为 XMI 文件上传到 {{site.data.keyword.knowledgestudioshort}} 项目。

#### 过程
{: #wks_uimawexstudio_procedure}

要从 Content Analytics Studio 集合中获取已分析的文档，请执行以下操作：

1. 启动 Content Analytics Studio 并打开 Studio 项目。
1. 右键单击包含要用于培训机器学习模型的文档的文件夹，然后选择**分析集合**。
1. 选择 UIMA 管道配置文件。
1. 转至“集合分析”视图，然后单击“集合分析”视图中的**保存**图标。指定要将保存的结果写入的文件夹，并指定文件名。
1. 打开指定的文件夹。已保存文件的文件扩展名为 `.annotations`。
1. 将 `.annotations` 文件复制到本地文件系统，并将文件扩展名从 `.annotations` 重命名为 `.zip`。
1. 解压缩该 ZIP 文件中的所有文件。解压缩的内容包括 XMI 文件 (`*.xmi`)、UIMA TypeSystem 描述符文件 (`TypeSystem.xml`) 和其他文件。

#### 后续步骤
{: #wks_uimawexstudio_next}

必须定义 UIMA 类型和 {{site.data.keyword.knowledgestudioshort}} 实体类型之间的映射。此外，还必须创建一个 ZIP 文件，其中包含将已分析的数据上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间所需的所有文件。

### 将 UIMA 类型映射到实体类型
{: #wks_uimawexmap}

将 XMI 文件上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间之前，必须定义 UIMA 类型与 {{site.data.keyword.knowledgestudioshort}} 实体类型之间的映射。

#### 开始之前
{: #wks_uimawexmap_prereqs}

{{site.data.keyword.knowledgestudioshort}} 工作空间中的类型系统必须包含要将 UIMA 类型映射到的实体类型。

#### 过程
{: #wks_uimawexmap_procedure}

要将 UIMA 类型映射到 {{site.data.keyword.knowledgestudioshort}} 实体类型，请执行以下操作：

1. 在包含 UIMA TypeSystem 描述符文件（例如，`exported_typesystem.xml` 或 `TypeSystem.xml`）的文件夹中创建名为 `cas2di.tsv` 的文件。
1. 使用文本编辑器打开 `cas2di.tsv` 文件。该文件中的每一行都指定一个映射。映射的格式取决于您要映射哪个注释器的注释：

    - 可以使用基本格式来创建映射：

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        以下示例定义由 {{site.data.keyword.watson}} Explorer Content Analytics 中的命名实体识别注释器生成的 UIMA 类型与 {{site.data.keyword.knowledgestudioshort}} 类型系统中定义的实体类型之间的映射：

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        另一个示例定义由 {{site.data.keyword.watson}} Explorer Content Analytics Studio 中创建的定制注释器所生成的 UIMA 类型与 {{site.data.keyword.knowledgestudioshort}} 实体类型之间的映射：

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - 可以基于 {{site.data.keyword.watson}} Explorer Content Analytics 中的“模式匹配器”注释器或“字典查找”注释器中使用的构面来创建映射。在文本分析规则文件 (`*.pat`) 中，构面表示为类别属性。要定义映射，请使用以下语法：

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        以下示例（适用于模式匹配程序注释器和字典查找注释器）定义类别 $.mykeyword.product 与 {{site.data.keyword.knowledgestudioshort}} 实体类型 PRODUCT 之间的映射：

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### 后续步骤
{: #wks_uimawexmap_next}

必须创建一个 ZIP 文件，其中包含将已分析的数据上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间所需的所有文件。

**相关信息**：

[模式匹配程序注释器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[字典查找注释器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[命名实体识别注释器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### 将 UIMA CAS XMI 文件上传到工作空间
{: #wks_uimaweximport}

要使用下载的已预注释文档来培训模型，必须创建一个 ZIP 文件，其中包含上传 XMI 文件所需的所有文件，然后将该 ZIP 文件上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间。

#### 开始之前
{: #wks_uimaweximport_prereqs}

上传 ZIP 文件之前，请确保 {{site.data.keyword.knowledgestudioshort}} 工作空间中的类型系统包含已将 UIMA 类型映射到的实体类型。

> **警告**：UIMA 分析引擎允许注释跨多个语句。在 {{site.data.keyword.knowledgestudioshort}} 中，注释必须位于单个语句的边界内。如果上传的 XMI 文件包含跨语句的注释，那么这些注释不会显示在参考标准编辑器中。

#### 过程
{: #wks_uimaweximport_procedure}

要将预注释的文档上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间，请执行以下操作：

1. 创建一个 ZIP 文件，其中包含 {{site.data.keyword.knowledgestudioshort}} 所需的所有文件。

    1. 选择包含 XMI 文件、UIMA 类型系统描述符文件和 `cas2di.tsv` 文件的文件夹，或者选择该文件夹中的所有文件。
    1. 创建一个包含所有文件的 ZIP 文件。确保 `cas2di.tsv` 和 UIMA 类型系统描述符文件存储在该 ZIP 文件的根目录中。这些文件不能存储在该 ZIP 文件的子文件夹中，否则 {{site.data.keyword.knowledgestudioshort}} 将无法读取这些文件，因而不会导入任何内容。

        在 Windows 中，可以右键单击并选择**发送到** > **压缩 (zipped) 文件夹**。

1. 将该 ZIP 文件上传到 {{site.data.keyword.knowledgestudioshort}} 工作空间。

    1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，打开要向其添加文档的工作空间，然后打开**资产** > **文档**页面。
    1. 单击**上传文档集**。
    1. 拖动所创建的 ZIP 文件，或者单击以找到并选择该文件。
    1. 选中相应复选框以指示 ZIP 文件包含 UIMA CAS XMI 文件。
    1. 单击**上传**。
