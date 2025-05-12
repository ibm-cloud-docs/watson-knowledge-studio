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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio/glossary.html).
{: tip}

# Glossary
{: #glossary}

This glossary includes terms and definitions for {{site.data.keyword.knowledgestudioshort}}.
{: shortdesc}

The following cross-references are used in this glossary:

- *See* refers you from a term to a preferred synonym, or from an acronym or abbreviation to the defined full form.
- *See also* refers you to a related or contrasting term.

[A](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_A) [B](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_B) [C](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_C) [D](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_D) [E](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_E) [F](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_F) [G](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_G) [H](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_H) [I](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_I) [K](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_K) [L](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_L) [M](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_M) [N](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_N) [O](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_O) [P](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_P) [R](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_R) [S](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_S) [T](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T)

## A
{: #gloss_A}

- **accuracy**

    A measure of the correctness of annotations that are produced by a machine learning model. See also [precision](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_P) and [recall](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_R).

- **accuracy analysis**

    Analyzing machine learning model scores to determine whether changes are needed to improve accuracy.

- **adjudication**

    An iterative process for resolving annotation conflicts by comparing the annotations added to the same document by different human annotators.

- **analysis engine**

    A program that analyzes artifacts, such as documents, and infers information about them, and which implements the UIMA Analysis Engine interface specification. Analysis engines are constructed from building blocks called annotators. An analysis engine can contain a single annotator, which is referred to as a primitive analysis engine, or multiple annotators, which is referred to as an aggregate analysis engine.

- **annotation**

    Information about a span of text. For example, an annotation might indicate that a span of text represents a company name.

- **annotation set**

    In human annotation, a collection of documents that are extracted from the corpus that allow the workload to be shared by multiple human annotators. In machine-based annotation, a collection of documents that can be used as blind data, training data, or test data.

- **annotation process manager**

    A role that is responsible for managing the full annotation lifecycle activities within a workspace. The project manager that is added to a workspace typically performs the activities of an annotation process manager.

- **annotator**

    See [human annotator](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_H) and [machine learning annotator](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_M).

- **attribute**

    A characteristic or trait of an entity that describes the entity; for example, the telephone number of an employee is one of the employee attributes.

## B
{: #gloss_B}

- **blind data**

    A set of documents annotated with the ground truth, such as question and answer pairs, semantic annotation, and passage judgment. Blind data is never released or seen by developers and is used to test the system periodically to evaluate performance on unseen data. Testing on blind data prevents accuracy from being tainted by over-fitting to known question sets or annotations. Reported results should only come from tests that are run on blind data. See also [testing data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T) and [training data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T).

## C
{: #gloss_C}

- **concordance**

    Provides a way to ensure that the same mention is annotated with the same entity type throughout a document and across annotation sets. Concordance helps ensure consistency across multiple occurrences of a mention without requiring the human annotator to manually label each occurrence.

- **confusion matrix**

    A table that provides a detailed numeric breakdown of annotated document sets. The table is used to compare the annotations that were added by a machine learning model to the annotations in the ground truth. The table reports the number of [false positives](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_F), [false negatives](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_F), [true positives](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T), and [true negatives](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T).

- **coreference**

    A relationship between two words or phrases in which both refer to the same person or thing and one stands as a linguistic antecedent of the other. For example, there is a coreference between the two pronouns in the phrase "She taught herself" but not in the phrase "She taught her". A coreference links two equivalent entities in the same text.

- **coreference chain**

    A list of entities that were annotated as coreferences. When you annotate mentions as coreferences, the system creates a coreference chain. The chain provides a way for you to view all of the mentions in context and verify that all of the occurrences belong together under the same entity type.

- **corpus**

    A collection of source documents that were added to a workspace and used to train a machine learning model.

- **curate**

    To select, collect, preserve, and maintain content relevant to a specific topic. Curation establishes, maintains, and adds value to data; it transforms data into trusted information and knowledge.

## D
{: #gloss_D}

- **dictionary**

    A collection of words that can be used to pre-annotate documents. A new annotation is created for each word in the document text that matches a term in the dictionary. A machine learning model can be configured with one or more independent dictionaries, which are typically domain-specific, such a dictionary for pharmaceuticals and a dictionary for wealth management. See also [lemma](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_L) and [surface form](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_S).

- **dictionary pre-annotator**

    A component that identifies mentions in text that match a specific set of words. By using domain-specific terminology to pre-annotate text, dictionary pre-annotators can accelerate a human annotator's ability to prepare a set of ground truth documents.

- **document set**

    A collection of documents. Documents that are imported together become a document set. Annotated documents that are grouped together for training purposes (Test, Train, Blind) are generated as document sets.

## E
{: #gloss_E}

- **entity**

    1. A mention that is annotated by an entity type.
    1. A person, object, or concept about which information is stored.
    1. A set of details that are held about a real-world object such as a person, location, or bank account. An entity is a kind of item.

- **entity type**

    The type of entity that a mention represents without consideration for context. For example, the mention {{site.data.keyword.IBM_notm}} might be annotated by the entity type ORGANIZATION.

    In an entity-relationship model, an entity type is the thing that is being modeled or the thing that a mention refers to, such as the name of a person or place. Different entity types have different sets of attributes such as "surname" or "home town", and are connected through relationships like "lives in". An entity type exists independently and can be uniquely identified.

## F
{: #gloss_F}

- **F1 score**

    A measure of a test's accuracy that considers both precision and recall to compute the score. The F1 score can be interpreted as a weighted average of the precision and recall values. An F1 score reaches its best value at 1 and worst value at 0.

- **false negative**

    An answer or annotation that is correct, but was predicted to be incorrect.

- **false positive**

    An answer or annotation that is incorrect, but was predicted to be correct.

- **feature**

    A data member or attribute of a type.

- **Fleiss Kappa score**

    A measure of how consistently the same annotation was applied by multiple human annotators across overlapping documents. The Fleiss Kappa score reaches its best value at 1 and worst value at 0.

## G
{: #gloss_G}

- **ground truth**

    The set of vetted data, consisting of annotations added by human annotators, that is used to adapt a machine learning model to a particular domain. Ground truth is used to train machine learning models, measure model performance (precision and recall), and calculate headroom to decide where to focus development efforts for improving performance. Accuracy of ground truth is essential since inaccuracies in the ground truth will correlate to inaccuracies in the components that use it.

## H
{: #gloss_H}

- **headroom analysis**

    The process of determining how much improvement in accuracy, precision, or recall can be expected by addressing some class of problems that are identified while performing accuracy analysis.

- **human annotator**

    A subject matter expert who reviews, modifies, and augments the results of pre-annotation by identifying mentions, entity type relationships, and mention coreferences. By examining text in context, a human annotator helps determine ground truth and improve the accuracy of the machine learning model.

## I
{: #gloss_I}

- **inter-annotator agreement**

    A measure of how similarly a document in two or more document sets is annotated.

## K
{: #gloss_K}

- **knowledge graph**

    A model that consolidates typed entities, their relationships, their properties, and hierarchical taxonomies to represent an organization of concepts for a given domain. After the knowledge graph store is loaded with inputs from structured and unstructured data sources, users and applications can access the knowledge graph to explore key elements of knowledge for a specific domain, explore interactions, and discover additional relationships.

## L
{: #gloss_L}

- **lemma**

    The normalized or canonical form of a word. Typically, the lemma is the underived and uninflected form of a noun or a verb. For example, the lemma of the terms 'organizing' and 'organized' is 'organize'. See also [dictionary](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_D) and [surface form](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_S).

## M
{: #gloss_M}

- **machine learning**

    A method of data analysis that iteratively learns from past data and independently adapts when exposed to new data. The mathematical model at the core of machine learning is built from ground truth inputs. Through training and refinement of example input data, the model can deliver accurate, repeatable results when it analyzes new data.

- **machine learning annotator**

    See [machine learning model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_M).

- **machine learning model**

    A component that identifies entities and entity relationships according to a statistical model that is based on ground truth. The model applies past experience, such as training data, to determine or predict the correct outcome of future experiences based on characteristics of the data. These past experiences are captured in the form of a model by calculating feature scores for each candidate answer or evidence and combining that with known outcomes. Sometimes referred to as *machine learning annotator*.

- **mention**

    A span of text that you consider relevant in your domain data. For example, in a type system about automotive vehicles, occurrences of terms like "airbag", "Ford Explorer", and "child restraint system" might be relevant mentions.

## N
{: #gloss_N}

- **named entity**

    A concept in a domain that falls in to a well-defined category, such as names of organizations, locations, authors, or diseases.

- **natural language processing**

    A field of artificial intelligence and linguistics that studies the problems inherent in the processing and manipulation of natural language, with an aim to increase the ability of computers to understand human languages.

## O
{: #gloss_O}

- **ontology**

    An explicit formal specification of the representation of the objects, concepts, and other entities that can exist in some area of interest and the relationships among them.

## P
{: #gloss_P}

- **part of speech (POS)**

    In a dictionary, individual lexical items are assigned part of speech (POS) tags. For example, the word 'fly' can be identified as a verb or a noun.

- **performance**

    The measurement of a {{site.data.keyword.watson}} system in terms of accuracy, precision, and recall, for example, when answering questions, discovering relationships, or annotating text.

- **pre-annotation**

    The process of annotating a set of documents prior to human annotation. Documents can be pre-annotated by using a rule-based model, a machine-learning model, {{site.data.keyword.nlufull}}, or a dictionary. Pre-annotation can help human annotators more quickly prepare a set of ground truth documents.

- **precision**

    A measurement that specifies the proportion of results that are relevant. Precision, which is a positive predictive value, is determined by the number of correct positive results divided by the number of all positive results. Accuracy is best measured by using both precision and recall. See also [accuracy](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_A) and [recall](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_R).

- **processing engine archive (PEAR)**

    A `.pear` archive file that includes an Unstructured Information Management Architecture (UIMA) analysis engine and all of the resources that are required to use it for custom analysis.

## R
{: #gloss_R}

- **recall**

    A measurement that specifies the percentage of relevant results returned, out of all available relevant results. Recall, which is a measure of sensitivity, is determined by the number of correct positive results divided by the number of positive results that should have been returned. Accuracy is best measured by using both precision and recall. See also [accuracy](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_A) and [precision](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_P).

- **relation**

    Typically a verb that reflects how entities are related to one another. For example, "lives in" is a relation between a person and a town. A relation links two different entities in the same sentence.

- **relation type**

    A binary, uni-directional relationship between two entities. For example, `Mary` `employedBy` {{site.data.keyword.IBM_notm}} is a valid relationship; {{site.data.keyword.IBM_notm}} `employedBy` `Mary` is not.

- **role**

    An attribute that provides a context-sensitive meaning of a mention. For example, in the phrase "I went to {{site.data.keyword.IBM_notm}} today", {{site.data.keyword.IBM_notm}} is the mention, Organization is the entity type, and Facility is the role of the entity type.

- **rule set**

    A set of rules that define patterns for annotating text. If a pattern applies, then the actions of the rule are performed on the matched annotations. A rule typically specifies the condition that must match, an optional quantifier, a list of additional constraints that the matched text must fulfill, and the actions to be taken when a match occurs, such as creating a new annotation or modifying an existing annotation.

## S
{: #gloss_S}

- **subtype**

    A type that extends or implements another type; the supertype.

- **surface form**

    The form of a word or multiword unit as it is found in the corpus. For example, some surface forms of the lemma 'organize' are the terms 'organizing' and 'organized'. See also [dictionary](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_D) and [lemma](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_L).

## T
{: #gloss_T}

- **testing data**

    A set of annotated documents that can be used to evaluate system metrics after ingestion and training. See also [blind data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_B) and [training data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T).

- **train**

    The process of setting up a {{site.data.keyword.watson}} instance with components that enable the system to function in a particular domain (for example: corpus content, training data that generates machine learning models, programmatic algorithms, or other ground truth components) and then making improvements and updates to these components based on accuracy analysis.

- **training data**

    A set of annotated documents that can be used to train machine learning models. See also [blind data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_B) and [testing data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-glossary#gloss_T).

- **true negative**

    An answer or annotation that is actually incorrect and is predicted to be incorrect.

- **true positive**

    An answer or annotation that is actually correct and is predicted to be correct.

- **type system**

    The type system defines the types of objects that can be discovered in a document. The type system defines all possible entity types and relationships between entity types. You can define any number of different types in a type system. Type systems are generally domain-specific and application-specific.
