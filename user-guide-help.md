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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/knowledge-studio/user-guide-help.html){: new_window}.
{: tip}

# Troubleshooting the ground truth editor
{: #ts_user_contactingsupport}

Find out what to do if you have questions or need help. Where to go for help depends on the type of issue you are having.
{: shortdesc}

## Access issues

- If you cannot access the {{site.data.keyword.knowledgestudioshort}} instance, then work with the workspace owner to ensure that he has invited you to join the workspace.
- If you can get to the {{site.data.keyword.knowledgestudioshort}} instance, but do not see any workspaces listed, then work with the administrator or manager of the workspace to resolve the issue. The administrator, which is a person with the Admin role, or manager, which is a person with the ProjectManager role in {{site.data.keyword.knowledgestudioshort}}, must 1.) associate you with an annotation set and 2.) create a task that assigns you to annotate the documents in the set. You will not see the workspace listed on the {{site.data.keyword.knowledgestudioshort}} home page until someone has performed these actions.

## Using the ground truth editor

First, review the information in this user guide. If you still have questions about how to use the ground truth editor, then you can check the community forum to see if anyone else has asked your question and received an answer. Or you can ask community members for help. To access the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Developer community forum, go to: [https://developer.ibm.com/answers/topics/wks/?smartspace=watson ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/topics/wks/?smartspace=watson){: new_window}.

## Annotation decisions

Can't decide which entity type to assign to an ambiguous term?

- If the workspace has annotation guidelines, refer to them. The purpose of the guideline is to help you answer just such types of questions. If you know there are guidelines but cannot find them, then ask the workspace administrator to add a link to the annotation guidelines from the ground truth editor. If there is no guideline, consider starting one. The first entry can address the question you are debating now, and can describe the resolution that you come to. This entry will save time for the next human annotator who stumbles upon the same issue.
- Discuss the question with other human annotators involved in the workspace, and try to decide together on the optimal solution. This type of discussion is expected and beneficial to the workspace overall. It will encourage you to all follow the same methodology as you annotate the documents.

## Related information

[Annotating documents](/docs/services/watson-knowledge-studio/user-guide.html)

[Dictionaries](/docs/services/watson-knowledge-studio/dictionaries.html)

[Type systems](/docs/services/watson-knowledge-studio/typesystem.html)
