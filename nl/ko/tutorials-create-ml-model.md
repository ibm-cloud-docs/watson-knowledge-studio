---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-24"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window}하십시오.
{: tip}

# 기계 학습 모델 작성
{: #wks_tutml_intro}

이 학습서는 배치하여 기타 {{site.data.keyword.watson}} 서비스와 함께 사용할 수 있는 기계 학습 모델을 빌드하는 프로세스를 이해하는 데 도움을 줍니다.
{: shortdesc}

## 학습 목표
{: #objectives}

이 튜토리얼의 학습을 완료하고 나면 다음 태스크를 수행하는 방법을 알게 됩니다.

- 문서 세트 작성
- 문서에 어노테이션 미리 작성 수행
- 사람 어노테이터의 태스크 작성
- 어노테이터 간 일치 분석 및 어노테이션 작성된 문서의 충돌 판정
- 기계 학습 모델 작성

이 학습을 완료하려면 약 60분이 소요됩니다. 이 튜토리얼과 관련된 다른 개념을 탐색하는 경우, 완료하는 데 시간이 더 소요될 수 있습니다. 

## 시작하기 전에
{: #prereqs}

- 지원되는 브라우저를 사용하고 있는지 확인하십시오. [브라우저 요구사항](/docs/services/watson-knowledge-studio/system-requirements.html)을 참조하십시오. 
- 작업공간 작성, 유형 시스템 작성 및 사전 추가를 다루는 [{{site.data.keyword.knowledgestudioshort}} 시작하기](/docs/services/watson-knowledge-studio/tutorials-create-project.html)를 성공적으로 완료했습니다. 
- Admin 또는 프로젝트 관리자 역할의 사용자 ID가 하나 이상 있어야 합니다. 

    > **참고:** 가급적이면 이 튜토리얼의 기계 학습 모델 태스크에 대해 여러 사용자 ID를 사용하십시오(하나의 Admin 또는 프로젝트 관리자 사용자 ID, 그리고 둘 이상의 사람 어노테이터 사용자 ID). 여러 사용자 ID를 사용하면 프로젝트 관리자가 여러 사람 어노테이터가 수행하는 어노테이션을 조정하고 판정해야 하는 실제 {{site.data.keyword.knowledgestudiofull}} 작업공간의 가장 현실적인 시뮬레이션이 제공됩니다. 그러나 하나의 사용자 ID만 이용할 수 있는 경우에도 대부분의 프로세스는 시뮬레이션할 수 있습니다.

    사용자 역할에 대한 정보는 [{{site.data.keyword.knowledgestudioshort}}의 사용자 역할](/docs/services/watson-knowledge-studio/roles.html)을 참조하십시오. 

## 결과
{: #results}

이 튜토리얼을 완료하고 나면 기타 {{site.data.keyword.watson}} 서비스와 사용할 수 있는 사용자 정의 기계 학습 모델이 작성됩니다.

## 학습 1: 어노테이션 작성을 위한 문서 추가
{: #tut_lessml1}

이 학습에서는 사람 어노테이터가 어노테이션을 작성할 수 있는 문서를 {{site.data.keyword.knowledgestudioshort}}의 작업공간에 추가하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #tut_lessml1_about}

문서 추가에 대한 자세한 정보는 [작업공간에 문서 추가](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)를 참조하십시오.

### 프로시저
{: #tut_lessml1_procedure}

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv` <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일을 컴퓨터에 다운로드하십시오. 이 파일에는 업로드하기에 적합한 문서 예가 포함되어 있습니다.
1. 작업공간 내에서 **Assets** > **Documents**를 클릭하십시오.
1. Documents 페이지에서 **Upload Document Sets**를 클릭하십시오.
1. 컴퓨터에서 `documents-new.csv` 파일을 업로드하십시오. 업로드된 파일이 테이블에 표시됩니다.

### 다음에 수행할 작업
{: #tut_lessml1_next}

이제 말뭉치를 여러 문서 세트로 나누고 이러한 문서 세트를 사람 어노테이터에게 지정할 수 있습니다.

## 학습 2: 어노테이션 세트 작성
{: #wks_tutless_ml2}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 어노테이션 세트를 작성하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless_ml2_about}

*어노테이션 세트*는 사용자가 사람 어노테이터에게 지정하는 업로드된 문서 세트의 문서 서브세트입니다. 사람 어노테이터는 어노테이션 세트 내의 문서에 어노테이션을 작성합니다. 나중에 각 사람 어노테이터가 추가한 어노테이션을 비교하기 위해 어노테이터 간 점수를 사용하려면 서로 다른 어노테이션 세트에 둘 이상의 사람 어노테이터를 지정해야 합니다. 세트 간에 겹치는 문서의 백분율 또한 어느 정도 지정해야 합니다.

> **참고:** 실제 시나리오에서는 작업공간에서 작업 중인 사람 어노테이터의 수에 따라 필요한 수의 어노테이션 세트를 작성할 수 있습니다. 이 튜토리얼에서는 두 개의 어노테이션 세트를 작성합니다. 여러 사용자 ID에 액세스할 수 없는 경우에는 두 어노테이션 세트를 모두 동일한 사용자에게 지정할 수 있습니다. 

어노테이션 세트에 대한 자세한 정보는 [어노테이션 세트 작성 및 지정](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)을 참조하십시오.

### 프로시저
{: #wks_tutless_ml2_procedure}

1. 작업공간 내에서 **Assets** > **Documents**를 클릭하십시오.
2. **Create Annotation Sets**를 클릭하십시오.

    Create Annotation Sets 창이 열립니다. 기본적으로 이 창은 모든 문서를 포함하는 기본 세트 및 새 어노테이션 세트의 정보를 지정할 수 있는 필드를 표시합니다. 

3. 추가 어노테이션 세트의 필드를 추가하려면 **Add another set and human annotator**를 클릭하십시오. 작성을 원하는 어노테이션 세트를 필요한 만큼 클릭하여 추가할 수 있습니다. 이 튜토리얼에서는 두 개의 어노테이션 세트만 필요합니다. 

    ![Create Annotation Sets 페이지의 화면 캡처입니다.](images/wks_tutdocset2.jpg "Create Annotation Sets 페이지의 화면 캡처입니다.")

4. **Overlap** 필드에 `100`을 지정하십시오. 이 값은 모든 사람 어노테이터에 의한 어노테이션 작성이 가능할 수 있도록 기본 세트의 문서의 100퍼센트를 모든 새 어노테이션 세트에 포함시키고자 함을 지정합니다. 
5. 각각의 새 어노테이션 세트에 대해 필수 정보를 지정하십시오. 

    - **Annotator** 필드에서 새 어노테이션 세트에 지정할 사람 어노테이터 사용자 ID를 선택하십시오. 실제 시나리오에서, 각 어노테이션 세트는 서로 다른 사람 어노테이터에게 지정되어야 합니다. 

        > **참고:** 튜토리얼에 하나의 관리자 ID밖에 사용할 수 없는 경우에는 이 사용자를 모든 어노테이션 세트에 지정하십시오. 실제 시나리오에서는 여러 사람 어노테이터가 있을 수 있지만, 튜토리얼에서는 관리자가 사람 어노테이터 역할을 수행할 수 있습니다. 

    - **Set name** 필드에 어노테이션 세트에 대한 설명적 이름을 지정하십시오. 이 튜토리얼에서는 이름 `Set 1` 및 `Set 2`를 사용할 수 있습니다. 

6. **Generate**를 클릭하십시오.

### 결과
{: #wks_tutless_ml2_results}

새 어노테이션 세트가 작성되었습니다. 

## 학습 3: 사전 기반 어노테이터를 사용한 어노테이션 미리 작성
{: #wks_tutless_ml3}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 사전 기반 어노테이터를 사용하여 문서에 어노테이션 미리 작성을 수행하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless_ml3_about}

문서에 어노테이션 미리 작성을 수행하는 것은 선택적인 단계입니다. 그러나 이는 나중에 사람 어노테이터의 작업을 용이하게 해 주므로 가치 있는 단계입니다.

사전으로 어노테이션 미리 작성에 대한 자세한 정보는 [사전으로 문서에 어노테이션 미리 작성](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)을 참조하십시오. 

### 프로시저
{: #wks_tutless_ml3_procedure}

1. 작업공간 내에서 **Assets** > **Dictionaries**를 클릭하십시오. 

  `Test dictionary` 사전이 열립니다. *{{site.data.keyword.knowledgestudioshort}} 시작하기* 튜토리얼의 [사전 추가](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) 학습에서는 이 사전을 작성하는 방법을 보여줍니다. 

1. **Entity type** 목록에서 `ORGANIZATION` 엔티티 유형을 선택하여 이를 `Test dictionary` 사전에 맵핑하십시오. 

  *{{site.data.keyword.knowledgestudioshort}} 시작하기* 튜토리얼의 [유형 시스템 작성](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless3) 학습에서는 `ORGANIZATION` 엔티티 유형이 포함된 유형 시스템의 작성 방법을 보여줍니다. 

1. **Machine Learning Model** > **Pre-annotation** > **Dictionaries** 탭에서 **Apply This Pre-annotator**를 클릭하십시오. 
1. [학습 1](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1)에서 작성한 문서 세트는 제외하고, [학습 2](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2)에서 작성한 어노테이션 세트를 선택하십시오. 
1. **Run**을 클릭하십시오.

    ![이 화면 캡처는 Run Annotator 페이지를 보여줍니다. Run 단추가 강조표시되어 있습니다.](images/wks_tutanno3.jpg "이 화면 캡처는 Run Annotator 페이지를 보여줍니다. Run 단추가 강조표시되어 있습니다.")

### 결과
{: #wks_tutless_ml3_results}

작성한 사전을 사용하여 선택한 세트의 문서에 어노테이션 미리 작성이 수행됩니다. 원하면 사전을 사용하여 나중에 추가하는 문서 세트 또는 어노테이션 세트에 어노테이션 미리 작성을 수행할 수 있습니다.

## 학습 4: 어노테이션 작성 태스크 작성
{: #wks_tutless_ml4}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 사람 어노테이터의 작업을 추적하기 위해 어노테이션 작성 태스크를 사용하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless_ml4_about}

어노테이션 작성 태스크에 대한 자세한 정보는 [어노테이션 작성 태스크 작성](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask)을 참조하십시오.

### 프로시저
{: #wks_tutless_ml4_procedure}

1. 작업공간 내에서 **Machine Learning Model** > **Annotation Tasks**를 클릭하십시오. 
2. Tasks 페이지에서 **Add Task**를 클릭하십시오.
3. 태스크의 세부사항을 지정하십시오.

    - **Task name** 필드에 `Test`를 입력하십시오.
    - **Deadline** 필드에서 미래의 날짜를 선택하십시오.

4. **Create**를 클릭하십시오.
5. [학습 2](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2)에서 작성한 어노테이션 세트를 선택하십시오. 

 두 어노테이션 세트 모두를 선택하면 이 태스크를 완료하기 위해  지정된 사람 어노테이터가 두 세트 모두에 어노테이션을 작성해야 함을 지정합니다. 

7. **Create Task**를 클릭하십시오.
8. 사람 어노테이터가 문서에 어노테이션 작성을 시작하면 태스크를 열어서 해당 진행상태를 볼 수 있습니다. 

## 학습 5: 문서에 어노테이션 작성
{: #wks_tutless_ml5}

이 학습에서는 *기준 실제값 편집기*를 사용하여 {{site.data.keyword.knowledgestudioshort}}에서 문서에 어노테이션을 작성하는 방법을 학습합니다. 

### 이 태스크에 대한 정보
{: #wks_tutless_ml5_about}

사람에 의한 어노테이션 작성에 대한 자세한 정보는 [기준 실제값 편집기를 사용한 어노테이션 작성](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte)을 참조하십시오.

### 프로시저
{: #wks_tutless_ml5_procedure}

1. [학습 4](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)에서 작성한 어노테이션 태스크에 지정된 사용자로 {{site.data.keyword.knowledgestudioshort}}에 로그인하십시오. 

    > **참고:** 이 튜토리얼을 진행하는 데 하나의 관리자 ID밖에 이용할 수 없는 경우에는 이 ID를 사용하여 사람에 의한 어노테이션 작성 작업을 수행하십시오. 그러나 실제 시나리오에서 사람 어노테이션은 사람 어노테이터 역할이 있는 서로 다른 사용자에 의해 수행된다는 점을 기억하십시오. 

1. `My workspace` 작업공간을 열고 **Machine Learning Model** > **Annotation Tasks**를 클릭하십시오. 
1. [학습 4](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)에서 작성한 `Test` 어노테이션 태스크를 여십시오. 
1. 지정된 어노테이션 세트 중 하나에 대해 **Annotate**를 클릭하십시오. 

  어노테이션 태스크를 설정하는 방법에 따라, 로그인한 사용자 ID에 하나 이상의 어노테이션 태스크를 지정할 수 있습니다. 

1. 문서 목록에서 *Technology - gmanews.tv* 문서를 찾아서 이를 여십시오. 

  참고로, `IBM` 용어에는 `ORGANIZATION` 엔티티 유형으로 이미 어노테이션이 있습니다. 이 어노테이션은 [학습 3](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3)에서 적용된 사전 프리어노테이터에 의해 추가되었습니다. 이 프리어노테이터는 정상이므로 이를 수정할 필요가 없습니다. 

  ![이 화면 캡처는 "IBM"에 대해 기존의 미리 작성된 어노테이션이 있는 열린 문서를 보여줍니다.](images/wks_tut_preannotation.png "이 화면 캡처는 기존의 미리 작성된 어노테이션이 있는 열린 문서를 보여줍니다.")

1. 멘션에 어노테이션을 작성하려면 다음 작업을 수행하십시오.

    1. 엔티티 탭을 클릭하십시오. 
    2. 문서 본문에서 텍스트 `Thomas Watson`을 선택하십시오.
    3. 엔티티 유형 목록에서 `PERSON`을 클릭하십시오. 엔티티 유형 `PERSON`이 선택된 멘션에 적용됩니다. 

        ![이 화면 캡처는 "Thomas Watson" 멘션에 적용된 "PERSON" 엔티티 유형을 보여줍니다.](images/wks_tut_annotatemention3.png "이 화면 캡처는 보여줍니다.")

1. 관계에 어노테이션을 작성하려면 다음 작업을 수행하십시오. 

    1. 관계 탭을 클릭하십시오. 
    1. `Thomas Watson` 및 `IBM` 멘션을 순서대로 선택하십시오. 멘션을 선택하려면 텍스트 위의 엔티티 유형 레이블을 클릭하십시오. 
    1. 관계 유형 목록에서 `founderOf`를 클릭하십시오. 2개의 멘션이 `founderOf` 관계와 연결됩니다. 

        ![이 화면 캡처는 관계 유형 "founderOf"에 의해 연결된 2개의 멘션을 보여줍니다.](images/wks_tut_annotaterelation.png "이 화면 캡처는 관계 유형에 의해 연결된 2개의 멘션을 보여줍니다.")

1. 상태 메뉴에서 **Completed**를 선택한 후 **Save** 단추를 클릭하십시오.
1. **Open document list**를 클릭하여 이 태스크에 대한 문서의 목록으로 리턴하고, **Submit All Documents**를 클릭하여 승인을 위해 문서를 제출하십시오. 

    > **참고:** 실제 상황에서는 더 많은 어노테이션을 작성하며, 제출하기 전에 세트 내의 모든 문서를 완료합니다. 

1. 이 어노테이션 세트를 닫은 후에 `Test` 태스크에서 다른 어노테이션 세트를 여십시오. 

   어노테이션 태스크를 설정한 방법과 이 태스크가 지정된 사용자에 따라, 어노테이션 태스크의 다른 어노테이션 세트에 지정된 사용자로 {{site.data.keyword.knowledgestudioshort}}에 로그인해야 할 수 있습니다. 

1. *Technology - gmanews.tv* 문서에서 동일한 어노테이션을 반복하고, 이번을 제외하면 `founderOf` 관계 대신 `employedBy` 관계를 사용하십시오. 

  다른 사용자로 로그인하면 다음 학습에서 어노테이터 간 일치를 예시하는 데 도움이 됩니다. 그러나 한 명의 사용자만 있는 경우에도 학습서를 완료하여 어노테이터 간 일치의 작동 방법을 파악할 수 있습니다. 

1. 두 번째 어노테이션 세트에 대한 어노테이션을 완료한 후에는 **Submit All Documents**를 클릭하십시오. 

## 학습 6: 어노테이터 간 일치 분석
{: #wks_tutless_ml6}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 여러 사람 어노테이터의 작업을 비교하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless_ml6_about}

여러 사람 어노테이터가 겹치는 문서에 일관되게 어노테이션을 작성하고 있는지 판별하려면 *어노테이터 간 일치*(IAA) 점수를 검토하십시오. 

{{site.data.keyword.knowledgestudioshort}}는 문서 세트의 상태에 관계 없이 태스크에 포함된 모든 문서 세트의 모든 겹치는 문서를 검사하여 IAA 점수를 계산합니다. IAA 점수는 여러 사람 어노테이터가 멘션, 관계 및 상호 참조 체인에 대해 얼마나 다르게 어노테이션을 작성했는지 보여줍니다. IAA 점수는 주기적으로 확인하여 여러 사람 어노테이터가 서로 일관된 작업을 수행하고 있는지 확인하는 것이 좋습니다.

이 튜토리얼에서는 사람 어노테이터가 승인을 위해 모든 문서를 제출했습니다. 어노테이터 간 일치 점수가 허용 가능한 경우에는 문서 세트를 승인할 수 있습니다. 문서 세트를 거부하면 개선을 위해 사람 어노테이터에게 반환됩니다.

어노테이터 간 일치에 대한 자세한 정보는 [기준 실제값 빌드](/docs/services/watson-knowledge-studio/build-groundtruth.html)를 참조하십시오. 

### 프로시저
{: #wks_tutless_ml6_procedure}

1. 관리자로 {{site.data.keyword.knowledgestudioshort}}에 로그인하여 **Machine Learning Model** > **Annotation Tasks**를 선택한 후에 `Test` 태스크를 클릭하십시오. 

  **Status** 열에서 문서 세트가 제출된 것을 볼 수 있습니다.

1. **Calculate Inter-Annotator Agreement**를 클릭하십시오.
1. 첫 번째 메뉴를 클릭하여 멘션, 관계 및 상호 참조 체인에 대한 IAA 점수를 보십시오. 사람 어노테이터 쌍을 기준으로 일치 점수를 볼 수도 있습니다. 특정 문서를 기준으로 일치 점수를 볼 수도 있습니다. 일반적으로 최고점 1(1은 완전 일치를 의미함)을 기준으로 .8점을 획득하는 것을 목표로 하십시오. 이 튜토리얼에서 두 엔티티 유형에만 어노테이션을 작성했으므로 대부분의 엔티티 유형 점수는 `N/A`(해당사항 없음)이며, 이는 점수를 부여하기 위해 사용 가능한 정보가 없음을 의미합니다. 

    *그림 1. `dave` 및 `phil`이라는 사용자의 어노테이터 간 점수 검토*

    ![이 화면 캡처는 태스크의 어노테이터 간 점수를 보여줍니다.](images/wks_tutiaa2.gif "이 화면 캡처는 태스크의 어노테이터 간 점수를 보여줍니다.")

1. 점수를 검토하고 나면 `SUBMITTED` 상태의 문서 세트를 승인할지 또는 거부할지 결정할 수 있습니다. 다음 조치 중 하나를 수행하십시오.

    - 어노테이션 세트에 대해 점수가 허용 가능한 경우에는 선택란을 선택하고 **Accept**를 클릭하십시오. 다른 문서 세트와 겹치지 않는 문서는 기준 실제값으로 승격됩니다. 겹치는 문서는 먼저 충돌을 해결하기 위해 판정을 통해 검토해야 합니다. 이 튜토리얼의 경우에는 두 문서 세트를 모두 승인하십시오.
    - 어노테이션 세트에 대해 점수가 허용 가능하지 않은 경우에는 선택란을 선택하고 **Reject**를 클릭하십시오. 해당 문서 세트는 사람 어노테이터의 재작업을 통해 어노테이션을 개선해야 합니다.

### 결과
{: #wks_tutless_ml6_results}

어노테이터 간 일치 점수를 평가하면 사람 어노테이터 쌍이 동일한 문서에 얼마나 다르게 어노테이션을 작성했는지 볼 수 있습니다. 어노테이터 간 일치 점수가 허용 가능한 경우에는 문서 세트를 승인합니다.

## 학습 7: 어노테이션 작성된 문서의 충돌 판정
{: #wks_tutless_ml7}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 문서 세트 간에 겹치는 문서의 충돌을 판정하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless_ml7_about}

문서 세트를 승인할 때는 다른 문서 세트와 겹치지 않는 문서만 기준 실제값으로 승격됩니다. 특정 문서가 여러 문서 세트 간에 겹치는 문서의 일부인 경우에는 이러한 문서를 기준 실제값으로 승격하기 전에 어노테이션 충돌을 판정해야 합니다.

판정에 대한 자세한 정보는 [기준 실제값 빌드](/docs/services/watson-knowledge-studio/build-groundtruth.html)를 참조하십시오. 

### 프로시저
{: #wks_tutless_ml7_procedure}

1. 관리자로 {{site.data.keyword.knowledgestudioshort}}에 로그인하여 **Machine Learning Model** > **Annotation Tasks**를 선택한 후에 `Test` 태스크를 클릭하십시오. 
1. 두 문서 세트가 승인됨 상태인지 확인하십시오.
1. **Check Overlapping Documents for Conflicts**를 클릭하십시오.

    둘 이상의 사람 어노테이터에 의해 어노테이션 작성된, 겹치는 문서가 표시됩니다.

1. 튜토리얼에서 *Technology - gmanews.tv* 문서에 대해 충돌 관계를 작성하도록 지시했으므로, 목록에서 해당 문서를 찾고 **Check for Conflicts**를 클릭하십시오. 
1. 충돌하는 두 개의 어노테이션 세트를 선택하고 **Check for Conflicts**를 클릭하십시오. 

    판정 모드가 열립니다. 판정 모드에서는 겹치는 문서를 보고 충돌을 확인할 수 있으며 문서를 기준 실제값으로 승격하기 전에 어노테이션을 제거하거나 대체할 수 있습니다. 

1. **Relation conflicts**를 선택하고 `founderOf` 관계를 승인한 후에 `employedBy` 관계를 거부하십시오. 
1. **Promote to Ground Truth**를 클릭하십시오.

    또는, Documents 페이지에서 **Accept**를 클릭하여 문서를 기준 실제값으로 승격할 수 있습니다.

### 결과
{: #wks_tutless_ml7_results}

어노테이션 충돌을 해결하고 문서를 기준 실제값으로 승격하고 나면 기계 학습 모델을 훈련시키는 데 이러한 문서를 사용할 수 있습니다.

## 학습 8: 기계 학습 모델 작성
{: #wks_tutless_ml8}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 기계 학습 모델을 작성하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless_ml8_about}

기계 학습 모델을 작성할 때는 이를 훈련시키는 데 사용할 문서 세트를 선택합니다. 또한 훈련 데이터, 테스트 데이터 및 블라인드 데이터로 사용될 문서의 백분율을 지정합니다. 판정 또는 승인을 통해 기준 실제값이 된 문서만 기계 학습 모델을 훈련시키는 데 사용할 수 있습니다.

기계 학습 모델에 대한 자세한 정보는 [기계 학습 모델 훈련](/docs/services/watson-knowledge-studio/train-ml.html) 및 [기계 학습 모델 성과 분석](/docs/services/watson-knowledge-studio/evaluate-ml.html)을 참조하십시오. 

### 프로시저
{: #wks_tutless_ml8_procedure}

1. {{site.data.keyword.knowledgestudioshort}}에 관리자로 로그인하십시오.
1. **Machine Learning Model** > **Performance** > **Train and evaluate**를 클릭하십시오. 
2. **All**을 선택한 후에 **Train & Evaluate**를 클릭하십시오. 

    > **참고:** 훈련에는 사람 어노테이션의 수와 모든 문서의 단어 수에 따라 10분 이상 또는 몇 시간이 소요될 수 있습니다. 

3. 기계 학습 모델의 훈련을 마치면, Version 페이지에서 이를 내보내거나 Performance 페이지의 각 그래프 위에 있는 **Detailed Statistics** 링크를 클릭하여 해당 성능에 대한 자세한 정보를 볼 수 있습니다. 
4. Training/Test/Blind Sets 페이지를 보려면 **Train and evaluate** 단추를 클릭하십시오.
5. 사람 어노테이터가 작업한 문서를 보려면 **View Ground Truth**를 클릭하십시오.
6. 기계 학습 모델이 동일한 문서 세트에 작성한 어노테이션을 보려면 **View Decoding Results**를 클릭하십시오.
7. 기계 학습 모델의 정밀도, 재현율 및 F1 점수에 대한 세부사항을 보려면 Performance 페이지를 클릭하십시오. 
8. 각 그래프 위에 있는 **Detailed Statistics** 링크를 클릭하십시오. 이러한 Statistics 페이지에서는 단일 선택 단추를 사용하여 멘션, 관계 및 상호 참조 체인에 대한 점수를 볼 수 있습니다.

    엔티티 유형, 관계 유형 및 상호 참조 체인에 대한 통계 요약을 보고 성능을 분석할 수 있습니다. *혼동 매트릭스*에 표시된 통계를 분석할 수도 있습니다. 매트릭스를 보려면 **Summary**를 **Confusion Matrix**로 변경하십시오. 혼동 매트릭스는 기계 학습 모델이 추가한 어노테이션을 기준 실제값의 어노테이션과 비교하는 데 도움을 줍니다. 

    > **참고:** 이 튜토리얼에서는 단 하나의 조직용 사전을 사용하여 문서에 어노테이션을 작성했습니다. 따라서 `ORGANIZATION`을 제외한 대부분의 엔티티 유형에 대해 표시되는 점수는 `0` 또는 `N/A`입니다. 점수는 낮지만, 사람에 의한 어노테이션 작성 또는 정정을 수행하지 않았으므로 이는 예상된 결과입니다.

    *그림 2. 기계 학습 모델에 대한 Statistics 페이지의 옵션*

    ![이 화면 캡처는 Statistics 페이지를 보여줍니다.](images/wks_tutanno9.gif "이 화면 캡처는 Statistics 페이지를 보여줍니다.")

9.  **Versions**를 클릭하십시오. Versions 페이지에서는 모델 및 모델을 작성할 때 사용된 리소스의 스냅샷을 작성할 수 있습니다(사전 및 어노테이션 작성 태스크 제외). 예를 들면, 모델을 다시 훈련시키기 전에 모델의 스냅샷을 작성하려 할 수 있습니다. 다음에 모델을 훈련시켰을 때 통계가 더 나빠진 경우에는 이전 버전을 승격하고 좋지 않은 결과를 리턴한 버전을 삭제할 수 있습니다.

### 결과
{: #wks_tutless_ml8_results}

기계 학습 모델을 작성하고, 훈련시키고, 테스트 데이터 및 블라인드 데이터에 어노테이션을 작성할 때의 성능을 평가했습니다. 성능 메트릭을 탐색하면 기계 학습 모델의 정확도를 개선할 방법을 식별할 수 있습니다.

## 튜토리얼 요약
{: #wks_tutml_sum}

기계 학습 모델이 작성되었습니다. 

### 학습한 내용
{: #lessons_learned}

이 튜토리얼을 완료하여 다음 개념에 대해 학습했습니다.

- 문서 세트
- 기계 학습 모델
- 사람에 의한 어노테이션 작성 태스크
- 어노테이터 간 일치 및 판정
