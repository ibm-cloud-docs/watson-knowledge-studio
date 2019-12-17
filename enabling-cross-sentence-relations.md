---

copyright:
  years: 2019
lastupdated: "2019-12-12"

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

# Enabling cross-sentence relations (Experimental)
{: #enabling-cross-sentence-relations}

English entities and relations workspaces that you create can support annotating relations between pairs of entity mentions that exist within spans of six sentences. In workspaces where the cross-sentence relations feature is not enabled, the ground truth editor and runtime models do not support annotating relations that cross sentence boundaries.
{: shortdesc}

Cross-sentence relations is an experimental feature that might be discontinued without notice. It is not recommended to use this feature in a production environment.
{: important}

Enabling cross-sentence relations might decrease the performance of the ground truth editor and the performance of any models that you deploy from the workspace at runtime.
The cross-sentence relations setting cannot be changed for a workspace after it is created.
{: note}

For example, if you plan to annotate a relation for an entity mention in the seventh sentence below, you are limited to selecting other entity mentions only in the seventh sentence unless you enable cross-sentence relations. With the feature enabled, you can annotate a related entity mention within a span of six sentences (across up to five sentence boundaries), so the second entity mention in the relation could be annotated anywhere from the second sentence to the twelfth sentence.

```
Sentence 1.
*** Sentence 2.
Sentence 3.
Sentence 4.
Sentence 5.
Sentence 6.
-----> Sentence 7.
Sentence 8.
Sentence 9.
Sentence 10.
Sentence 11.
*** Sentence 12.
Sentence 13.
```

## Procedure
{: #enabling-cross-sentence-relations-procedure}

1. Launch the {{site.data.keyword.knowledgestudioshort}} application.
1. If you have existing workspaces, click **Create Workspace**.
1. Click **Create entities and relations workspace**.
1. Click **Advanced options**. 
1. Click the **Enable cross sentence relations** box.
1. Click **Create**.

In the new workspace, you will be able to annotate relations between pairs of entity mentions that exist within spans of six sentences.









