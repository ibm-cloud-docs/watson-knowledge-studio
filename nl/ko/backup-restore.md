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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/backup-restore.html){: new_window}.
{: tip}

# 데이터 백업 및 복원
{: #backup-restore}

{{site.data.keyword.knowledgestudioshort}}의 작업공간을 백업하고 복원해야 하는 경우에는 다음 태스크를 수행하십시오. {{site.data.keyword.IBM_notm}} Marketplace의 인스턴스에서 {{site.data.keyword.cloud_notm}}의 인스턴스로의 마이그레이션과 같이 한 {{site.data.keyword.knowledgestudioshort}} 인스턴스에서 다른 인스턴스로 수동 데이터 마이그레이션을 수행해야 하는 경우에도 다음 태스크를 수행하십시오.
{: shortdesc}

_수동 데이터 마이그레이션_은 한 인스턴스에서 데이터를 백업하여 다른 인스턴스에서 복원하는 프로세스입니다. 

**참고**: {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}에서는 _작업공간_이란 용어를 사용하는 반면, {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace에서는 _프로젝트_라는 용어를 사용합니다. 기능은 동일합니다. 용어만 다를 뿐입니다. 

데이터를 백업하고 복원하려면 다음 단계를 완료하십시오. 

1. [어떤 데이터를 백업할 수 있는지 이해](#data)
1. [백업 준비](#prepare)
1. [현재 인스턴스에서 아티팩트 내보내기](#export)
1. [새 인스턴스에서 작업공간 다시 작성](#recreateproj)
1. [작업공간 데이터 복원](#restoredata)
1. [모델 복원](#restoremodels)
1. [완료되지 않은 어노테이션 작성 태스크 복원](#restoretasks)

## 백업할 수 있는 데이터
{: #data}

다음 아티팩트는 수동으로 백업하고 마이그레이션할 수 있습니다. 

- 편집 가능한 사전
- 유형 시스템
- 승인된 기준 실제값 문서 세트

다음 유형의 아티팩트는 수동으로 백업하고 마이그레이션할 수 없습니다. 

- 진행 중인 사람에 의한 어노테이션 작성 문서
- 어노테이션 작성 태스크
- 모델 및 스냅샷
- 읽기 전용 사전

## 백업 준비
{: #prepare}

데이터 백업 및 복원을 준비하려면 다음 단계를 완료하십시오. 

1. 작업공간에서 진행 중인 모든 작업을 완료하십시오. 

    - >**중요:** 진행 중인  어노테이션 작성 태스크를 완료하십시오. 어노테이션이 작성되고 판정되어 기준 실제값으로 승인 및 승격된 문서만 백업할 수 있습니다. 어노테이션 작성 작업을 완료하지 않으면 진행 중이지만 완료되지 않은 어노테이션 작성 작업 내용을 모두 잃게 됩니다. 

    - 수행할 작업을 추적하기 위해 어노테이션 작성 태스크를 작성했으나 어노테이션 작성 태스크가 시작되지 않았으며 작업공간이 복원될 때까지 이러한 태스크가 수행되지 않는 경우에는 미해결 어노테이션 작성 태스크의 목록을 작성하십시오. 가져왔으나 아직 기준 실제값에 추가되지 않은 문서 세트는 잊지 않고 기록해야 합니다. 각 문서 세트에 어노테이션을 작성하도록 지정한 사용자 또한 기록해 두십시오. 작업공간이 복원된 후 이러한 문서를 다시 업로드하고 어노테이션 작성 태스크를 다시 작성해야 합니다. 

1. 토크나이저 사용법을 이해하십시오. 

    기계 학습 모델의 경우 작업공간에서는 기본적으로 기계 학습 기반 토크나이저를 사용합니다. 사전 기반 토크나이저를 사용하고 있으며 계속 이를 사용해야 하는 특정 이유가 있는 경우에는 작업공간을 복원한 후 사전 기반 토크나이저를 사용하도록 구성할 수 있습니다. 자세한 정보는 [토크나이저](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)를 참조하십시오. 

1. 모델 리소스를 관리하십시오. 

    모델, 해당 버전 및 스냅샷 데이터는 마이그레이션할 수 없습니다. 이러한 아티팩트를 훈련하는 데 사용한 리소스(읽기 전용 사전 제외)는 마이그레이션할 수 있습니다. 따라서 마이그레이션 후에는 모델을 다시 작성할 수 있습니다. 훈련에 사용되는 리소스가 동일하므로 작성되는 모델은 마이그레이션 이전에 생성한 모델과 동일하게 작동합니다. 

    **주의**: 이미 배치된 모델이 있으며 작업공간을 백업한 후 삭제하려는 경우에는 배치에서 모델을 철회하십시오. 백업으로부터 작업공간을 복원한 후 모델을 다시 빌드하고 다시 배치할 수 있습니다. 모델 배치 취소에 대한 정보는 [기계 학습 모델 배치 취소](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) 및 [규칙 기반 모델 배치 취소](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)를 참조하십시오. 

    **배치에서 모델을 철회하지 못하면 _고아_ 배치 모델이 발생합니다. 고아 배치 모델은 계속해서 월별 청구 요금에 추가 요금을 발생시킵니다. **

1. 읽기 전용 사전 정보를 관리하십시오. 

    읽기 전용 사전은 마이그레이션할 수 없습니다. 마이그레이션 후 다시 업로드할 수 있도록 읽기 전용 사전을 가져온 소스 위치를 파악하십시오. 

1. 현재 사용자 역할의 목록을 작성하십시오. 

    **참고**: 이 단계는 선택사항입니다. 이는 인스턴스 간에 작업공간이 마이그레이션되며 새 작업공간이 원본 작업공간과 동일해야 하는 경우 일반적으로 수행됩니다. 새 작업공간으로 작업공간 데이터만 마이그레이션하려는 경우에는 이 단계를 건너뛸 수 있습니다. 

    서로 다른 인스턴스 간에 작업공간을 마이그레이션하는 경우에는 백업하는 인스턴스의 사용자 및 해당 역할의 목록을 작성하는 것을 고려하십시오. Admin 역할의 사용자는 User Account Management 페이지에서 이 목록을 인쇄할 수 있습니다. 새 인스턴스에서 작업공간이 다시 작성되고 나면 Admin 역할의 사용자가 사용자를 추가하고 해당 역할을 지정해야 합니다. 

    역할에 대한 자세한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오. 

1. 작업공간 정보를 기록해 두십시오. 

    현재 인스턴스에 대한 액세스 권한이 있는 동안, 마이그레이션할 각 작업공간에 대해 다음 정보를 기록해 두십시오. 
    - 작업공간 이름
    - 작업공간 설명
    - 작업공간 소유자
    - 언어
    - 완료되지 않은 어노테이션 작성 태스크가 있는 경우 이들은 백업하거나 마이그레이션할 수 없으므로 작업공간에서 이러한 완료되지 않은 태스크에 지정된 사람 어노테이터를 기록해 두십시오. 태스크 이름, 마감 날짜, 문서 세트와 사용자 간의 지정 관계 등과 같은 어노테이션 작성 태스크 세부사항 또한 기록해 두십시오. 

## 아티팩트 다운로드
{: #export}

마이그레이션할 각 작업공간에 대해 다음 아티팩트를 다운로드하십시오. 나중에 새 인스턴스에 업로드할 수 있는 안전한 위치에 이를 저장하십시오. 

- 유형 시스템
- 사전

  **참고**: 편집 가능한 사전만 다운로드할 수 있습니다. 읽기 전용 사전은 다운로드할 수 없습니다. 

- 문서

  새 작업공간으로 가져올 수 있도록 이러한 아티팩트를 다운로드하는 방법에 대한 정보는 [다른 작업공간의 리소스 업로드](/docs/services/watson-knowledge-studio/exportimport.html)를 참조하십시오. 

## 작업공간 다시 작성
{: #recreateproj}

**참고**: 이 단계에서, 원본(다운로드된) 작업공간의 설정과 일치해야 하는 설정은 언어뿐입니다. 나머지 설정은 원본 작업공간의 설정과 달라도 됩니다. 

이전 인스턴스에서 새 인스턴스로 다음 정보를 복사하여 각 작업공간을 다시 작성하십시오. 

- 작업공간 이름
- 작업공간 설명
- 문서의 언어(이 설정은 원본 작업공간의 설정과 일치해야 함)
- 이전에 사전 기반 토크나이저를 사용했으며 이를 계속해서 사용해야 하는 타당한 이유가 있는 경우에는 작업공간을 작성할 때 기본 토크나이저 대신 사전 기반 토크나이저를 사용할 것임을 지정해야 합니다. 옵션에 대한 자세한 정보는 [토크나이저](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)를 참조하십시오. 

  사전 기반 토크나이저를 사용하려면 Create Workspace 창의 Advanced Options 섹션({{site.data.keyword.IBM_notm}} Marketplace의 경우에는 Create Workspace 창)을 펼치고 토크나이저 설정을 변경하십시오. 

## 작업공간 데이터 복원
{: #restoredata}

작업공간을 다시 작성한 후에는 이전에 다운로드한 아티팩트를 업로드하십시오. 

1. 이전에 작성한 유형 시스템 백업으로부터 유형 시스템을 업로드하십시오.
   세부사항은 [다른 작업공간의 리소스 업로드](/docs/services/watson-knowledge-studio/exportimport.html)를 참조하십시오. 

  **참고**: 백업한 작업공간에서 이동하는 다른 아티팩트를 업로드하려면 먼저 유형 시스템을 업로드해야 합니다. 

1. 이전에 작성된 사전 백업에서 사전을 업로드하십시오.
   세부사항은 [다른 작업공간의 리소스 업로드](/docs/services/watson-knowledge-studio/exportimport.html)를 참조하십시오. 

  이전 작업공간 버전에서 읽기 전용 사전을 사용한 경우에는 원본 소스에서 이 작업공간으로 이러한 사전을 다시 업로드하십시오. 

  **참고**: 사전을 추가하면 사전 프리어노테이터(pre-annotator)가 자동으로 작성됩니다. 사용자는 이러한 프리어노테이터를 실행할 때 사전을 엔티티 유형과 연관시킵니다. 

1. 이전 작업공간 버전에서 다운로드한 문서를 이 작업공간 버전으로 업로드하십시오.
   세부사항은 [다른 작업공간의 리소스 업로드](/docs/services/watson-knowledge-studio/exportimport.html)를 참조하십시오. 

## 모델 복원
{: #restoremodels}

이 시점에서는 이전(백업된) 작업공간 버전에서 모델을 훈련하는 데 사용된 모든 아티팩트를 이 새 인스턴스에서 사용할 수 있습니다. 

이전 인스턴스에서 배치했던 기계 학습 모델을 다시 배치하려면 다음 단계를 완료하십시오. 

1. 기계 학습 모델을 훈련시키십시오. 세부사항은 [기계 학습 모델 작성](/docs/services/watson-knowledge-studio/train-ml.html)을 참조하십시오. 

  **참고**: 이 작업공간으로 마이그레이션한, 어노테이션이 작성된 문서에 대해 프리어노테이터를 실행하지 마십시오. 이렇게 하면 사람 어노테이터가 추가한 어노테이션을 잃게 됩니다. 

1. 모델을 작성한 후에는 이를 다시 배치하십시오. 세부사항은 [기계 학습 모델 사용](/docs/services/watson-knowledge-studio/publish-ml.html)을 참조하십시오. 

이전 인스턴스에서 배치했던 규칙 기반 모델을 다시 배치하려면 다음 단계를 완료하십시오. 

1. [규칙 기반 모델을 작성하십시오](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html). 
1. [규칙 기반 모델을 배치하십시오](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html). 

## 완료되지 않은 어노테이션 작성 태스크 복원
{: #restoretasks}

이전 작업공간에서 작성되었으나 완료되지 않은 어노테이션 작성 태스크가 있는 경우에는 다음 단계를 완료하여 완료되지 않은 어노테이션 작성 태스크를 다시 작성하십시오. 

1. 아직 어노테이션이 작성되지 않았으나 모델을 계속 개선하기 위해 기준 실제값에 추가하려는 문서를 업로드하십시오. 
1. 새로 가져왔으며 어노테이션을 작성하지 않은 문서로부터 어노테이션을 위한 문서 세트를 작성하십시오. 이러한 세트는 이제 _어노테이션 세트_라고 합니다. 세부사항은 [어노테이션 세트 작성 및 지정](/docs/services/watson-knowledge-studio/document-for-annotation.html)을 참조하십시오. 
1. 어노테이션 작성 태스크를 다시 작성하십시오. 이러한 태스크에 동일한 이름 및 적절한 마감 날짜를 지정하고, 어노테이션 세트를 적절한 사람 어노테이터에게 지정하십시오. 
