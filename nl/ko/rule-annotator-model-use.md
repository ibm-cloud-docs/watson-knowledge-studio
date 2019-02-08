---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}하십시오.
{: tip}

# 규칙 기반 모델 사용
{: #wks_rule_publish}

{{site.data.keyword.knowledgestudioshort}}로 작성한 규칙 기반 모델을 기타 {{site.data.keyword.watson}} 애플리케이션이 사용할 수 있도록 함으로써 모델을 활용하십시오.
{: shortdesc}

**주의**: 규칙 기반 모델은 이러한 서비스에서 [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 기능으로 사용할 수 있도록 배치할 수 있습니다.

특정 서비스가 모델을 사용할 수 있도록 배치하려면 먼저 해당 서비스에 대한 구독을 보유해야 합니다. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 서비스는 {{site.data.keyword.IBM_notm}}용 클라우드 플랫폼인 {{site.data.keyword.Bluemix_notm}}에서 호스팅됩니다. 이 플랫폼에 대한 자세한 정보는 [{{site.data.keyword.Bluemix_notm}}의 개념 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}을 참조하십시오. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 서비스 중 하나를 구독하려면 [{{site.data.keyword.Bluemix_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/){: new_window} 웹 사이트에서 계정을 작성하십시오.

일부 서비스의 경우에는 {{site.data.keyword.Bluemix_notm}} 영역 이름 및 서비스 인스턴스 이름과 같이 모델을 배치할 서비스 인스턴스의 세부사항을 알아야 합니다. 영역 및 인스턴스 이름 정보는 {{site.data.keyword.Bluemix_notm}} 서비스 페이지에 있습니다.

규칙 기반 모델을 사용하여 새 문서에 어노테이션 미리 작성을 수행할 수도 있습니다. 세부사항은 [규칙 기반 모델을 사용하여 문서에 어노테이션 미리 작성 수행](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)을 참조하십시오.

## 규칙 기반 모델을 IBM Watson Discovery에 배치
{: #wks_rule_discovery}

모델을 배치하여 {{site.data.keyword.discoveryshort}} 서비스를 사용하는 애플리케이션이 규칙 기반 모델을 사용해 문서 인리치먼트 중에 엔티티를 찾고 추출할 수 있도록 하십시오.

**주의**: 이는 현재 서비스의 [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 기능입니다.

### 시작하기 전에
{: #wks_rule_discovery_prereqs}

{{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} 서비스 인스턴스에 대한 관리 액세스 권한이 있어야 하며, 이와 연관된 {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스 이름을 알고 있어야 합니다.

### 프로시저
{: #wks_rule_discovery_procedure}

규칙 기반 모델을 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}에 배치하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Rule-based Model** > **Versions** > **Rule-based Model** 탭을 선택하십시오. 
1. 배치할 모델의 버전을 선택하십시오.

    모델의 작동하는 버전이 하나뿐인 경우에는 **Save for Deployment**를 클릭하여 현재 모델을 배치를 위해 저장하십시오. 이는 모델을 버전화하며, 이렇게 하면 현재 버전과 동일한 버전을 배치한 채로 현재 버전을 계속해서 개선할 수 있습니다. 버전 저장에는 몇 분 정도 소요됩니다. 버전을 작성해야 배치 옵션이 표시됩니다.

    **참고**: 각 버전은 하나의 서비스 인스턴스에만 배치될 수 있습니다. 둘 이상의 인스턴스에 동일한 모델을 배치하려면 각 인스턴스에 대한 버전을 작성하십시오.

1. **Deploy**를 클릭하고 {{site.data.keyword.discoveryshort}}에 배치하도록 선택한 후 **Next**를 클릭하십시오.
1. {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스를 제공하십시오. 필요한 경우에는 다른 지역을 선택하십시오.
1. **Deploy**를 클릭하십시오.
1. 배치 프로세스에는 몇 분 정도 소요됩니다. 배치 상태를 확인하려면 **Versions** 탭에서 배치한 버전 옆에 있는 **Status**를 클릭하십시오.

    모델이 여전히 배치 중인 경우에는 상태가 "publishing"으로 표시됩니다. 배치가 완료된 후, 배치가 성공한 경우에는 상태가 "available"로, 문제점이 발생한 경우에는 "error"로 변경됩니다.

    모델이 사용 가능한 상태가 되면 모델 ID(model_id)를 기록해 두십시오. 서비스가 사용자 정의 모델을 사용할 수 있도록 설정하려면 {{site.data.keyword.discoveryshort}} 서비스에 이 ID를 제공해야 합니다.

### 다음에 수행할 작업
{: #wks_rule_discovery_next}

배치된 모델을 사용하려면 {{site.data.keyword.discoveryshort}} 서비스 인리치먼트 구성 프로세스 중에 요청되는 모델 ID를 제공해야 합니다.

## 규칙 기반 모델을 IBM Watson Natural Language Understanding에 배치
{: #wks_rule_nlu}

규칙 기반 모델을 배치하여 {{site.data.keyword.nlushort}} 서비스를 사용하는 애플리케이션이 모델을 사용해 도메인과 관련된 엔티티를 찾고 추출할 수 있도록 하십시오.

**주의**: 이는 현재 서비스의 [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 기능입니다.

### 시작하기 전에
{: #wks_rule_prereqs}

{{site.data.keyword.nlushort}} 서비스 인스턴스에 대한 관리 액세스 권한이 있어야 하며, 이와 연관된 {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스 이름을 알고 있어야 합니다.

### 프로시저
{: #wks_rule_procedure}

규칙 기반 모델을 {{site.data.keyword.nlushort}}에 배치하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Rule-based Model** > **Versions** > **Rule-based Model** 탭을 선택하십시오. 
1. 배치할 모델의 버전을 선택하십시오.

    모델의 작동하는 버전이 하나뿐인 경우에는 **Save for Deployment**를 클릭하여 현재 모델을 배치를 위해 저장하십시오. 이는 모델을 버전화하며, 이렇게 하면 현재 버전과 동일한 버전을 배치한 채로 현재 버전을 계속해서 개선할 수 있습니다. 버전 저장에는 몇 분 정도 소요됩니다. 버전을 작성해야 배치 옵션이 표시됩니다.

    **참고**: 각 버전은 하나의 서비스 인스턴스에만 배치될 수 있습니다. 둘 이상의 인스턴스에 동일한 모델을 배치하려면 각 인스턴스에 대한 버전을 작성하십시오.

1. **Deploy**를 클릭하고 {{site.data.keyword.nlushort}}에 배치하도록 선택한 후 **Next**를 클릭하십시오.
1. {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스를 제공하십시오. 필요한 경우에는 다른 지역을 선택하십시오.
1. **Deploy**를 클릭하십시오.
1. 배치 프로세스에는 몇 분 정도 소요됩니다. 배치 상태를 확인하려면 **Versions** 탭에서 배치한 버전 옆에 있는 **Status**를 클릭하십시오.

    모델이 여전히 배치 중인 경우에는 상태가 "publishing"으로 표시됩니다. 배치가 완료된 후, 배치가 성공한 경우에는 상태가 "available"로, 문제점이 발생한 경우에는 "error"로 변경됩니다.

    모델이 사용 가능한 상태가 되면 모델 ID(model_id)를 기록해 두십시오. 서비스가 사용자 정의 모델을 사용할 수 있도록 설정하려면 {{site.data.keyword.nlushort}} 서비스에 이 ID를 제공해야 합니다.

### 다음에 수행할 작업
{: #wks_rule_next}

배치된 모델을 사용하려면 `entities.model` 매개변수에 사용자 정의 모델의 모델 ID를 지정해야 합니다.

모델을 {{site.data.keyword.nlushort}} `GET /analyze` 요청과 함께 사용하여 엔티티를 추출할 수 있습니다.

[{{site.data.keyword.nlushort}} 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/natural-language-understanding/index.html){: new_window}를 참조하십시오.

## 모델 배치 취소
{: #undeploy-view-model}

모델을 배치 취소하거나 모델 ID를 찾으려는 경우에는 **Deployed Models** 페이지를 보십시오.

### 이 태스크에 대한 정보
{: #wks_undeploy_about}

배치된 모델 페이지에서 보는 내용은 {{site.data.keyword.knowledgestudioshort}} 인스턴스를 호스팅하는 [지역 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/resources/services_region.html){: new_window}에 따라 다릅니다. 해당 지역에서 [IAM ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/iam/users_roles.html){: new_window} 및 [Cloud Foundry ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/iam/cfaccess.html){: new_window} 액세스 관리 방법으로 관리되는 인스턴스를 지원하는 경우에는 각 방법마다 탭이 표시됩니다. IAM에 의해 관리되는 인스턴스의 모델은 **Resource Groups** 탭에 나열되어 있습니다. Cloud Foundry에 의해 관리되는 인스턴스의 모델은 **Organizations** 탭에 나열되어 있습니다. 

해당 지역에서 액세스 관리 방법 중 하나로만 관리되는 인스턴스를 지원하면 하나의 액세스 관리 방법만 적용되므로 하나의 모델 목록만 표시됩니다. 

### 프로시저
{: #wks_deploy_procedure}

모델을 배치 취소하거나 모델 ID를 찾으려면 다음 작업을 수행하십시오.

1. {{site.data.keyword.knowledgestudioshort}}를 시작하십시오.
1. 오른쪽 상단 메뉴 표시줄의 **Settings** 메뉴에서 **Manage deployed models**를 선택하십시오.
1. 배치된 모델의 목록에서 보거나 배치 취소할 모델을 찾으십시오.
1. 모델을 배치 취소하려면 해당 행의 마지막 열에서 **Undeploy model**을 클릭하십시오.
1. 모델 ID를 찾으려면 **Model ID** 열을 보십시오.

또는 규칙 기반 모델 및 기계 학습 모델의 버전 페이지에서 모델의 배치를 취소할 수 있습니다. 

## IBM Watson Explorer에서의 규칙 기반 모델 활용
{: #wks_rule_export}

규칙 기반 모델을 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 사용할 수 있도록 규칙 기반 모델이 작성되면 작성되는 PEAR 파일을 내보내십시오.

### 프로시저
{: #wks_rule_export_procedure}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 규칙 기반 모델을 활용하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Rule-based Model** > **Versions** > **Rule-based Model** 탭을 선택하십시오. 
1. **Export current model**을 클릭하십시오.

    라이트 플랜 구독을 보유하고 있는 경우에는 내보내기 옵션을 사용할 수 없습니다. 

    모델이 PEAR 파일로 저장되며 이 파일을 다운로드할지 묻는 프롬프트가 표시됩니다. PEAR(Processing Engine ARchive) 파일은 UIMA 컴포넌트에 대한 UIMA 표준 패키징 형식입니다. 모델은 분배되어 UIMA 애플리케이션 내에서 다시 사용할 수 있도록 PEAR 형식으로 저장됩니다.

1. 이 파일을 로컬 시스템에 다운로드하십시오.
1. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 애플리케이션에서 PEAR 파일을 가져오십시오.
