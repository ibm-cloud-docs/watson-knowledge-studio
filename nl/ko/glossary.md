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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/glossary.html){: new_window}.
{: tip}

# 용어집
{: #glossary}

이 용어집에는 {{site.data.keyword.knowledgestudioshort}}에서 사용하는 용어 및 정의가 포함되어 있습니다.
{: shortdesc}

이 용어집에서는 다음 상호 참조가 사용됩니다. 

- '참조하십시오'는 특정 용어에서 선호되는 동의어로, 또는 약어에서 정의된 전체 형태로 사용자를 안내합니다. 
- '도 참조하십시오'는 관련되거나 대조되는 용어로 사용자를 안내합니다. 

기타 {{site.data.keyword.IBM}} 제품의 용어집을 보려면 [www.ibm.com/software/globalization/terminology ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/software/globalization/terminology/){: new_window}로 이동하십시오. 

[가](/docs/services/watson-knowledge-studio/glossary.html#gloss_GA) [마](/docs/services/watson-knowledge-studio/glossary.html#gloss_MA) [바](/docs/services/watson-knowledge-studio/glossary.html#gloss_BA) [사](/docs/services/watson-knowledge-studio/glossary.html#gloss_SA) [아](/docs/services/watson-knowledge-studio/glossary.html#gloss_AA) [자](/docs/services/watson-knowledge-studio/glossary.html#gloss_JA) [차](/docs/services/watson-knowledge-studio/glossary.html#gloss_CHA) [카](/docs/services/watson-knowledge-studio/glossary.html#gloss_KA) [타](/docs/services/watson-knowledge-studio/glossary.html#gloss_TA) [파](/docs/services/watson-knowledge-studio/glossary.html#gloss_PA) [하](/docs/services/watson-knowledge-studio/glossary.html#gloss_HA) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F)


## 가
{: #gloss_GA}

- **개체명(named entity)**

    조직, 위치, 작가 또는 질병 이름과 같이 잘 정의된 카테고리에 속하는 도메인 내의 개념입니다. 

- **거짓 부정(false negative)**

    실제로는 올바르지만 올바르지 않은 것으로 예상된 응답 또는 어노테이션입니다. 

- **거짓 긍정(false positive)**

    실제로는 올바르지 않지만 올바른 것으로 예상된 응답 또는 어노테이션입니다. 

- **관계(relation)**

    일반적으로 여러 엔티티가 서로 어떻게 관련되어 있는지 나타내는 동사입니다. 예를 들면, "에서 거주함"은 사람과 도시의 관계입니다. 관계는 동일한 문장 내의 서로 다른 두 엔티티를 연결합니다. 

- **관계 유형(relation type)**

    두 엔티티 간의 2진 단방향 관계입니다. 예를 들면, Mary employedBy {{site.data.keyword.IBM_notm}}은 유효한 관계입니다. {{site.data.keyword.IBM_notm}} employedBy Mary는 유효한 관계가 아닙니다. 

- **규칙 세트(rule set)**

    텍스트에 어노테이션을 작성하기 위한 패턴을 정의하는 규칙 세트입니다. 패턴이 적용되는 경우에는 규칙의 조치가 일치하는 어노테이션에 수행됩니다. 규칙은 일반적으로 일치 조건, 선택적 수량사, 일치하는 텍스트가 만족시켜야 하는 추가 제한조건 목록, 그리고 일치하는 경우 수행하는 조치(새 어노테이션 작성 또는 기존 어노테이션 수정 등)를 지정합니다. 

- **기계 학습(machine learning)**

    과거 데이터를 반복적으로 학습하고 새 데이터에 노출되면 이에 독립적으로 적응하는 데이터 분석 방법입니다. 기계 학습의 핵심인 수학 모델은 기준 실제값 입력으로부터 빌드됩니다. 입력 데이터 예의 훈련 및 정제를 통해, 모델은 새 데이터를 분석할 때 정확하며 반복 가능한 결과를 제공할 수 있습니다. 

- **기계 학습 모델(machine learning model)**

    기준 실제값을 기반으로 하는 통계 모델에 따라 엔티티 및 엔티티 관계를 식별하는 컴포넌트입니다. 모델은 훈련 데이터와 같은 과거 경험을 적용하여, 데이터의 특성을 기반으로 미래 경험의 올바른 결과를 판별하거나 예측합니다. 이러한 과거의 경험은 각 후보 응답 또는 증거의 특성 점수를 계산하고 이를 알려진 결과와 결합하여 모델의 형태로 캡처됩니다. 이는 *기계 학습 어노테이터*라고도 합니다. 

- **기계 학습 어노테이터(machine learning annotator)**

    [기계 학습 모델(machine learning model)](/docs/services/watson-knowledge-studio/glossary.html#gloss_M)을 참조하십시오. 

- **기준 실제값(ground truth)**

    기계 학습 모델을 특정 도메인에 적응시키는 데 사용되는, 사람 어노테이터가 추가한 어노테이션으로 구성된 검증된 데이터의 세트입니다. 기준 실제값은 기계 학습 모델을 훈련시키고, 모델 성능(정밀도 및 재현율)을 측정하고, 성능 개선을 위해 어느 부분에 개발 노력을 집중해야 하는지 결정하는 데 필요한 헤드룸을 계산하는 데 사용됩니다. 기준 실제값이 부정확한 경우에는 이를 사용하는 컴포넌트가 부정확해지므로 이러한 항목의 정확도는 매우 중요합니다. 

## 마
{: #gloss_MA}

- **말뭉치(corpus)**

    작업공간에 추가되어 기계 학습 모델을 훈련시키는 데 사용되는 소스 문서의 콜렉션입니다. 

- **멘션(mention)**

    도메인 데이터와 관련이 있다고 간주하는 텍스트 범위입니다. 예를 들어, 자동차에 대한 유형 시스템에서는 "에어백", "Ford Explorer" 및 "어린이용 카시트"등이 관련 멘션입니다. 

- **문서 세트(document set)**

    문서의 콜렉션입니다. 함께 가져온 문서는 문서 세트가 됩니다. 훈련 용도(테스트, 훈련, 블라인드)로 함께 그룹화되는 어노테이션 작성된 문서는 문서 세트로 생성됩니다. 

## 바
{: #gloss_BA}

- **분석 엔진(analysis engine)**

    문서와 같은 아티팩트를 분석하고 이에 대한 정보를 추측하며, UIMA 분석 엔진 인터페이스 스펙을 구현하는 프로그램입니다. 분석 엔진은 어노테이터라고 하는 구성 요소로 구성됩니다. 하나의 어노테이터를 포함하는 분석 엔진은 기본 분석 엔진이라고 하고, 여러 어노테이터를 포함하는 분석 엔진은 집계 분석 엔진이라고 합니다. 

- **블라인드 데이터(blind data)**

    질문 및 답변 쌍, 의미 어노테이션 및 구절 판정과 같은, 기준 실제값으로 어노테이션 작성된 문서 세트입니다. 블라인드 데이터는 개발자에게 공개되거나 개발자가 본 적이 없는 데이터로, 새로운 데이터에 대한 성능의 평가를 위해 주기적으로 시스템을 테스트하는 데 사용됩니다. 블라인드 데이터에 대한 테스트를 수행하면 알려진 질문 세트 또는 어노테이션에 대한 과적합으로 인해 정확도가 오염되는 것을 방지할 수 있습니다. 보고된 결과는 블라인드 데이터에 대해 실행된 테스트만의 결과여야 합니다. [테스트 데이터(testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) 및 [훈련 데이터(training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)도 참조하십시오. 

## 사
{: #gloss_SA}

- **사람 어노테이터(human annotator)**

    멘션, 엔티티 유형 관계 및 멘션 상호 참조를 식별함으로써 어노테이션 미리 작성의 결과를 검토하고, 수정하고, 보완하는 주제 관련 전문가입니다. 사람 어노테이터는 특정 컨텍스트의 텍스트를 검사하여 기준 실제값을 판별하고 기계 학습 모델의 정확도를 개선하는 데 도움을 줍니다. 

- **사전(dictionary)**

    문서에 어노테이션 미리 작성을 수행하는 데 사용할 수 있는 단어의 콜렉션입니다. 문서 텍스트에서 단어의 용어와 일치하는 각 단어에 대해 새 어노테이션이 작성됩니다. 기계 학습 모델은 제약 분야에 대한 사전 또는 재산 관리에 대한 사전과 같이, 일반적으로 특정 도메인에 고유한 하나 이상의 독립된 사전으로 구성될 수 있습니다. [표제어(lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) 및 [표층형(surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_S)도 참조하십시오. 

- **사전 프리어노테이터(dictionary pre-annotator)**

    텍스트에서 특정 단어 세트와 일치하는 멘션을 식별하는 컴포넌트입니다. 도메인 고유 용어를 사용하여 텍스트에 어노테이션 미리 작성(pre-annotation)을 수행함으로써, 사전 프리어노테이터는 사람 어노테이터가 기준 실제값 문서 세트를 더욱 빠르게 준비할 수 있게 해 줍니다. 

- **상호 참조(coreference)**

    두 단어 또는 구문이 동일한 사람 또는 물건을 가리키며 한 쪽이 다른 하나보다 언어적으로 우선하는 관계입니다. 예를 들면, 구문 "She taught herself"에는 두 대명사 간에 상호 참조가 있으나 "She taught her"에는 없습니다. 상호 참조는 동일한 텍스트 내의 두 동격 엔티티를 연결합니다. 

- **상호 참조 체인(coreference chain)**

    상호 참조로 어노테이션 작성된 엔티티의 목록입니다. 멘션을 상호 참조로 어노테이션 작성하면 시스템이 상호 참조 체인을 작성합니다. 이 체인은 특정 컨텍스트의 모든 멘션을 보고 모든 발생이 동일한 엔티티 유형에 속하는지 확인하는 수단을 제공합니다. 

- **성능(performance)**

    질문에 대한 응답, 관계 발견 또는 텍스트에 대한 어노테이션 작성과 같은 작업에 대한, {{site.data.keyword.watson}} 시스템의 정확도, 정밀도 및 재현율 수치입니다. 

- **속성(attribute)**

    특정 엔티티를 나타내는 엔티티의 특성 또는 특징입니다. 예를 들면, 직원의 전화 번호는 직원의 속성 중 하나입니다. 

## 아
{: #gloss_AA}

- **어노테이션(annotation)**

    특정 텍스트 범위에 대한 정보입니다. 예를 들면, 특정 어노테이션은 회사 이름을 나타내는 텍스트 범위를 표시할 수 있습니다. 

- **어노테이션 미리 작성(pre-annotation)**

    사람에 의한 어노테이션 작성 이전에 문서 세트에 어노테이션을 작성하는 프로세스입니다. 문서에는 규칙 기반 모델, 기계 학습 모델, {{site.data.keyword.nlufull}} 또는 사전을 사용하여 어노테이션 미리 작성을 수행할 수 있습니다. 어노테이션 미리 작성은 사람 어노테이터가 더욱 신속하게 기준 실제값 문서 세트를 준비하는 데 도움을 줄 수 있습니다. 

- **어노테이션 세트(annotation set)**

    사람에 의한 어노테이션 작성에서는 워크로드를 여러 사람 어노테이터가 공유할 수 있도록 해 주는, 말뭉치에서 추출된 문서 콜렉션입니다. 기계 기반 어노테이션에서는 블라인드 데이터, 훈련 데이터 또는 테스트 데이터로 사용할 수 있는 문서 콜렉션입니다. 

- **어노테이션 작성 프로세스 관리자(annotation process manager)**

    작업공간 내의 전체 어노테이션 라이프사이클 활동을 관리하는 역할입니다. 작업공간에 추가된 프로젝트 관리자는 일반적으로 어노테이션 작성 프로세스 관리자 활동을 수행합니다. 

- **어노테이터(annotator)**

    [사람 어노테이터(human annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) 및 [기계 학습 어노테이터(machine learning annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_M)를 참조하십시오. 

- **어노테이터 간 일치(inter-annotator agreement)**

    둘 이상의 문서 세트에 포함된 특정 문서가 얼마나 유사하게 어노테이션 작성되었는지 나타내는 수치입니다. 

- **엔티티(entity)**

    1. 엔티티 유형으로 어노테이션 작성되는 멘션입니다. 
    1. 정보 저장의 대상이 되는 사용자, 오브젝트 또는 개념입니다. 
    1. 사람, 위치 또는 은행 계좌와 같은 실제 오브젝트에 대해 보유되는 세부사항 세트입니다. 엔티티는 일종의 항목입니다. 

- **엔티티 유형(entity type)**

    컨텍스트에 대한 고려 없이 멘션이 나타내는 엔티티 유형입니다. 예를 들어, 멘션 {{site.data.keyword.IBM_notm}}은 엔티티 유형 ORGANIZATION으로 어노테이션 작성될 수 있습니다. 

    엔티티-관계 모델에서 엔티티 유형은 사람 또는 장소의 이름과 같이, 모델링되는 항목 또는 멘션이 가리키는 항목입니다. 엔티티 유형이 다르면 "성" 또는 "고향"과 같이 속성 세트 또한 달라지며, 이들은 "에서 거주함"과 같은 관계로 연결됩니다. 엔티티 유형은 독립적으로 존재하며 고유하게 식별할 수 있습니다. 

- **역할(role)**

    멘션의 컨텍스트 의미를 제공하는 속성입니다. 예를 들어, 구문 "I went to {{site.data.keyword.IBM_notm}} today"에서 {{site.data.keyword.IBM_notm}}은 멘션이며, 엔티티 유형은 Organization이고, 엔티티 유형의 역할은 Facility입니다. 

- **온톨로지(ontology)**

    특정 관심 분야에 존재하는 오브젝트, 개념, 기타 엔티티와 이들 간의 관계에 대한 표현의 명시적 정규 명세입니다. 

- **용어 색인(concordance)**

    문서 및 어노테이션 세트 전체에서 동일한 멘션이 동일한 엔티티 유형으로 어노테이션 작성될 수 있도록 하는 수단을 제공합니다. 용어 색인은 사람 어노테이터가 특정 멘션의 각 발생에 수동으로 레이블을 지정할 필요 없이 해당 멘션의 여러 발생에 대해 일관성을 유지할 수 있도록 도와줍니다. 

- **유형 시스템(type system)**

    유형 시스템은 문서에서 발견할 수 있는 오브젝트의 유형을 정의합니다. 유형 시스템은 가능한 모든 엔티티 유형과 이러한 엔티티 유형 간의 관계를 정의합니다. 유형 시스템에는 다양한 유형을 원하는 만큼 정의할 수 있습니다. 유형 시스템은 일반적으로 도메인 및 애플리케이션에 대해 고유합니다. 

## 자
{: #gloss_JA}

- **자연어 처리(natural language processing)**

    자연어의 처리 및 조작에 내재된 문제점을 연구하고, 컴퓨터가 사람의 언어를 이해하는 능력을 증가시키는 것을 목표로 하는 인공지능 및 어학의 분야입니다. 

- **재현율(recall)**

    모든 사용 가능한 관련 결과 중 리턴된 관련 결과의 백분율을 지정하는 수치입니다. 민감도를 나타내는 수치인 재현율은 올바른 긍정 결과의 수를 리턴되어야 하는 긍정 결과의 수로 나눈 수입니다. 정확도는 정밀도와 재현율을 모두 사용했을 때 가장 정확하게 측정됩니다. [정확도(accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) 및 [정밀도(precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_P)도 참조하십시오. 

- **정밀도(precision)**

    관계 있는 결과의 비율을 지정하는 수치입니다. 정밀도는 긍정 예측 값으로, 올바른 긍정 결과의 수를 모든 긍정 결과의 수로 나눈 수입니다. 정확도는 정밀도와 재현율을 모두 사용했을 때 가장 정확하게 측정됩니다. [정확도(accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) 및 [재현율(recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_R)도 참조하십시오. 

- **정확도(accuracy)**

    기계 학습 모델에 의해 작성된 어노테이션의 정확성에 대한 수치입니다. [정밀도(precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) 및 [재현율(recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_R)도 참조하십시오. 

- **정확도 분석(accuracy analysis)**

    기계 학습 모델 점수를 분석하여 정확도를 개선하기 위해 변경을 수행해야 하는지 판별하는 것입니다. 

- **지식 그래프(knowledge graph)**

    유형 지정된 엔티티, 엔티티 간의 관계, 해당 특성 및 계층 분류를 통합하는 모델로, 특정 도메인의 개념 조직을 나타냅니다. 지식 그래프 저장소가 구조화되거나 구조화되지 않은 데이터 소스의 입력으로 로드되면, 사용자 및 애플리케이션은 지식 그래프에 액세스하여 특정 도메인에 대한 지식의 주요 요소를 탐색하고, 상호작용을 탐색하고, 추가 관계를 발견할 수 있습니다. 

## 차
{: #gloss_CHA}

- **참 긍정(true positive)**

    올바른 것으로 예상되었으며 실제로도 올바른 응답 또는 어노테이션입니다. 

- **참 부정(true negative)**

    올바르지 않은 것으로 예상되었으며 실제로도 올바르지 않은 응답 또는 어노테이션입니다. 

- **처리 엔진 아카이브(processing engine archive)**

    UIMA(Unstructured Information Management Architecture) 분석 엔진과 이를 사용자 정의 분석에 사용하는 데 필요한 모든 리소스를 포함하는 `.pear` 아카이브 파일입니다. 

## 카
{: #gloss_KA}

- **큐레이션(curate)**

    특정 주제와 관련된 컨텐츠를 선택하고, 수집하고, 보존하고, 유지보수하는 것입니다. 큐레이션은 데이터에 가치를 확립하고, 유지보수하며 추가함으로써 신뢰할 수 있는 정보 및 지식으로 변환합니다. 

## 타
{: #gloss_TA}

- **테스트 데이터(testing data)**

    수집 및 훈련 후 시스템 메트릭을 평가하는 데 사용할 수 있는, 어노테이션 작성된 문서 세트입니다. [블라인드 데이터(blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) 및 [훈련 데이터(training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)도 참조하십시오. 

- **특성(feature)**

    유형의 데이터 멤버 또는 속성입니다. 

## 파
{: #gloss_PA}

- **판정(adjudication)**

    여러 사람 어노테이터가 동일한 문서에 추가한 어노테이션을 비교하여 어노테이션 충돌을 해결하는 반복 프로세스입니다. 

- **표제어(lemma)**

    단어의 표준화된 형태 또는 규범적 형태입니다. 일반적으로 표제어는 명사 또는 동사의 근본적이며 변화하지 않은 형태입니다. 예를 들어, 용어 'organizing' 및 'organized'의 표제어는 'organize'입니다. [사전(dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) 및 [표층형(surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_S)도 참조하십시오. 

- **표층형(surface form)**

    말뭉치에 포함되어 있는 단어 또는 다중 단어 단위 그대로의 형태입니다. 예를 들어, 표제어 'organize'의 몇 가지 표층형에는 용어 'organizing' 및 'organized'가 있습니다. [dictionary(사전)](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) 및 [표제어(lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_L)도 참조하십시오. 

- **품사(part of speech)**

    사전에서, 개별 어휘 항목에는 품사(POS) 태그가 지정됩니다. 예를 들면, 단어 'fly'는 동사 또는 명사로 식별될 수 있습니다. 

## 하
{: #gloss_HA}

- **하위 유형(subtype)**

    다른 유형(상위 유형)을 확장하거나 구현하는 유형입니다. 

- **헤드룸 분석(headroom analysis)**

    정확도 분석 중에 식별된 몇몇 유형의 문제점을 해결하여 기대할 수 있는 정확도, 정밀도 또는 재현율 개선 정도를 판별하는 프로세스입니다. 

- **혼동 매트릭스(confusion matrix)**

    어노테이션 작성된 문서 세트에 대한 자세한 수치 분석을 제공하는 표입니다. 이 표는 기계 학습 모델이 추가한 어노테이션을 기준 실제값의 어노테이션과 비교하는 데 사용됩니다. 이 표는 [거짓 긍정(false positive)](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [거짓 부정(false negative)](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [참 긍정(true positive)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) 및 [참 부정(true negative)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)의 수를 보고합니다. 

- **훈련(train)**

    시스템이 특정 도메인에서 기능할 수 있도록 해 주는 컴포넌트(예: 말뭉치 컨텐츠, 기계 학습 모델을 생성하는 훈련 데이터, 프로그래밍 방식 알고리즘, 어노테이터 및 기타 기준 실제값 컴포넌트)를 사용하여 {{site.data.keyword.watson}} 인스턴스를 설정한 후 정확도 분석에 따라 이러한 컴포넌트를 개선하고 업데이트하는 프로세스입니다. 

- **훈련 데이터(training data)**

    기계 학습 어노테이터를 훈련시키는 데 사용할 수 있는, 어노테이션 작성된 문서 세트입니다. [블라인드 데이터(blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) 및 [테스트 데이터(testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)도 참조하십시오. 

## F
{: #gloss_F}

- **Fleiss Kappa 점수(Fleiss Kappa score)**

    겹치는 문서에서 여러 사람 어노테이터가 얼마나 일관되게 동일한 어노테이션을 적용했는지 나타내는 수치입니다. Fleiss Kappa 점수의 최고 값은 1이며 최악의 값은 0입니다. 

- **F1 점수(F1 score)**

    점수 계산을 위해 정밀도와 재현율을 모두 고려하는, 테스트의 정확도에 대한 수치입니다. F1 점수는 정밀도와 재현율 값의 가중치 적용된 평균으로 해석할 수 있습니다. F1 점수의 최고 값은 1이며 최악의 값은 0입니다. 






