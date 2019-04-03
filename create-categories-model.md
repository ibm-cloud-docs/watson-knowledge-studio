---

copyright:
  years: 2019
lastupdated: "2019-03-20"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:warning: .warning}
{:important: .important}
{:note: .note}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Creating a custom categories model
{: #create-categories-model}

This tutorial describes how to train a custom categories model and deploy it to {{site.data.keyword.nlushort}} or {{site.data.keyword.discoveryshort}}.
{: shortdesc}

The custom categories feature is experimental. The feature might be unstable, change frequently in ways that are not compatible with earlier versions, and might be discontinued with short notice. This feature is not recommended for use in production environments.
{: important}

## Before you begin
{: #create-categories-model-before-you-begin}

The custom categories feature is available only in {{site.data.keyword.knowledgestudioshort}} instances hosted in the **Dallas** location that are on a **Lite** or **Standard** plan. Custom categories models can be deployed only to [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) or [{{site.data.keyword.discoveryshort}}](https://{DomainName}/catalog/services/discovery) service instances that are hosted in the **Dallas** location.
{: note}

1. [Create an instance of {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#instance) in the **Dallas** location. Select the **Lite** or **Standard** plan.
1. From the **Manage** page of your {{site.data.keyword.knowledgestudioshort}} service instance, click **Launch tool**.

## Procedure
{: #create-categories-model-procedure}

1. Create a categories workspace.

    1. [Launch the {{site.data.keyword.knowledgestudioshort}} application](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#launching-the-knowledge-studio-application).
    2. If you already have other workspaces, click **Create workspace**.
    3. Click **Create categories workspace**. Enter a name for your workspace, then click **Create**.

2. Create a training file.

    Create a CSV file that defines your custom categories with associated key phrases according to the format outlined in [Creating a training file](#creating-a-csv-file).

3. Import the training file.

    On the **Train your categories model** screen, upload your CSV file by dragging and dropping the file to the **Drag and drop file here** area or by clicking the **or browse file** link on the  screen. This automatically initiates training of the model.

    If the model training succeeds, you will see the **Test Your Model** screen. If training fails and the error message suggests that you can fix the issue, edit your CSV file to correct any errors and upload it again.

4. Tune your model for each category.

     1. Find a text sample that pertains to a category label from your CSV file and paste it into the **Enter input text** area. 
     2. Click **Run Test** to evaluate the performance of your model against your text sample. A score closer to 1.0 indicates a very high level of certainty that the text passage corresponds to the respective category.
     3. If the model does not perform well for the tested category, adjust the key phrases for the category in your CSV file, then click **Retrain model** to upload the updated file.
     4. Repeat steps 4.a through 4.c until you are satisfied with the model performance.

5. Deploy your custom model to {{site.data.keyword.nlufull}} or {{site.data.keyword.discoveryfull}}

    1. Click **Deploy model**.
    2. In the **Create a version** dialog, enter a description for the model, and click **OK** to save a version of the model.
    3. Follow the instructions to select a target service instance, and click **Deploy** to execute the model deployment. You will get a model ID which is required to use the custom model with {{site.data.keyword.nlushort}} or {{site.data.keyword.discoveryshort}}.

    You can manage model versions and deployment from the **Versions** page in the left navigation menu.

6. Test your custom model with {{site.data.keyword.nlushort}} or {{site.data.keyword.discoveryshort}}

    Use the model ID that you received in step 5.c as the value for the categories **model** option. For details, see the following pages.
      - {{site.data.keyword.nlushort}}: [Customizing](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)
      - {{site.data.keyword.discoveryshort}}: [Integrating with Watson Knowledge Studio](/docs/services/discovery?topic=discovery-integrating-with-wks#integrating-with-wks)

## Creating a training file
{: #creating-a-csv-file}

You can download a sample CSV file to use as a template by clicking **Download sample CSV** on the **Model Training** page. If you've already trained a model, click **Retrain model** to see the link again.
{: tip}

The CSV (comma-separated value) file that you use to train your categories model must be formatted according to the following rules.

- Each line of the CSV file represents a separate category with its associated key phrases. 
- **(required)** The first value on a line must specify the label of the category or subcategory. 
  - To specify a subcategory label, enter the parent categories separated by forward slashes (`/`) before the name of the subcategory. 
  - You can build subcategories 5 levels deep, so subcategories can have up to 4 parent categories.
  - Labels must be unique for all categories or subcategories at the same level. The labels are case insensitive, so a file with two labels `/sports` and `/Sports` is not allowed.
- **(required)** The second value on a line must specify a key phrase to associate only with the respective category or subcategory. You can repeat the name of the category or subcategory if necessary.
  - Key phrases are case insensitive and cannot be repeated at the same level. For example, `/sports/soccer` and `/sports/football` both cannot have `football` as one of the key phrases.
- (optional) You can specify more key phrases as additional values, up to a maximum of 20.


Example CSV file subset:

```csv
/Sports,sports
/Sports/Motor Sports,motor sports
/Sports/Motor Sports/Motorcycle Racing,motorcycle racing
/Sports/Sporting Goods,sporting goods
/Sports/Sporting Goods/American Football Equipment,shoulder pads,football helmet,football gloves
/Sports/Sporting Goods/Baseball Equipment,baseball bat,baseball glove
/Sports/Sporting Goods/Basketball Equipment,basketball shoes
```

## Tips
{: #create-categories-tips}

- Generally, it's best to limit your training file to 1000 categories and subcategories total.
- It's recommended that you limit the names of categories and subcategories to 64 characters at each category level.
- Additional key phrases are optional, but they are strongly recommended if you want to increase the accuracy of your model. Try starting with at least 3-5 key phrases per category.


