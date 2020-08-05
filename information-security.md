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

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

If you need to request GDPR support for {{site.data.keyword.cloud}} {{site.data.keyword.watson}} resources that are created

- In the European Union, see [Requesting support for IBM Cloud Watson resources created in the European Union](/docs/watson?topic=watson-gdpr-sar#request-EU).
- Outside the European Union, see [Requesting support for resources outside the European Union](/docs/watson?topic=watson-gdpr-sar#request-non-EU).

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here](http://www.ibm.com/gdpr){: external}.

## Health Insurance Portability and Accountability Act (HIPAA)
{: #hipaa}

US Health Insurance Portability and Accountability Act (HIPAA) support is available for Premium plans in the Washington, DC location created on or after 1 April 2019. See [Enabling EU and HIPAA supported settings](/docs/account?topic=account-eu-hipaa-supported#eu-hipaa-supported) for more information.

## GDPR in {{site.data.keyword.knowledgestudioshort}}
{: #gdpr-wks}

{{site.data.keyword.knowledgestudiofull}} provides a graphical interface through which you can access and delete uploaded artifacts that contain data. The following artifacts can be uploaded to {{site.data.keyword.knowledgestudioshort}}:
- Type systems
- Dictionaries
- Documents

If you receive a request to delete data, complete the following steps:
1. [Delete the applicable artifact](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-artifacts).
1. [Retrain and redeploy the model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-train-ml).
1. [Delete previous versions of the model that used the deleted data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-improve-ml#wks_maversions).
