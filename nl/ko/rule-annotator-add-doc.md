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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}.
{: tip}

# 규칙 정의를 위한 문서 추가
{: #wks_rule_anno_add}

정의할 규칙의 유형을 나타내는 언어 패턴을 포함하는 문서를 추가하십시오.
{: shortdesc}

규칙 정의를 위해 추가하는 문서는 어노테이션 작성을 위해 추가하는 문서와 별도로 보관됩니다. 이들의 유일한 용도는 패턴의 마이닝 예로 사용되는 것입니다. 이러한 문서는 훈련에 사용되지 않으며 다운로드되지 않습니다. 

## 규칙 편집기에 문서를 추가하는 방법

- **UTF-8 형식의 텍스트 문서 작성**

    패턴을 나타내는 텍스트를 규칙 편집기에 직접 추가할 수 있습니다. 문서에 대해 지정하는 이름은 256자를 초과할 수 없습니다. 

- **CSV 파일 업로드**

    문서 텍스트를 포함하는 CSV 형식의 파일을 업로드하십시오. 

- **어노테이션 작성을 위해 가져온 문서 복사**

    어노테이션 작성을 위해 가져온 세트의 일부인 문서에 규칙으로 캡처할 패턴의 예가 포함되어 있는 경우에는 해당 문서를 규칙 편집기로 복사할 수 있습니다. 복사한 문서를 변경해도 어노테이션 작성에 사용되는 원본 문서 버전에는 영향을 주지 않습니다. 문서 업로드에 대한 정보는 [작업공간에 문서 추가](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)를 참조하십시오. 

복사하거나 업로드하는 문서의 경우, 문서 내의 엔티티 유형을 식별하는 데 도움을 주는 뚜렷한 패턴을 포함하는 문서를 선택하십시오. 
