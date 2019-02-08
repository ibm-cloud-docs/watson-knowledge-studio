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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/knowledge-studio/preannotation.html){: new_window}하십시오.
{: tip}

# 어노테이션 작성 부트스트래핑
{: #preannotation}

작업공간 내의 문서에 어노테이션 미리 작성(pre-annotation)을 수행하여 사람 어노테이터의 작업을 단순화하십시오. 프리어노테이터(pre-annotator)는 멘션을 자동으로 찾아 어노테이션을 작성하기 위해 실행할 수 있는 {{site.data.keyword.knowledgestudioshort}} 사전, 규칙 기반 모델 또는 기계 학습 모델입니다.
{: shortdesc}

어노테이션 미리 작성은 단순한 어노테이션 작성을 처리하며 문서 어노테이션 작성 작업을 선행하여 진행하므로 사람 어노테이터의 작업을 용이하게 해 줍니다.

문서에 어노테이션 미리 작성을 수행하는 데 사용되는 방법은 결과 모델을 사용하는 방식을 제한하지 않습니다. 예를 들면, 문서에 어노테이션 미리 작성을 수행하는 데 {{site.data.keyword.nlushort}} 서비스를 사용했다고 해서 빌드한 최종 기계 학습 모델을 {{site.data.keyword.nlushort}} 서비스에 배치해야 하는 것은 아닙니다. 어노테이션 미리 작성은 전적으로 사람에 의한 어노테이션 작성을 부트스트랩하기 위한 것입니다.

## 중요 참고
{: #preannotation_notes}

- 사람 어노테이터가 추가한 어노테이션이 제거되므로, 사람 어노테이터가 어노테이션을 작성한 문서에 프리어노테이터를 실행하지 마십시오.
- 문서에 대해 하나의 프리어노테이터만 실행할 수 있습니다. 한 프리어노테이터를 실행한 후 두 번째 프리어노테이터를 실행하면 첫 번째 프리어노테이터가 추가한 어노테이션을 두 번째 프리어노테이터가 제거합니다. 자신의 유스 케이스에 가장 적합한 어노테이션 미리 작성 방법을 선택한 후 해당 프리어노테이터를 하나만 사용하십시오.

## 어노테이션 미리 작성 방법
{: #preannotation_methods}

다음 프리어노테이터를 사용할 수 있습니다.

- **{{site.data.keyword.nlushort}}**

    문서 내의 엔티티 멘션을 자동으로 찾는 데 사용할 수 있는 프리어노테이터입니다. 소스 문서에 일반적인 지식과 관련된 주제가 있는 경우에는 이 프리어노테이터를 사용하는 것이 좋습니다. 특허법 연구와 같은 특정 분야의 내용이 많은, 고도로 전문적인 문서에 대해 작업하는 경우에는 사전 프리어노테이터 또는 규칙 기반 모델을 사용하는 것이 더 좋습니다.

- **사전**

    사용자가 제공하는 용어 사전을 사용하여 엔티티 유형과 연관시킴으로써 문서 내의 해당 엔티티 유형에 대한 멘션을 찾습니다. 이 프리어노테이터는 기계 학습 프리어노테이터처럼 용어가 사용되는 컨텍스트를 분석하지 않으므로, 고유하거나 전문적인 용어를 사용하는 분야에 적합합니다. 대신 사용된 컨텍스트에 관계 없이 의미를 해석할 수 있을 정도로 용어가 고유해야 합니다. 예를 들면, 식물, 스포츠, 무엇인가를 부수는 것을 의미하는 동사를 가리킬 수 있는 *squash*의 엔티티 유형을 판별하는 것보다는 *asbestos*를 광물 엔티티 유형으로 인식하는 것이 더 쉽습니다.

- **기계 학습**

    기계 학습 모델을 사용하여 문서에 자동으로 어노테이션을 작성합니다. 이 선택사항은 {{site.data.keyword.knowledgestudioshort}}를 사용하여 이미 기계 학습 모델을 작성한 경우에만 사용할 수 있습니다. 새 문서 세트를 추가하는 경우에는 이전에 작성한 기계 학습  어노테이터를 실행하여 새 문서에 어노테이션 미리 작성을 수행할 수 있습니다. 새 문서 세트가 원래 기계 학습 어노테이터를 훈련시키는 데 사용된 문서와 유사한 경우에는 어노테이션 미리 작성을 수행하는 데 이 어노테이터를 선택하는 것이 가장 좋습니다.

- **규칙**

    규칙 기반 모델을 사용하여 문서에 자동으로 어노테이션을 작성합니다. 이 선택사항은 {{site.data.keyword.knowledgestudioshort}}를 사용하여 이미 규칙 기반 모델을 작성한 경우에만 사용할 수 있습니다. 문서가 의미를 끌어낼 수 있는 공통 토큰 패턴을 포함하는 경우에는 이 모델을 선택하는 것이 좋습니다. 이 모델에서는 또한 문서에서 찾는 사전 용어의 클래스 유형을 식별함으로써 사전 프리어노테이터의 일부 기능을 사용할 수도 있습니다.

또는, 이미 어노테이션이 작성된 문서를 업로드한 후 이를 사용하여 기계 학습 모델 훈련을 시작할 수 있습니다. 업로드하는 어노테이션 작성된 문서에 어노테이션 미리 작성을 실행하면 문서에서 기존 어노테이션이 제거되며 해당 프리어노테이터가 작성한 어노테이션만으로 대체되므로 이와 같이 해서는 안 됩니다.

> **참고:** 현재 작업공간의 일부로서 기준 실제값에 추가된 문서에는 프리어노테이터를 실행할 수 *있습니다*. 현재 작업공간 내에서 문서에 추가되어, 검토 및 승인을 거쳐 기준 실제값으로 승격된 어노테이션은 제거되지 않습니다.

## {{site.data.keyword.nlushort}}을 사용하여 문서에 어노테이션 미리 작성 수행
{: #wks_preannotnlu}

{{site.data.keyword.nlushort}} 서비스를 사용하여 말뭉치에 추가된 문서에 어노테이션 미리 작성을 수행할 수 있습니다.

### 시작하기 전에
{: #wks_preannotnlu_prereqs}

{{site.data.keyword.nlushort}} 프리어노테이터가 사용자의 유스 케이스에 대한 값을 추가할지 판별하십시오. 지원되는 [{{site.data.keyword.nlushort}} 서비스 엔티티 유형 및 하위 유형 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/docs/services/natural-language-understanding/entity-types.html){: new_window}을 검토하여 이들이 유형 시스템의 유형과 자연스럽게 겹치는지 판별하십시오. 겹치는 경우에는 이 프로시저를 계속하십시오. 그렇지 않은 경우에는 사용할 다른 프리어노테이터를 선택하십시오.

### 이 태스크에 대한 정보
{: #wks_preannotnlu_about}

{{site.data.keyword.nlushort}}은 자연어 처리를 통한 텍스트 분석을 제공하는 서비스입니다. {{site.data.keyword.nlushort}} 프리어노테이터를 사용하면 문서 내의 엔티티를 찾고 어노테이션을 작성하기 위해 {{site.data.keyword.nlushort}} 서비스가 호출됩니다.

사용자는 {{site.data.keyword.nlushort}} 엔티티 유형을 {{site.data.keyword.knowledgestudioshort}} 유형 시스템에 추가한 해당 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형에 맵핑하여 서비스가 찾도록 할 엔티티 유형을 지정해야 합니다. 맵핑한 엔티티 유형의 멘션만 찾고 어노테이션을 작성할 수 있습니다.

### 프로시저
{: #wks_preannotnlu_procedure}

{{site.data.keyword.nlushort}} 서비스를 사용하여 문서에 어노테이션 미리 작성을 수행하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Machine Learning Model** > **Pre-annotation** > **Natural Language Understanding** 탭을 선택하십시오. 
1. **Edit**를 클릭하여 **Entity Types** 페이지에 정의된 각 엔티티 유형을 해당 {{site.data.keyword.nlushort}} 엔티티 유형에 맵핑하십시오.

    - {{site.data.keyword.nlushort}} 엔티티 유형의 드롭 다운 목록은 {{site.data.keyword.nlushort}} 서비스가 인식한 엔티티 유형으로 미리 채워져 있습니다.
    - 하나 이상의 엔티티 유형을 맵핑해야 합니다.
    - {{site.data.keyword.nlushort}} 엔티티 유형을 {{site.data.keyword.knowledgestudioshort}} 엔티티 역할에 맵핑할 수는 없으며, {{site.data.keyword.knowledgestudioshort}} 엔티티 유형에만 맵핑할 수 있습니다.
    - 하나의 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형에 둘 이상의 {{site.data.keyword.nlushort}}  엔티티 유형을 맵핑할 수 있으며, 반대의 경우도 가능합니다. 예를 들면, 다음 맵핑은 허용됩니다.

    <table summary="엔티티 유형의 샘플 맵핑">
    <caption>표 1. 엔티티 유형의 샘플 맵핑</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">{{site.data.keyword.nlushort}} 엔티티 유형</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENGINEER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Person
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          LOCATION
        </td>
        <td headers="d20428e298">
          CityTown<br/>
          Country
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. 적용할 모든 엔티티 유형을 맵핑한 후에는 **Apply This Pre-annotator**를 클릭하십시오.

    하나 이상의 엔티티 유형을 맵핑하기 전까지는 **Apply This Pre-annotator** 단추를 사용할 수 없습니다.

1. 어노테이션 미리 작성을 수행할 각 문서 세트에 대한 선택란을 선택하십시오.

    이 프리어노테이터를 처음 실행하는 경우에는 먼저 프리어노테이터가 맵핑된 엔티티를 예상대로 찾을 수 있는지 유효성 검증하십시오. 각 개별 데이터 소스의 대표적인 문서를 포함하는 하나의 문서 세트를 작성하십시오.
    {: tip}

1. **Run**을 클릭하십시오.

    프리어노테이터의 유효성 검증을 수행하는 경우에는 어노테이션이 작성된 문서를 열고 추가된 어노테이션을 검토하십시오. 충분한 수의 정확한 어노테이션이 작성되었는지 확인하십시오. 어노테이션이 정확한 경우에는 더 크고 많은 문서 세트에 대해 이 어노테이터를 다시 실행할 수 있습니다. 어노테이션이 정확하지 않은 경우에는 유형에 다른 {{site.data.keyword.nlushort}} 엔티티 유형을 맵핑하는 것을 고려하십시오. 유형이 자연스럽게 겹치지 않는 경우에는 {{site.data.keyword.nlushort}} 프리어노테이터가 아닌 다른 프리어노테이터를 사용하는 것이 좋습니다.

    어노테이션 미리 작성은 특정 문서가 속할 수 있는 다양한 문서 세트를 고려하지 않고 개별 문서에 적용됩니다. 선택한 문서 세트와 선택하지 않은 문서 세트 간에 겹치는 문서는 두 문서 세트 모두에서 어노테이션 미리 작성이 수행됩니다.

1. 프리어노테이터를 한 번 실행한 후에는 이를 사용하여 말뭉치에 추가된 다른 문서 세트에 어노테이션 미리 작성을 수행하려 하는 경우 언제든지 **Apply This Pre-annotator**를 클릭할 수 있습니다.

    > **제한사항:** {{site.data.keyword.nlushort}} 프리어노테이터의 유형 맵핑 정의를 편집하는 경우에는 어노테이션 미리 작성이 수행된 문서 세트를 포함하는 어노테이션 태스크를 다시 작성해야 합니다. 변경된 프리어노테이터 맵핑 정의를 기반으로 하는 어노테이션 미리 작성은 이미 어노테이션 작성 태스크에 지정된 문서 세트에 적용할 수 없습니다.

### 결과
{: #wks_preannotnlu__export-warning}

{{site.data.keyword.nlushort}} 서비스가 어노테이션 미리 작성을 수행한 문서에 의해 작성된 기준 실제값은 직접 {{site.data.keyword.knowledgestudioshort}} 외부에서 사용할 수 없습니다. 사용자는 이 기준 실제값(읽을 수 없는 양식임)을 다운로드하여 한 {{site.data.keyword.knowledgestudioshort}} 작업공간에서 다른 작업공간으로 이동해야 합니다. 그 후에는 기준 실제값 개발을 계속하며 이를 사용하여 {{site.data.keyword.knowledgestudioshort}} 외부의 서비스에서 사용하기 위해 배치할 수 있는 기계 학습 모델 또는 규칙 기반 모델을 빌드할 수 있습니다.

> **제한사항:** {{site.data.keyword.nlushort}}으로 어노테이션 미리 작성이 수행된 문서는 다운로드 시 읽을 수 없는 형식으로 숨겨집니다. 그러나 이뿐만 아니라, 사람 어노테이터가 추가한 어노테이션을 비롯하여 이러한 문서의 모든 어노테이션은 숨겨집니다.

**관련 정보**:

[{{site.data.keyword.nlushort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## 사전을 사용하여 문서에 어노테이션 미리 작성 수행
{: #wks_preannot}

사람 어노테이터가 어노테이션 작성 태스크를 시작하는 데 도움을 주기 위해, 사전을 작성하고 이를 사용하여 말뭉치에 추가된 문서에 어노테이션 미리 작성을 수행할 수 있습니다.

### 이 태스크에 대한 정보
{: #wks_preannot_about}

사람 어노테이터가 어노테이션 미리 작성이 수행된 문서에 대해 작업을 시작할 때는 사전 항목을 기반으로 여러 멘션이 이미 엔티티 유형으로 표시되어 있을 가능성이 높습니다. 사람 어노테이터는 어노테이션 미리 작성된 엔티티 유형을 변경하거나 제거하고 어노테이션 작성되지 않은 멘션에 엔티티 유형을 지정할 수 있습니다. 사전에 의한 어노테이션 미리 작성은 관계 및 상호 참조에 어노테이션을 작성하지 않습니다. 관계 및 상호 참조는 사람 어노테이터가 어노테이션을 작성해야 합니다.

**참고**: 이 태스크는 편집 가능한 사전을 작성하는 방법을 보여줍니다. 문서를 업로드하고 읽기 전용 사전으로 이의 어노테이션 미리 작성을 수행하려는 경우에는 **Create Dictionary** 단추 옆의 **메뉴** 아이콘을 클릭하십시오. **Upload Dictionary**를 클릭하십시오. 

### 프로시저
{: #wks_preannot_procedure}

편집 가능한 사전을 작성하고 문서에 어노테이션 미리 작성을 수행하려면 다음 작업을 수행하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Assets** > **Dictionaries** 페이지를 선택하십시오. 
1. **Create Dictionary**를 클릭하고 이름을 입력한 후에 **Save**를 클릭하십시오. 
1. **Entity types** 목록에서 사전과 연관시킬 엔티티 유형을 선택하십시오.
3. 사전의 항목을 추가하거나 사전 용어를 포함하는 파일을 업로드하십시오.
4. **Machine Learning Model** > **Pre-annotation**를 클릭하십시오.
5. **Dictionaries** 탭에서 **Apply This Pre-annotator**를 클릭하십시오.
6. 어노테이션 미리 작성을 수행할 각 문서 세트에 대한 선택란을 선택하고 **Run**을 클릭하십시오.

    어노테이션 미리 작성은 특정 문서가 속할 수 있는 다양한 문서 세트 또는 어노테이션 세트를 고려하지 않고 개별 문서에 적용됩니다. 선택한 문서 세트와 선택하지 않은 문서 세트 간에 겹치는 문서는 두 문서 세트 모두에서 어노테이션 미리 작성이 수행됩니다.

7. 사전이 작성된 후에는 사전을 사용하여 말뭉치에 추가된 다른 문서 세트에 어노테이션 미리 작성을 수행하려는 경우 언제든지 **Run**을 클릭하십시오.

    > **제한사항:** 사전을 편집하여 항목을 추가하거나 제거하는 경우에는 어노테이션 미리 작성이 수행된 문서 세트를 포함하는 어노테이션 작성 태스크를 다시 작성해야 합니다. 변경된 사전 어노테이터를 기반으로 하는 어노테이션 미리 작성은 이미 어노테이션 작성 태스크에 지정된 어노테이션 세트에 적용할 수 없습니다.

**관련 정보**:

[사전 작성](/docs/services/watson-knowledge-studio/dictionaries.html)

[시작하기 > 사전 추가](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## 기계 학습 모델을 사용하여 문서에 어노테이션 미리 작성 수행
{: #wks_preannotsire}

기존 기계 학습 모델을 사용하여 말뭉치에 추가된 문서에 어노테이션 미리 작성을 수행할 수 있습니다.

### 이 태스크에 대한 정보
{: #wks_preannotsire_about}

10 - 30개의 문서에 어노테이션이 작성되고 나면 이러한 데이터를 사용하여 기계 학습 모델을 훈련시킬 수 있습니다. 이와 같이 훈련도가 낮은 모델을 프로덕션에서 사용하면 안 되지만, 후속 문서의 사람 어노테이션의 속도를 높이는 데 도움을 주기 위해 문서의 어노테이션 미리 작성에 사용될 수 있습니다. 예를 들어, 기계 학습 모델을 훈련시킨 후 말뭉치에 문서를 추가하는 경우에는 이 모델을 새 문서 세트에 어노테이션 미리 작성을 수행하는 데 사용할 수 있습니다. 사람이 어노테이션을 작성한 문서에 대해 프리어노테이터를 실행하지 마십시오. 프리어노테이터는 사람이 작성한 어노테이션을 제거합니다.

### 프로시저
{: #wks_preannotsire_procedure}

기존 기계 학습 모델을 사용하여 문서에 어노테이션 미리 작성을 수행하려면 다음 작업을 수행하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자로 로그인하여 작업공간을 선택하십시오.
2. **Machine Learning Model** > **Versions**를 선택하십시오. 
3. 새 문서에 어노테이션 미리 작성을 수행하려면 **Run this model**을 클릭하십시오. 
4. 어노테이션 미리 작성을 수행할 각 문서 세트에 대한 선택란을 선택하고 **Run**을 클릭하십시오.

    어노테이션 미리 작성은 특정 문서가 속할 수 있는 다양한 문서 세트 또는 어노테이션 세트를 고려하지 않고 개별 문서에 적용됩니다. 선택한 문서 세트와 선택하지 않은 문서 세트 간에 겹치는 문서는 두 문서 세트 모두에서 어노테이션 미리 작성이 수행됩니다.

5. 기계 학습 모델을 사용하여 말뭉치에 추가된 다른 문서 세트에 어노테이션 미리 작성을 수행하려는 경우에는 언제든지 **Run this model**을 클릭할 수 있습니다.

## 규칙 기반 모델을 사용하여 문서에 어노테이션 미리 작성 수행
{: #wks_preannotrule}

기존 규칙 기반 모델을 사용하여 말뭉치에 추가된 문서에 어노테이션 미리 작성을 수행할 수 있습니다.

### 프로시저
{: #wks_preannotrule_procedure}

규칙 기반 모델을 사용하여 문서에 어노테이션 미리 작성을 수행하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.knowledgestudioshort}} 관리자로 로그인하여 작업공간을 선택하십시오.
1. **Rule-based Model** > **Versions** > **Rule-based Model** 탭을 선택하십시오. 
1. 아직 완료하지 않은 경우에는 **Map entity types and classes**를 클릭하여 {{site.data.keyword.knowledgestudioshort}} 유형 시스템에 정의한 엔티티 유형을 하나 이상의 규칙 기반 모델 클래스에 맵핑하십시오.
2. 맵핑할 각 엔티티 유형에 대해 **Edit**를 클릭하십시오. 

    - **Class Name** 열의 드롭 다운 목록은 규칙 기반 모델과 연관된 클래스로 미리 채워져 있습니다.
    - 하나 이상의 엔티티 유형을 클래스에 맵핑해야 합니다.

3. **Rule-based Model** 탭에서 **Run this model**을 클릭하십시오. 

    하나 이상의 엔티티 유형을 클래스에 맵핑하기 전까지는 **Run this model** 단추를 사용할 수 없습니다.

4. 어노테이션 미리 작성을 수행할 문서 세트 또는 어노테이션 세트를 선택하십시오. 선택하는 문서에 사람이 작성한 어노테이션이 있는 문서가 포함되지 않았는지 확인하십시오. 프리어노테이터는 사람이 작성한 어노테이션을 제거합니다.
5. **Run**을 클릭하십시오.

    어노테이션 미리 작성은 특정 문서가 속할 수 있는 다양한 문서 세트를 고려하지 않고 개별 문서에 적용됩니다. 선택한 문서 세트와 선택하지 않은 문서 세트 간에 겹치는 문서는 두 문서 세트 모두에서 어노테이션 미리 작성된 것으로 표시됩니다.

6. 규칙 기반 학습 모델을 사용하여 말뭉치에 추가된 문서 세트에 어노테이션 미리 작성을 수행하려는 경우에는 언제든지 **Run this model**을 클릭할 수 있습니다.

    > **제한사항:** 규칙 기반 모델의 엔티티 유형 대 클래스 맵핑을 편집하는 경우에는 어노테이션 미리 작성이 수행된 문서 세트를 포함하는 어노테이션 작성 태스크를 다시 작성해야 합니다. 변경된 프리어노테이터 맵핑 정의를 기반으로 하는 어노테이션 미리 작성은 이미 어노테이션 작성 태스크에 지정된 문서 세트에 적용할 수 없습니다.

## 어노테이션 미리 작성이 수행된 문서의 업로드
{: #wks_uima}

UIMA(Unstructured Information Management Architecture) 분석 엔진을 통해 어노테이션 미리 작성이 수행된 문서를 업로드하여 모델의 훈련을 빠르게 시작할 수 있습니다.

어노테이션 미리 작성이 수행된 문서의 형식은 UIMA CAS XMI(UIMA Common Analysis Structure의 XMI 직렬화)여야 합니다. 업로드하는 ZIP 파일은 UIMA TypeSystem 디스크립터 파일과 UIMA 유형을 {{site.data.keyword.knowledgestudioshort}} 유형 시스템의 엔티티 유형에 맵핑하는 파일을 포함해야 합니다.

UIMA CAS XMI는 Apache UIMA의 표준 형식입니다. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer의 분석된 콜렉션으로부터 올바른 형식으로 파일을 작성하는 방법에 대한 가이드라인이 제공됩니다. 다른 Apache UIMA 구현을 사용하는 경우에는 자신의 목적에 맞게 이러한 가이드라인을 변경하십시오. XMI 파일을 작성하는 방법에 관계 없이, 유형 시스템 맵핑 파일 및 ZIP 파일 작성에 대한 요구사항은 모든 사용자에게 동일하게 적용됩니다.

가져온 문서를 사람 어노테이터에게 지정하면 문서가 기준 실제값 편집기에 어노테이션 미리 작성된 상태로 표시되며, 여러 멘션에 이미 어노테이션이 작성되어 있을 수 있습니다. 따라서 사람 어노테이터는 표시되지 않은 멘션에 어노테이션 가이드라인을 적용하는 데 집중할 수 있습니다. 또는, 사람에 의한 어노테이션 작성 단계를 건너뛰고 어노테이션 미리 작성이 수행된 문서를 사용하여 즉시 기계 학습 모델의 훈련 및 평가를 시작할 수 있습니다.

### Watson Explorer Content Analytics에서 분석된 문서 내보내기
{: #wks_uimawexca}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics에서 크롤링되고 분석된 문서를 내보내고, 분석된 문서를 {{site.data.keyword.knowledgestudioshort}} 작업공간에 XMI 파일로 업로드할 수 있습니다.

#### 프로시저
{: #wks_uima_procedure}

{{site.data.keyword.watson}} Explorer Content Analytics 콜렉션에서 분석된 문서를 가져오려면 다음 작업을 수행하십시오.

1. 웹 브라우저에서 Content Analytics 관리 콘솔을 여십시오.
1. 콜렉션 보기에서 문서를 내보낼 콜렉션을 펼치십시오. 구문 분석 및 색인화 분할창에서 구문 분석 및 색인화 프로세스가 실행 중인지 확인한 후 **분석된 문서 컨텐츠 및 메타데이터 내보내기**의 화살표 아이콘을 클릭하십시오.
1. **분석된 문서 내보내기 옵션** 영역에서 **문서를 XML 파일로 내보내기**를 선택하고, **XMI 형식 내보내기로 CAS를 사용할 수 있도록 설정** 선택란을 선택한 다음, 내보낸 데이터가 기록될 출력 경로를 지정한 후 **확인**을 클릭하십시오.
1. 콜렉션에 대한 구문 분석 및 색인화 서비스를 중지한 후 다시 시작한 다음, 다음 단계 중 하나를 수행하십시오.

    - 콜렉션의 문서 캐시에 기계 학습 모델의 훈련에 사용할 색인화된 문서가 이미 포함되어 있는 경우에는 전체 색인 빌드를 다시 시작하십시오.
    - 콜렉션이 기계 학습 모델의 훈련에 사용할 색인화된 문서를 포함하고 있지 않은 경우에는 문서를 업로드하고, 문서를 크롤링할 하나 이상의 크롤러를 구성한 후 크롤러를 시작하십시오.

1. **내보내기** 영역에서 내보내기 요청의 상태를 확인하십시오. 진행상태는 얼마나 많은 문서를 내보냈는지를 나타냅니다.
1. 내보내기 옵션을 구성할 때 지정한 출력 폴더로 이동하십시오. 문서를 XML 파일로 내보낼 때 출력 폴더 이름은 내보내기가 발생한 시점의 시간소인에 따라 지정됩니다. 이 출력 폴더는 XMI 파일(`*.xmi`)과 UIMA TypeSystem 디스크립터 파일(`exported_typesystem.xml`)을 포함합니다.

#### 다음에 수행할 작업
{: #wks_uimawexca__preUIMAimport}

UIMA 유형과 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형 간의 맵핑을 정의해야 합니다. 또한 분석된 데이터를 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드하는 데 필요한 모든 파일을 포함하는 ZIP 파일을 작성해야 합니다.

**관련 정보**:

[크롤링되거나 분석된 문서 내보내기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[내보낸 문서의 출력 경로 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### Content Analytics Studio에서 분석된 콜렉션 내보내기
{: #wks_uimawexstudio}

{{site.data.keyword.watson}} Explorer Content Analytics Studio에서 분석된 문서의 콜렉션을 내보내고, 분석된 문서를 {{site.data.keyword.knowledgestudioshort}} 프로젝트에 XMI 파일로 업로드할 수 있습니다.

#### 프로시저
{: #wks_uimawexstudio_procedure}

Content Analytics Studio 콜렉션에서 분석된 문서를 가져오려면 다음 작업을 수행하십시오.

1. Content Analytics Studio를 실행하고 스튜디오 프로젝트를 여십시오.
1. 기계 학습 모델을 훈련시키는 데 사용할 문서를 포함하는 폴더를 마우스 오른쪽 단추로 클릭하고 **콜렉션 분석**을 선택하십시오.
1. UIMA 파이프라인 구성 파일을 선택하십시오.
1. 콜렉션 분석 보기로 이동하여 콜렉션 분석 보기에 있는 **저장** 아이콘을 클릭하십시오. 저장된 결과가 기록되는 폴더를 지정하고 파일 이름을 지정하십시오.
1. 지정한 폴더를 여십시오. 저장된 파일의 파일 확장자는 `.annotations`입니다.
1. `.annotations` 파일을 로컬 파일 시스템으로 복사한 후 파일 확장자를 `.annotations`에서 `.zip`으로 바꾸십시오.
1. ZIP 파일에서 모든 파일의 압축을 푸십시오. 압축이 풀린 컨텐츠에는 XMI 파일(`*.xmi`), UIMA TypeSystem 디스크립터 파일(`TypeSystem.xml`) 및 기타 파일이 포함되어 있습니다.

#### 다음에 수행할 작업
{: #wks_uimawexstudio_next}

UIMA 유형과 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형 간의 맵핑을 정의해야 합니다. 또한 분석된 데이터를 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드하는 데 필요한 모든 파일을 포함하는 ZIP 파일을 작성해야 합니다.

### UIMA 유형을 엔티티 유형에 맵핑
{: #wks_uimawexmap}

XMI 파일을 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드하기 전에, UIMA 유형과 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형 간의 맵핑을 정의해야 합니다.

#### 시작하기 전에
{: #wks_uimawexmap_prereqs}

{{site.data.keyword.knowledgestudioshort}} 작업공간의 유형 시스템이 UIMA 유형에 맵핑할 엔티티 유형을 포함해야 합니다.

#### 프로시저
{: #wks_uimawexmap_procedure}

UIMA 유형을 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형에 맵핑하려면 다음 작업을 수행하십시오.

1. `exported_typesystem.xml` 또는 `TypeSystem.xml`과 같은 UIMA TypeSystem 디스크립터 파일을 포함하는 폴더에 `cas2di.tsv`라는 파일을 작성하십시오.
1. `cas2di.tsv` 파일을 텍스트 편집기로 여십시오. 파일의 각 행은 하나의 맵핑을 지정합니다. 맵핑의 형식은 맵핑할 어노테이터의 어노테이션에 따라 달라집니다.

    - 기본 형식을 사용하여 맵핑을 작성할 수 있습니다.

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        다음 예는 {{site.data.keyword.watson}} Explorer Content Analytics의 개체명 인식 어노테이터에 의해 작성된 UIMA 유형과 {{site.data.keyword.knowledgestudioshort}} 유형 시스템에 정의된 엔티티 유형 간의 맵핑을 정의합니다.

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        또 다른 다음 예는 {{site.data.keyword.watson}} Explorer Content Analytics Studio에서 사용자 정의 어노테이터에 의해 작성된 UIMA 유형과 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형 간의 맵핑을 정의합니다.

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - {{site.data.keyword.watson}} Explorer Content Analytics에서는 패턴 일치 어노테이터 또는 사전 검색 어노테이터에서 사용하는 패싯에 따라 맵핑을 작성할 수 있습니다. 텍스트 분석 규칙 파일(`*.pat`)에서 패싯은 카테고리 속성으로 표현됩니다. 맵핑을 정의하려면 다음 구문을 사용하십시오.

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        패턴 일치 및 사전 검색 어노테이터를 적용하는 다음 예는 카테고리 $.mykeyword.product와 {{site.data.keyword.knowledgestudioshort}} 엔티티 유형 PRODUCT 간의 맵핑을 정의합니다.

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### 다음에 수행할 작업
{: #wks_uimawexmap_next}

분석된 데이터를 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드하는 데 필요한 모든 파일을 포함하는 ZIP 파일을 작성해야 합니다.

**관련 정보**:

[패턴 일치 어노테이터 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[사전 검색 어노테이터 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[개체명 인식 어노테이터 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### UIMA CAS XMI 파일을 작업공간에 업로드
{: #wks_uimaweximport}

다운로드한 어노테이션 미리 작성이 수행된 문서를 모델을 훈련시키는 데 사용하려면 XMI 파일을 업로드하는 데 필요한 모든 파일을 포함하는 ZIP 파일을 작성한 후 이 ZIP 파일을 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드해야 합니다.

#### 시작하기 전에
{: #wks_uimaweximport_prereqs}

ZIP 파일을 업로드하기 전에, {{site.data.keyword.knowledgestudioshort}} 작업공간의 유형 시스템이 UIMA 유형에 맵핑한 엔티티 유형을 포함하는지 확인하십시오.

> **경고:** UIMA 분석 엔진은 여러 문장에 걸친 어노테이션을 허용합니다. {{site.data.keyword.knowledgestudioshort}}에서 어노테이션은 하나의 문장 경계 내에 존재해야 합니다. 업로드하는 XMI 파일이 여러 문장에 걸친 어노테이션을 포함하는 경우 이러한 어노테이션은 기준 실제값 편집기에 표시되지 않습니다.

#### 프로시저
{: #wks_uimaweximport_procedure}

어노테이션 미리 작성이 수행된 문서를 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드하려면 다음 작업을 수행하십시오.

1. {{site.data.keyword.knowledgestudioshort}}에서 필요로 하는 모든 파일을 포함하는 ZIP 파일을 작성하십시오.

    1. XMI 파일, UIMA TypeSystem 디스크립터 파일 및 `cas2di.tsv` 파일을 포함하는 폴더를 선택하거나, 이 폴더 내의 모든 파일을 선택하십시오.
    1. 모든 파일을 포함하는 ZIP 파일을 작성하십시오. `cas2di.tsv` 및 UIMA TypeSystem 디스크립터 파일이 ZIP 파일의 루트 디렉토리에 저장되도록 하십시오. 이러한 파일을 ZIP 파일 내의 서브폴더에 저장하면 {{site.data.keyword.knowledgestudioshort}}가 이를 읽을 수 없으며, 아무것도 가져오지 않습니다.

        Windows에서는 마우스 오른쪽 단추로 클릭한 후 **보내기** > **압축(ZIP) 폴더**를 선택할 수 있습니다.

1. ZIP 파일을 {{site.data.keyword.knowledgestudioshort}} 작업공간에 업로드하십시오.

    1. {{site.data.keyword.knowledgestudioshort}} 관리자 또는 프로젝트 관리자로 로그인하여 문서를 추가할 작업공간을 열고 **Assets**> **Documents** 페이지를 여십시오. 
    1. **Upload Document Sets**를 클릭하십시오.
    1. 작성한 ZIP 파일을 끌어 오거나, 클릭하여 이 파일을 찾아 선택하십시오.
    1. 선택란을 선택하여 ZIP 파일이 UIMA CAS XMI 파일을 포함하고 있음을 표시하십시오.
    1. **Upload**를 클릭하십시오.
