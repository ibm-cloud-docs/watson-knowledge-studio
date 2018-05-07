---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-14"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# IBM Cloud로 마이그레이션
{: #migrate}

IBM은 2017년 12월 18일 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}를 출시했으며, 이와 함께 {{site.data.keyword.IBM_notm}} Marketplace에서 {{site.data.keyword.cloud_notm}}로 모든 {{site.data.keyword.knowledgestudioshort}} 인스턴스를 마이그레이션하는 프로세스가 시작되었습니다.
{: shortdesc}

**참고**: {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}에서는 _작업공간_이란 용어를 사용하는 반면, {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace에서는 _프로젝트_라는 용어를 사용합니다. 기능은 동일합니다. 용어만 다를 뿐입니다. 

## 프로세스 및 스케줄
{: #process}

{{site.data.keyword.knowledgestudioshort}} 프로젝트의 마이그레이션 프로세스 및 스케줄은 다음 표에 표시되어 있는 바와 같이 현재 [{{site.data.keyword.IBM_notm}} Marketplace 상의 가격 책정 플랜 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} 및 계정 유형에 따라 달라집니다. 

| 플랜 및 계정 | 마이그레이션 프로세스 | 마이그레이션 스케줄 |
|------|-------------------|--------------------|
| 무료 사용제 | 고객이 인스턴스 및 데이터를 마이그레이션합니다. | 2018년 2월 1일까지 마이그레이션을 완료해야 합니다. 2018년 2월 2일에는 연관된 프로젝트 데이터를 포함, {{site.data.keyword.IBM_notm}} Marketplace 상의 모든 무료 사용제가 영구 제거됩니다. |
| 종량과금제 계정 사용 표준 플랜 | 고객이 인스턴스 및 데이터를 마이그레이션합니다. | 2018년 6월 29일까지 마이그레이션을 완료해야 합니다. 2018년 6월 30일에는 연관된 프로젝트 데이터를 포함, {{site.data.keyword.IBM_notm}} Marketplace 상의 모든 종량과금제 계정 사용 표준 플랜이 영구 제거됩니다. | 계약 중인 표준 플랜 | 고객이 인스턴스 및 데이터를 마이그레이션합니다. {{site.data.keyword.IBM_notm}}이 계약을 갱신합니다. | 2018년 6월 29일까지 마이그레이션을 완료해야 합니다. {{site.data.keyword.IBM_notm}} 지정 계정 담당자 또는 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. |
| 계약 중인 프리미엄 플랜 | {{site.data.keyword.IBM_notm}}에서 인스턴스 및 데이터를 마이그레이션합니다. {{site.data.keyword.IBM_notm}}이 계약을 갱신합니다. | 2018년 6월 29일까지 마이그레이션을 완료해야 합니다. {{site.data.keyword.IBM_notm}} 지정 계정 담당자 또는 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. |
{: caption="표 1. {{site.data.keyword.IBM_notm}} Marketplace에서 {{site.data.keyword.cloud_notm}}로의 {{site.data.keyword.knowledgestudioshort}} 마이그레이션 프로세스 및 스케줄" caption-side="top"}

## 무료 사용제 마이그레이션
{: migratefree}

{{site.data.keyword.knowledgestudioshort}} 무료 사용제를 보유하고 있는 경우에는 {{site.data.keyword.IBM_notm}} Marketplace에서 {{site.data.keyword.cloud_notm}}로 인스턴스 및 프로젝트를 마이그레이션하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.cloud_notm}} 계정이 없는 경우에는 {{site.data.keyword.IBM_notm}} Marketplace의 {{site.data.keyword.ibmid}}를 사용하여 [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/wks_cloud){: new_window}에 가입하십시오. 

   {{site.data.keyword.ibmid}}는 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace에 로그인하는 데 사용하는 ID입니다. 

1. [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/dashboard/apps/){: new_window}에 로그인하십시오. 
1. {{site.data.keyword.cloud_notm}}에 {{site.data.keyword.knowledgestudioshort}} 인스턴스가 없는 경우에는 [{{site.data.keyword.cloud_notm}} 카탈로그 {{site.data.keyword.knowledgestudioshort}} 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}에서 이를 작성하십시오. 
1. [백업 및 복원](/docs/services/watson-knowledge-studio/backup-restore.html) 프로세스에 따라 {{site.data.keyword.IBM_notm}} Marketplace 인스턴스에서 {{site.data.keyword.cloud_notm}}의 인스턴스로 프로젝트를 수동으로 마이그레이션하십시오. 

  **참고**: 이미 배치된 모델이 있으며 작업공간을 백업한 후 삭제하려는 경우에는 배치에서 모델을 철회하십시오. 백업으로부터 작업공간을 복원한 후 모델을 다시 빌드하고 다시 배치할 수 있습니다. 모델 배치 취소에 대한 정보는 [기계 학습 모델 배치 취소](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) 및 [규칙 기반 모델 배치 취소](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)를 참조하십시오. 

## 종량과금제 계정의 표준 플랜 마이그레이션
{: migratepaygo}

표준 플랜 및 [종량과금제 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/pricing/billable.html){: new_window} 계정을 보유하고 있는 경우에는 {{site.data.keyword.IBM_notm}} Marketplace에서 {{site.data.keyword.cloud_notm}}로 인스턴스 및 프로젝트를 마이그레이션하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.cloud_notm}} 계정이 없는 경우에는 {{site.data.keyword.IBM_notm}} Marketplace의 {{site.data.keyword.ibmid}}를 사용하여 [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/){: new_window}에 가입하십시오. 

   {{site.data.keyword.ibmid}}는 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace에 로그인하는 데 사용하는 ID입니다. 

1. [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/dashboard/apps/){: new_window}에 로그인하십시오. 
1. {{site.data.keyword.cloud_notm}}에 {{site.data.keyword.knowledgestudioshort}} 인스턴스가 없는 경우에는 [{{site.data.keyword.cloud_notm}} 카탈로그 {{site.data.keyword.knowledgestudioshort}} 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}에서 이를 작성하십시오. 
1. [백업 및 복원](/docs/services/watson-knowledge-studio/backup-restore.html) 프로세스에 따라 {{site.data.keyword.IBM_notm}} Marketplace 인스턴스에서 {{site.data.keyword.cloud_notm}}의 인스턴스로 프로젝트를 수동으로 마이그레이션하십시오. 

  **참고**: 이미 배치된 모델이 있으며 작업공간을 백업한 후 삭제하려는 경우에는 배치에서 모델을 철회하십시오. 백업으로부터 작업공간을 복원한 후 모델을 다시 빌드하고 다시 배치할 수 있습니다. 모델 배치 취소에 대한 정보는 [기계 학습 모델 배치 취소](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) 및 [규칙 기반 모델 배치 취소](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)를 참조하십시오. 

## 계약 계정의 표준 플랜 마이그레이션
{: migratecontract}

계약 중인 {{site.data.keyword.knowledgestudioshort}} 표준 플랜을 보유하고 있는 경우에는 계약을 갱신하고 {{site.data.keyword.IBM_notm}} Marketplace에서 {{site.data.keyword.cloud_notm}}로 인스턴스 및 프로젝트를 마이그레이션하려면 다음 단계를 완료하십시오. 

1. 계약을 갱신하려면 {{site.data.keyword.IBM_notm}} 지정 계정 담당자 또는 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. 
1. {{site.data.keyword.cloud_notm}}에서 계약을 갱신한 후 [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/dashboard/apps/){: new_window}에 로그인하십시오. 
1. {{site.data.keyword.cloud_notm}}에 {{site.data.keyword.knowledgestudioshort}} 인스턴스가 없는 경우에는 [{{site.data.keyword.cloud_notm}} 카탈로그 {{site.data.keyword.knowledgestudioshort}} 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}에서 이를 작성하십시오. 
1. [백업 및 복원](/docs/services/watson-knowledge-studio/backup-restore.html) 프로세스에 따라 {{site.data.keyword.IBM_notm}} Marketplace 인스턴스에서 {{site.data.keyword.cloud_notm}}의 인스턴스로 프로젝트를 수동으로 마이그레이션하십시오. 

  **참고**: 이미 배치된 모델이 있으며 작업공간을 백업한 후 삭제하려는 경우에는 배치에서 모델을 철회하십시오. 백업으로부터 작업공간을 복원한 후 모델을 다시 빌드하고 다시 배치할 수 있습니다. 모델 배치 취소에 대한 정보는 [기계 학습 모델 배치 취소](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) 및 [규칙 기반 모델 배치 취소](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)를 참조하십시오. 

## 계약 계정의 프리미엄 플랜 마이그레이션
{: migratecontract}

계약 중인 {{site.data.keyword.knowledgestudioshort}} 프리미엄 플랜이 있는 경우에는 {{site.data.keyword.IBM_notm}} 지정 계정 담당자 또는 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. 계약이 {{site.data.keyword.cloud_notm}}에서 갱신되면 사용자와 {{site.data.keyword.cloud_notm}} 간의 협상을 통해 정해지는 스케줄에 따라 IBM에서 데이터를 마이그레이션합니다. 
