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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，[请单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/train-ml.html){: new_window}。
{: tip}

# 培训机器学习模型
{: #train-ml}

在 {{site.data.keyword.knowledgestudiofull}} 中，创建机器学习模型包括培训机器学习模型和评估模型在注释测试数据和盲区数据时的执行情况。
{: shortdesc}

## 创建机器学习模型
{: #wks_madocsets}

在创建机器学习模型时，请选择要用于培训模型的文档集，并指定要用作培训数据、测试数据和盲区数据的文档的百分比。

### 关于本任务

通过探索性能度量值，您可以识别提高模型准确性的方法。

> **限制：**每个 {{site.data.keyword.knowledgestudioshort}} 实例一次只能培训三个机器学习注释器。如果实例包含多个工作空间，并且其他工作空间中正在培训的机器学习注释器的数量合计已达 3，那么在您的工作空间中培训机器学习模型的请求将排队，直至其他培训过程完成。

### 过程


要创建机器学习模型：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录，然后选择工作空间。
1. 选择**模型管理** > **性能**。
1. 验证所有文档集是否均已获得核准，以及是否已通过裁定解决了所有注释冲突。只有通过裁定或核准成为参考标准的文档才能用于培训模型。
1. 单击**培训和评估**。
1. 可选：要指定想要如何从文档集分配文档以供系统级别培训、测试或盲区集使用，请单击**编辑设置**。

    请参阅[文档集管理](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata)以获取帮助来确定要应用的比率。

1. 可选：将想要机器学习模型在培训期间使用的任何字典与字典条目的实体类型相关联。

    如果已经创建了字典预注释器，那么已准备好执行此步骤。单击**复用针对字典预注释器定义的映射**以复用映射或者定义新映射。

    模型使用字典术语的类型信息作为培训期间考虑的众多语言分析特征中的一个特征。

1. 单击**培训**以培训模型，或者单击**培训和评估**来培训模型、评估机器学习模型添加的注释，并分析性能统计信息。

    > **重要信息：**培训机器学习模型可能需要几分钟或数小时，具体取决于存在的人工注释数量以及所有文档中的总字数。

1. 选择想要用于培训模型的文档集。

    > **注：**文档集必须包含至少 10 个已注释的文档。

1. 创建模型后，选择以下操作之一：

    <table border="1" frame="hsides" rules="rows" cellpadding="4" cellspacing="0" summary="此表中的每一行都描述选择的一个选项。" class="simpletable choicetable choicetableborder">
      <thead><tr><th id="d33883e137-option" valign="bottom" align="left" class="ncol thleft thbot">选项</th>
          <th id="d33883e137-desc" valign="bottom" align="left" class="ncol thleft thbot">描述</th></tr></thead>
      <tbody><tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e139" class="stentry choption ncol"><p class="p wrapper"><strong>日志</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e139" class="stentry chdesc ncol"><p class="p wrapper">查看日志文件以确定是否发生了任何问题。</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e144" class="stentry choption ncol"><p class="p wrapper"><strong>详细信息</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e144" class="stentry chdesc ncol"><p class="p wrapper">查看注释性能统计信息，更改想要用于培训和测试模型的文档集，以及创建模型工件的快照版本。</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e149" class="stentry choption ncol"><p class="p wrapper"><strong>导出</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e149" class="stentry chdesc ncol"><p class="p wrapper">将 <code>ZIP</code> 文件导出到本地系统，其中包含模型在机器学习运行时环境中运行所需的组件。</p></td>
        </tr>
      </tbody>
    </table>

## 评估模型添加的注释
{: #wks_matest}

您可以将人类注释者添加的注释的参考标准视图与模型添加的注释进行比较。

### 过程

要评估模型添加的注释：

1. 选择**模型管理** > **性能** > **培训和评估**。此时将显示“培训/测试/盲区集”页面。
1. 针对培训集或测试集单击**查看参考标准**以查看通过预注释添加的注释和人类注释者添加的注释。此时将打开参考标准编辑器。单击以打开单个文档并查看如何注释提及项、关系和指代的提及项。
1. 在**性能**页面上，单击**查看解译结果**以查看机器学习模型向测试集内的文档添加的注释。仅在评估模型后，此按钮才可用。通过查看结果，您可以查看机器学习模型对测试数据中的提及项、关系和指代的提及项进行标注的良好程度。
1. 如果想要更改在培训、测试和盲区数据集之间划分文档的方式，请单击**性能** > **培训和评估** >**编辑设置**。例如，如果初始结果看起来可接受，那么您可能想要增加测试集内的文档数量以进一步测试机器学习模型的结果。您可以更改针对不同用途自动划分文档的比率，也可以选择特定文档集以用作培训数据、测试数据和盲区数据。
1. 如果执行了任何更改，请单击**培训和评估**以重新培训模型并重新评估注释。

## 删除机器学习模型
{: #wks_madelete}

您无法删除机器学习模型。

您可以删除用于开发模型的工作空间，但无法删除模型自身。删除模型并不是最佳方法。请改为更新或替换用于培训模型的工件。即使模型未生成期望的结果，您仍可以继续优化模型。每次创建新版本时，都将重新构建模型。您可以编辑诸如字典和类型系统之类的工件，并选择在培训下一个版本时使用不同的注释集。
