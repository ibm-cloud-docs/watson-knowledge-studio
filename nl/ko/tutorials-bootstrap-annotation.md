---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}하십시오.
{: tip}

# 문서에 어노테이션 미리 작성
{: #wks_tutboot_intro}

이 튜토리얼은 사람 어노테이터의 어노테이션 프로세스를 부트스트랩하는 문서에 어노테이션 미리 작성을 수행하는 방법을 이해하는 데 도움을 줍니다.
{: shortdesc}

## 학습 목표
{: #objectives}

이 튜토리얼을 완료하고 나면 기계 학습 모델을 사용하여 문서에 어노테이션 미리 작성을 수행하는 방법을 알게 됩니다.

이 튜토리얼을 완료하는 데는 약 5분이 소요됩니다. 이 튜토리얼과 관련된 기타 개념을 탐색하는 경우에는 완료하는 데 시간이 더 소요될 수 있습니다.

## 시작하기 전에
{: #prereqs}

- 지원되는 브라우저를 사용하고 있는지 확인하십시오. 자세한 정보는 [브라우저 요구사항](/docs/services/watson-knowledge-studio/system-requirements.html)을 참조하십시오.
- 작업공간 작성, 유형 시스템 작성 및 사전 추가를 다루는 [{{site.data.keyword.knowledgestudioshort}} 시작하기](/docs/services/watson-knowledge-studio/tutorials-create-project.html)를 성공적으로 완료했습니다. 
- [기계 학습 모델 작성](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html)을 성공적으로 완료했습니다. 
- Admin 또는 프로젝트 관리자 역할의 사용자 ID가 하나 이상 있어야 합니다. 사용자 역할에 대한 정보는 [{{site.data.keyword.knowledgestudioshort}}의 사용자 역할](/docs/services/watson-knowledge-studio/roles.html)을 참조하십시오. 

## 결과
{: #results}

이 튜토리얼을 완료하고 나면 일부 어노테이션이 있는 문서 세트를 보유하게 됩니다. 그 후에는 어노테이션 작성 작업을 완료하도록 사람 어노테이터에게 이러한 문서를 지정할 수 있습니다.

## 학습 1: 기계 학습 모델을 사용하여 새 문서에 어노테이션 미리 작성 수행
{: #wks_tutboot_ml}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 기계 학습 모델을 사용하여 문서에 어노테이션 미리 작성을 수행하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutboot_ml_about}

기계 학습 모델을 훈련시킨 후에는 이를 사용하여 말뭉치에 추가된 새 문서에 어노테이션 미리 작성을 수행할 수 있습니다.

> **주의:** 사람이 어노테이션을 작성했으나 아직 기준 실제값에 추가되지 않은 문서에 대해 프리어노테이터(pre-annotator)를 실행하지 마십시오. 이렇게 하면 모든 현재 어노테이션이 문서에서 제거됩니다.

이 튜토리얼에서는 `documents-ml.csv` 파일을 사용하여 두 번째 문서 세트를 추가할 수 있습니다. `documents-new.csv` 파일을 또 다시 추가하면 기준 실제값에 중복 문서가 발생하므로 다시 추가하지 마십시오. 중복은 다음 문제점을 발생시킬 수 있습니다.

- 각 문서의 어노테이션이 일치하지 않는 경우, 이러한 항목은 기계 학습 모델의 품질을 저하시킵니다.
- 각 문서의 어노테이션이 일치하는 경우, 이러한 항목은 중복된 파일에 대해 기계 학습 모델을 과도하게 훈련시킵니다.

문서에 어노테이션 미리 작성에 대한 자세한 정보는 어노테이션 미리 작성 방법을 추가적으로 설명하는 [어노테이션 부트스트랩](/docs/services/watson-knowledge-studio/preannotation.html)을 참조하십시오. 

### 프로시저
{: #wks_tutboot_ml_procedure}

1. {{site.data.keyword.knowledgestudioshort}}에 관리자로 로그인하십시오.
1. 작업공간에 문서를 추가로 업로드하십시오. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일을 사용할 수 있습니다.

    작업공간에 문서 추가에 대한 자세한 정보는 [어노테이션 관련 문서 추가](/docs/services/watson-knowledge-studio/documents-for-annotation.html)를 참조하십시오. 

1. `documents-ml.csv` 파일을 기본 세트로 사용하는 어노테이션 세트를 작성하고 이를 관리자인 자신에게 지정하십시오. 

    새 문서에 어노테이션 미리 작성을 수행하기 위한 다음 단계를 완료하고 나면, 어노테이션 세트를 보고 기계 학습 모델이 문서에 어노테이션 작성을 수행한 방법을 확인할 수 있습니다. 일반적으로는 어노테이션 세트를 하나 이상의 사람 어노테이터에게 지정합니다. 어노테이션 세트 작성 및 지정에 대한 자세한 정보는 [어노테이션 관련 문서 추가](/docs/services/watson-knowledge-studio/documents-for-annotation.html)를 참조하십시오. 

1. 새 문서에 어노테이션 미리 작성을 수행하려면 **Machine Learning Model** > **Versions**를 클릭한 후에 **Run this model**을 클릭하십시오. 
1. 말뭉치에 추가한 문서 세트인 `documents-ml.csv`를 선택하고 **Run**을 클릭하십시오.
1. 어노테이션 미리 작성이 완료되면, 작성된 어노테이션 세트가 포함된 사람 어노테이션 태스크를 작성할 수 있습니다. 

    어노테이션 태스크 작성에 대한 자세한 정보는 [어노테이션 설정](/docs/services/watson-knowledge-studio/annotate-documents.html)을 참조하십시오. 

1. 기계 학습 모델에 의해 새 문서에 적용된 어노테이션을 보려면 어노테이션 태스크를 여십시오. 

    기계 학습 모델로 새 문서에 어노테이션이 미리 작성되었으므로, 사람 어노테이션은 더 적은 시간을 요구합니다. 사람 어노테이터에 의한 어노테이션 추가에 대한 자세한 정보는 [문서의 어노테이션 작성](/docs/services/watson-knowledge-studio/user-guide.html)을 참조하십시오. 

### 결과
{: #wks_tutboot_ml_results}

기계 학습 모델을 사용하여 새 문서 세트에 어노테이션 미리 작성을 수행함으로써 이러한 문서에 대한, 사람에 의한 어노테이션 작성 태스크를 가속화할 수 있습니다.
