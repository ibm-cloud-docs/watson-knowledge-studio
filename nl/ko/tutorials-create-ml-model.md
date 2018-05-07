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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window}.
{: tip}

# 기계 학습 모델 작성
{: #wks_tutml_intro}

이 학습서는 배치하여 기타 {{site.data.keyword.watson}} 서비스와 함께 사용할 수 있는 기계 학습 모델을 빌드하는 프로세스를 이해하는 데 도움을 줍니다.
{: shortdesc}

## 학습 목표

이 튜토리얼의 학습을 완료하고 나면 다음 태스크를 수행하는 방법을 알게 됩니다. 

- 문서 세트 작성
- 문서에 어노테이션 미리 작성 수행
- 사람 어노테이터의 태스크 작성
- 어노테이터 간 일치 분석 및 어노테이션 작성된 문서의 충돌 판정
- 기계 학습 어노테이터 작성

이 튜토리얼을 완료하는 데는 약 60분이 소요됩니다. 이 튜토리얼과 관련된 기타 개념을 탐색하는 경우에는 완료하는 데 시간이 더 소요될 수 있습니다. 

## 시작하기 전에

- 지원되는 브라우저를 사용하고 있는지 확인하십시오. 자세한 정보는 [브라우저 요구사항](/docs/services/watson-knowledge-studio/system-requirements.html)을 참조하십시오. 
- [튜토리얼: 작업공간 작성](/docs/services/watson-knowledge-studio/tutorials-create-project.html)을 완료했는지 확인하십시오. 
- Admin 또는 ProjectManager 역할이 있는 사용자 ID가 하나 이상 있어야 합니다. 

    > **참고:** 가능한 경우에는 이 튜토리얼의 기계 학습 모델 태스크에 대해 여러 사용자 ID를 사용하십시오(하나의 Admin 또는 ProjectManager 사용자 ID, 그리고 둘 이상의 HumanAnnotator 사용자 ID). 여러 사용자 ID를 사용하면 한 명의 프로젝트 관리자가 여러 사람 어노테이터가 수행하는 어노테이션 작성 작업을 조정하고 판정해야 하는 실제 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}™ {{site.data.keyword.knowledgestudioshort}} 작업공간을 가장 유사하게 시뮬레이션할 수 있습니다. 그러나 하나의 사용자 ID만 이용할 수 있는 경우에도 대부분의 프로세스는 시뮬레이션할 수 있습니다. 

    사용자 역할에 대한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오. 

## 결과

이 튜토리얼을 완료하고 나면 기타 {{site.data.keyword.watson}} 서비스와 사용할 수 있는 사용자 정의 기계 학습 모델이 작성됩니다. 

## 학습 1: 어노테이션 작성을 위한 문서 추가
{: #tut_lessml1}

이 학습에서는 사람 어노테이터가 어노테이션을 작성할 수 있는 문서를 {{site.data.keyword.knowledgestudioshort}}의 작업공간에 추가하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

문서 추가에 대한 자세한 정보는 [작업공간에 문서 추가](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)를 참조하십시오. 

### 프로시저

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv`<img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일을 컴퓨터에 다운로드하십시오. 이 파일에는 업로드하기에 적합한 문서 예가 포함되어 있습니다. 
1. 작업공간의 사이드바에서 **Documents**를 클릭하십시오. 
1. Documents 페이지에서 **Upload Document Sets**를 클릭하십시오. 
1. 컴퓨터에 있는 `documents-new.csv` 파일을 선택하고 **Upload**를 클릭하십시오. 업로드된 파일이 테이블에 표시됩니다. 

### 다음에 수행할 작업

이제 말뭉치를 여러 문서 세트로 나누고 이러한 문서 세트를 사람 어노테이터에게 지정할 수 있습니다. 

## 학습 2: 어노테이션 세트 작성
{: #wks_tutless_ml2}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 어노테이션 세트를 작성하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

어노테이션 세트는 사용자가 사람 어노테이터에게 지정하는, 업로드된 문서 세트의 문서 서브세트입니다. 사람 어노테이터는 어노테이션 세트 내의 문서에 어노테이션을 작성합니다. 나중에 각 사람 어노테이터가 추가한 어노테이션을 비교하기 위해 어노테이터 간 점수를 사용하려면 서로 다른 어노테이션 세트에 둘 이상의 사람 어노테이터를 지정해야 합니다. 세트 간에 겹치는 문서의 백분율 또한 어느 정도 지정해야 합니다. 

> **참고:** 실제 작업공간에서는 작업공간에서 작업 중인 사람 어노테이터의 수에 따라 필요한 만큼 어노테이션 세트를 작성할 수 있습니다. 이 튜토리얼에서는 두 개의 어노테이션 세트를 작성합니다. 여러 사용자 ID를 이용할 수 없는 경우에는 두 어노테이션 세트를 모두 동일한 사용자에게 지정할 수 있습니다. 

어노테이션 세트에 대한 자세한 정보는 [어노테이션 세트 작성 및 지정](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)을 참조하십시오. 

### 프로시저

1. 작업공간의 사이드바에서 **Documents**를 클릭하십시오. 
1. **Create Annotation Sets**를 클릭하십시오. 

    Create Annotation Sets 창이 열립니다. 기본적으로 이 창은 기본 세트(모든 문서를 포함함)를 표시하며, 새 어노테이션 세트의 정보를 지정할 수 있는 필드 또한 표시합니다. 

1. 추가 어노테이션 세트의 필드를 추가하려면 **Add another set and human annotator**를 클릭하십시오. 어노테이션 세트는 필요한 만큼 클릭하여 추가할 수 있으나, 이 튜토리얼에서는 두 개만 필요합니다. 

    ![Create Annotation Sets 페이지의 화면 캡처입니다. ](images/wks_tutdocset2.jpg)

1. **Overlap** 필드에 `100`을 지정하십시오. 이는 기본 세트의 문서를 100퍼센트 모든 새 어노테이션 세트에 포함시켜 모든 사람 어노테이터가 여기에 어노테이션을 작성하도록 하기 위해서입니다. 
1. 작성하는 각각의 새 어노테이션 세트에 대해 필수 정보를 지정하십시오. 

    - **Annotator** 필드에서 새 어노테이션 세트에 지정할 사람 어노테이터 사용자 ID를 선택하십시오. 각 어노테이션 세트는 서로 다른 사람 어노테이터에게 지정해야 합니다. 

        > **참고:** 튜토리얼에 하나의 관리자 ID밖에 사용할 수 없는 경우에는 이 사용자를 모든 어노테이션 세트에 지정하십시오. 실제 작업공간에서는 여러 사람 어노테이터가 있을 수 있으나 이 튜토리얼에서는 관리자가 사람 어노테이터 역할을 수행할 수 있습니다. 

    - **Set name** 필드에 어노테이션 세트에 대한 설명적 이름을 지정하십시오(`Set 1` 또는 `DaveSet` 등). 

1. **Generate**를 클릭하십시오. 

### 결과

새 어노테이션 세트가 작성되어 Documents 페이지의 **Annotation Sets** 탭에 표시됩니다. 

## 학습 3: 사전 기반 어노테이터를 사용한 어노테이션 미리 작성
{: #wks_tutless_ml3}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 사전 기반 어노테이터를 사용하여 문서에 어노테이션 미리 작성을 수행하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

문서에 어노테이션 미리 작성을 수행하는 것은 선택적인 단계입니다. 그러나 이는 나중에 사람 어노테이터의 작업을 용이하게 해 주므로 가치 있는 단계입니다. 

사전 기반 어노테이터를 사용한 어노테이션 미리 작성에 대한 자세한 정보는 [사전 프리어노테이터를 사용하여 문서에 어노테이션 미리 작성 수행](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)을 참조하십시오. 

### 프로시저

1. 작업공간의 **Assets & Tools** > **Pre-annotators** 사이드바에서 **Manage Dictionaries**를 클릭하십시오. 

  `Test dictionary` 사전이 열립니다. 

1. **Entity type** 목록에서 **ORGANIZATION**을 선택하여 ORGANIZATION 엔티티 유형을 *작업공간 작성* 튜토리얼의 [사전 추가](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) 학습에서 작성한 `Test dictionary` 사전에 맵핑하십시오. 
1. 왼쪽 상단에 있는 뒤로 화살표를 클릭하여 Pre-annotators 페이지로 돌아간 후 **Apply This Pre-annotator**를 클릭하십시오. 
1. Run Annotator 페이지에서 해당 선택란을 선택하여 이 튜토리얼의 앞부분에서 작성한 두 어노테이션 세트를 모두 선택하십시오(기본 세트는 포함하지 않음). 
1. **Run**을 클릭하십시오. 

    ![이 화면 캡처는 Run Annotator 페이지를 보여줍니다. Run 단추가 강조표시되어 있습니다. ](images/wks_tutanno3.jpg)

### 결과

작성한 사전 어노테이터를 사용하여 선택한 세트의 문서에 어노테이션 미리 작성이 수행됩니다. 그 후에는 **Apply This Pre-annotator**를 클릭하여 추가 문서 세트에 동일한 어노테이터를 사용해 어노테이션 미리 작성을 수행할 수 있습니다. 

## 학습 4: 어노테이션 작성 태스크 작성
{: #wks_tutless_ml4}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 사람 어노테이터의 작업을 추적하기 위해 어노테이션 작성 태스크를 사용하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

어노테이션 작성 태스크에 대한 자세한 정보는 [어노테이션 작성 태스크 작성](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask)을 참조하십시오. 

### 프로시저

1. 작업공간의 **Assets & Tools** > **Documents** 사이드바에서 **Tasks** 탭을 선택하십시오. 
1. Tasks 페이지에서 **Add Task**를 클릭하십시오. 
1. 태스크의 세부사항을 지정하십시오. 

    - **Task name** 필드에 `Test`를 입력하십시오. 
    - **Deadline** 필드에서 미래의 날짜를 선택하십시오. 

1. **Create**를 클릭하십시오. 
1. Add Annotation Sets to the Task 창에서 해당 선택란을 선택하여 [학습 3: 사전 기반 어노테이터를 사용하여 어노테이션 미리 작성 수행](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3)에서 작성한 어노테이션 세트를 모두 선택하십시오. 이는 이 태스크의 일부로서 지정된 사람 어노테이터가 두 어노테이션 세트 모두에 어노테이션을 작성해야 함을 지정합니다. 
1. **Create Task**를 클릭하십시오. 
1. 이후에 사람에 의한 어노테이션 작성 작업의 진행상태를 보려면 해당 태스크를 클릭하여 여십시오. 

## 학습 5: 문서에 어노테이션 작성
{: #wks_tutless_ml5}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 기준 실제값 편집기를 사용하여 문서에 어노테이션을 작성하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

사람에 의한 어노테이션 작성에 대한 자세한 정보는 [기준 실제값 편집기를 사용한 어노테이션 작성](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte)을 참조하십시오. 

### 프로시저

1. [학습 4: 어노테이션 작성 태스크 작성](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)에서 작성한 어노테이션 작성 태스크에 지정된 사람 어노테이터로 {{site.data.keyword.knowledgestudioshort}}에 로그인하십시오. 

    > **참고:** 이 튜토리얼을 진행하는 데 하나의 관리자 ID밖에 이용할 수 없는 경우에는 이 ID를 사용하여 사람에 의한 어노테이션 작성 작업을 수행하십시오. 그러나 실제 작업공간에서 사람에 의한 어노테이션 작성은 HumanAnnotator 역할이 있는 서로 다른 여러 사용자에 의해 수행된다는 점을 기억하십시오. 

1. `My workspace` 작업공간을 여십시오. 
1. 사이드바에서 **Document Annotation** > **Relations**를 클릭하십시오. 
1. [학습 4: 어노테이션 작성 태스크 작성](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)에서 작성한 `Test` 어노테이션 작성 태스크를 여십시오. 
1. *Technology - gmanews.tv* 문서로 스크롤한 후 이를 클릭하여 어노테이션을 작성할 수 있도록 여십시오. `IBM`이 이미 ORGANIZATION 엔티티 유형으로 어노테이션 작성된 것을 볼 수 있습니다. 이 어노테이션은 [학습 2: 어노테이션 작성 세트 작성](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2)에서 사전 프리어노테이터(pre-annotator)에 의해 추가된 것입니다. 이 미리 작성된 어노테이션은 올바르므로 수정할 필요가 없습니다. 

    ![이 화면 캡처는 IBM에 대해 기존의 미리 작성된 어노테이션이 있는 열린 문서를 보여줍니다. ](images/wks_tut_preannotation.png)

1. 멘션에 어노테이션을 작성하려면 다음 작업을 수행하십시오. 

    1. **멘션** 아이콘을 클릭하여 멘션에 어노테이션 작성을 시작하십시오. 
    1. 문서 본문에서 텍스트 `Thomas Watson`을 선택하십시오. 
    1. 엔티티 유형 목록에서 **PERSON**을 클릭하십시오. 엔티티 유형 PERSON이 선택한 멘션에 적용됩니다. 

        ![이 화면 캡처는 멘션 Thomas Watson에 적용된 PERSON 엔티티 유형을 보여줍니다. ](images/wks_tut_annotatemention3.png)

1. 사이드바에서 **Document Annotation** > **Relations**를 클릭하여 관계에 어노테이션 작성을 시작하십시오. 
1. `Thomas Watson` 및 `IBM` 멘션을 순서대로 선택하십시오. 멘션을 선택하려면 텍스트 위에 있는 엔티티 유형 레이블을 클릭하십시오. 
1. 관계 유형 목록에서 **founderOf**를 클릭하십시오. 두 멘션이 founderOf 관계로 연결됩니다. 

    ![이 화면 캡처는 관계 유형 founderOf로 연결된 두 멘션을 보여줍니다. ](images/wks_tut_annotaterelation.png)

1. 상태 메뉴에서 **Completed**를 선택한 후 **Save** 단추를 클릭하십시오. 
1. 문서 목록으로 돌아와 **Submit All Documents**를 클릭하여 승인을 위해 문서를 제출하십시오. 

    > **참고:** 실제 상황에서는 더 많은 어노테이션을 작성하며, 제출하기 전에 세트 내의 모든 문서를 완료합니다. 

1. 어노테이션 작성 태스크의 다른 문서에 지정된 사람 어노테이터로 {{site.data.keyword.knowledgestudioshort}}에 로그인하십시오. 
1. *Technology - gmanews.tv* 문서에 동일한 어노테이션 작성을 반복하되, 이번에는 founderOf 관계 대신 employedBy 관계를 사용하십시오. 

  다른 사용자로 로그인하면 다음 학습에서 어노테이터 간 일치를 설명하는 데 도움이 됩니다. 어노테이션 작성을 완료하고 **Submit All Documents**를 클릭하십시오. 

## 학습 6: 어노테이터 간 일치 분석
{: #wks_tutless_ml6}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 여러 사람 어노테이터의 작업을 비교하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

여러 사람 어노테이터가 겹치는 문서에 일관되게 어노테이션을 작성하고 있는지 판별하려면 어노테이터 간 일치(`IAA`) 점수를 검토하십시오. 

{{site.data.keyword.knowledgestudioshort}}는 문서 세트의 상태에 관계 없이 태스크에 포함된 모든 문서 세트의 모든 겹치는 문서를 검사하여 IAA 점수를 계산합니다. IAA 점수는 여러 사람 어노테이터가 멘션, 관계 및 상호 참조 체인에 대해 얼마나 다르게 어노테이션을 작성했는지 보여줍니다. IAA 점수는 주기적으로 확인하여 여러 사람 어노테이터가 서로 일관된 작업을 수행하고 있는지 확인하는 것이 좋습니다. 

이 튜토리얼에서는 사람 어노테이터가 승인을 위해 모든 문서를 제출했습니다. 어노테이터 간 일치 점수가 허용 가능한 경우에는 문서 세트를 승인할 수 있습니다. 문서 세트를 거부하면 개선을 위해 사람 어노테이터에게 반환됩니다. 

### 프로시저

1. 관리자로 {{site.data.keyword.knowledgestudioshort}}에 로그인하여 **Assets & Tools** > **Documents**를 선택한 후 `Test` 태스크를 클릭하십시오. 

  **Status** 열에서 문서 세트가 제출된 것을 볼 수 있습니다. 

1. **Calculate Inter-Annotator Agreement**를 클릭하십시오. 
1. 첫 번째 메뉴를 클릭하여 멘션, 관계 및 상호 참조 체인에 대한 IAA 점수를 보십시오. 사람 어노테이터 쌍을 기준으로 일치 점수를 볼 수도 있습니다. 예를 들면, 모든 Dave의 어노테이션을 모든 Phil의 어노테이션과 비교할 수 있습니다. 특정 문서를 기준으로 일치 점수를 볼 수도 있습니다. 예를 들면, 특정 문서에 작성된 Dave의 어노테이션을 동일한 문서에 작성된 Phil의 어노테이션과 비교하여 볼 수 있습니다. 일반적으로 최고점 1(1은 완전 일치를 의미함)을 기준으로 .8점을 획득하는 것을 목표로 하십시오. 이 튜토리얼에서는 두 엔티티 유형에만 어노테이션을 작성했으므로 대부분의 엔티티 유형 점수는 N/A(해당사항 없음)이며, 이는 점수를 계산하기 위해 사용 가능한 정보가 없음을 의미합니다. 

    *그림 1. Dave 및 Phil이라는 사용자의 어노테이터 간 점수 검토*

    ![이 화면 캡처는 태스크의 어노테이터 간 점수를 보여줍니다. ](images/wks_tutiaa2.gif)

1. 점수를 검토하고 나면 `Submitted` 상태의 문서 세트를 승인할지 또는 거부할지 결정할 수 있습니다. 문서 세트가 제출되면 해당 이름 옆에 선택란이 표시됩니다. 다음 조치 중 하나를 수행하십시오. 

    - 문서 세트의 점수가 허용 가능한 경우에는 선택란을 선택하고 **Accept**를 클릭하십시오. 다른 문서 세트와 겹치지 않는 문서는 기준 실제값으로 승격됩니다. 겹치는 문서는 먼저 충돌을 해결하기 위해 판정을 통해 검토해야 합니다. 이 튜토리얼의 경우에는 두 문서 세트를 모두 승인하십시오. 
    - 문서 세트의 점수가 허용 불가능한 경우에는 선택란을 선택하고 **Reject**를 클릭하십시오. 해당 문서 세트는 사람 어노테이터의 재작업을 통해 어노테이션을 개선해야 합니다. 

### 결과

어노테이터 간 일치 점수를 평가하면 사람 어노테이터 쌍이 동일한 문서에 얼마나 다르게 어노테이션을 작성했는지 볼 수 있습니다. 어노테이터 간 일치 점수가 허용 가능한 경우에는 문서 세트를 승인합니다. 

## 학습 7: 어노테이션 작성된 문서의 충돌 판정
{: #wks_tutless_ml7}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 문서 세트 간에 겹치는 문서의 충돌을 판정하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

문서 세트를 승인할 때는 다른 문서 세트와 겹치지 않는 문서만 기준 실제값으로 승격됩니다. 특정 문서가 여러 문서 세트 간에 겹치는 문서의 일부인 경우에는 이러한 문서를 기준 실제값으로 승격하기 전에 어노테이션 충돌을 판정해야 합니다. 

### 프로시저

1. 관리자로 {{site.data.keyword.knowledgestudioshort}}에 로그인하여 **Assets & Tools** > **Documents**를 선택한 후 `Test` 태스크를 클릭하십시오. 
1. 두 문서 세트가 승인됨 상태인지 확인하십시오. 
1. **Check Overlapping Documents for Conflicts**를 클릭하십시오. 

    둘 이상의 사람 어노테이터에 의해 어노테이션 작성된, 겹치는 문서가 표시됩니다. 

1. 여러 사람 어노테이터가 문서에 작성한 어노테이션에 충돌이 있는지 보려면 **Check for Conflicts**를 클릭하십시오. 
1. 판정 모드에서는 충돌 상태인 어노테이션의 수를 볼 수 있으며 문서를 기준 실제값으로 승격하기 전에 어노테이션을 제거하거나 대체할 수 있습니다. 
1. 이 튜토리얼의 경우에는 사용자가 모든 충돌을 해결했으며 변경사항을 승인했다고 가정합니다. **Promote to Ground Truth**를 클릭하십시오. 이러한 단계를 반복하여 두 번째 문서 세트의 충돌을 해결하십시오. 

    또는, Documents 페이지에서 **Accept**를 클릭하여 문서를 기준 실제값으로 승격할 수 있습니다. 

### 결과

어노테이션 충돌을 해결하고 문서를 기준 실제값으로 승격하고 나면 기계 학습 모델을 훈련시키는 데 이러한 문서를 사용할 수 있습니다. 

## 학습 8: 기계 학습 모델 작성
{: #wks_tutless_ml8}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 기계 학습 모델을 작성하는 방법을 학습합니다. 

### 이 태스크에 대한 정보

기계 학습 모델을 작성할 때는 이를 훈련시키는 데 사용할 문서 세트를 선택합니다. 또한 훈련 데이터, 테스트 데이터 및 블라인드 데이터로 사용될 문서의 백분율을 지정합니다. 판정 또는 승인을 통해 기준 실제값이 된 문서만 기계 학습 모델을 훈련시키는 데 사용할 수 있습니다. 

### 프로시저

1. {{site.data.keyword.knowledgestudioshort}}에 관리자로 로그인하십시오. 
1. **Model Management** > **Performance** 사이드바에서 **Train and evaluate**를 클릭하십시오. 
1. 기계 학습 모델을 작성하는 데 사용할 문서 세트를 선택하십시오. 각 문서 세트 이름 옆에 있는 선택 표시를 클릭하십시오. 
1. 훈련, 테스트 및 블라인드 데이터를 작성하기 위한 두 개의 어노테이션 세트를 선택하십시오. 그런 다음 **Train &amp; Evaluate**를 클릭하십시오. 

    > **참고:** 훈련에는 사람이 작성한 어노테이션의 수와 문서 전체의 총 단어 수에 따라 10분 이상 또는 몇 시간이 소요될 수 있습니다. 

1. 기계 학습 모델이 훈련되고 나면 이를 내보내거나, 각 그래프 위에 있는 **Detailed Statistics** 링크를 클릭하여 해당 모델의 성능에 대한 자세한 정보를 볼 수 있습니다. 
1. Training/Test/Blind Sets 페이지를 보려면 **Train and evaluate** 단추를 클릭하십시오. 
1. 사람 어노테이터가 작업한 문서를 보려면 **View Ground Truth**를 클릭하십시오. 
1. 기계 학습 모델이 동일한 문서 세트에 작성한 어노테이션을 보려면 **View Decoding Results**를 클릭하십시오. 
1. 기계 학습 모델의 정밀도, 재현율 및 F1 점수에 대한 세부사항을 보려면 Performance 페이지를 선택하십시오. 
1. 각 그래프 위에 있는 **Detailed Statistics** 링크를 클릭하십시오. 이러한 Statistics 페이지에서는 단일 선택 단추를 사용하여 멘션, 관계 및 상호 참조 체인에 대한 점수를 볼 수 있습니다. 

    엔티티 유형, 관계 유형 및 상호 참조 체인에 대한 통계 요약을 보고 성능을 분석할 수 있습니다. 기본값이 **Summary**인 메뉴에서 **Confusion Matrix**를 선택하여 혼동 매트릭스에 표시된 통계를 분석할 수도 있습니다. *혼동 매트릭스*는 기계 학습 모델이 추가한 어노테이션을 기준 실제값의 어노테이션과 비교하는 데 도움을 줍니다. 

    > **참고:** 이 튜토리얼에서는 단 하나의 조직용 사전을 사용하여 문서에 어노테이션을 작성했습니다. 따라서 `ORGANIZATION`을 제외한 대부분의 엔티티 유형에 대해 표시되는 점수는 `0` 또는 `N/A`입니다. 점수는 낮지만, 사람에 의한 어노테이션 작성 또는 정정을 수행하지 않았으므로 이는 예상된 결과입니다. 

    *그림 2. 기계 학습 모델에 대한 Statistics 페이지의 옵션*

    ![이 화면 캡처는 Statistics 페이지를 보여줍니다. ](images/wks_tutanno9.gif)

1. 사이드바에서 **Model Management** > **Versions**를 선택하십시오. Versions 페이지에서는 모델 및 모델을 작성할 때 사용된 리소스의 스냅샷을 작성할 수 있습니다(사전 및 어노테이션 작성 태스크 제외). 예를 들면, 모델을 다시 훈련시키기 전에 모델의 스냅샷을 작성하려 할 수 있습니다. 다음에 모델을 훈련시켰을 때 통계가 더 나빠진 경우에는 이전 버전을 승격하고 좋지 않은 결과를 리턴한 버전을 삭제할 수 있습니다. 

### 결과

기계 학습 모델을 작성하고, 훈련시키고, 테스트 데이터 및 블라인드 데이터에 어노테이션을 작성할 때의 성능을 평가했습니다. 성능 메트릭을 탐색하면 기계 학습 모델의 정확도를 개선할 방법을 식별할 수 있습니다. 

## 튜토리얼 요약
{: #wks_tutml_sum}

{{site.data.keyword.knowledgestudioshort}}에 대해 학습하면서, 기계 학습 모델을 작성했습니다. 

### 학습한 내용

이 튜토리얼을 완료하여 다음 개념에 대해 학습했습니다. 

- 문서 세트
- 기계 학습 모델
- 사람에 의한 어노테이션 작성 태스크
- 어노테이터 간 일치 및 판정
