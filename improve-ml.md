---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-03"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:preview: .preview}
{:beta: .beta}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# Making machine learning model improvements
{: #improve-ml}

After you determine areas in which the model is having trouble, take steps to improve its performance.
{: shortdesc}

## Creating model versions
{: #wks_maversions}

After you create a machine learning model, you can take a snapshot to keep a backup version of the current resources in case you want to restore the resources in a future iteration.

### About this task
{: #wks_maversions_about}

The F1 score provides an indication of the quality of the model. If the model performance results are good, you might want to store a version of the component before changing any of the resources. If changes that you make result in poorer quality, you can revert to a version that you stored. When you revert to an older version, all annotation tasks are archived because they are no longer valid.

You can have a maximum of 10 versions of a workspace. If you reach that limit, delete older versions or versions that you no longer need before creating a new version.

When you create a new version, the following resources are captured:

- Type system
- Corpus
- Ground truth
- Machine learning model
- Machine learning model evaluation results

The following resources are excluded:

- Annotation tasks, because they are temporal by design, used only for determining ground truth
- Dictionaries, because dictionaries can be large, and various types of dictionaries are managed in different ways

### Procedure
{: #wks_maversions_procedure}

To create and restore machine learning model versions:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select **Machine Learning Model** > **Performance**. Performance statistics about the current version, labeled version 1.0, are displayed.
1. To take a snapshot of the current version, click **Machine Learning Model** > **Versions**, and then click **Take Snapshot**. The resources in version 1.0 are frozen, and a new version, labeled 1.1, becomes the current version. For each new version that you create, the minor version number is incremented, for example, 1.0 becomes 1.1 and then becomes 1.2.
1. Revise the workspace resources as needed, re-train, and re-evaluate the model.
1. If you are pleased with the performance results and want to store the new version before making future changes, create another version. Continue revising resources and re-training the model as needed, creating a new version for each iteration that you want to retain.
1. If performance results are worse, and you want to revert to a previous version before testing any further:

    1. Open the **Assets** > **Dictionaries** page and download any dictionaries that you want to re-use in the restored model.
    1. Click **Machine Learning Model** > **Versions** and click **Promote** for the version that you want to restore. The version that you promote becomes the current version, and the version number changes to 2.0. When you promote a version, the major version number is incremented and the minor version number becomes 0, for example, 1.1 becomes 2.0.
    1. Open the **Dictionaries** page and upload the dictionaries that you downloaded.
    1. If testing of the new version requires changes to ground truth, open the **Machine Learning Model** > **Annotations** page. Click the **Annotation Tasks** tab and create a new annotation task.

## Modifying a type system without losing human annotations
{: #wks_projtypesysmod}

You might need to make modifications while you train a model, based on the performance statistics. But, generally, you want the type system to be as close to final as possible before you begin large-scale annotation tasks. If you change the type system after human annotators began their work, they must revisit the documents that they annotated. They must assess the applicability of the type system changes.

### About this task
{: #wks_projtypesysmod_about}

This process propagates the current type system, ground truth editor keyboard shortcuts, and color settings to all document sets in a task.

### Procedure
{: #wks_projtypesysmod_procedure}

To modify the type system without losing the work that was done by human annotators:

1. Change the type system. For example, you can add or remove entity types or relation types.
1. Decide whether you want to propagate the changes to existing human annotation tasks.
1. Open the **Machine Learning Model** > **Annotations** page and click the **Annotation Tasks** tab. Open each task that you want to update and click **Apply Type System Updates**.

    If you removed entity types or relation types from the type system, all occurrences of those types are highlighted in gray in the documents. These invalid types are ignored by the machine learning model. They do not prevent you from submitting and approving document sets.

1. Provide details to the human annotators about what changed in the type system.
1. Ask human annotators to update their documents to reflect the changes in the type system. For example, if you added new entity types or relation types, they must review their documents and annotate them appropriately.

    > **Note:** If the task contains completed documents, human annotators cannot alter those documents to assess type system changes until they are back in an editable state. To become editable, ask human annotators to submit the document sets so that you can reject them.

**Related concepts**:
{: #wks_projtypesysmod_related}

[Type systems](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-typesystem#wks_typesystem)

## Document set management
{: #wks_mamanagedata}

Use the right sets of data to test and train the model at the right time.

The documents that you add to the system must be allocated to the following system-level data sets when you create a machine learning model:

- **Training set**

    A set of documents that have been annotated through pre-annotation or by human annotators that is used to train the model. The goal of the training set is to teach the machine learning model about correct annotations, which includes teaching the model through text that was not annotated.

- **Test set**

    A set of annotated documents that is used to test the trained model. After you run a test on the test set, perform a detailed diagnostic-purposed error analysis of the results. Close analysis helps you find weaknesses in the current model that can be addressed.

- **Blind set**

    A set of annotated documents that is set aside and used to test the system periodically after several iterations of testing and improvement have occurred. To prevent accuracy from being tainted (for example, by making changes based only on annotations in known documents), blind data should be data that has not previously been viewed by users involved with creating the model. Reported results should come only from tests that are run on blind data. After you run a test on the blind set, look at only the most high-level scores, such as the overall mention and relation F1 scores. You don't want to learn too many details about the performance or it might influence the improvements that you choose to make to the model.

The goal of {{site.data.keyword.knowledgestudioshort}} is to enable large teams to work together to build models. As such, it assumes that models are being produced by a team that includes a group of human annotators and a separate person or group of people that builds and tests the model, and makes improvements to it. Due to this assumption, the application is configured to push an equally proportioned grouping of documents from a single document set into the test, train, and blind sets. However, if your team is not segregated - if the people doing human annotation are also reviewing model test results in detail, for example - then you might need to change the allocation of documents into these sets to more explicitly separate the documents that are being used in each one.

### Why do I need a blind set?
{: #wks_mamanagedata_why}

Because you use test data to assess accuracy in detail, you get to know the documents and their features after a while. For example, you start to know which entity types, relation types, and text types in the documents are best understood by the machine learning model, and which are not. This information is important because it helps you focus on making the right improvements - refining the type system, supplementing the training data to fill gaps, or adding dictionaries, for example. As the test documents get used iteratively to improve the model, they can start to influence the model training indirectly. That's why the "blind" set of documents is so important.

### How do I control which documents are allocated to a set?
{: #wks_mamanagedata_how}

When you create a machine learning model, you must specify the ratio of documents from the set to allocate to the train, test, or blind sets. {{site.data.keyword.knowledgestudioshort}} automatically applies a ratio of 70/23/7 to the document sets that you use to build a machine learning model. You can change these values.

- To add a set that was annotated by humans to the training set, specify a 100/0/0 breakdown ratio.
- After training with a set, you can use it for testing. To use a document set for testing only, specify a 0/100/0 breakdown ration.
- Only add a document set that has never been used for training or testing to the blind set. To do so, specify a 0/0/100 breakdown ratio for the document set.

Plan to stop using a blind set after a few iterations. The more you use a blind set, the less "blind" it becomes. The same goes for your test data. Rather than discard the sets, you can migrate them to serve a new purpose. Follow this migration flow:

```
blind --> test --> train
```
{: screen}

As the sets migrate, you can add new, unseen document sets as blind data, and as test data. But, be sure to retain a method for evaluating accuracy across model versions. One way to establish a baseline is to run an earlier version of the model on the new document sets. The results of this run give you a basis of comparison with runs of newer models on those same sets.
