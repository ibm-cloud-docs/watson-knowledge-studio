---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}하십시오.
{: tip}

# {{site.data.keyword.knowledgestudioshort}} 시작하기
{: #wks_tutintro}

이 {{site.data.keyword.knowledgestudiofull}} 튜토리얼은 다른 튜토리얼을 시작하기 전에 완료해야 하는 전제조건 태스크를 수행하는 데 도움을 줍니다.
{: shortdesc}

## 시작하기 전에
{: #prereq}

- 지원되는 브라우저를 사용하고 있는지 확인하십시오. 자세한 정보는 [브라우저 요구사항](/docs/services/watson-knowledge-studio/system-requirements.html)을 참조하십시오.
-  이 튜토리얼을 완료하려면 {{site.data.keyword.knowledgestudioshort}}에서 사용할 수 있는 사용자 ID가 하나 이상 있어야 합니다. 이 사용자 ID에는 Admin 역할이 있어야 합니다. 라이트 플랜에 가입한 경우에는 유일한 사용자로서 Admin 역할을 보유합니다. 사용자 역할에 대한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오.

## 서비스 인스턴스 작성
{: #instance}

1. 아직 가입하지 않은 경우에는 [{{site.data.keyword.ibmid}}에 가입 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net){: new_window}하고 {{site.data.keyword.cloud_notm}}에 로그인하십시오.
1. {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ 서비스 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/developer/watson/services){: new_window}에서 {{site.data.keyword.knowledgestudioshort}} 타일을 클릭하고 플랜에 가입하십시오. 
1. 플랜에 가입한 후에는 기존 서비스의 목록에서 {{site.data.keyword.knowledgestudioshort}}를 실행하십시오. 

## 학습 1: 사용자 역할 지정
{: #wks_tutless1}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 사용자에게 지정할 수 있는 다양한 역할에 대해 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless1_about}

기계 학습 모델을 작성하려면 주제 관련 전문가, 프로젝트 관리자, 그리고 통계적 모델을 이해하고 해석할 수 있는 사용자의 의견이 필요합니다. 관리자는 각 사용자가 자신의 태스크에 대해 적절한 권한을 가질 수 있도록 사용자에게 역할을 지정합니다. 사용자 역할에 대한 자세한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오.

### 프로시저
{: #wks_tutless1_procedure}

1. 관리자 ID를 사용하여 {{site.data.keyword.knowledgestudioshort}}에 로그인하십시오. 기존 {{site.data.keyword.knowledgestudioshort}} 인스턴스가 있는 경우에는 {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ 서비스 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/developer/watson/services){: new_window}에서 이를 찾을 수 있습니다. 
1. 설정 아이콘을 클릭하여 Service Details 페이지를 여십시오. 이 페이지에는 {{site.data.keyword.knowledgestudioshort}} 사용자로 등록된 모든 사용자 ID가 나열됩니다. 각 사용자 ID에는 다음 역할 중 하나가 있습니다(권한이 큰 역할에서 작은 역할 순서대로 나열됨).

    - Admin
    - 프로젝트 관리자
    - 사람 어노테이터

    사용자 역할에 대한 정보는 [{{site.data.keyword.knowledgestudioshort}}의 사용자 역할](/docs/services/watson-knowledge-studio/roles.html)을 참조하십시오. 

1. Admin 역할이 있는 사용자가 하나 이상인지 확인하십시오. 이 역할이 있는 사용자 ID는 작업공간을 작성할 수 있으며, 프로젝트 관리자 또는 사람 어노테이터 역할을 수행할 수 있습니다.
1. 추가 사용자 ID에 대한 액세스 권한이 있는 경우에는 사람 어노테이터 역할이 있는 사용자가 둘 이상인지 확인하십시오. 

    > **참고:** 실제 모델을 작성할 때는 일반적으로 관리자 또는 프로젝트 관리자 외에 여러 사람 어노테이터가 포함됩니다. 그러나 이 튜토리얼은 하나의 사용자 ID만 있어도 진행할 수 있습니다.

1. 선택사항: 사용자 ID에 지정된 역할을 변경하십시오. 테이블의 **Action** 열에서 **Edit** 링크를 클릭한 후에 지정된 사용자 역할을 변경하십시오. 

    > **참고:** 보다 많은 권한의 역할로 사용자 ID를 업그레이드하는 것은 가능하지만, Admin 또는 프로젝트 관리자 역할이 있는 사용자를 사람 어노테이터 역할로 다운그레이드할 수는 없습니다. 

## 학습 2: 작업공간 작성
{: #wks_tutless2}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}} 내에 작업공간을 작성하는 방법을 학습합니다.

### 이 태스크에 대한 정보
{: #wks_tutless2_about}

작업공간은 훈련 문서, 유형 시스템, 사전, 사람 어노테이터가 추가하는 어노테이션을 비롯하여 기계 학습 모델을 작성하는 데 필요한 모든 리소스를 정의합니다. 작업공간 작성에 대한 자세한 정보는 [작업공간 작성](/docs/services/watson-knowledge-studio/create-project.html)을 참조하십시오.

### 프로시저
{: #wks_tutless2_procedure}

1. {{site.data.keyword.knowledgestudioshort}} 관리자로서 {{site.data.keyword.cloud_notm}} [대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net){:new_window}에서 {{site.data.keyword.knowledgestudioshort}} 서비스를 실행하십시오.
1. **Create Worskpace**를 클릭하십시오.
1. 새 작업공간의 세부사항을 지정하십시오.

    - **Workspace name** 필드에 `My workspace`를 입력하십시오.
    - **Workspace description** 필드에 `Watson Knowledge Studio tutorial workspace`를 입력하십시오.
    - **Language of documents** 필드에 기본값 **English**를 사용하십시오. 이 튜토리얼에서 사용할 샘플 파일은 영어로 되어 있습니다.

1. **Create**를 클릭하십시오.

### 결과
{: #wks_tutless2_results}

작업공간이 작성되어 자동으로 열립니다.

### 다음에 수행할 작업
{: #wks_tutless2_next}

이제 유형 시스템과 같은 작업공간 리소스의 구성을 시작할 수 있습니다.

## 학습 3: 유형 시스템 작성
{: #wks_tutless3}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}} 내에 유형 시스템을 업로드하고 수정하는 방법을 학습합니다. 어노테이션 작성 태스크를 시작하려면 먼저 유형 시스템을 작성하거나 업로드해야 합니다.

### 이 태스크에 대한 정보
{: #wks_tutless3_about}

유형 시스템에 대한 자세한 정보는 [유형 시스템](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)을 참조하십시오.

### 프로시저
{: #wks_tutless3_procedure}

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일을 컴퓨터에 다운로드하십시오. 이 파일에는 KLUE 유형 시스템 예가 포함되어 있습니다.
1. **Assets**> **Entity Types**를 클릭하십시오. 
1. Entity Types 페이지에서 **Upload**를 클릭하십시오.
1. 컴퓨터에서 `en-klue2-types.json` 파일을 업로드하십시오. 업로드된 유형 시스템이 테이블에 표시됩니다.
1. 업로드된 데이터를 볼 수 있도록 유형 시스템을 탐색하십시오.
1. 엔티티 유형을 편집하십시오.

    1. MONEY 엔티티 유형을 찾으십시오.
    1. 테이블 행의 임의의 위치를 두 번 클릭하여 이 엔티티 유형을 편집하십시오.
    1. **Roles** 열에서 AWARD 역할 옆에 있는 **역할 삭제** 아이콘 ![ "역할 삭제" 아이콘](images/wks_delete.jpg " ")을 클릭하십시오. 

        ![엔티티 유형에서 역할을 삭제하는 화면 캡처입니다.](images/wks_tut_delete_role.jpg "커서 올려놓기를 보여주는 화면 캡처입니다.")

    1. **Save**를 클릭하십시오.

### 다음에 수행할 작업
{: #wks_tutless3_next}

유형 시스템 변경을 완료한 후에는 작업공간에 문서 추가를 시작할 수 있습니다.

## 학습 4: 사전 추가
{: #wks_tutless4}

이 학습에서는 {{site.data.keyword.knowledgestudioshort}}에서 작업공간에 사전을 추가하는 방법을 학습합니다. 사전은 기계 학습 모델을 작성할 때 텍스트에 어노테이션 미리 작성을 수행하는 데 사용됩니다.

### 이 태스크에 대한 정보
{: #wks_tutless4_about}

사전에 대한 자세한 정보는 [작업공간에 사전 추가](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries)를 참조하십시오.

### 프로시저
{: #wks_tutless4_procedure}

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일을 컴퓨터에 다운로드하십시오. 이 파일에는 {{site.data.keyword.knowledgestudioshort}} 사전에 업로드하는 데 적합한, CSV 형식의 사전 용어가 포함되어 있습니다.
1. **Assets** > **Dictionaries**를 클릭하십시오. 
1. **Create Dictionary**를 클릭하여 사전을 추가하십시오.

    > **참고:** 사용할 사전을 있는 그대로 업로드하는 데 사용되는 **Upload dictionary**를 클릭하지 마십시오. 이 튜토리얼에서는 편집 가능한 새 사전을 작성한 후 여기에 용어를 업로드합니다.

1. **Name** 필드에 `Test dictionary`를 입력하고 **Save**를 클릭하여 비어 있는 사전을 작성하십시오.

    새 사전이 작성되며 자동으로 편집할 수 있도록 열립니다.

1. 사전 분할창에서 **Upload**를 클릭하십시오.
1. 컴퓨터에서 `dictionary-items-organization.csv` 파일을 업로드하십시오. 파일에 있는 용어가 사전에 업로드됩니다.
1. **Add Entry**를 클릭하여 새 용어를 작성하십시오. 테이블의 맨 위에 편집 가능한 행이 추가됩니다.
1. **Surface Forms** 열에서 `IBM` 및 `International Business Machines Corporation`을 각각 별도의 행에 입력하십시오. (새 표층형을 입력하기 시작하면 추가 표층형을 위해 아래에 공간이 추가됩니다.) `IBM` 옆의 단일 선택 단추는 선택된 채로 두십시오. 이는 `IBM`이 표제어임을 나타냅니다.
1. **Part of Speech** 열에서 **Noun**을 선택하십시오.
1. **Save**를 클릭하십시오.

    ![Dictionaries 페이지의 화면 캡처입니다. "IBM" 사전 항목이 선택되어 있으며 해당 표층형 및 품사가 강조표시되어 있습니다.](images/wks_tutdict4.jpg "Dictionaries 페이지의 화면 캡처입니다.")

### 다음에 수행할 작업
{: #wks_tutless4_next}

사전을 작성한 후에는 이를 사용하여 문서에 어노테이션 미리 작성을 수행함으로써 사람에 의한 어노테이션 작성 태스크를 가속화할 수 있습니다.

## 튜토리얼 요약
{: #wks_tutsum}

{{site.data.keyword.knowledgestudioshort}}에 대해 학습하면서, 작업공간을 작성하고 여기에 아티팩트를 추가했습니다.

### 학습한 내용
{: #lessons_learned}

이 튜토리얼을 완료하여 다음 개념에 대해 학습했습니다.

- 작업공간
- 유형 시스템
- 사전
