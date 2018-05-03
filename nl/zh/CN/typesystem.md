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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，[请单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window}。
{: tip}

# 建立类型系统
{: #typesystem}

类型系统控制注释内容的方式。
{: shortdesc}

## 类型系统
{: #wks_typesystem}

类型系统定义领域内容中您感兴趣并且想要使用注释标注的项。类型系统控制注释内容的方式（通过定义可以标注的实体类型）和不同实体间关系的标注方式。模型流程管理者通常与您的领域的主题专家一起工作，以定义类型系统。

在 {{site.data.keyword.knowledgestudioshort}} 中，您可以从头开始创建类型系统或者上传现有类型系统。要快速启动工作空间，您可能想要上传针对类似领域创建的类型系统。然后，您可以编辑类型系统以添加或除去实体类型，或者重新定义关系类型。

提供基于 KLUE 类型系统的样本类型系统以供用于 {{site.data.keyword.knowledgestudioshort}} 教程。KLUE 代表 Knowledge from Language Understanding and Extraction，是 {{site.data.keyword.IBM_notm}} Research 根据新闻文章集合分析衍生出来的。您可以从<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>此处<img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 下载样本 KLUE 类型系统。

众多行业（如冶金、地质、市场情报、生命科学、电子健康记录和肿瘤学等领域）发布特定于领域的术语的字典或本体。考虑引用此类型的资源以了解可能想要在自己的类型系统中定义的实体类型。

### 提及项
{: #wks_typesystem__wks_typesystemS2}

提及项是您在领域数据中视为相关的任何范围的文本。例如，在有关车辆的类型系统中，出现的 *airbag*、*Ford Explorer* 和 *child restraint system* 等术语可能是相关的提及项。

### 实体类型
{: #wks_typesystem__wks_typesystemS3}

实体类型是您对现实世界事物的分类方式。实体提及项是该类型事物的一个示例。例如，提及项“President Obama”可注释为 PERSON 实体类型。提及项“{{site.data.keyword.IBM_notm}}”可注释为 ORGANIZATION 实体类型。实体通常为名词，但也可以是动词，只要捕获相应动词对于将使用类型系统的应用程序的用途很重要。例如，对于有关车辆的类型系统，EVENT_CRASH 可以是有效实体类型，因此可注释句子“The car hit the barrier.”中的词 *hit*。

注释工作空间的目标是使用相应类型来注释文档中的每个提及项。在按实体类型对提及项分类之后，标注的文本范围称为实体。

使用 {{site.data.keyword.knowledgestudioshort}} 构建的类型系统可包含以下实体类型属性。这些属性帮助限定文本中的提及项，但是机器学习模型不会将它们标记为实体类型。例如，如果实体类型 ORGANIZATION 具有名为 COMMERCIAL 的实体子类型，那么 COMMERCIAL 本身不会标记为实体类型。

- **角色**

    按提及项出现的上下文限定该提及项。例如，语句“the students went to France”中的提及项“France”将使用实体类型 GPE 进行标记，因为 France 是地缘政治实体。但是，因为此上下文中的 France 也是旅行学生的目的地，因此将通过添加属性（在此情况下为角色 LOCATION）来限定该实体类型。再例如，提及项“Lawyers”可使用实体类型 PEOPLE 以及角色 OCCUPATION 进行标记。

- **实体子类型**

    进一步对实体类型分类。例如，实体类型 ORGANIZATION 可能包含子类型 COMMERCIAL、GOVERNMENT、MILITARY 和 EDUCATION。

- **提及项类型**

    通过特定词性限定提及项：
    - NAM：提及项是专有名词，例如，人员的姓名或组织的名称。
    - NOM：提及项是名词性词（普通名词），例如，company 或 president。
    - PRO：提及项是代词，例如，he、we 或 it。
    - NONE：其他三个提及项类型均不适用。

- **提及项类**

    通过指示提及项是特定、通用还是否定来限定提及项：
    - SPC：提及项为特定，通常在英语中包含词“the”，例如，“the book”或“the hurricane occurred in September”。在这些示例中，将使用属性 SPC 来注释提及项“book”和“hurricane”。
    - GEN：提及项为通用，例如“a book”或“hurricanes usually occur in the fall”。在这些示例中，将使用属性 GEN 来注释提及项“book”和“hurricanes”。
    - NEG：提及项为否定，例如，对“no book”的引用。在培训模型时，算法可学习否定和肯定示例，因此标记两种类型的提及项非常重要。

### 关系类型
{: #wks_typesystem__wks_typesystemS4}

关系类型定义两个实体之间的二元排序关系。要使关系提及项存在，文本必须明确同时定义两个实体的关系和绑定提及项，并且必须在单个语句中执行此操作。例如，语句 *Mary works for {{site.data.keyword.IBM_notm}}* 是 **employedBy** 关系类型的文本证据。

对于某些关系类型，实体提及项的顺序非常重要。例如，employedBy 关系类型允许实体类型 PERSON 或 PEOPLE 作为关系中的第一个提及项，ORGANIZATION 或 GPE 作为第二个提及项，但不得相反。Mary employedBy {{site.data.keyword.IBM_notm}} 是有效关系；{{site.data.keyword.IBM_notm}} employedBy Mary 则不是。对于某些关系类型，例如，spouseOf、colleague 或 sibling，顺序不重要。在定义顺序不重要的关系类型时，最佳实践是向注释准则添加信息以规范化关系类型的使用方式。用于注释此类对称关系的约定为：文本中第一次出现的实体提及项应该是关系中的第一个提及项。

**相关概念**：

[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)

## 向工作空间添加类型系统
{: #wks_projtypesys}

必须在开始任何注释任务之前创建或上传类型系统。

### 关于本任务

以下命名规则适用于类型系统条目：

- 名称不能包含空格。
- 在添加到类型系统的值中仅使用以下字母数字 ASCII 字符和下划线字符：A 到 Z、a 到 z 以及 0 到 9。
- 实体或关系类型名称中的第一个字符必须是字母。
- 实体类型名称长度不能超过 64 个字符。
- 关系类型名称长度不能超过 128 个字符。

按照约定，以大写字符指定实体类型名称 (ORGANIZATION)，以驼峰式大小写指定关系类型名称 (employedBy)。但是，此约定是可选的。

### 过程

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后打开**资产和工具** > **实体类型**页面。
1. 选择以下某种方法来创建类型系统：

    - 要上传现有类型系统：

        1. 单击**上传**以上传现有类型系统。

            如果先前从 {{site.data.keyword.knowledgestudioshort}} 工作空间下载了类型系统，那么将以 `JSON` 格式下载类型系统。您可以上传此类型系统以快速启动新工作空间的创建。有关详细信息，请参阅[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)。

            > **注：**无论类型系统的来源如何，其中的条目必须满足先前列出的命名规则。

        1. 按照从头开始创建类型系统时的相同方式，添加、编辑和删除实体类型和关系类型。

    - 要从头开始创建类型系统：

        1. 单击**添加实体类型**。
        1. 指定描述性实体类型名称，同时记住，实体类型是用于注释领域内容中的重要文本范围（提及项）的标签。请保持名称简短且具有代表性，以便人类注释者可轻松记住名称。

            您还可以选择定义实体类型的角色和子类型：
            - 角色帮助限定提及项出现的上下文中的实体类型。例如，可使用实体类型 PEOPLE 以及此上下文中的角色 OCCUPATION 标注提及项 Software Engineer。请参阅[何时定义角色](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles)以获取更多信息。
            - 子类型帮助进一步对实体类型分类。例如，实体类型 GOVERNMENT 可能有子类型 MILITARY 和 CIVILIAN。

            > **注：**通过定义实体的角色或子类型，您为在注释时将类型信息关联到提及项的人员提供了更多选项。人类注释者可应用仅指定实体类型或者实体类型加现在所定义角色或子类型的注释。

            尝试定义足够的实体类型以捕获想要注释的关键概念，但是实体类型不要过多，以免人类注释者很难准确应用标签。

        1. 单击**提及项类**和**提及项类型**以查看缺省提及项类和提及项类型（您无法编辑这些值）。

            属性的用途是帮助按其类型标注每个提及项。提及项类型指示提及项为名称、名词性词还是代词，而提及项类指示提及项为特定、通用还是否定。

        1. 打开**资产和工具** > **关系类型**页面并指定两个提及项之间的相互关系。

            关系类型中的第一个实体和第二个实体之间的顺序通常是相关的。例如，PERSON 实体可以是 ORGANIZATION 实体或地缘政治实体 (GPE) 的员工，例如，Mary employedBy {{site.data.keyword.IBM_notm}}，但是人员无法雇佣组织和地缘政治实体。在人类注释者单击参考标准编辑器中的实体时，可用关系类型的列表由类型系统中定义的内容进行控制。

            请勿定义关系属性。机器学习模型不会使用这些属性。模型仅使用关系类型和顺序，而忽略关系属性。

        1. 使用**编辑**和**删除**图标修改实体类型及其关联的关系类型，或者从类型系统中删除实体类型或关系类型。

            如果删除在关系类型定义中使用的实体，那么也会删除关系类型定义。

**相关任务**：

[修改类型系统而不丢失人工注释](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## 类型系统创建准则
{: #wks_typesys_guidelines}

{{site.data.keyword.knowledgestudioshort}} 中任何类型系统的用途是定义文本范围的注释方式。如果选择从头开始创建类型系统，请遵循以下准则。

关注于创建实体类型和关系类型的清单，这些类型涵盖了将在其中使用类型系统的应用程序所需的信息。请勿涵盖不需要的内容。请勿分割类型或者生成应用程序不需要的差别。例如，如果源文档包含语句 *Murder on the Orient Express made headlines*，那么根据将使用您通过类型系统构建的模型的应用程序类型，您定义实体类型以捕获语句中关键信息的方式将有所不同。

- 对于文学应用程序，您可以创建捕获以下信息的类型：

    ```
               [NOVEL]           [CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Murder on the Orient Express] [made headlines]
    ```
    {: screen}

- 对于公共安全应用程序，您可以创建以下类型：

    ```
    [EVENT_CRIME]      [LOCATION]
    ```
    {: screen}

    ```
      [Murder] on the [Orient Express] made headlines
    ```
    {: screen}

结构通常由将从中抽取信息的文档的特征驱动，但是应该始终按照应用程序实际将从这些文档使用的信息进行调节。例如，您可能正在创建用于从医疗记录获取洞察的应用程序。要构建类型系统，您开始查看患者记录以了解必须捕获的信息种类。患者记录可能全都包含一个描述患者午餐所吃食物的字段。但是，如果应用程序将不使用该信息，请勿将其添加到类型系统。在决定省略此项时，请注意，这意味着患者记录文档的一些部分将保持未注释状态。这是正常的，甚至是期望的情况。

提及项对某个文本范围进行注释；它们不会替换该文本。类型系统不是领域的本体。期望有一般实体类型（如 MEDICATION_NAME），而不是每种药物类型对应一种实体类型。文档文本将继续包含特定药物名称。使用标识其类型的注释就可加以改进，从而更易于以编程方式查找和抽取信息。

开始时，请定义 10 到 40 个实体类型和关系类型。如果操作工作空间的人类注释者并非在相应领域高度专业化的人士，请定义更接近此范围的下限的数量。请勿定义超过 50 个。

在团队开始任何人工注释任务前，请计划花费比较多的时间来定义类型系统。在团队开始对文档进行注释时，请以较小的集合（可能不超过 50 个）开始。初始仅对提及项进行注释，检查结果，然后根据需要优化注释准则和类型系统。在对提及项注释的结果感到满意后，接着对关系和指代进行注释。

在执行基础工作来定义一组实体类型和提及项注释准则时，避免投入大量工作来对关系提及项进行注释。提及项更改会撤销关系注释工作。请花一些时间来定义一组关系类型及其允许的实体类型对，从而在最终完成实体类型清单之前考虑关系类型需求。

期望类型系统随着尝试对其进行注释的人员的经验一起演进。如果在创建人工注释任务后修改类型系统，那么必须决定是否将更改应用于每个任务。如果应用更改，那么人类注释者必须重新访问他们先前注释的文档。

在测试模型时，您可以查看说明实体类型和关系类型在样本文档中出现的频率的统计信息。请务必查看这些统计信息。要确保应用程序收到足够的上下文来对大量文档进行准确注释，测试数据必须包含最重要的实体类型和关系类型的大规模采样。

> **重要信息：**在培训第一个模型后，您可能需要根据性能统计信息进行修改。但是，要为机器注释创建可靠的统计模型，您会希望类型系统在开始大规模注释任务之前尽可能接近最终状态。

## 何时定义角色
{: #wks_typesystem_roles}

使用角色，您可以定义更精确的实体类型。

您添加的每个实体都有一个角色。除非进行更改，否则角色名称与实体名称相同。您可以选择为实体定义其他角色以捕获提及项的更细致用法。应用角色的词或短语本身就是实体类型的示例，但是在语句中，它扮演另一个实体类型的角色。例如，在语句 *the White House vetoed the bill* 中，如果我们注释实体类型 FACILITY 以及角色 ORGANIZATION 或 PERSON，那么我们可更精确地捕获 *White House* 的含义。White House 是建筑物 (FACILITY)，但是在此构造中表示政府 (ORGANIZATION) 或美国总统 (PERSON)。实体类型 + 角色标签为文本中的提及项创建了更精确的分类。

角色还可为您提供一种方法以在不依赖使用重叠提及项的情况下捕获关系信息。例如，您可能想要对文本 *31-year-old male* 进行注释，从而使其捕获以下想法，即这是对年龄属性为 31 岁且性别属性为男性的人员的引用。通过检查文本，我们确定 *31-year-old* 是年龄，*male* 是性别，它们一起表示一个人。您主要处理 3 种实体类型：AGE、GENDER 和 PERSON。表示这种情况的一种方法是将 *31-year-old* 注释为 AGE，将 *male* 注释为 GENDER，此外，因为 PERSON 的独特提及项缺失，但 *male* 已表示人员，因此词 *male* 可具有角色 PERSON。然后，您可以捕获 PERSON 角色与想要捕获的人员中所有属性之间的关系。例如，您可以定义 PERSON 角色与 AGE 提及项之间的 hasAttribute 关系。因为已将 GENDER 实体类型和 PERSON 角色类型标签应用于同一个词 *male*，您无法在这两者之间定义 hasAttribute 关系。但是，由于这两个标签应用于同一提及项，因此两者彼此关联。机器学习模型会认可此关联，而无需您定义 hasAttribute 关系类型来明确声明此关系。

类似示例是，将短语 *2008 Ford F-150* 用作 *2008 Ford F-150 truck* 的缩写的情况。此处，*2008* 注释为 MODEL_YEAR 实体类型，*Ford* 注释为 MANUFACTURER 实体类型，并且为 *F-150* 指定了 MODEL 实体类型。但由于单词“truck”缺失，*F-150* 也表示车辆。说 *the F-150* 类似于说 *the truck*。除 MODEL 实体类型外，您还可以通过向提及项添加 VEHICLE 角色来捕获该用法。然后，可以定义 VEHICLE 角色与 MANUFACTURER 和 MODEL_YEAR 实体提及项之间的 hasAttribute 关系。

### 角色与子类型有何差别？

实体子类型用于将实体类型的清单分层为层次结构。例如，如果您希望区分 40 件事物，但它们在逻辑上分组为 10 组，每组 4 个（VITALSIGN_BLOODpreSSURE、VITALSIGN_HEARTRATE、MEDICATION_DOSAGE 和 MEDICATION_FREQUENCY），那么您可以将它们构造为类型和子类型，这将生成更紧凑的菜单，但会使标注过程的深度和麻烦程度提高一个级别。对于信息抽取用途，类型和子类型组合可以与大量不含子类型的类型交换使用。与之相反，应用角色的词或短语是一种实体类型的示例，但是它扮演另一个实体类型的角色，该实体类型并非其他类型的子类型。

### 如何处理角色？

{{site.data.keyword.knowledgestudioshort}} 机器学习模型通过将实体类型与角色值并置，针对在源文档中找到的实体的每个提及项定义分类器标签。在提供角色值时，可创建更精确的标签。培训数据中一种标签类型的每一组实例都构成一组更加统一的提及项。困难在于，通过选择提高精确性，您还必须同意提供更多培训数据以确保模型表现良好。但是，提供的培训数据越多，模型变得越好。因此，如果不介意执行更多注释，那么使用角色可获得更好的结果。

例如，假定在源文档中出现以下语句，并且我们想要捕获“Acme”（其中 Acme 是著名的卡车制造商）、“sedan”和“truck”作为类似实体，因为它们全都指示物理车辆：

- a) The Acme crashed into the concrete barrier.
- b) The sedan crashed into the concrete barrier.
- c) The Acme A-160 truck crashed into the concrete barrier.

您可以通过两种方式来处理类型系统设计：

1. 定义两个实体类型：**MANUFACTURER** 和 **VEHICLE**。对于 **MANUFACTURER** 实体，定义除缺省 **MANUFACTURER** 角色外还可使用的 **VEHICLE** 角色。

    使用此类型系统时，将按如下所示对语句进行注释：
    - a) “Acme”注释为 **MANUFACTURER** 实体，但是角色为 **VEHICLE**，因为它指示实际车辆。因此，其内部标签为 **MANUFACTURER-VEHICLE**。
    - b) “sedan”注释为实体类型 **VEHICLE**。它自动分配有 **VEHICLE** 角色，因为未定义其他任何角色。
    - c) “Acme”注释为实体类型 **MANUFACTURER**，并且“truck”注释为实体类型 **VEHICLE**。未分配任何角色，因此将使用缺省角色。

1. 定义两个无角色的实体类型：**MANUFACTURER** 和 **VEHICLE**。

    使用此类型系统时，将按如下所示对语句进行注释：
    - a) “Acme”注释为实体类型 **VEHICLE**。
    - b) “sedan”注释为实体类型 **VEHICLE**。
    - c) “Acme”注释为实体类型 **MANUFACTURER**，并且“truck”注释为实体类型 **VEHICLE**。

两种不同的类型系统表现如何？假定一组文档已由人类注释者进行注释。在注释通过后，将在培训语料库中标识以下培训事件（手动标注的实体）：

- **类型系统 1**

    ```
    MANUFACTURER-MANUFACTURER 800 events
    MANUFACTURER-VEHICLE 200 events
    VEHICLE-VEHICLE 400 events
    ```
    {: screen}

- **类型系统 2**

    ```
    MANUFACTURER 800 events
    VEHICLE 200 + 400 = 600 events
    ```
    {: screen}

在模型处理新文档时，大多数时间可能会将“Acme”标注为 MANUFACTURER，因为单词拼写是一个很强的特征，而单词“Acme”可能将在 MANUFACTURER 字典中进行定义。将需要大量上下文以不同方式对其进行标注。如果使用类型系统 1，那么只有 200 个 MANUFACTURER-VEHICLE 培训事件，与类型系统 2 中 600 个 VEHICLE 事件相比，这是劣势。但是，类型系统 1 中的培训事件集群全部相当统一，这可实现更好的性能。对于类型系统 2，针对 VEHICLE 的 600 个培训事件的集合实际上由两个完全不相交的集群组成：一个包含指示实际车辆的制造商名称（例如，“Acme”和“Ford”），而另一个包含车辆类型（例如，“sedan”、“SUV”和“truck”）。直观地说，这两个集群各自本身都是统一的，但两者混合在一起会削弱培训集群并呈现更难于解决的问题。如果继续执行注释并且添加更多培训事件，类型系统 1 的性能将越来越好，而解决类型系统 2 导致的两个不相交集群的问题则并不会通过更多培训得到改进。
