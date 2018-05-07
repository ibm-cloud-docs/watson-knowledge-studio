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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/artifacts.html){: new_window}.
{: tip}

# 아티팩트의 유형
{: #artifacts}

먼저 어노테이터를 훈련시키는 데 사용할 아티팩트를 작성하거나 업로드하십시오.
{: shortdesc}

어노테이터는 사용자가 작업공간에 추가하는 다음 아티팩트 유형을 학습합니다. 

- **유형 시스템**

    유형 시스템은 중요 엔티티 및 엔티티 간 관계를 정의합니다. [유형 시스템 설정](/docs/services/watson-knowledge-studio/typesystem.html)을 참조하십시오. 

- **사전**

    사전은 모델에서 동등한 것으로 취급해야 하는 단어 및 구문을 함께 그룹화합니다. [사전 작성](/docs/services/watson-knowledge-studio/dictionaries.html)을 참조하십시오. 

- **문서**

    문서는 작성하는 항목이 기계 학습 모델인지 또는 규칙 기반 모델인지에 따라 용도가 달라집니다. 자세한 정보는 다음 주제를 참조하십시오. 
    - 기계 학습 모델 문서: [어노테이션 작성을 위한 문서 추가](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)
    - 규칙 기반 모델 문서: [규칙 정의를 위한 문서 추가](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)

많은 이러한 아티팩트는 외부 리소스에서 업로드할 수 있습니다(다른 {{site.data.keyword.knowledgestudioshort}} 작업공간에서 다운로드한 아티팩트 포함). 다른 작업공간의 아티팩트를 업로드하는 데 대한 정보는 [다른 작업공간의 리소스 업로드](/docs/services/watson-knowledge-studio/exportimport.html)를 참조하십시오. 

가져오는 아티팩트의 크기 한계 및 지원되는 파일 유형과 같은 아티팩트에 대한 주요 정보는 [입력, 출력 및 제한사항 요약](/docs/services/watson-knowledge-studio/create-project.html#wks_formats)을 참조하십시오. 

