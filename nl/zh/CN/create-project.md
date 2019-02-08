---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/create-project.html){: new_window}。
{: tip}

# 创建工作空间
{: #create-project}

构建定制模型的第一步是创建工作空间。
{: shortdesc}

## 关于本任务

对于要构建和使用的每个模型，请创建一个工作空间以包含构建模型所需的工件和资源。然后，可以对模型进行培训，以生成可以部署到外部服务以供使用的定制模型。

在创建工作空间之前，请先回答以下问题：

- **要创建哪种类型的模型？**

    - 机器学习模型：使用统计方法在文档中查找实体和关系。此类型的模型可以随着数据量的增长而调整。
    - 基于规则的模型：使用声明式方法在文档中查找实体。此类型的模型可预测性更强，也更易于理解和维护。但是，这种模型不会从新数据进行学习。它只能找到自己培训为查找的模式。

    > **注**：还可以创建一个工作空间以包含一个基于规则的模型和一个机器学习模型。

- **哪些服务将使用该模型？**

    有关定制模型可用于的其他 {{site.data.keyword.watson}} 服务的信息，请参阅 [{{site.data.keyword.watson}} 服务集成](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg)。

## 过程

要创建工作空间，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录，然后单击**创建工作空间**。

    > **注**：具有“项目经理”角色的人员可以执行除创建工作空间以外的几乎所有任务。管理员必须初始创建工作空间，并为该工作空间分配项目经理。

1. 为工作空间命名。选择可反映领域内容或模型用途的短名称。如果需要，日后可以更改工作空间名称。
1. 确定工作空间中文档的语言。添加到工作空间的文档以及创建或上传的字典必须采用您指定的语言。
1. 可选：如果要更改应用程序使用的缺省基于机器学习的记号化器，可以展开**高级选项**部分，然后选择**基于字典的记号化器**。

    缺省记号化器比基于字典的记号化器更高级；它通过机器学习根据源文档语言中已执行的统计学习，识别源文档中的记号。它能够更精确地识别记号，因为它理解语言的更自然、更细致的模式。基于字典的记号化器根据语言规则来识别记号。有关更多详细信息，请参阅[记号化器](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)。

1. 可选：如果要将项目经理添加到工作空间，请展开**高级选项**部分，然后从列表中选择要添加为项目经理的人员的姓名。管理员日后可以通过编辑工作空间来添加或除去项目经理。

    这将仅显示在实例的“用户帐户管理”页面中为其分配“项目经理”角色的人员的姓名。有关添加用户的更多信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

    > **注**：如果您有轻量套餐预订，请跳过此步骤。您无法添加其他用户，因此也无法为任何人分配“项目经理”角色。您无需单独的项目经理。作为管理员，您可以执行项目经理通常会执行的所有任务。

1. 单击**创建**。

## 后续步骤

创建工作空间后，即可以开始配置工作空间资源。

要更改工作空间描述或工作空间名称，或者日后要添加或除去项目经理，管理员可以编辑工作空间。在 {{site.data.keyword.knowledgestudioshort}} 主页中，单击工作空间磁贴上的**显示菜单**图标，然后选择**编辑**菜单选项。

**相关概念**：

[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)

**相关参考**：

[语言支持](/docs/services/watson-knowledge-studio/language-support.html)

## 记号化器
{: #wks_tokenizer}

记号化器用于将字符分组成记号，再将记号分组成语句。一个记号大致相当于一个词。

记号化器为了识别文档记号而必须执行的操作将根据文档语言而有所不同。在英语中，记号通常等同于语句中用空格分隔的单词。但是，记号并不总是与单词一一对应；其他文本元素在某些情况下会视为记号。例如，语句末尾的标点符号会视为记号，而缩略词通常会展开为两个记号。在不使用空格的语言（例如，中文）中，将使用更复杂的统计算法来识别记号。

记号化过程用于确定用户可在参考标准编辑器中为注释突出显示的字符组，因此非常重要。实体和关系提及项的注释通常与记号边界对齐，并且必须在语句内进行标注；这些注释不能跨越语句边界。

### 支持的类型

{{site.data.keyword.knowledgestudioshort}} 支持以下记号化器：

- **基于机器学习的记号化器（缺省）**

    这是一种更高级的记号化器，用于根据源文档语言中已执行的统计学习来识别源文档中的记号。此记号化器可查找用于捕获语言的更自然、更细致模式的记号。无法定制此记号化器。

- **基于字典的记号化器**

    此记号化器基于语言字典，用于查找符合源文档语言规则的记号。只有高级用户才能定制此记号化器。

创建工作空间时，必须选择要使用的记号化器。日后无法切换到其他记号化器。为了获得最佳结果，请使用缺省记号化器。仅当高级用户希望通过确定性字典机制来修改记号化器行为时，才可选择基于字典的记号化器。然后，可以通过向字典添加新条目来对记号化器进行定制。但是，执行定制时必须谨慎，因为向字典添加新词时，这些更改可能会以意外的方式影响机器学习模型。

## 输入、输出和限制摘要
{: #wks_formats}

模型开发的不同阶段需要不同的输入并生成不同的输出。

下表总结了模型开发过程中每个阶段执行的典型活动、支持的输入文件格式、可生成的输出以及任何大小限制或其他需求。

### 所有模型类型

<table summary="此表提供所有模型类型的输入、输出和限制摘要。">
<caption>表 1. 所有模型类型</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
任务</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
典型用途</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
支持的输入格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
支持的输出格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
限制和需求</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>类型系统管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>创建类型系统或上传并修改现有类型系统。</p>
      <p>针对领域定义实体类型和关系类型。</p>
      <p>您看不到类型系统的可视化。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>从 {{site.data.keyword.knowledgestudioshort}} 工作空间下载的 JSON 文件</p>
        </li>
        <li>
          <p>从 Human Annotation Tool (HAT) 下载的 ZIP 文件</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>为了避免人工注释时产生视觉疲劳，定义实体类型和关系类型时，数量都不要超过 50 个。</p>
      <p>上传类型系统的文件大小限制：20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>字典管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>以只读方式上传 CSV 字典文件或从其他工作空间下载的字典 ZIP。</p>
      <p>创建新字典，然后上传术语条目的 CSV 文件或向其添加术语条目。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>字典文件：</p>
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 文件</p>
        </li>
        <li>
          <p>从其他工作空间下载的字典 ZIP</p>
        </li>
      </ul>
      <p>术语条目文件：</p>
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 文件</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 文件</p>
        </li>
        <li>
          <p>要在其他工作空间中使用的字典 ZIP</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>文件大小限制：</p>
      <ul>
        <li>
          <p>每个 CSV 术语条目文件 1 MB</p>
        </li>
        <li>
          <p>每个 CSV 只读字典文件 16 MB</p>
        </li>
        <li>
          <p>每个字典 15,000 个条目（只读字典除外）</p>
        </li>
        <li>
          <p>每个工作空间 64 个字典</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### 机器学习模型

<table summary="此表提供机器学习模型的输入、输出和限制摘要。">
<caption>表 2. 机器学习模型</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">任务</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">典型用途</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">支持的输入格式</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">支持的输出格式</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">限制和需求</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>文档管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>上传一小部分代表性文档</p>
      <p>上传包含先前由人工注释者、机器学习模型或 UIMA 分析引擎添加的注释的文档</p>
      <p>无法从 {{site.data.keyword.ibmwatson_notm}} Explorer 中获取整个语料库来计算高值文档的注释。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 文件</p>
        </li>
        <li>
          <p>UTF-8 格式的文本</p>
        </li>
        <li>
          <p>包含从其他语料库下载的文档的 ZIP 文件</p>
        </li>
        <li>
          <p>包含 UIMA CAS XMI 格式文档的 ZIP 文件</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>文档的 ZIP 归档文件</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>每个文档 40,000 个字符</p>
        </li>
        <li>
          <p>每个工作空间 10,000 个文档</p>
        </li>
        <li>
          <p>每个工作空间 1,000 个文档集（包括注释集）</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>预注释</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>使用字典或 {{site.data.keyword.nlufull}} 预注释器来提供人工注释的起点。</p>
       <p>无法通过 {{site.data.keyword.ibmwatson_notm}} Explorer 对语料库进行重新注释。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>原始文档。</p>
      <p><b>注</b>：不要对人工注释者已注释的文档进行预注释，否则将丢失人工注释者完成的工作。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>部分注释的文档</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>无</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>文档注释</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>管理人工注释</p><p>对实体、关系和指代链进行注释以创建参考标准</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>注释任务</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>参考标准</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>每个工作空间 256 个活动注释任务</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>培训和优化</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>培训受监督的机器学习模型，以从非结构化文本中抽取特定于领域的信息。</p><p>评估和改进受监督的机器学习模型。</p>
      <p>无法创建半监督或未监督的机器学习模型。</p>
      <p>无法执行广泛的功能工程设计。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>不适用</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>机器学习模型</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>每个工作空间 1 个机器学习模型</p>
        </li>
        <li>
          <p>每个工作空间 10 个模型版本</p>
        </li>
        <li>
          <p>最大工作空间数由预订套餐确定。</p>
        </li>
        <li>
          <p>每月可以执行的最大培训操作数由预订套餐确定。</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>发布</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>发布机器学习模型，以用于在其他 {{site.data.keyword.watson}} 应用程序中执行文本抽取。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>不适用</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>模型标识（在 {{site.data.keyword.nlufull}} 或 {{site.data.keyword.discoveryfull}} 中使用）</p>
        </li>
        <li>
          <p>ZIP 文件（在 {{site.data.keyword.ibmwatson_notm}} Explorer 中使用）</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>要部署到 {{site.data.keyword.watson}} 服务，必须知道 {{site.data.keyword.cloud_notm}} 服务空间和实例名称。</p>
    </td>
  </tr>
</table>

### 基于规则的模型

<table summary="此表提供基于规则的模型的输入、输出和限制摘要。">
<caption>表 3. 基于规则的模型</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
任务</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
典型用途</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
支持的输入格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
支持的输出格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
限制和需求</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>规则编辑器</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>创建文档或将文档上传到规则编辑器，在其中定义类、正则表达式和规则。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>纯文本（在编辑器中添加）</p>
        </li>
        <li>
          <p>UTF-8 格式的 CSV 文件</p>
        </li>
        <li>
          <p>从“所有文档集”中复制的内容</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>无</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>每个工作空间 1 个基于规则的模型</p>
        </li>
        <li>
          <p>每个文档 5,000 个字符</p>
        </li>
        <li>
          <p>每个工作空间 100 个文档</p>
        </li>
        <li>
          <p>文档标题的最大大小为 256 个字符</p>
        </li>
        <li>
          <p>每个工作空间 200 个规则</p>
        </li>
        <li>
          <p>每个工作空间 400 个类</p>
        </li>
        <li>
          <p>每个工作空间 100 个正则表达式组</p>
        </li>
        <li>
          <p>每个正则表达式组 100 个正则表达式条目</p>
        </li>
        <li>
          <p>每个正则表达式条目 1,000 个字符</p>
        </li>
        <li>
          <p>每个工作空间 5 个基于规则的模型版本</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>发布</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>发布基于规则的模型，以用于在其他 {{site.data.keyword.watson}} 应用程序中执行模式识别。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>不适用</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>模型标识（在 {{site.data.keyword.nlufull}} 或 {{site.data.keyword.discoveryfull}} 中使用）</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>要部署到 {{site.data.keyword.watson}} 服务，必须知道 {{site.data.keyword.cloud_notm}} 服务空间和实例名称。</p>
    </td>
  </tr>
</table>
