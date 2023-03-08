---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-24"

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
{:shortdesc: .shortdesc}

# Release notes
{: #release-notes}

The following new features and changes to {{site.data.keyword.knowledgestudiofull}} are available.
{: shortdesc}

## May 2022
{: #watson-knowledge-studio-may22}
{: release-note}

Advanced Rules Editor (Beta) will be ending on 30 June 2022.
:   The Advanced Rules Editor (ARE) (Beta) feature will end on 30 June 2022. Existing rules created in ARE workspaces can be edited and exported until that time. Any rules models that are exported can continue to be run in {{site.data.keyword.discoveryfull}} or IBM Datacap after that date.

    After 30 June 2022, Rules models can be created using the {{site.data.keyword.knowledgestudioshort}} [Rules annotator](https://cloud.ibm.com/docs/watson-knowledge-studio?topic=watson-knowledge-studio-rule-annotator). You may also use {{site.data.keyword.discoveryshort}}; the creation of rules is provided by teaching {{site.data.keyword.discoveryshort}} to [recognize patterns in your data](https://cloud.ibm.com/docs/discovery-data?topic=discovery-data-domain#patterns).

## March 2020
{: #watson-knowledge-studio-mar20}
{: release-note}

Enhanced pre-annotation workflow
:   Run multiple pre-annotators at once and configure the order of pre-annotators to resolve annotation conflicts between them. Existing pre-annotator results are preserved unless you remove them with the *Wipe* option.
:   Human annotations are preserved when running pre-annotators, even when using the *Wipe* option.

## December 2019
{: #watson-knowledge-studio-dec19}
{: release-note}

### New features and changes
{: #new-december-2019}

New advanced rules tokenizer
:   Advanced rules has introduced a new tokenizer which is not compatible with the previous one. The following extractor categories are affected:

    - **Parts of Speech** extractor names are renamed automatically
        - **Cardinal** is renamed to **Numeral**
        - **Preposition** is renamed to **Adposition**
    - **Machine Data Analytics** Splitter extractors have been removed and will disappear from the canvas. There is no substitute for these extractors that is provided by the new tokenizer.
        - Generic Splitters:
            - **Date Time Splitter**
            - **Day First Splitter**
            - **Month First Splitter**
            - **Year First Splitter**
        - Syslog Splitter:
            - **Date Time Splitter**
:   Cross-sentence relations (Experimental)

    - English entities and relations workspaces can now support annotating relations between entities within spans of six sentences. To get started, see [Enabling cross-sentence relations](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-enabling-cross-sentence-relations).

:   Full support for IBM Cloud IAM

    - {{site.data.keyword.knowledgestudioshort}} now supports the full implementation of {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). API keys for Watson services are no longer limited to a single service instance. You can create access policies and API keys that apply to more than one service, and you can grant access between services.
    - For more information about IAM, see [Authenticating to Watson services](/docs/watson?topic=watson-iam).
    - To support this change, the API service endpoints use a different domain and include the service instance ID. The pattern is `api.{location}.{offering}.watson.cloud.ibm.com/instances/{instance_id}`.

        The previous public endpoint domain was `watsonplatform.net`.

        These URLs do not introduce a breaking change. The new URLs work both for your existing service instances and for new instances. The original URLs continue to work on your existing service instances for at least one year (until December 2020).

| Region | Old | New |
|--|--|--|
| Dallas | `gateway.watsonplatform.net` | `us-south.knowledge-studio.watson.cloud.ibm.com` |
| Frankfurt | `gateway-fra.watsonplatform.net` | `eu-de.knowledge-studio.watson.cloud.ibm.com` |
| Sydney | `gateway-syd.watsonplatform.net` | `au-syd.knowledge-studio.watson.cloud.ibm.com` |
| Washington, D.C. | `gateway-wdc.watsonplatform.net` | `us-east.knowledge-studio.watson.cloud.ibm.com` |
| Tokyo | `gateway-tok.watsonplatform.net` | `jp-tok.knowledge-studio.watson.cloud.ibm.com` |
| London | `gateway-lon.watsonplatform.net` | `eu-gb.knowledge-studio.watson.cloud.ibm.com` |
| Seoul | `gateway-seo.watsonplatform.net` | `kr-seo.knowledge-studio.watson.cloud.ibm.com` |

New network and data security features
:   Support for data encryption with customer-managed keys

    - Users of new premium and dedicated instances can integrate {{site.data.keyword.keymanagementservicefull}} with {{site.data.keyword.knowledgestudioshort}} to encrypt their data and manage encryption keys. For more information, see [Protecting sensitive information in your Watson service](/docs/watson?topic=watson-keyservice).
    - **Support for private network endpoints**
        - Users of Premium plans can create private network endpoints to connect to {{site.data.keyword.knowledgestudioshort}} over a private network. Connections to private network endpoints do not require public internet access. For more information, see [Public and private network endpoints](/docs/watson?topic=watson-public-private-endpoints).

Custom categories deprecation
:   The experimental custom categories feature is deprecated and will be retired on 17 December 2019. Access to custom categories models will not be available after that date.

## November 2019
{: #watson-knowledge-studio-nov19}
{: release-note}

### New features and changes
{: #new-november-2019}
{: release-note}

New South Korea location
:   You can now create {{site.data.keyword.knowledgestudioshort}} instances in the Seoul location. As with other locations, the {{site.data.keyword.cloud_notm}} Seoul location uses token-based Identity and Access Management (IAM) authentication.

## October 2019
{: #watson-knowledge-studio-oct19}
{: release-note}

### New features and changes
{: #new-oct19}
{: release-note}

Advanced Rules workspaces (Beta) in Dallas and Frankfurt
:   Advanced rules workspaces (Beta) are now available for service instances in **Dallas** and **Frankfurt**. Create advanced rules extractors and run them to extract text from documents that you upload to the workspace. To get started, see [Creating an advanced rules model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-advanced-rules-model).

Dictionary suggestions
:   As you add entries to a dictionary, {{site.data.keyword.knowledgestudioshort}} will search the documents in your workspace to recommend additional entries that are likely to be in the same domain.

## September 2019
{: #watson-knowledge-studio-sep19}
{: release-note}

### New features and changes
{: #new-sep19}
{: release-note}

Rule-based model versions increased
:   Increased the maximum number of rule-based model versions per workspace from 5 to 10.

Updated visual style
:   Updated the visual style of the {{site.data.keyword.knowledgestudioshort}} application.

## July 2019
{: #watson-knowledge-studio-jul19}
{: release-note}

### New features and changes
{: #new-jul19}
{: release-note}

Annotation tasks are no longer required to create ground truth
:   Admins and Project Managers can annotate document sets directly from the **Ground Truth** tab on the **Annotations** page.
:   Annotation tasks are still available. You can manage them from the **Annotation Tasks** tab on the **Annotations** page.
:   Annotations applied directly to ground truth are not applied to related active annotation tasks. It is recommended that you annotate document sets directly only when they are not associated with any active annotation tasks.
:   The **Annotation Sets** tab has been removed from the **Documents** page. You can manage annotation sets from the **Annotation Tasks** tab of the **Annotations** page.

      - To create new annotation sets, click **Add task**. Then, click **Create Annotation Sets**.
      - To manage existing annotation sets, click an existing annotation task, then click **Edit**.

## March 2019
{: #watson-knowledge-studio-mar19}
{: release-note}

### New features and changes
{: #new-mar19}
{: release-note}

Custom categories workspace (Experimental)
:   Introduced an experimental custom categories workspace for {{site.data.keyword.knowledgestudioshort}} service instances on **Lite** and **Standard** plans that are hosted in the **Dallas** location. With the new workspace, you can deploy your own custom text categorization model to {{site.data.keyword.nlushort}} or {{site.data.keyword.discoveryshort}}.

## January 2019
{: #watson-knowledge-studio-jan19}
{: release-note}

Migrating Cloud Foundry service instances
:   You can now migrate {{site.data.keyword.knowledgestudioshort}} Cloud Foundry service instances to a resource group.

## December 2018
{: #watson-knowledge-studio-dec18}
{: release-note}

### New features and changes
{: #new-dec18}
{: release-note}

Support to deploy same model to multiple instances
:   Introduced support to deploy the same machine learning model version to multiple service instances and general improvements to the **Version History and Deployment** page. For more information about deploying multiple instances of the same model version see [Deploying the same model version to multiple services](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_secdep)

Added `models` method
:   Added the `models` method to the {{site.data.keyword.nlushort}} service allowing users to list deployed {{site.data.keyword.knowledgestudioshort}} models.

## September 2018
{: #watson-knowledge-studio-sep18}
{: release-note}

### New features and changes
{: #new-sep18}
{: release-note}

Support for additional document types
:   Introduced support for HTML, DOC, DOCX, and PDF files. For more information about the supported document types, size limits, and other information, see  [Creating a workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-project#cp-mlm). For more information about adding documents for annotation, see [Adding documents to a workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation#wks_projadd).

## August 2018
{: #watson-knowledge-studio-aug18}
{: release-note}

### New features and changes
{: #new-aug18}
{: release-note}

New automated migration option
:   Introduced a new option for automated migration of Standard plan instances from the deprecated {{site.data.keyword.IBM_notm}} Marketplace platform to the {{site.data.keyword.cloud_notm}} platform. If you have a Standard instance on the deprecated platform, you'll have the option to migrate. For more information, see [Migrating to {{site.data.keyword.cloud_notm}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-migrate).

## July 2018
{: #watson-knowledge-studio-jul18}
{: release-note}

### New features and changes
{: #new-jul18}
{: release-note}

Deployed Models page updated
:   The **Deployed Models** page was updated to include models from {{site.data.keyword.knowledgestudioshort}} instances that are managed by [IAM *resource groups*](/docs/iam?topic=iam-userroles){: external}, in addition to models that are managed by [Cloud Foundry *organizations*](/docs/iam?topic=iam-cfaccess){: external}.

    What you see on the Deployed Models page depends on the [region](/docs/resources?topic=resources-services_region){: external} that hosts your {{site.data.keyword.knowledgestudioshort}} instance. If the region supports instances managed by both access management methods, you see a tab for each method. Models from instances that are managed by IAM are listed on the **Resource Groups** tab. Models from instances that are managed by Cloud Foundry are listed on the **Organizations** tab.

    If the region supports instances managed by only one of the access management methods, you see only one list of models, because only one access management method is applicable.

    To view the **Deployed Models** page, from the **Settings** menu in the top right menu bar, click **Manage deployed models**. For more information about undeploying models on the **Deployed Models** page, see [Undeploying machine learning models](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#pm-um) and [Undeploying rule-based models](//docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish).

Navigation changed to better align with the {{site.data.keyword.knowledgestudioshort}} workflow.
:   In addition, the following functionality was reorganized:

    - In the previous version, management of dictionaries was included as part of the Pre-annotators page. Now, management of dictionaries is located on the Dictionaries page in the Assets section of the navigation.
    - In the previous version, human annotation functionality was distributed across the Mentions, Relations, and Coreferences tabs in the Document Annotation section of the navigation. Now, the functionality is merged under the Annotation Tasks page in the Machine Learning Model section of the navigation.
    - To manage human annotation tasks, in the previous version, you found the Tasks tab under the Assets & Tools > Documents page. Now, you add tasks and manage existing tasks on the Annotation Tasks page in the Machine Learning Model section of the navigation.
    - In the previous version, the Rules, Regex and Dictionaries pages were separate pages in the Document Annotation section of the navigation. Now, the functionality is merged under the Rules page in the Rule-based Model section of the navigation.

    For more details about the navigation changes, see Figure 1 and Table 3.

![Screen captures of the previous navigation (left side) and new navigation (right side).](images/nav3-0718.svg "Screen captures of the previous navigation and new navigation. Details of the changes are listed in Table 3 and the previous text.") Figure 1. Screen captures of the previous navigation (left side) and new navigation (right side).

| Feature | Previous location | Current location |
|---------|--------------------------|----------------------|
| Annotation tasks | Assets & Tools > Documents > Tasks | Machine Learning Model > Annotation Tasks |
| Coreferences tab | Document Annotation | Machine Learning Model > Annotation Tasks > task > annotation set > document |
| Dictionaries page (management) | Assets & Tools > Pre-annotators > Manage Dictionaries | Assets |
| Dictionaries tab (mapping to classes for rule-based model) | Document Annotation | Rule-based Model > Rules |
| Documents page | Assets & Tools | Assets |
| Entity Types page | Assets & Tools | Assets |
| Mentions tab | Document Annotation | Machine Learning Model > Annotation Tasks > task > annotation set > document |
| Performance page | Model Management | Machine Learning Model |
| Pre-annotators page | Assets & Tools | Machine Learning Model > Pre-annotation |
| Regex tab | Document Annotation | Rule-based Model > Rules |
| Relation Types page | Assets & Tools | Assets |
| Relations tab | Document Annotation | Machine Learning Model > Annotation Tasks > task > annotation set > document |
| Rules tab | Document Annotation | Rule-based Model |
| Tasks tab | Assets & Tools > Documents | Machine Learning Model > Annotation Tasks |
| Versions page (machine learning model) | Model Management | Machine Learning Model |
| Versions page (rule-based model) | Model Management | Rule-based Model |
{: caption="Table 3. Navigation changes (July 2018)" caption-side="top"}

## May 2018
{: #watson-knowledge-studio-may18}
{: release-note}

### New features and changes
{: #new-may18}
{: release-note}

Configuration issue fixed
:   A configuration issue was fixed that caused service instances in Sydney region to not appear in US South region.

Deploy Model window support changes
:   In the Deploy Model window, if the region you're deploying to supports both {{site.data.keyword.iamlong}} *resource groups* and Cloud Foundry *spaces*, to see the list, you will need to choose the method of access management that your service instance uses.

Data collection setting added
:   Added the data collection setting on the Service Details page. For more information about data collection, see [Troubleshooting, support, and FAQs](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-troubleshooting#content)

Support for Chinese (Traditional)
:   Added Chinese (traditional) language support.

Administrators can see number of workspaces
:   Users who have the Admin role can now see the number of workspaces that are used. This info is available on the Service Details page.

Alchemy no longer available
:   {{site.data.keyword.alchemylanguagefull}} is no longer available to deploy models to.

Confirm workspace deletions
:   Now, if you delete a workspace, you will be asked to confirm your action. We hope this confirmation prevents accidental deletions.

Data privacy details
:   The documentation includes some new details about data privacy. Read more in [Information security](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-information-security).

## April 2018
{: #watson-knowledge-studio-apr18}
{: release-note}

### New features and changes
{: #new-apr18}
{: release-note}

Free plan replaced by Lite plan
:   The {{site.data.keyword.knowledgestudioshort}} Free plan was replaced with the Lite plan. For more information, see [Go Lite with Watson {{site.data.keyword.knowledgestudioshort}}](https://www.ibm.com/cloud/blog/announcements/go-lite-watson-knowledge-studio?mhsrc=ibmsearch_a&mhq=go%20lite%20with%20Watson%20Knowledge%20Studio){: external}.

## March 2018
{: #watson-knowledge-studio-mar18}
{: release-note}

### New features and changes
{: #new-mar18}
{: release-note}

New Deployed Models page
:   A **Deployed Models** page is available where you can view all the {{site.data.keyword.knowledgestudioshort}} models that are deployed to services in the spaces that you have access to. To view the **Deployed Models** page, from the **Settings** menu in the top right menu bar, click **Manage deployed models**. For more information about undeploying and viewing models on the **Deployed Models** page, see [Undeploying models](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#pm-um) and [Undeploying rule-based models](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish#ramu-um).

French interface available
:   A French translation of the {{site.data.keyword.knowledgestudioshort}} interface is now available.

Alchemy no longer available
:   {{site.data.keyword.alchemylanguagefull}} is no longer available as a pre-annotator. Instead of {{site.data.keyword.alchemylanguageshort}}, you can use {{site.data.keyword.nlushort}} to pre-annotate your documents. For more information, see [Bootstrapping annotation](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-preannotation).

## December 2017
{: #watson-knowledge-studio-dec17}
{: release-note}

### New features and changes
{: #new-dec17}
{: release-note}

Launch on Cloud
:   {{site.data.keyword.knowledgestudioshort}} launched on {{site.data.keyword.cloud_notm}}. For more information about the migration process and schedule, see [Migrating to {{site.data.keyword.cloud_notm}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-migrate).

Redesigned navigation
:   For more information about the navigation changes, see [Table 2](#september2017) in the September 2017 release notes.

Added pre-annotator
:   Added {{site.data.keyword.nlufull}} as a pre-annotator.

Added setting to Service Details page
:   Added user and storage management settings to the Service Details page. For more information about adding users, see [Assembling a team](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-team). For more information about setting storage limits, see [Troubleshooting > Storage space issues](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-troubleshooting#storage).

Added Performance page
:   Added a Performance page for model quality evaluation and guidance about how to improve quality.

## November 2017
{: #watson-knowledge-studio-nov17}
{: release-note}

### Changes
{: #new-nov17}
{: release-note}

Bug fixes
:   Fixed an issue where some relation annotations were missing in the downloaded corpus.
:   Fixed an issue where a model could not be withdrawn from deployment if its status was **None**.
:   Fixed an issue where the model could not be evaluated for Korean.

## October 2017
{: #watson-knowledge-studio-oct17}
{: release-note}

### Changes
{: #new-oct17}
{: release-note}

Export issue fixed
:   Fixed the issue with the **Export** button not being enabled until you refreshed the browser window in the {{site.data.keyword.cloud_notm}} [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release.

Button label issue fixed
:   Fixed the button labels and tooltips to match the changes for the terms _upload_ and _download_ in the {{site.data.keyword.cloud_notm}} [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release. These terms  are used instead of _import_ and _export_ when referring to type systems, documents, and dictionaries.

Description delay issue fixed
:   Fixed the delay in updating the descriptions on the {{site.data.keyword.knowledgestudioshort}} User Account Management page in the {{site.data.keyword.cloud_notm}} [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release.

UI changes to pre-annotation interface
:   In the pre-annotation section of the interface, made a couple GUI changes to clarify the functionality of the machine learning model, the rule-based model, the dictionary, and {{site.data.keyword.alchemylanguagefull}}. Changed the button label from **Run** to **Pre-annotate**, changed the title of the window from **Run Annotator** to **Run Pre-annotation**, and changed the error message to clarify that you can't add automated annotations after humans annotated the documents.

Dictionary-based tokenizer fix
:   For projects or workspaces that use dictionary-based tokenizers, fixed an issue that showed empty sentences if you imported documents without ground truth.

## September 2017
{: #watson-knowledge-studio-sep17}
{: release-note}

### New features and changes
{: #new-sep17}
{: release-note}

New front-end experience released
:   Released a new front-end user experience for {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud}} as an [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) service. Changes include a reorganized navigation and a new model performance analysis page. For a summary of the navigation changes, see the table in the known issues.

Support for Chinese (Simplified) and Dutch
:   Added Chinese (simplified) and Dutch language support.

### Known issues
{: #issues-sep17}
{: release-note}

Export button not enabled
:   For a rule-based model, after you map classes and entity types, the **Export** button is not enabled until you refresh the browser window.

Experimental Cloud release
:   For the {{site.data.keyword.cloud_notm}} [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release, some of the documentation terminology does not match the new interface. The documentation matches the interface in {{site.data.keyword.IBM_notm}} Marketplace. The following terms have changed in the [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release:

| Term in {{site.data.keyword.IBM_notm}} Marketplace | Term in {{site.data.keyword.cloud_notm}} | Notes |
|----------|----------|----------|
| _project_ | _workspace_ | This term was changed because {{site.data.keyword.cloud_notm}} also uses the term _project_ |
| _import_ and _export_ | _upload_ and _download_ | The terms _import_ and _export_ are now referred to as _upload_ and _download_ when used in terms of documents and entity types. The term _export_ is still used when referring to exporting a model to applications such as {{site.data.keyword.watson}} Explorer. |
{: caption="Table 1. Terminology changes for {{site.data.keyword.cloud_notm}} version" caption-side="top"}

Experimental Cloud release documentation
:   For the {{site.data.keyword.cloud_notm}} [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release, some of the documentation task steps do not match the new interface. The documentation matches the interface in {{site.data.keyword.IBM_notm}} Marketplace. The following table summarizes the navigation changes for the [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) release:

| Feature | {{site.data.keyword.IBM_notm}} Marketplace location | {{site.data.keyword.cloud_notm}} location
|----------|----------|----------|
|Annotator Component tab | Main navigation | No longer exists |
|Confusion Matrix table (from the Statistics tab) | Annotator Component > Details | Model Management > Performance > Detailed Statistics link |
|Dictionaries tab | Main navigation | Assets & Tools > Pre-annotators |
|Dictionary Mapping page | Annotator Component | Assets & Tools > Pre-annotators |
|Entity Types tab | Type System | Assets & Tools > Entity Types |
|Ground Truth Editor | Human Annotation | Document Annotation tab |
|Ground Truth Editor Settings tab | Human Annotation | Settings > Document Annotation Settings |
|Models, running and exporting | Annotator Component | Model Management > Versions |
|Rules tab | Main navigation | Document Annotation > Rules |
|Statistics tab | Annotator Component > Details | Model Management > Performance |
|Summary table (from the Statistics tab) | Annotator Component > Details | Model Management > Performance > Detailed Statistics link |
|Type Mapping tab (for the rule-based model) | Annotator Component > Details | Model Management > Versions > Rule-based model type mapping |
{: caption="Table 2. Navigation changes for {{site.data.keyword.cloud_notm}} version" caption-side="top"}

## July 2017
{: #watson-knowledge-studio-jul17}
{: release-note}

Header bug fix
:   Fixed a defect that, in some cases, caused the header to disappear

Security updates
:   Applied security updates for infrastructure components

## June 2017
{: #watson-knowledge-studio-jun17}
{: release-note}

Improved stability
:   Improved stability for handling large data under certain conditions

Adjudication bug fix
:   Fixed a defect for an adjudication error

## May 2017
{: #watson-knowledge-studio-may17}
{: release-note}

Rename ability added
:   Added ability to rename various objects, such as projects, document sets, and so on

Ability to deploy NLU models
:   Added ability to deploy NLU models to specific {{site.data.keyword.cloud_notm}} regions

Improved performance
:   Improved performance for displaying large table for IAA

Bug fixes
:   Fixed minor defects
:   Applied security fixes

## April 2017
{: #watson-knowledge-studio-apr17}
{: release-note}

Improved stability
:   Improved stability for {{site.data.keyword.knowledgestudioshort}} Premium

Usage analysis added
:   Added usage analysis for business metrics

## Releases prior to April 2017
{: #watson-knowledge-studio-preapr17}
{: release-note}

See [{{site.data.keyword.IBM_notm}} release notes, document 283189](https://www.ibm.com/support/pages/node/283189){: external}.
