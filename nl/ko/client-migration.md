---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/knowledge-studio/client-migration.html){: new_window}하십시오.
{: tip}

# IBM Cloud로 마이그레이션
{: #migrate}

2017년 12월 18일, IBM은 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}를 출시했습니다. 이는 {{site.data.keyword.IBM_notm}} Marketplace의 모든 {{site.data.keyword.knowledgestudioshort}} 인스턴스를 [{{site.data.keyword.cloud_notm}} 플랫폼 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}으로 마이그레이션하는 프로세스의 시작을 알려줍니다.
{: shortdesc}

**참고**: {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}에서는 _작업공간_이란 용어를 사용하는 반면, {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace에서는 _프로젝트_라는 용어를 사용합니다. 기능은 동일합니다. 용어만 다를 뿐입니다.

**주의**: GDPR을 준수해야 하는 경우에는 {{site.data.keyword.cloud_notm}} 플랫폼으로 마이그레이션해야 합니다. {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace는 더 이상 사용되지 않으며, 유럽 연합(European Union)의 일반 개인정보 보호법률(General Data Protection Regulation) (EU) 2016/679를 준수해야 하는 고객에는 적합하지 않습니다. 

## 프로세스
{: #process}

{{site.data.keyword.knowledgestudioshort}} 프로젝트의 마이그레이션 프로세스는 다음 표에 표시된 대로 {{site.data.keyword.IBM_notm}} Marketplace 구독에 따라 결정됩니다. 

|구독|마이그레이션 프로세스 |세부사항|
|------|-------------------|--------------------|
| 셀프 서비스 구독의 표준 플랜 |고객이 인스턴스 및 데이터를 마이그레이션합니다. |{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}의 최신 버전에 액세스할 수 있도록 가급적 빨리 마이그레이션합니다.
|구독 계약의 표준 플랜| {{site.data.keyword.IBM_notm}}이 구독 계약을 마이그레이션합니다. 고객이 인스턴스 및 데이터를 마이그레이션합니다. |{{site.data.keyword.IBM_notm}} 지정 계정 담당자 또는 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. |
|구독 계약의 프리미엄 플랜 | {{site.data.keyword.IBM_notm}}이 구독 계약을 마이그레이션합니다. {{site.data.keyword.IBM_notm}}이 인스턴스 및 데이터를 마이그레이션합니다. |{{site.data.keyword.IBM_notm}} 지정 계정 담당자 또는 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. |
{: caption="표 1. {{site.data.keyword.IBM_notm}} Marketplace에서 {{site.data.keyword.cloud_notm}}로의 {{site.data.keyword.knowledgestudioshort}} 마이그레이션 프로세스 및 스케줄" caption-side="top"}

## 표준 플랜 인스턴스의 자체 마이그레이션
{: migratestandard}

표준 플랜을 보유 중인 경우에는 다음 단계를 완료하여 {{site.data.keyword.IBM_notm}} Marketplace의 인스턴스를 {{site.data.keyword.cloud_notm}}로 마이그레이션하십시오. 

1. {{site.data.keyword.cloud_notm}} 계정이 없는 경우에는 {{site.data.keyword.IBM_notm}} Marketplace의 {{site.data.keyword.ibmid}}를 사용하여 [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/registration/){: new_window}에 가입하십시오.

   {{site.data.keyword.ibmid}}는 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace에 로그인하는 데 사용하는 ID입니다.

2. [{{site.data.keyword.cloud_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}){: new_window}에 로그인하십시오.
3. {{site.data.keyword.cloud_notm}} 계정이 라이트 계정이면 유료 계정으로 업그레이드하십시오. 유료 계정의 유형에 대한 자세한 정보는 [계정 유형 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/account/index.html){: new_window}을 참조하십시오. 
4. [{{site.data.keyword.cloud_notm}} 콘솔 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/knowledge-studio){: new_window}에서 {{site.data.keyword.knowledgestudioshort}} 표준 플랜을 작성하십시오. 
5. {{site.data.keyword.IBM_notm}} Marketplace의 인스턴스를 {{site.data.keyword.cloud_notm}}로 마이그레이션하고자 함을 표시하여 화면의 지시사항을 따르십시오. 
6. 마이그레이션할 프로세스가 2개 이상이면 해당 프로세스를 반복하십시오.

## 프리미엄 플랜 인스턴스의 마이그레이션
{: migratesubscription}

{{site.data.keyword.knowledgestudioshort}} 프리미엄 플랜이 있는 경우에는 {{site.data.keyword.IBM_notm}} 지정 계정 담당자에게 문의하거나 [{{site.data.keyword.cloud_notm}} 영업 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)에 문의하십시오. 일단 구독이 {{site.data.keyword.cloud_notm}}로 마이그레이션되면, 사용자와 {{site.data.keyword.IBM_notm}} 간의 협의된 스케줄에 따라 IBM에서 사용자의 데이터를 마이그레이션합니다. 
