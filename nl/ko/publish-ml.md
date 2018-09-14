---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}하십시오.
{: tip}

# 기계 학습 모델 사용
{: #publish-ml}

{{site.data.keyword.knowledgestudioshort}}로 훈련시킨 기계 학습 모델을 기타 {{site.data.keyword.watson}} 애플리케이션이 사용할 수 있도록 함으로써 모델을 활용하십시오.
{: shortdesc}

기계 학습 모델은 배치하거나 내보낼 수 있습니다. 사전 또는 {{site.data.keyword.nlushort}} 프리어노테이터(pre-annotator)는 {{site.data.keyword.knowledgestudioshort}} 내의 문서에 어노테이션 미리 작성을 수행하는 데만 사용할 수 있습니다.

특정 서비스가 모델을 사용할 수 있도록 배치하려면 먼저 해당 서비스에 대한 구독을 보유해야 합니다. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 서비스는 {{site.data.keyword.IBM_notm}}용 클라우드 플랫폼인 {{site.data.keyword.Bluemix_short}}에서 호스팅됩니다. 이 플랫폼에 대한 자세한 정보는 [{{site.data.keyword.Bluemix_notm}}의 개념 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}을 참조하십시오. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 서비스 중 하나를 구독하려면 [{{site.data.keyword.Bluemix_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/){: new_window} 웹 사이트에서 계정을 작성하십시오.

일부 서비스의 경우에는 {{site.data.keyword.Bluemix_notm}} 영역 이름 및 서비스 인스턴스 이름과 같이 모델을 배치할 서비스 인스턴스의 세부사항을 알아야 합니다. 영역 및 인스턴스 이름 정보는 {{site.data.keyword.Bluemix_notm}} 서비스 페이지에 있습니다.

기계 학습 모델을 사용하여 새 문서에 어노테이션 미리 작성을 수행할 수도 있습니다. 세부사항은 [기계 학습 모델을 사용하여 문서에 어노테이션 미리 작성 수행](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire)을 참조하십시오. 

## 기계 학습 모델을 IBM Watson Discovery에 배치
{: #wks_madiscovery}

모델 성능이 만족스러운 경우에는 해당 모델의 버전을 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}에 배치할 수 있습니다. 이 기능은 애플리케이션이 배치된 기계 학습 모델을 사용하여 도메인과 관련된 개념 및 관계 인식을 포함시킴으로써 데이터로부터 얻는 인사이트를 더욱 풍부하게 할 수 있게 해 줍니다.

### 시작하기 전에
{: #wks_madiscovery_prereqs}

{{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} 서비스 인스턴스에 대한 관리 액세스 권한이 있어야 하며, 이와 연관된 {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스 이름을 알고 있어야 합니다.

### 이 태스크에 대한 정보
{: #wks_madiscovery_about}

기계 학습 모델을 배치할 때는 배치할 버전을 선택합니다.

### 프로시저
{: #wks_madiscovery_procedure}

기계 학습 모델을 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}에 배치하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Machine Learning Model** > **Versions**를 선택하십시오. 
1. 배치할 모델의 버전을 선택하십시오.

    모델의 작동하는 버전이 하나뿐인 경우에는 현재 모델의 스냅샷을 작성하십시오. 이는 모델을 버전화하며, 이렇게 하면 현재 버전과 동일한 버전을 배치한 채로 현재 버전을 계속해서 개선할 수 있습니다. 하나 이상의 버전을 작성해야 배치 옵션이 표시됩니다.

    **참고**: 각 버전은 하나의 서비스 인스턴스에만 배치될 수 있습니다. 둘 이상의 인스턴스에 동일한 모델을 배치하려면 각 인스턴스에 대한 버전을 작성하십시오.

1. **Deploy**를 클릭하고 {{site.data.keyword.discoveryshort}}에 배치하도록 선택한 후 **Next**를 클릭하십시오.
1. {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스를 선택하십시오. 필요한 경우에는 다른 지역을 선택하십시오.
1. **Deploy**를 클릭하십시오.
1. 배치 프로세스에는 몇 분 정도 소요됩니다. 배치 상태를 확인하려면 **Versions** 탭에서 배치한 버전 옆에 있는 **Status**를 클릭하십시오.

    모델이 여전히 배치 중인 경우에는 상태가 "publishing"으로 표시됩니다. 배치가 완료된 후, 배치가 성공한 경우에는 상태가 "available"로, 문제점이 발생한 경우에는 "error"로 변경됩니다.

    모델이 사용 가능한 상태가 되면 모델 ID(model_id)를 기록해 두십시오. 서비스가 사용자 정의 모델을 사용할 수 있도록 설정하려면 {{site.data.keyword.discoveryshort}} 서비스에 이 ID를 제공해야 합니다.

### 다음에 수행할 작업
{: #wks_madiscovery_next}

배치된 모델을 사용하려면 {{site.data.keyword.discoveryshort}} 서비스 인리치먼트 구성 프로세스 중에 요청되는 모델 ID를 제공해야 합니다. 세부사항은 [{{site.data.keyword.discoveryshort}} 서비스 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/discovery/integrate-wks.html){: new_window}를 참조하십시오.

## 기계 학습 모델을 IBM Watson Natural Language Understanding에 배치
{: #wks_manlu}

모델 성능이 만족스러운 경우에는 해당 모델의 버전을 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}에 배치할 수 있습니다. 이 기능은 애플리케이션이 배치된 기계 학습 모델을 사용하여 엔티티 및 관계를 포함, 텍스트 입력의 의미 특성을 분석할 수 있게 해 줍니다.

### 시작하기 전에
{: #wks_manlu_prereqs}

모델을 배치할 {{site.data.keyword.nlushort}} 서비스를 보유하고 있어야 합니다. 서비스와 연관된 {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스 이름을 알아야 합니다. 영역 또는 인스턴스 이름이 기억나지 않는 경우에는 {{site.data.keyword.Bluemix_notm}}에 로그인하여 이를 찾으십시오. {{site.data.keyword.Bluemix_notm}} 계정이 없는 경우에는 계정에 가입하십시오.

### 이 태스크에 대한 정보
{: #wks_manlu_about}

기계 학습 모델을 배치할 때는 배치할 버전을 선택합니다.

### 프로시저
{: #wks_manlu_procedure}

기계 학습 모델을 {{site.data.keyword.nlushort}} 서비스에 배치하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Machine Learning Model** > **Versions**를 선택하십시오. 
1. 배치할 모델의 버전을 선택하십시오.

    모델의 작동하는 버전이 하나뿐인 경우에는 현재 모델의 스냅샷을 작성하십시오. 이는 모델을 버전화하며, 이렇게 하면 현재 버전과 동일한 버전을 배치한 채로 현재 버전을 계속해서 개선할 수 있습니다. 하나 이상의 버전을 작성해야 배치 옵션이 표시됩니다.

    **참고**: 각 버전은 하나의 서비스 인스턴스에만 배치될 수 있습니다. 둘 이상의 인스턴스에 동일한 모델을 배치하려면 각 인스턴스에 대한 버전을 작성하십시오.

1. **Deploy**를 클릭하고 {{site.data.keyword.nlushort}}에 배치하도록 선택한 후 **Next**를 클릭하십시오.
1. {{site.data.keyword.Bluemix_notm}} 영역 및 인스턴스를 선택하십시오. 필요한 경우에는 다른 지역을 선택하십시오.
1. **Deploy**를 클릭하십시오.
1. 배치 프로세스에는 몇 분 정도 소요됩니다. 배치 상태를 확인하려면 **Versions** 탭에서 배치한 버전 옆에 있는 **Status**를 클릭하십시오. 모델이 여전히 배치 중인 경우에는 상태가 "publishing"으로 표시됩니다. 배치가 완료된 후, 배치가 성공한 경우에는 상태가 "available"로, 문제점이 발생한 경우에는 "error"로 변경됩니다.

    모델이 사용 가능한 상태가 되면 모델 ID(model_id)를 기록해 두십시오. 서비스가 사용자 정의 모델을 사용할 수 있도록 설정하려면 {{site.data.keyword.nlushort}} 서비스에 이 ID를 제공해야 합니다.

### 다음에 수행할 작업
{: #wks_manlu_next}

배치된 모델을 사용하려면 `entities.model` 매개변수에 사용자 정의 모델의 모델 ID를 지정해야 합니다.

모델을 {{site.data.keyword.nlushort}} `GET /analyze` 요청과 함께 사용하여 다음 특성을 추출할 수 있습니다.

- **엔티티**

    다음 명령은 text 매개변수를 사용하여 전달된 문장에 있는 엔티티를 찾습니다.

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    서비스는 사용자 정의 모델에 정의된 엔티티 유형을 발견한 인스턴스의 JSON 오브젝트를 리턴합니다.

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **관계**

    다음 명령은 text 매개변수를 사용하여 전달된 문장에 있는 관계를 찾습니다.

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    서비스는 사용자 정의 모델에 정의된 관계 유형을 발견한 인스턴스의 JSON 오브젝트를 리턴합니다.

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

[{{site.data.keyword.nlushort}} 문서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window}를 참조하십시오.

## 모델 배치 취소
{: #undeploy-view-model}

모델을 배치 취소하거나 모델 ID를 찾으려는 경우에는 **Deployed Models** 페이지를 보십시오.

### 이 태스크에 대한 정보
{: #wks_undeploy_about}

배치된 모델 페이지에서 보는 내용은 {{site.data.keyword.knowledgestudioshort}} 인스턴스를 호스팅하는 [지역 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/resources/services_region.html){: new_window}에 따라 다릅니다. 해당 지역에서 [IAM ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} 및 [Cloud Foundry ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window} 액세스 관리 방법으로 관리되는 인스턴스를 지원하는 경우에는 각 방법마다 탭이 표시됩니다. IAM에 의해 관리되는 인스턴스의 모델은 **Resource Groups** 탭에 나열되어 있습니다. Cloud Foundry에 의해 관리되는 인스턴스의 모델은 **Organizations** 탭에 나열되어 있습니다. 

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

## IBM Watson Explorer에서의 기계 학습 모델 활용
{: #wks_maexport}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 사용할 수 있도록 훈련된 기계 학습 모델을 내보내십시오.

### 시작하기 전에
{: #wks_maexport_prereqs}

관계 유형을 식별하고 이에 어노테이션을 작성하려는 경우에는 둘 이상의 관계 유형을 정의하고, 모델을 내보내기 전에 기준 실제값 내 관계의 인스턴스에 어노테이션을 작성해야 합니다. 한 관계 유형만을 정의하고 어노테이션 작성하는 것은 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 릴리스 11.0.1.0에서 후속 문제를 발생시킬 수 있습니다.

### 이 태스크에 대한 정보
{: #wks_maexport_about}

이제 기계 학습 모델이 특정 도메인의 엔티티 및 관계를 인식할 수 있도록 훈련되었으므로, 이를 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 활용할 수 있습니다.

모델을 내보내어 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 사용하는 방법을 보여주는 2분 미만의 동영상을 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window}를 클릭하십시오.

### 프로시저
{: #wks_maexport_procedure}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 기계 학습 모델을 활용하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Machine Learning Model** > **Versions**를 선택하십시오. 
1. **Export current model**을 클릭하십시오.

    라이트 플랜 구독을 보유하고 있는 경우에는 내보내기 옵션을 사용할 수 없습니다. 

    모델이 ZIP 파일로 저장되며 이 파일을 다운로드할지 묻는 프롬프트가 표시됩니다.

1. 이 파일을 로컬 시스템에 다운로드하십시오.
1. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 애플리케이션에서 모델을 가져오십시오.

    그 후에는 모델을 {{site.data.keyword.watson}} Explorer Content Analytics의 기계 학습 모델에 맵핑할 수 있습니다. 맵핑 단계를 수행한 후 문서를 크롤링하면 모델이 자신이 인식하는 엔티티 및 관계의 인스턴스를 찾습니다. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer에서 모델을 가져오고 구성하는 방법을 알아보려면 통합에 대해 설명하는 기술 문서([http://www.ibm.com/support/docview.wss?uid=swg27048147 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window})를 참조하십시오.

#### 관련 태스크
{: #wks_maexport_related}

[{{site.data.keyword.watson}} Explorer Content Analytics에서 분석된 문서 내보내기](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
