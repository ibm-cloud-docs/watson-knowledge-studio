---

copyright:
  years: 2018, 2022
lastupdated: "2022-04-06"

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

# {{site.data.keyword.knowledgestudioshort}} model build and deployment paths
{: #model-paths}

In {{site.data.keyword.knowledgestudiofull}}, there are three types of models that can be produced and deployed: machine Learning, rule-based, and advanced rules.
{: shortdesc}

The table below shows supported model deployment paths **From** {{site.data.keyword.knowledgestudioshort}} source **To** target services.

| From: Public Cloud - {{site.data.keyword.knowledgestudioshort}} | To: {{site.data.keyword.icp4dfull_notm}} - {{site.data.keyword.discoveryfull}} | To: Public Cloud - {{site.data.keyword.discoveryfull}} | To: Public Cloud - {{site.data.keyword.nlufull}} |
|------------|-------|-----------------|-----------------|
| Machine learning | Upload via {{site.data.keyword.discoveryshort}} UI | Upload via UI | Deploy via {{site.data.keyword.knowledgestudioshort}} UI |
| Rule-based | Upload via {{site.data.keyword.discoveryshort}} UI | Upload via UI | Deploy via {{site.data.keyword.knowledgestudioshort}} UI |
| Advanced rules | Upload via {{site.data.keyword.discoveryshort}} UI | Upload via UI | Deploy via API <sup>1</sup> |
{: caption="Table 1. Model deployment paths" caption-side="top"}

<sup>1</sup> Deploying an advanced rules model to {{site.data.keyword.nlushort}} is deprecated. As of June 10, 2021, you cannot deploy advanced rules models to {{site.data.keyword.nlushort}}.
