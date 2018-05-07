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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/train-ml.html){: new_window}.
{: tip}

# 기계 학습 모델 훈련
{: #train-ml}

{{site.data.keyword.knowledgestudiofull}}에서, 기계 학습 모델의 작성 프로세스는 기계 학습 모델 훈련, 그리고 테스트 데이터 및 블라인드 데이터에 어노테이션 작성 시의 모델 성능에 대한 평가를 포함합니다.
{: shortdesc}

## 기계 학습 모델 작성
{: #wks_madocsets}

기계 학습 모델을 작성할 때는 모델을 훈련시키는 데 사용할 문서 세트를 선택하고 훈련 데이터, 테스트 데이터 및 블라인드 데이터로 사용될 문서의 백분율을 지정합니다. 

### 이 태스크에 대한 정보

성능 메트릭을 탐색하면 모델의 정확도를 개선할 방법을 식별할 수 있습니다. 

> **제한사항:** 기계 학습 어노테이터는 {{site.data.keyword.knowledgestudioshort}} 인스턴스당 셋만 훈련시킬 수 있습니다. 인스턴스가 여러 작업공간을 포함하며 다른 작업공간에서 훈련 중인 기계 학습 어노테이터의 수가 이미 셋인 경우에는 다른 훈련 프로세스가 완료될 때까지 작업공간의 기계 학습 모델 훈련 요청이 큐에 삽입됩니다. 

### 프로시저

기계 학습 모델을 작성하려면 다음 작업을 수행하십시오. 

1. {{site.data.keyword.knowledgestudioshort}} 관리자로 로그인하여 작업공간을 선택하십시오. 
1. **Model Management** > **Performance**를 선택하십시오. 
1. 모든 문서 세트가 승인되었으며 모든 어노테이션 충돌이 판정을 통해 해결되었는지 확인하십시오. 판정 또는 승인을 통해 기준 실제값이 된 문서만 모델을 훈련시키는 데 사용할 수 있습니다. 
1. **Train and evaluate**를 클릭하십시오. 
1. 선택사항: 문서 세트의 문서가 시스템 레벨 훈련, 테스트 또는 블라인드 세트로 사용되도록 할당되는 방식을 지정하려면 **Edit settings**를 클릭하십시오. 

    적용할 비율을 결정하는 데 도움을 받으려면 [문서 세트 관리](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata)를 참조하십시오. 

1. 선택사항: 기계 학습 모델이 훈련 중에 사용할 사전을 사전 항목의 엔티티 유형과 연관시키십시오. 

    사전 프리어노테이터(pre-annotator)를 작성한 경우에는 이 단계를 이미 수행한 것입니다. **Reuse mapping that is defined for dictionary pre-annotator**를 클릭하여 기존 맵핑을 다시 사용하거나, 새 맵핑을 정의하십시오. 

    모델은 사전 용어의 유형 정보를 훈련 중에 고려하는 많은 언어 분석 특성 중 하나로 사용합니다. 

1. **Train**을 클릭하여 모델을 훈련시키거나, **Train & Evaluate**를 클릭하여 모델을 훈련시키고, 기계 학습 모델이 추가한 어노테이션을 평가하고, 성능 통계를 분석하십시오. 

    > **중요:** 기계 학습 모델의 훈련에는 사람이 작성한 어노테이션의 수와 모든 문서의 총 단어 수에 따라 몇 분에서 몇 시간이 소요될 수 있습니다. 

1. 모델 훈련에 사용할 문서 세트를 선택하십시오. 

    > **참고:** 이러한 문서 세트는 10개 이상의 어노테이션 작성된 문서를 포함해야 합니다. 

1. 모델이 작성되면 다음 조치 중 하나를 선택하십시오. 

    <table border="1" frame="hsides" rules="rows" cellpadding="4" cellspacing="0" summary="이 표의 각 행에는 하나의 옵션이 설명되어 있습니다. " class="simpletable choicetable choicetableborder">
      <thead><tr><th id="d33883e137-option" valign="bottom" align="left" class="ncol thleft thbot">옵션</th>
          <th id="d33883e137-desc" valign="bottom" align="left" class="ncol thleft thbot">설명</th></tr></thead>
      <tbody><tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e139" class="stentry choption ncol"><p class="p wrapper"><strong>Log</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e139" class="stentry chdesc ncol"><p class="p wrapper">로그 파일이 표시되어 문제점이 발생했는지 확인할 수 있습니다. </p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e144" class="stentry choption ncol"><p class="p wrapper"><strong>Details</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e144" class="stentry chdesc ncol"><p class="p wrapper">어노테이션 성능 통계를 보고, 모델 훈련 및 테스트에 사용할
              문서 세트를 변경하고, 모델 아티팩트의 스냅샷 버전을
              작성합니다. </p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e149" class="stentry choption ncol"><p class="p wrapper"><strong>Export</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e149" class="stentry chdesc ncol"><p class="p wrapper">기계 학습 런타임 환경에서 모델을 실행하는 데 필요한
              컴포넌트를 포함하는 <code>ZIP</code> 파일을 로컬 시스템에 내보냅니다. </p></td>
        </tr>
      </tbody>
    </table>

## 모델이 추가한 어노테이션의 평가
{: #wks_matest}

사람 어노테이터가 추가한 어노테이션에 대한 기준 실제값 보기를 모델이 추가한 어노테이션과 비교할 수 있습니다. 

### 프로시저

모델이 추가한 어노테이션을 평가하려면 다음 작업을 수행하십시오. 

1. **Model Management** > **Performance** > **Train and evaluate**를 선택하십시오. Training/Test/Blind Sets 페이지가 표시됩니다. 
1. 훈련 세트 또는 테스트 세트에 대해 **View Ground Truth**를 클릭하여 어노테이션 미리 작성을 통해 추가되거나 사람 어노테이터가 추가한 어노테이션을 보십시오. 기준 실제값 편집기가 열립니다. 개별 문서를 클릭하여 열고 멘션, 관계 및 상호 참조 멘션이 어떻게 어노테이션 작성되었는지 보십시오. 
1. **Performance** 페이지에서 **View Decoding Results**를 클릭하여 기계 학습 모델이 테스트 세트의 문서에 추가한 어노테이션을 보십시오. 이 단추는 모델을 평가한 후에만 사용 가능합니다. 결과를 보면 기계 학습 모델이 테스트 데이터에 멘션, 관계 및 상호 참조 멘션을 얼마나 잘 레이블 지정했는지 볼 수 있습니다. 
1. 훈련, 테스트 및 블라인드 데이터 세트 간에 문서가 분할되는 방식을 변경하려면 **Performance** > **Train and evaluate** > **Edit Settings**를 클릭하십시오. 예를 들어, 초기 결과가 만족스러운 경우에는 테스트 세트의 문서 수를 늘려 기계 학습 모델의 결과를 추가로 테스트하려 할 수 있습니다. 사용자는 여러 용도로 문서가 자동으로 분할되는 비율을 변경하거나, 특정 문서 세트를 훈련 데이터, 테스트 데이터 또는 블라인드 데이터로 사용하도록 선택할 수 있습니다. 
1. 특정 항목을 변경한 경우에는 **Train & Evaluate**를 클릭하여 모델을 다시 훈련시키고 어노테이션을 다시 평가하십시오. 

## 기계 학습 모델 삭제
{: #wks_madelete}

기계 학습 모델은 삭제할 수 없습니다. 

모델을 개발하는 데 사용된 작업공간은 삭제할 수 있지만, 모델 자체를 삭제할 수는 없습니다. 모델을 삭제하는 것은 최선의 접근법이 아닙니다. 대신 모델을 훈련시키는 데 사용된 아티팩트를 업데이트하거나 대체하십시오. 모델이 예상한 결과를 작성하지 않더라도 모델을 계속 정제할 수 있습니다. 새 버전을 작성할 때마다 모델은 다시 빌드됩니다. 사용자는 사전 및 유형 시스템과 같은 아티팩트를 편집하고, 다음 버전을 훈련시킬 때 다른 어노테이션 세트를 사용하도록 선택할 수 있습니다. 
