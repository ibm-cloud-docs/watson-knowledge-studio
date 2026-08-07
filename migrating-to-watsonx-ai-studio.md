---

copyright:
  years: 2025, 2026
lastupdated: "2026-08-07"

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

# Migrating from Watson Knowledge Studio to watsonx.ai Studio with Watson NLP

## Useful links
{: #useful-links}

- [Doccano annotation tool](https://github.com/doccano/doccano)
- [BRAT annotation tool](https://brat.nlplab.org/features.html)
- [Watson NLP custom entity model training in watsonx.ai Studio](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/watson-nlp-entities-transformer.html?context=cpdaas&audience=wdp&locale=en)
- [Watson NLP in watsonx.ai Studio in IBM Cloud documentation](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/watson-nlp.html)
- [Watson NLP in watsonx.ai Studio in Cloud Pak for Data docs](https://www.ibm.com/docs/en/cloud-paks/cp-data/latest?topic=studio-watson-natural-language-processing)

## Overview
{: #overview}

IBM Watson Knowledge Studio (WKS) is deprecated. The following timeline applies to all existing WKS customers:

|Milestone|Date|Description|
|---|---|---|---|
|End of marketing|31 July 2026|No new WKS instances can be provisioned or downloaded.|
|End of support|31 July 2027|WKS can still be used but IBM support is no longer available.|
|End of life|31 January 2028|WKS is decommissioned from IBM Cloud. All instances are permanently withdrawn.|

Existing customers must migrate their workloads before 31 January 2028.

IBM Watson Knowledge Studio (WKS) is a tool for training custom natural language processing (NLP) models to identify domain-specific entities and relations in unstructured text. WKS provided a browser-based environment for managing type systems, annotating documents, training machine learning models, and deploying entity and relation extractors to services such as IBM Watson Natural Language Understanding and IBM Watson Discovery.

The following migration steps describe how to migrate from WKS to IBM watsonx.ai and help you understand the functional mapping between WKS capabilities and watsonx.ai capabilities. The recommended migration path is to use watsonx.ai Prompt Lab for prompt engineering and watsonx.ai Tuning Studio for prompt tuning, by using IBM Granite foundation models. These capabilities replace the model training and customization functions that WKS provided.

**Note:** IBM is not providing a replacement for the WKS annotation editor in the IBM Cloud UI. Customers who require text annotation tooling must use open-source tools such as Doccano or BRAT to prepare labeled training data before importing it into watsonx.ai.
{: note}

## Migration process
{: #migration-process}

### 1. Assess your WKS workspace
{: #assess-wks-workspace}

1. Identify the capabilities that you are using in WKS: entity extraction (ML-based) or relation extraction (ML-based).
2. Export all ground-truth annotations, dictionaries, and trained model artifacts from WKS before the service end-of-life date.
3. Review the capability-mapping sections in this topic to identify the corresponding migration path for each capability.

### 2. Install the prerequisites
{: #install-prerequisites}

Prepare your instance of watsonx.ai Studio.

#### In watsonx.ai Studio SaaS in IBM Cloud
{: #prerequisites-saas}

1. Create an instance of [watsonx.ai Studio](https://cloud.ibm.com/catalog/services/watsonxai-studio).
2. Create an instance of the [Watson Machine Learning (WML) service](https://cloud.ibm.com/catalog/services/watson-machine-learning).

#### In watsonx.ai Studio in Cloud Pak for Data (on-premises)
{: #prerequisites-cpd}

1. Configure by using [IBM Sales Configurator](https://app.ibmsalesconfigurator.com/#/) and ensure that Watson Studio and Watson Machine Learning services are selected.
2. Install the Watson NLP models required for your application. See [Installing pre-trained NLP models for Python-based notebook runtimes](https://www.ibm.com/docs/en/software-hub/5.1.x?topic=studio-post-installation-setup#nlp).

### 3. Set up your annotation tool
{: #setup-annotation-tool}

IBM does not provide a UI product for annotation as a replacement for WKS. Select an open source annotation tool based on your use case:

- **Doccano** — for entity extraction annotation
- **BRAT** — for entity extraction annotation or relation extraction annotation

See the Annotation sections under [Entity Extraction](#entity-extraction) and [Relation Extraction](#relation-extraction) for setup guidance.

### 4. Select your training path
{: #select-training-path}

For entity and relation extraction model training, two paths are available:

- **watsonx.ai Prompt Engineering and Prompt Tuning** — Use Prompt Lab or Tuning Studio with IBM Granite foundation models. This is the recommended path for both entity and relation extraction.
- **watsonx.ai Studio with Watson NLP** — Use Watson NLP within watsonx.ai Studio notebooks to train and deploy custom NLP models. This path is documented for entity extraction. 

**Note:** Watson NLP relation extraction training is not currently publicly documented. See [Relation Extraction: Model Training](#relation-extraction-model-training) for details.

### 5. Deploy your model
{: #deploy-model}

Deploy your trained model as an online deployment in watsonx.ai Studio. For deployment instructions, see:

#### In watsonx.ai Studio SaaS in IBM Cloud
{: #deploy-saas}

- [Documentation](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/deploy-NLP-model.html?context=wx&audience=wdp)
- [Sample notebook](https://www.ibm.com/docs/en/cloud-paks/cp-data/5.2.x?topic=assets-deploying-nlp-models#nlp-model-deployment-examples)

#### In watsonx.ai Studio in Cloud Pak for Data (on-premises) 
{: #deploy-cpd}

- [Documentation](https://www.ibm.com/docs/en/cloud-paks/cp-data/5.4.x?topic=assets-deploying-nlp-models)
- [Sample notebook](https://www.ibm.com/docs/en/cloud-paks/cp-data/5.2.x?topic=assets-deploying-nlp-models#nlp-model-deployment-examples)

### 6. Sizing and pricing
{: #sizing-and-pricing}

Watson NLP model performance varies by model type. Transformer-based entity extractors require more compute than rule-based or dictionary-based models.

- **In SaaS IBM Cloud:** Pricing is based on Compute Unit Hours (CUH). See [watsonx.ai Studio plan](https://cloud.ibm.com/catalog/services/watsonxai-studio) for current pricing.
- **In Cloud Pak for Data (on-premises):** Pricing is per VPC. Use throughput measurements to estimate the number of VPCs required.

For additional assistance with calculating costs, contact IBM Sales.

## Capability mapping
{: #capability-mapping}

This section describes how to migrate each WKS capability to watsonx.ai Studio with Watson NLP.

## Entity extraction
{: #entity-extraction}

### ML-based entity extraction
{: #ml-entity-extraction}

#### Annotation
{: #entity-extraction-annotation}

IBM does not provide a UI product for data annotation in watsonx.ai. Use one of the following open source tools to create labeled training data for your ML-based entity extraction model.

##### Option 1: Doccano
{: #entity-annotation-doccano}

Doccano is an open source, web-based annotation tool for sequence labeling tasks such as named entity recognition (NER).

1. Install Doccano by following the setup instructions in the [Doccano GitHub repository](https://github.com/doccano/doccano).
2. Create a new project and select the **Sequence Labeling** task type.
3. Import your source documents in plain text or JSONL format.
4. Define your entity label set to match the entity types you intend to extract.
5. Annotate each document by selecting text spans and assigning the appropriate label.
6. Export your completed annotations by using **Action > Export Dataset** in JSONL format.

**Note:** Doccano exports annotated data in JSONL format, which is compatible with watsonx.ai prompt tuning (Tuning Studio). To use annotations for Watson NLP custom NER model training in watsonx.ai Studio, convert the exported JSONL file to the Watson NLP span-annotation format before training.

##### Option 2: BRAT
{: #entity-annotation-brat}

BRAT is an open source, browser-based annotation tool that supports both entity annotation and relation annotation.

1. Download and install BRAT by following the [installation guide on the BRAT website](https://brat.nlplab.org/features.html).
2. Configure your annotation schema in the `annotation.conf` file to define the entity types and relation types you need.
3. Place your source text documents in the BRAT data directory.
4. Open the BRAT web interface and annotate text spans as entities and optionally define relations between entities.
5. Export the completed annotations in BRAT standoff format (`.ann` files).
6. Convert the BRAT standoff output to Watson NLP span-annotation format before using the data for model training.

**Note:** BRAT standoff format is not natively compatible with watsonx.ai training pipelines. You must convert BRAT output to JSONL (for prompt tuning) or to Watson NLP span-annotation format (for Watson NLP custom NER training) before proceeding to model training.

#### Model training
{: #entity-extraction-model-training}

Two training paths are available after you have prepared and exported your annotated data.

##### Option 1: watsonx.ai Prompt Engineering and Prompt Tuning
{: #entity-training-prompt-tuning}

Use the watsonx.ai Prompt Lab for prompt engineering or the Tuning Studio to run prompt tuning experiments with IBM Granite models. This option is suitable when you want to adapt a foundation model to entity extraction without training a model from scratch.

1. Log in to watsonx.ai and open your project.
2. Format your annotated entity data as prompt-response pairs in JSONL format. Each record should include an input prompt containing the source text and a response containing the expected entity output.
3. To test prompt engineering without tuning, open **Prompt Lab**, select an IBM Granite model, and iterate on your prompt instructions and few-shot examples.
4. To run prompt tuning, open **Tuning Studio** from your project and click **Tune a foundation model with labeled data**.
5. Name your tuning experiment and click **Create**.
6. Select an IBM Granite model as the base foundation model.
7. Upload your JSONL prompt-response pairs as training data.
8. Configure tuning parameters and start the experiment.
9. Evaluate the tuned model output and compare performance against the base model.
10. Save and deploy the tuned model when performance meets your requirements.

**Note:** Prompt tuning in Tuning Studio is an efficient, low-cost method to adapt IBM Granite models to downstream tasks such as entity extraction without updating all model weights.

##### Option 2: watsonx.ai Studio with Watson NLP
{: #entity-training-watson-nlp}

This is the documented path for training a custom NER model by using the Watson NLP transformer-based workflow in watsonx.ai Studio.

For full instructions, see the [Watson NLP entities transformer documentation](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/watson-nlp-entities-transformer.html?context=cpdaas&audience=wdp&locale=en).

###### In watsonx.ai Studio SaaS in IBM Cloud
{: #entity-training-nlp-saas}

1. Create an instance of [watsonx.ai Studio](https://cloud.ibm.com/catalog/services/watsonxai-studio).
2. Create an instance of the [Watson Machine Learning (WML) service](https://cloud.ibm.com/catalog/services/watson-machine-learning).
3. Open your project in watsonx.ai Studio and create a new notebook.
4. Select the **DO + NLP Runtime** environment to access Watson NLP libraries.
5. Install and import the Watson NLP Python library in your notebook.
6. Load your annotated training data in Watson NLP span-annotation format.
7. Configure and train a custom NER model by using the transformer-based workflow. See the [Watson NLP entities transformer documentation](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/watson-nlp-entities-transformer.html?context=cpdaas&audience=wdp&locale=en) for code examples.
8. Evaluate model performance by using held-out test data.
9. Save the trained model artifact to your project.

###### In watsonx.ai Studio in Cloud Pak for Data (on-premises)
{: #entity-training-nlp-cpd}

1. Configure your Cloud Pak for Data environment by using the [IBM Sales Configurator](https://app.ibmsalesconfigurator.com/#/). Ensure that Watson Studio and Watson Machine Learning services are selected.
2. Install the required NLP models for your notebook runtime. For instructions, see [Installing pre-trained NLP models for Python-based notebook runtimes](https://www.ibm.com/docs/en/software-hub/5.4.x?topic=studio-post-installation-setup#nlp).
3. Open your project in watsonx.ai Studio and create a new notebook.
4. Select the **DO + NLP Runtime** environment to access Watson NLP libraries.
5. Load your annotated training data in Watson NLP span-annotation format.
6. Configure and train a custom NER model by using the transformer-based workflow. See the [Watson NLP entities transformer documentation](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/watson-nlp-entities-transformer.html?context=cpdaas&audience=wdp&locale=en) for code examples.
7. Evaluate model performance by using held-out test data.
8. Save the trained model artifact to your project.

**Note:** Disambiguation is not available in Watson NLP in watsonx.ai Studio.

#### Model inference
{: #entity-extraction-inference}

Run inference by using the method that corresponds to how you trained your model.

##### Option 1: Inference for Granite prompt-tuned models
{: #entity-inference-granite}

Use the watsonx.ai Prompt Lab or REST API to run inference against your deployed prompt-tuned Granite model.

###### Using Prompt Lab
{: #entity-inference-granite-prompt-lab}

1. Open **Prompt Lab** in watsonx.ai.
2. Select your deployed tuned Granite model from the model selector.
3. Enter the input text that you want to extract entities from, following the same prompt format used during tuning.
4. Review the model response and adjust parameters such as max tokens and decoding method as needed.

###### Using the REST API
{: #entity-inference-granite-rest-api}

1. Obtain your IBM Cloud API key or Cloud Pak for Data authentication token.
2. Retrieve the deployment ID of your tuned model from the watsonx.ai deployment space.
3. Send a POST request to the watsonx.ai REST inference endpoint, specifying the deployment ID and your input prompt.
4. Parse the JSON response to extract the entity predictions returned by the model.

**Note:** You can retrieve the API command directly from Prompt Lab by clicking **View code** after building your prompt.

##### Option 2: Inference for Watson NLP custom NER models
{: #entity-inference-watson-nlp}

Use the watsonx.ai Studio deployment pipeline and Watson Machine Learning inference APIs to serve and query your custom Watson NLP NER model.

1. Open your project in watsonx.ai Studio and navigate to the saved custom NER model artifact.
2. Promote the model to a deployment space by clicking **Promote to space**.
3. In the deployment space, click **Deploy** and select **Online** deployment to create a REST endpoint.
4. Note the endpoint URL and deployment ID after deployment is complete.
5. Authenticate with your IBM Cloud API key or Cloud Pak for Data token.
6. Send a POST request to the Watson Machine Learning scoring endpoint with your input text payload in the required Watson NLP request format.
7. Parse the JSON response to extract entity mention spans, entity types, and confidence scores returned by the model.

**Note:** Both online and batch deployment options are available for Watson NLP custom models in watsonx.ai Studio. Use batch deployment for large-scale, asynchronous inference workloads.

## Relation extraction
{: #relation-extraction}

### ML-based relation extraction
{: #ml-relation-extraction}

Use this guidance to migrate machine learning (ML)-based relation extraction models from Watson Knowledge Studio to watsonx.ai. The migration covers three phases: annotation, model training, and model inference.

#### Annotation
{: #relation-extraction-annotation}

IBM does not provide a UI product for annotation as a replacement for WKS. Use BRAT (brat rapid annotation tool) as the recommended third-party annotation tool. BRAT supports both entity span labeling and typed binary relation annotation.

For more information about BRAT features, see the [BRAT features page](https://brat.nlplab.org/features.html).

**Note:** Doccano can also be used for annotation but has limited support for relation annotation. BRAT is preferred for relation extraction workflows.

##### Setting up BRAT for relation annotation
{: #brat-relation-setup}

1. Download and install BRAT from the [BRAT GitHub repository](https://github.com/nlplab/brat). BRAT requires Python and a web server (Apache or the built-in server).

2. Run the BRAT installation script:
   ```sh
   python install.py
   ```

3. Start the BRAT server:
   ```sh
   python standalone.py
   ```

4. Open a browser and navigate to `http://localhost:8001` to access the BRAT interface.

5. Place your plain-text documents (`.txt` files, one document per file) into a subdirectory under the BRAT `data/` folder. For example: `brat/data/my_relation_project/`

6. Create an `annotation.conf` file in the same subdirectory. Define your entity types under `[entities]` and your relation types under `[relations]`. For example:
   ```
   [entities]
   Organization
   Person
   Location

   [relations]
   EmployedBy   Arg1:Person, Arg2:Organization
   LocatedIn    Arg1:Organization, Arg2:Location

   [events]
   [attributes]
   ```

7. Reload the BRAT interface. Your entity and relation types now appear in the annotation panel.

8. Annotate each document by:
   - Selecting a text span to create an entity mention.
   - Clicking the source entity, then the target entity, to draw a relation arc and assign a relation type.

9. Export the completed annotations. BRAT saves annotations automatically in standoff format as paired `.txt` and `.ann` files in the same data directory.

##### Converting BRAT output for watsonx.ai training
{: #brat-output-conversion}

Convert the BRAT standoff (`.ann`) files to JSON Lines (JSONL) format for use with watsonx.ai Tuning Studio. Each line should represent one training example as a prompt-response pair. See [Model Training](#relation-extraction-model-training) for the required format.

#### Model training
{: #relation-extraction-model-training}

Use Prompt Lab for prompt engineering or Tuning Studio for prompt tuning with IBM Granite models to train a relation extraction model in watsonx.ai.

##### watsonx.ai Prompt Engineering and Prompt Tuning
{: #relation-training-prompt-tuning}

Use Prompt Lab for prompt engineering or Tuning Studio for prompt tuning with IBM Granite models. This is the recommended documented path.

###### Step 1: Format your training data
{: #relation-training-format-data}

1. Convert your BRAT annotation output to JSONL format. Each record must contain an `input` field (the prompt) and an `output` field (the expected relation label or structured response).

   Example JSONL record:
   ```json
   {"input": "Extract relations from the following sentence. Sentence: 'Jane Doe works at IBM.' Entities: [Person: Jane Doe], [Organization: IBM]", "output": "EmployedBy(Jane Doe, IBM)"}
   ```

2. Prepare a minimum of 100 to 1000 labeled examples for effective prompt tuning. More examples improve model performance.
3. Save the file with the `.jsonl` extension.

###### Step 2: Create a watsonx.ai project
{: #relation-training-create-project}

4. Log in to IBM Cloud and open the watsonx.ai console.
5. Create a new project or open an existing project.

###### Step 3: Prompt engineer with Prompt Lab (optional, before tuning)
{: #relation-training-prompt-lab}

6. Open **Prompt Lab** from your project.
7. Select an IBM Granite model (for example, `ibm/granite-13b-instruct-v2`).
8. Write a few-shot prompt template that includes entity context and asks the model to identify the relation type. Evaluate model output quality.
9. Iterate on prompt wording until outputs are consistently structured.

###### Step 4: Tune the Granite model with Tuning Studio
{: #relation-training-tuning-studio}

10. Open **Tuning Studio** from your project.
11. Click **New tuning experiment**.
12. Select your IBM Granite base model.
13. Upload your JSONL training file.
14. Configure tuning parameters (number of epochs, batch size, learning rate). Accept defaults for an initial experiment.
15. Click **Start experiment**. Tuning Studio trains a soft prompt layer on top of the frozen base model.
16. Monitor training loss in the experiment dashboard.
17. When training completes, save the tuned model to your project.

**Note:** Prompt tuning does not update the base model weights. It produces a lightweight soft prompt that is applied at inference time.

#### Model inference
{: #relation-extraction-inference}

Use the watsonx.ai Prompt Lab UI or the watsonx.ai REST API to run inference against a deployed Granite prompt-tuned model.

##### Deploying the tuned model
{: #relation-inference-deploy}

1. In your watsonx.ai project, open the tuned model asset.
2. Click **Promote to deployment space** and select or create a deployment space.
3. In the deployment space, click **Deploy**.
4. Select **Online** as the deployment type.
5. Provide a deployment name and click **Create**.
6. Wait for the deployment status to show **Deployed**.

##### Running inference from Prompt Lab
{: #relation-inference-prompt-lab}

7. Open **Prompt Lab** from your project.
8. Select **My tuned models** and choose your deployed model.
9. Enter the relation extraction prompt template, including the sentence and entity mentions.
10. Click **Generate** to retrieve the predicted relation.

##### Running inference from the REST API
{: #relation-inference-rest-api}

11. Obtain your IBM Cloud API key and the watsonx.ai instance URL from the IBM Cloud console.
12. Generate an IAM bearer token:
    ```sh
    POST https://iam.cloud.ibm.com/identity/token
    Content-Type: application/x-www-form-urlencoded

    grant_type=urn:ibm:params:oauth:grant-type:apikey&apikey=<YOUR_API_KEY>
    ```

13. Send a generation request to the watsonx.ai inference endpoint:
    ```sh
    POST https://<REGION>.ml.cloud.ibm.com/ml/v1/text/generation?version=2023-05-29
    Authorization: Bearer <IAM_TOKEN>
    Content-Type: application/json

    {
      "model_id": "<YOUR_TUNED_MODEL_ID>",
      "input": "Extract relations from the following sentence. Sentence: 'Jane Doe works at IBM.' Entities: [Person: Jane Doe], [Organization: IBM]",
      "parameters": {
        "max_new_tokens": 50
      },
      "project_id": "<YOUR_PROJECT_ID>"
    }
    ```

14. Parse the `results[0].generated_text` field from the JSON response to extract the predicted relation.

**Note:** Replace `<REGION>`, `<YOUR_TUNED_MODEL_ID>`, `<YOUR_API_KEY>`, and `<YOUR_PROJECT_ID>` with values from your IBM Cloud environment.
