---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# {{site.data.keyword.knowledgestudioshort}}에서 사용자 역할 
{: #roles}

{{site.data.keyword.knowledgestudiofull}} 역할은 기계 학습 또는 규칙 기반 모델을 작성하는 사용자 팀을 구성하는 데 사용됩니다.
{: shortdesc}

## {{site.data.keyword.knowledgestudioshort}}의 역할에 대한 참고사항
{: #notes}

- {{site.data.keyword.knowledgestudioshort}}에서 사용자 역할은 다음 레벨에서 관리됩니다. 
  - {{site.data.keyword.cloud}} 역할은 {{site.data.keyword.cloud_notm}} 서비스에 대한 액세스를 제어합니다. {{site.data.keyword.knowledgestudioshort}}에서는 액세스 제어에 Cloud Foundry를 사용하며, 이를 위해 {{site.data.keyword.knowledgestudioshort}} 사용자에게는 개발자 역할이 있어야 합니다. 자세한 정보는 [Cloud Foundry 액세스 권한 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}을 참조하십시오.
  - {{site.data.keyword.knowledgestudioshort}} 역할은 이 페이지에서 설명하는 대로 {{site.data.keyword.knowledgestudioshort}} 기능에 대한 액세스를 제어합니다. 
- {{site.data.keyword.knowledgestudioshort}} 역할은 {{site.data.keyword.knowledgestudioshort}}의 인스턴스를 작성할 필요가 없습니다. 그러나 사용자가 {{site.data.keyword.knowledgestudioshort}}의 인스턴스를 작성할 때 {{site.data.keyword.knowledgestudioshort}}를 실행하는 첫 번째 사용자에게는 {{site.data.keyword.knowledgestudioshort}} admin 역할이 지정됩니다. 
- 작업공간을 관리하려면 프로젝트 관리자가 Admin에 의해 작업공간에 지정되어야 합니다. 
- Admin 및 프로젝트 관리자는 사람 어노테이터의 역할을 수행할 수 있지만, 사람 어노테이터가 어노테이션 세트에 지정되어야 하는 것과 동일한 방법으로 어노테이션 세트에 지정되어야 합니다. 
- 일단 지정되면 사용자 역할은 보다 높은 권한 레벨에서 보다 낮은 권한 레벨로 다운그레이드될 수 없습니다. Admin은 프로젝트 관리자 또는 사람 어노테이터로 다운그레이드될 수 없으며, 프로젝트 관리자는 사람 어노테이터로 다운그레이드될 수 없습니다. 사용자 추가, 역할 업그레이드 및 사용자 계정 비활성화에 대한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오. 

## 역할 설명
{: #descriptions}
{{site.data.keyword.knowledgestudioshort}} 역할은 다음 표에 설명되어 있습니다. 역할은 최상위 레벨에서 최하위 레벨의 권한 순으로 나열되어 있습니다. 

|역할 |설명 |
|------|-------------|
|Admin |사용자, 리소스 이용 및 월별 비용 관리를 포함하는 사용자 태스크를 담당합니다. 대규모 팀 설정에서 Admin은 모델 개발 프로세스에 거의 참여하지 않습니다.
|프로젝트 관리자 |자신이 지정된 작업공간의 전체 조직을 책임집니다. 태스크에는 유형 시스템 작성, 자산 관리, 어노테이션 작업 관리, 기계 학습 모델 평가 및 모델 배치가 포함됩니다. 유형 시스템을 작성함은 물론 유형 시스템을 올바르게 적용하고 모델 품질을 평가하는 방법을 사람 어노테이터에게 가르치므로, 이 역할의 사용자에게는 산업 주제 관련 전문 지식이 필요합니다. |
|사람 어노테이터 |자신이 지정된 훈련 문서에서 엔티티 멘션 및 관계 멘션의 레이블링을 수행합니다. 작업은 사람 어노테이터에게 지정되며 프로젝트 관리자에 의해 모니터됩니다. 유형 시스템을 올바르게 적용하는 방법을 프로젝트 관리자가 가르쳐주지 않는 한, 사람 어노테이터에게 업계 주제 관련 전문 지식이 없을 수 있습니다. |
{:caption="표 1. 역할 설명" caption-side="top"}

## 역할 권한
{: #permissions}

각 역할의 권한을 비교하려면 다음 표를 참조하십시오. 하나의 권한이 각 행에 나열되어 있습니다. 역할에 해당 권한이 있으면 역할 열이 체크 표시(&checkmark;)로 표시됩니다.

|권한|Admin |프로젝트 관리자 |사람 어노테이터 |
|------------|-------|-----------------|-----------------|
|사용자 액세스 및 역할 관리 | &checkmark; |  |  |
|작업공간 관리| &checkmark; |  |  |
|유형 시스템 및 어노테이션 가이드라인 작성| &checkmark; | &checkmark; |  |
|훈련 문서 업로드| &checkmark; | &checkmark; |  |
|규칙 관리| &checkmark; | &checkmark; |  |
|문서에 어노테이션 미리 작성 수행 | &checkmark; | &checkmark; |  |
|관리 태스크 관리 | &checkmark; | &checkmark; |  |
|사람 어노테이션과의 어노테이션 충돌 해결(*판정*) | &checkmark; | &checkmark; |  |
| 기계 학습 모델의 훈련 및 평가| &checkmark; | &checkmark; |  |
|런타임 서비스에 모델 배치 및 배치 취소| &checkmark; | &checkmark; |  |
|문서 어노테이션 수행 | &checkmark; | &checkmark; | &checkmark; |
{:caption="표2. 역할 권한" caption-side="top"}
