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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/language-support.html){: new_window}.
{: tip}

# 언어 지원
{: #language-support}

{{site.data.keyword.knowledgestudiofull}}는 여러 언어로 모델을 훈련시키는 것에 대한 지원을 제공합니다. 

다중 언어 지원이 제품 자체가 번역되었음을 의미하지는 않습니다. {{site.data.keyword.knowledgestudioshort}} 사용자 인터페이스, 메시지 및 문서는 영어로만 사용 가능합니다.
{: shortdesc}

다음 언어로 모델을 훈련시킬 수 있습니다. 

- 영어(기본 언어)
- 아랍어
- 포르투갈어(브라질)
- 중국어
- 네덜란드어
- 프랑스어
- 독일어
- 이탈리아어
- 일본어
- 한국어
- 스페인어

지원에는 작업공간에 이러한 언어로 된 문서 추가, 사전 추가, 어노테이션 미리 작성 실행, 문서에 어노테이션 작성을 위한 기준 실제값 편집기 사용, 기계 학습 모델 훈련 기능이 포함됩니다. 언어를 선택하면 시스템이 사전 항목, 텍스트 토큰화 및 텍스트 분할을 처리하기 위한 언어 고유 템플리트를 적용합니다. 시스템이 다양한 언어의 사전을 처리하는 방법에 대한 정보는 [사전](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries)을 참조하십시오. 

> **참고:** 규칙 편집기 및 규칙 기반 모델은 양방향 텍스트를 처리할 수 없으므로 아랍어 문서와 함께 사용할 수 없습니다. 

> **제한사항:**
>
> 근본이 되는 기계 학습 기술의 문자 제한사항으로 인해, 유형 시스템의 항목은 공백을 포함할 수 없으며 다음 ASCII 문자만 포함할 수 있습니다. 
>
> - A - Z, a - z
> - 0 - 9
> - 밑줄 문자 _
>
> 다음 규칙 또한 적용됩니다. 
>
> - 이름의 첫 번째 문자는 알파벳이어야 합니다. 
> - 엔티티 유형 이름 길이는 64자를 초과할 수 없습니다. 
> - 관계 유형 이름 길이는 128자를 초과할 수 없습니다. 
>
> 따라서, 사람 어노테이터가 기준 실제값 편집기에서 일본어 텍스트에 어노테이션을 작성할 때 적용할 수 있는 엔티티 유형 및 관계 유형 이름은 일본어가 아닙니다. 

### 관련 태스크

[아랍어 지원 구성](/docs/services/watson-knowledge-studio/language-support-arabic.html)
