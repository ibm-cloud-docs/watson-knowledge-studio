---

copyright:
  years: 2020
lastupdated: "2020-08-27"

keywords: troubleshooting access for knowledge studio

subcollection: watson-knowledge-studio

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}

<!-- You must add the troubleshoot content type in your attribute definitions AND on a new line under each troubleshooting topic H1 ID. -->

# Why can't users access the application?
{: #wks_ts_access}
{: troubleshoot}
{: support}

Find out how to grant users access to {{site.data.keyword.knowledgestudioshort}} and address common access issues.
{:shortdesc}

Users see a message such as "you are not authorized" when opening the Knowledge Studio application.
{:tsSymptoms}

Review the following scenarios to troubleshoot access problems:
{:tsResolve}
* Are you using a plan that allows for multiple users? Lite plans are limited to one user.  Select Standard or Premium plan to work with a team.

* Are you using a supported browser? For information, see [Browser requirements](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-system-requirements).

* Has an administrator added the user, with an appropriate role?  
  Each {{site.data.keyword.knowledgestudioshort}} instance has an administrator role that is associated with it. The first user to launch the {{site.data.keyword.knowledgestudioshort}} application is assigned the Admin role. The administrator can invite other people.

  The administrator must add a user in Knowledge Studio for each person who needs to log in. To invite people to use your instance of the application, follow the steps in [Adding users in Knowledge Studio](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-team#team-add).  Read [User roles in Knowledge Studio](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-roles) to understand the roles that you can assign.

* Have you and the administrator completed the steps for a human annotator?  
   When someone invited you to an instance of {{site.data.keyword.knowledgestudioshort}} to serve as a human annotator, you likely received an email invitation. First, you must register for an IBMid if you have not already. After you register with {{site.data.keyword.IBM_notm}} and accept the invitation, you are given access to the instance.

   Before you can start to annotate documents, the administrator or a project manager of the instance must add you to a workspace and assign an annotation task to you. It is not until after you are assigned a task that you can perform any actions in the {{site.data.keyword.knowledgestudioshort}} instance.
  
