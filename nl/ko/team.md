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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# 팀 구성
{: #team}

모델을 작성하려면 주제 관련 전문가, 프로젝트 관리자, 그리고 통계적 모델을 이해하고 해석할 수 있는 사용자의 의견이 필요합니다. 사용자는 로그인해야 하는 각 사용자에 대해 {{site.data.keyword.knowledgestudioshort}}에 사용자를 추가해야 합니다.
{: shortdesc}

**참고**: 표준 플랜 및 프리미엄 플랜만 사용자를 추가할 수 있습니다. 무료 사용제는 사용자가 한 명으로 제한됩니다. 이 유일한 사용자에게는 가장 높은 권한인 Admin 권한이 있는 역할이 지정됩니다. 

## 시작하기 전에

- 지원되는 브라우저를 사용하고 있는지 확인하십시오. 자세한 정보는 [브라우저 요구사항](/docs/services/watson-knowledge-studio/system-requirements.html)을 참조하십시오. 
- [{{site.data.keyword.knowledgestudioshort}}의 인스턴스를 작성하십시오](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance). 
- 표준 또는 프리미엄 플랜에 가입한 경우에는 {{site.data.keyword.cloud_notm}} **관리** 탭에서 {{site.data.keyword.knowledgestudioshort}}의 사용자로서 추가할 다른 사용자를 조직으로 초대하십시오. 사용자 초대에 대한 자세한 정보는 [사용자 초대 및 액세스 권한 지정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}을 참조하십시오. 

  **중요**:

  - 초대된 사용자에게 **개발자** Cloud Foundry 역할이 있는지 확인하십시오. 자세한 정보는 [Cloud Foundry 액세스 권한 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}을 참조하십시오. 
  - {{site.data.keyword.knowledgestudioshort}}를 처음으로 실행하는 사용자에게 {{site.data.keyword.knowledgestudioshort}} 인스턴스의 Admin 역할이 부여됩니다. 이 태스크에서는 사용자가 플랜에 가입한 후 {{site.data.keyword.knowledgestudioshort}}를 처음 실행한 사용자라고 가정하며, 이는 사용자에게 Admin 역할이 있음을 의미합니다. 

## 이 태스크에 대한 정보

일반적으로 다음 역할을 지정하기 위해 사용자가 추가됩니다. 

**참고:** 무료 사용제에 가입한 경우에는 {{site.data.keyword.knowledgestudioshort}}의 인스턴스에 다른 사용자를 추가할 수 없습니다. 대신 {{site.data.keyword.knowledgestudioshort}}를 실행할 때 해당 인스턴스에 Admin 역할이 부여된 상태로 추가됩니다. Admin 역할이 있는 상태에서는 일반적으로 그 외의 역할이 지정된 다른 사용자가 수행하는 많은 기능을 수행할 수 있습니다. 이러한 사용자는 도메인의 다양한 영역에 대한 전문가들이 기계 학습 모델 또는 규칙 기반 모델을 빌드하기 위해 어떻게 협력할 수 있는지 테스트할 수 있습니다. 

- **HumanAnnotator**

    사람 어노테이터는 일반적으로 특정 도메인과 관련된 엔티티 및 관계를 식별하기 위해 해당 도메인의 문서를 검토하는 주제 관련 전문가입니다. 이러한 사용자는 제한된 방식으로 애플리케이션과 상호작용합니다. 이들은 기준 실제값 편집기를 사용하여 자신에게 지정된 문서 세트에 어노테이션을 작성합니다. 

- **ProjectManager**

    프로젝트 관리자는 작업공간 아티팩트 작성과 모델 훈련, 작성 및 배치 등의 태스크를 수행하여 모델 작성을 용이하게 하는 데 도움을 주는 사용자입니다. 기계 학습 어노테이터를 빌드하는 데 사용되는 작업공간의 경우, 프로젝트 관리자는 문서 검토 태스크를 사람 어노테이터에게 지정하고, 어노테이션 충돌을 판정하고, 기준 실제값에 추가할 문서를 승인함으로써 문서 어노테이션 작성 프로세스 또한 관리합니다. 

## {{site.data.keyword.knowledgestudioshort}}에서의 사용자 추가

{{site.data.keyword.cloud_notm}} 조직에서 {{site.data.keyword.knowledgestudioshort}}로 사용자를 추가하십시오. 

**참고**: 표준 플랜 및 프리미엄 플랜만 사용자를 추가할 수 있습니다. 무료 사용제는 사용자가 한 명으로 제한됩니다. 

{{site.data.keyword.knowledgestudioshort}} 인스턴스에 사용자를 추가하려면 다음 작업을 수행하십시오. 

1. {{site.data.keyword.ibmid}}를 사용하여 [{{site.data.keyword.cloud_notm}} 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/dashboard/apps/){: new_window}에 로그인하고 {{site.data.keyword.knowledgestudioshort}}를 실행하십시오. 
1. **설정** 아이콘을 클릭한 후 **View/modify service details**를 클릭하십시오. 
1. **Manager users** 섹션에서 추가할 사용자의 {{site.data.keyword.ibmid}}를 입력하십시오. 
1. 해당 사용자에게 부여할 역할을 선택하십시오. 

   참고: 사용자 역할은 지정한 후 다운그레이드할 수 없으므로, Admin 역할 또는 ProjectManager 역할을 지정할 때는 각 역할이 수행할 수 있는 태스크를 먼저 이해하십시오. 

1. **Add**를 클릭하십시오. 

## 사용자 역할 업그레이드

{{site.data.keyword.knowledgestudioshort}}에 사용자를 추가한 후에는 권한이 낮은 역할을 높은 역할로 업그레이드할 수 있습니다. 사용자는 아래에 설명된 역할이 지정되어야 해당 태스크를 수행할 수 있습니다. 

**참고**: 표준 플랜 및 프리미엄 플랜만 사용자를 업그레이드할 수 있습니다. 무료 사용제는 사용자가 이미 권한이 가장 높은 Admin 역할이 있는 한 명으로 제한됩니다. 

> **주의: 권한이 높은 역할에서 낮은 역할로의 다운그레이드는 허용되지 않습니다. **

{{site.data.keyword.knowledgestudioshort}} 사용자의 권한을 업그레이드하려면 다음 작업을 수행하십시오. 

1. {{site.data.keyword.ibmid}}를 사용하여 [{{site.data.keyword.cloud_notm}} 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/dashboard/apps/){: new_window}에 로그인하고 {{site.data.keyword.knowledgestudioshort}}를 실행하십시오. 
1. 오른쪽 맨 위의 탐색 메뉴에서 **설정** 아이콘 ![설정 아이콘](images/settings.png)을 클릭한 후 **View/modify service details**를 클릭하십시오. Service Details 페이지의 **Manage users** 섹션에는 이 {{site.data.keyword.knowledgestudioshort}} 인스턴스 사용자의 모든 사용자 ID가 나열됩니다. 
1. 변경할 사용자의 이름을 찾아 **Edit** 링크를 클릭하십시오. 

    {{site.data.keyword.knowledgestudioshort}}에는 다음 역할이 있습니다(권한이 높은 역할에서 낮은 역할 순서대로 나열되어 있음). 
    - **Admin**

      이 역할의 사용자는 다음 태스크를 수행할 수 있습니다. 

        - 기능, 스토리지 및 사용자 추가와 같은 구독 관리
        - Service Details 페이지에서 사용자에게 구독에 대한 액세스 권한 부여
        - 해당 구독 내의 모든 작업공간 작성 및 관리
        - 모든 작업공간의 프로젝트 관리자 또는 사람 어노테이터 역할을 사용자에게 지정

    - **ProjectManager**

      이 역할이 있는 사용자는 다음 태스크를 수행할 수 있습니다. 

      - 추가되는 작업공간 관리
      - 작업공간에 사람 어노테이터 지정

      이 역할이 있는 사용자는 다음 태스크를 수행할 수 없습니다. 

      - 작업공간 작성
      - Service Details 페이지에서 사용자 액세스 권한 및 역할 관리

    - **HumanAnnotator**

      이 역할이 있는 사용자는 자신에게 사람 어노테이터 역할이 지정된 작업공간에 있는 문서, 그리고 자신에게 지정된 어노테이션 작성 태스크와 연관된 문서 세트에 있는 문서에 어노테이션을 작성할 수 있습니다. 

      **중요:** **HumanAnnotator** 역할이 있는 사용자가 {{site.data.keyword.knowledgestudioshort}} 애플리케이션에 나열된 작업공간을 보려면 먼저 작업공간을 작성하고, 해당 사용자를 문서 세트와 연관시키고, 해당 사용자에게 어노테이션 작성 태스크를 지정해야 합니다. 사용자가 처음 애플리케이션에 액세스할 때 작업공간을 볼 수 있도록 사용자가 등록한 후 가능한 한 빨리 작업공간을 설정하십시오. 작업공간을 설정한 후에는 문서에 어노테이션을 작성할 수 있다고 사용자에게 알리는 것이 좋습니다. 

1. 사용자의 역할을 클릭하고 해당 사용자에 대해 업그레이드할 역할을 선택하십시오. 
1. 선택사항: {{site.data.keyword.knowledgestudioshort}}에서 사용자 관리를 마친 후에는 웹 브라우저를 닫아 세션을 종료하십시오. {{site.data.keyword.knowledgestudioshort}} 사용자 인터페이스는 명시적 로그아웃 조치를 제공하지 않습니다. 

## 사용자 계정 비활성화

나중에 사용자를 제거하려는 경우에는 이전 Service Details 페이지 열기 단계를 따르십시오. 사용자 ID 목록에서 제거할 사용자를 찾아 **Deactivate**를 클릭하십시오. 

> **주의**: 사용자에게 어노테이션을 작성할 문서가 지정되어 있는 상태에서 해당 계정을 비활성화하면 해당 사용자의 어노테이션이 영향을 받습니다. 비활성화된 사용자가 작성한 어노테이션이 기준 실제값으로 승격되지 않은 경우 이러한 어노테이션은 삭제됩니다. 

### 관련 태스크

[어노테이션 세트 작성 및 지정](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
