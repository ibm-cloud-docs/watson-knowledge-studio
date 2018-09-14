---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}하십시오.
{: tip}

# 규칙 기반 모델 작성
{: #wks_rule_train}

규칙을 정의한 후에는 규칙 기반 모델을 작성할 수 있습니다.
{: shortdesc}

## 프로시저
{: #wks_rule_train_procedure}

규칙 기반 모델을 작성하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Rule-based Model** > **Versions** > **Rule-based Model** 탭을 선택하십시오. 
2. **Map entity types and classes**를 클릭하십시오.
3. 유형 시스템의 엔티티 유형을 규칙을 정의하는 데 사용한 하나 이상의 클래스에 맵핑하십시오.

  엔티티 유형이 맵핑되고 나면 [규칙 기반 모델을 배치](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)하거나 이를 사용하여 기계 학습 모델 작성 프로세스 중에 [문서에 어노테이션 미리 작성을 수행](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)할 수 있습니다.

## 규칙 기반 모델 삭제
{: #wks_rule_delete_model}

규칙 기반 모델은 삭제할 수 없습니다.

규칙 기반 모델을 개발하는 데 사용된 작업공간은 삭제할 수 있지만, 모델 자체를 삭제할 수는 없습니다. 모델을 삭제하는 것은 최선의 접근법이 아닙니다. 대신 이를 정의하는 데 사용된 규칙을 다시 작성하십시오. 규칙을 편집하면 규칙 기반 모델의 작동이 직접적으로 변경됩니다.
