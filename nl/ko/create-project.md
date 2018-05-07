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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/create-project.html){: new_window}.
{: tip}

# 작업공간 작성
{: #create-project}

사용자 정의 모델 빌드의 첫 번째 단계는 작업공간을 작성하는 것입니다.
{: shortdesc}

## 이 태스크에 대한 정보

사용자는 빌드하여 사용할 각 모델에 대해, 모델을 빌드하는 데 필요한 아티팩트 및 리소스를 포함하는 하나의 작업공간을 작성합니다. 그 후 모델을 훈련시켜, 사용하기 위해 외부 서비스에 배치할 수 있는 사용자 정의 모델을 작성합니다. 

작업공간을 작성하기 전에 다음 질문에 응답하십시오. 

- **어떤 유형의 모델을 작성할 것입니까?**

    - 기계 학습 모델: 통계적 접근법을 사용하여 문서 내에서 엔티티 및 관계를 찾습니다. 이 유형의 모델은 데이터 양의 변화에 적응할 수 있습니다. 
    - 규칙 기반 모델: 선언적 접근법을 사용하여 문서 내에서 엔티티를 찾습니다. 이 유형의 모델은 예측, 이해 및 유지보수가 더 용이합니다. 그러나 새 데이터로부터 학습하지는 않습니다. 이 모델은 찾도록 훈련된 패턴만 발견할 수 있습니다. 

    > **참고:** 한 규칙 기반 모델과 한 기계 학습 모델을 모두 포함하는 하나의 작업공간을 작성할 수도 있습니다. 

- **어떤 서비스가 모델을 사용합니까?**

    사용자 정의 모델과 함께 사용할 수 있는 기타 {{site.data.keyword.watson}} 서비스에 대한 정보는 [{{site.data.keyword.watson}} 서비스 통합](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg)을 참조하십시오. 

## 프로시저

작업공간을 작성하려면 다음 단계를 완료하십시오. 

1. {{site.data.keyword.knowledgestudioshort}} 관리자로 로그인하여 **Create Workspace**를 클릭하십시오. 

    > **참고:** 프로젝트 관리자 역할이 있는 사용자는 작업공간 작성을 제외한 거의 모든 태스크를 수행할 수 있습니다. 관리자가 먼저 작업공간을 작성한 후 여기에 프로젝트 관리자를 지정해야 합니다. 

1. 작업공간에 이름을 지정하십시오. 도메인 컨텐츠 또는 모델의 용도를 나타내는 간단한 이름을 선택하십시오. 필요한 경우에는 작업공간 이름을 나중에 변경할 수 있습니다. 
1. 작업공간의 문서에서 사용하는 언어를 식별하십시오. 작업공간에 추가하는 문서, 그리고 작성하거나 업로드하는 사전은 지정하는 언어로 되어 있어야 합니다. 
1. 선택사항: 애플리케이션이 사용하는 토크나이저를 기본 기계 학습 기반 토크나이저에서 변경하려는 경우에는 **Advanced Options** 섹션을 펼치고 **Dictionary-based tokenizer**를 선택하십시오. 

    기본 토크나이저는 사전 기반 토크나이저보다 더 발전된 것으로, 기계 학습 기능을 사용하여 소스 문서의 언어로 수행된 통계적 학습을 기반으로 소스 문서의 토큰을 식별합니다. 이는 언어의 더 자연스럽고 미묘한 패턴을 이해하므로 토큰을 더 정확하게 식별합니다. 사전 기반 토크나이저는 언어 규칙을 기반으로 합니다. 세부사항은 [토크나이저](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)를 참조하십시오. 

1. 선택사항: 작업공간에 프로젝트 관리자를 추가하려는 경우에는 **Advanced Options** 섹션을 펼치고 프로젝트 관리자로 추가할 사용자의 이름을 목록에서 선택하십시오. 관리자는 작업공간을 편집하여 나중에 프로젝트 관리자를 추가하거나 제거할 수 있습니다. 

    인스턴스의 User Account Management 페이지에서 프로젝트 관리자 역할에 지정한 사용자의 이름만 표시됩니다. 사용자 추가에 대한 자세한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오. 

    > **참고:** 무료 사용제를 보유하고 있는 경우에는 이 단계를 건너뛰십시오. 이러한 사용자는 다른 사용자를 추가할 수 없으므로 다른 사용자에게 프로젝트 관리자 역할을 지정할 수 없습니다. 이러한 사용자는 별도의 프로젝트 관리자가 필요하지 않습니다. 사용자는 관리자로서 프로젝트 관리자가 일반적으로 수행하는 모든 태스크를 수행할 수 있습니다. 

1. **Create**를 클릭하십시오. 

## 다음에 수행할 작업

작업공간이 작성되면 작업공간 리소스 구성을 시작할 수 있습니다. 

관리자는 나중에 작업공간 설명 또는 작업공간 이름을 변경하거나, 프로젝트 관리자를 추가하거나 제거하기 위해 작업공간을 편집할 수 있습니다. {{site.data.keyword.knowledgestudioshort}} 홈 페이지의 작업공간 타일에서 **메뉴 표시** 아이콘을 클릭하고 **Edit** 메뉴 옵션을 선택하십시오. 

**관련 개념**:

[다른 작업공간의 리소스 업로드](/docs/services/watson-knowledge-studio/exportimport.html)

**관련 참조**:

[다중 언어 지원](/docs/services/watson-knowledge-studio/language-support.html)

## 토크나이저
{: #wks_tokenizer}

토크나이저는 문자를 토큰으로, 토큰을 문장으로 그룹화합니다. 토큰은 단어와 막연히 동격입니다. 

토크나이저가 문서의 토큰을 식별하기 위해 취해야 하는 조치는 문서의 언어에 따라 달라집니다. 영어의 경우 토큰은 보통 문장에서 공백으로 구분된 단어와 동일시됩니다. 그러나 토큰이 항상 단어와 일대일로 일치하는 것은 아니며, 일부 경우에는 다른 텍스트 요소 또한 토큰으로 간주됩니다. 예를 들어, 문장 끝의 마침표는 토큰으로 간주되며, 축약형은 보통 두 개의 토큰으로 확장됩니다. 중국어와 같이 공백을 사용하지 않는 언어의 경우에는 토큰을 식별하는 데 더 복잡한 통계적 알고리즘이 사용됩니다. 

토큰화 프로세스는 기준 실제값 편집기에서 어노테이션을 위해 강조표시할 수 있는 문자 그룹을 결정하므로 중요합니다. 엔티티 및 관계 멘션의 어노테이션은 일반적으로 토큰 경계와 맞춰지며, 문장 내에서 레이블 지정되어야 합니다. 문장 경계를 벗어날 수는 없습니다. 

### 지원되는 유형

{{site.data.keyword.knowledgestudioshort}}는 다음 토크나이저를 지원합니다. 

- **기계 학습 기반 토크나이저(기본값)**

    이는 소스 문서의 언어로 수행된 통계적 학습을 기반으로 소스 문서의 토큰을 식별하는 더 발전된 토크나이저입니다. 이 토크나이저는 언어의 더 자연스럽고 미묘한 패턴을 담은 토큰을 찾습니다. 이 토크나이저는 사용자 정의할 수 없습니다. 

- **사전 기반 토크나이저**

    이 토크나이저는 언어 사전을 기반으로 합니다. 이는 소스 문서 언어의 규칙을 따르는 토큰을 찾습니다. 고급 사용자만 이 토크나이저를 사용자 정의할 수 있습니다. 

작업공간을 작성할 때 사용할 토크나이저를 선택해야 합니다. 나중에 다른 토크나이저로 전환할 수는 없습니다. 최선의 결과를 위해서는 기본 토크나이저를 사용하십시오. 결정론적 사전 메커니즘을 통해 토크나이저 작동을 수정하려는 고급 사용자만 사전 기반 토크나이저를 선택할 수 있습니다. 이러한 사용자는 그 후 사전에 새 항목을 추가하여 해당 토크나이저를 사용자 정의할 수 있습니다. 그러나 사전에 새 단어를 추가하면 변경사항이 기계 학습 모델에 의도하지 않은 방식으로 영향을 줄 수 있으므로 사용자 정의는 주의하여 수행해야 합니다. 

## 입력, 출력 및 제한사항 요약
{: #wks_formats}

다양한 모델 개발 단계는 다양한 입력을 필요로 하며 다양한 결과를 작성합니다. 

이 표에는 각 모델 개발 프로세스 단계에서 일반적으로 수행하는 활동, 지원되는 입력 파일 형식, 작성될 수 있는 출력, 크기 한계 및 기타 요구사항이 요약되어 있습니다. 

### 모든 모델 유형

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e252" class="stentry thleft thbot">태스크</th>
<th valign="bottom" align="left" id="d25459e254" class="stentry thleft thbot">일반적인 용도</th>
<th valign="bottom" align="left" id="d25459e256" class="stentry thleft thbot">지원되는 입력 형식</th>
<th valign="bottom" align="left" id="d25459e258" class="stentry thleft thbot">지원되는 출력 형식</th>
<th valign="bottom" align="left" id="d25459e260" class="stentry thleft thbot">한계 및 요구사항</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">유형 시스템 관리</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">유형 시스템을 작성하거나 기존 유형 시스템을 업로드 및 수정합니다. </p><p class="p">도메인에 대한
엔티티 유형 및 관계 유형을 정의합니다. </p>
<p class="p">유형 시스템을 시각화하여 볼 수는
없습니다. </p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Watson Knowledge Studio 작업공간에서
다운로드한
JSON
파일</p></li>
<li class="li"><p class="p wrapper">HAT(Human Annotation Tool)에서 다운로드한 ZIP 파일</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">JSON</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">사람이 작성한 어노테이션이 시각적으로 과부하를 일으키지 않도록, 엔티티 유형과 관계 유형은 각각 50개까지만
지정하십시오. </p><p class="p">유형 시스템 업로드에 대한 파일 크기 제한사항: 20MB</p>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">사전 관리</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">CSV 사전 파일을 읽기 전용로 업로드하거나 다른 작업공간에서 다운로드한
ZIP 사전을 업로드합니다. </p><p class="p">새 사전을 작성한 후 용어 항목의 CSV 파일을 업로드하거나 여기에
용어 항목을 추가합니다. </p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><p class="p wrapper">사전 파일:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">UTF-8 형식의 CSV 파일</p></li>
<li class="li"><p class="p wrapper">다른 작업공간에서 다운로드한 사전의 ZIP 파일</p></li>
</ul><p class="p wrapper">
용어 항목 파일:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">UTF-8 형식의 CSV 파일</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">UTF-8 형식의 CSV 파일</p></li>
<li class="li"><p class="p wrapper">다른 작업공간에서 사용할 사전의 ZIP 파일</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">파일 크기 제한사항:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">CSV 용어 항목 파일당 1MB</p></li>
<li class="li"><p class="p wrapper">CSV 읽기 전용 사전 파일당 16MB</p></li>
<li class="li"><p class="p wrapper">사전당 15,000개 항목(읽기 전용 사전 제외)</p></li>
<li class="li"><p class="p wrapper">작업공간당 64개 사전</p></li>
</ul>
</td>
</tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### 기계 학습 모델

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e331" class="stentry thleft thbot">태스크</th>
<th valign="bottom" align="left" id="d25459e333" class="stentry thleft thbot">일반적인 용도</th>
<th valign="bottom" align="left" id="d25459e335" class="stentry thleft thbot">지원되는 입력 형식</th>
<th valign="bottom" align="left" id="d25459e337" class="stentry thleft thbot">지원되는 출력 형식</th>
<th valign="bottom" align="left" id="d25459e339" class="stentry thleft thbot">한계 및 요구사항</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">문서 관리</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">적은 양의 대표적인 문서 서브세트를 업로드</p><p class="p">이전에 사람 어노테이터,
기계 학습 모델 또는 UIMA 분석 엔진에 의해 추가된 어노테이션을
포함하는
문서 업로드</p>
<p class="p">어노테이션을
위한 고가치 문서를 계산하기 위해
IBM Watson Explorer의
전체 말뭉치를 수집할 수는
없습니다. </p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">UTF-8 형식의 CSV 파일</p></li>
<li class="li"><p class="p wrapper">UTF-8 형식의 DOCXML 파일</p></li>
<li class="li"><p class="p wrapper">UTF-8 형식의 텍스트 파일</p></li>
<li class="li"><p class="p wrapper">다른 말뭉치에서 다운로드한 문서를 포함하는 ZIP 파일</p></li>
<li class="li"><p class="p wrapper">UIMA CAS XMI 형식의 문서를
포함하는
ZIP 파일</p></li>
</ul>
</td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">문서의 ZIP 아카이브 파일</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">문서당 40,000자</p></li>
<li class="li"><p class="p wrapper">작업공간당 10,000개 문서</p></li>
<li class="li"><p class="p wrapper">작업공간당 1,000개 문서 세트(어노테이션 세트 포함)</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">어노테이션 미리 작성</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">사전 또는
{{site.data.keyword.nlushort}}
프리어노테이터(pre-annotator)를 사용하여
사람에 의한 어노테이션 작성의 시작 지점을 제공합니다. </p><p class="p">IBM Watson Discovery Advisor 또는
IBM Watson Explorer에서 말뭉치에 대해
다시 어노테이션을 작성할 수는 없습니다
.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">원시 문서. </p><p class="p wrapper"><b>참고:</b> 사람 어노테이터가 이미 어노테이션을 작성한 문서에 대해 어노테이션 미리 작성을 수행하지 마십시오.
이렇게 하면 사람 어노테이터가 수행한 작업을 잃게 됩니다. </p>
</td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">부분적으로 어노테이션 작성된 문서</p></td>
<td valign="top" headers="d25459e339" class="stentry"><p class="p wrapper">없음</p></td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">문서 어노테이션</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">사람에 의한 어노테이션 작성 관리</p><p class="p">기준 실제값을 작성하기 위해 엔티티, 관계 및 상호 참조에
어노테이션 작성</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">어노테이션 작성 태스크</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">기준 실제값</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">작업공간당 256개 활성 어노테이션 작성 태스크</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">훈련 및 정제</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">지도 기계 학습 모델을 훈련시켜 구조화되지 않은 텍스트에서 도메인 고유 정보를
추출합니다. </p><p class="p">지도 기계 학습 모델을 평가하고 개선합니다. </p>
<p class="p">준 지도 또는 비지도 기계 학습 모델을
작성할 수는 없습니다. </p>
<p class="p">광범위한 기능
엔지니어링을 수행할 수 없습니다. </p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">해당사항 없음</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">기계 학습 모델</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">작업공간당 1개 기계 학습 모델</p></li>
<li class="li"><p class="p wrapper">작업공간당 10개 모델 버전</p></li>
<li class="li"><p class="p wrapper">최대 작업공간 수는 구독 플랜에 의해 결정됩니다. </p></li>
<li class="li"><p class="p wrapper">1개월당 수행할 수 있는 최대 훈련 조치 수는 구독 플랜에 의해 결정됩니다. </p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">공개</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">다른 Watson 애플리케이션에서 텍스트 추출을 수행하는 데 사용할 수 있도록

기계 학습 모델을
공개합니다. </p></td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">해당사항 없음</p></td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">모델 ID(AlchemyLanguage
또는
Watson Discovery
서비스에서
사용)</p></li>
<li class="li"><p class="p wrapper">ZIP 파일(IBM
Watson Explorer에서
사용)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry">
  <p class="p">AlchemyLanguage에 배치하려면,
    유효한 AlchemyLanguage Advanced
    플랜 키 ID가 있어야 합니다. </p>
  <p class="p">Watson Discovery 서비스에
    배치하려면 서비스 {{site.data.keyword.cloud_notm}} 영역
    및 인스턴스 이름을 알고 있어야 합니다. </p>
</td>
</tr>
</table>

### 규칙 기반 모델

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e509" class="stentry thleft thbot">태스크</th>
<th valign="bottom" align="left" id="d25459e511" class="stentry thleft thbot">일반적인 용도</th>
<th valign="bottom" align="left" id="d25459e513" class="stentry thleft thbot">지원되는 입력 형식</th>
<th valign="bottom" align="left" id="d25459e515" class="stentry thleft thbot">지원되는 출력 형식</th>
<th valign="bottom" align="left" id="d25459e517" class="stentry thleft thbot">한계 및 요구사항</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">규칙 편집기</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p">클래스, 정규식 및 규칙을 정의하는 데 사용되는 문서를 작성하거나 규칙 편집기에
업로드합니다. </p>
</td>
<td valign="top" headers="d25459e513" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">일반 텍스트(편집기에서 추가됨)</p></li>
<li class="li"><p class="p wrapper">UTF-8 형식의 CSV 파일</p></li>
<li class="li"><p class="p wrapper">모든 문서 세트에서 복사됨</p></li>
</ul>
</td>
<td valign="top" headers="d25459e515" class="stentry"><p class="p wrapper">없음</p></td>
<td valign="top" headers="d25459e517" class="stentry"><ul class="ul bullets">
<li class="li"><p class="p wrapper">작업공간당 1개 규칙 기반 모델</p></li>
<li class="li"><p class="p wrapper">문서당 5,000자</p></li>
<li class="li"><p class="p wrapper">작업공간당 100개 문서</p></li>
<li class="li"><p class="p wrapper">문서 제목의 최대 길이는 256자</p></li>
<li class="li"><p class="p wrapper">작업공간당 200개 규칙</p></li>
<li class="li"><p class="p wrapper">작업공간당 400개 클래스</p></li>
<li class="li"><p class="p wrapper">작업공간당 100개 정규식 그룹</p></li>
<li class="li"><p class="p wrapper">정규식 그룹당 100개 정규식 항목</p></li>
<li class="li"><p class="p wrapper">정규식 항목당 1,000자</p></li>
<li class="li"><p class="p wrapper">작업공간당 5개 규칙 기반 모델 버전</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">공개</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p wrapper">다른 Watson 애플리케이션에서 패턴 인식을 수행하는 데 사용되는
규칙 기반 모델을
공개합니다. </p></td>
<td valign="top" headers="d25459e513" class="stentry"><p class="p wrapper">해당사항 없음</p></td>
<td valign="top" headers="d25459e515" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">모델 ID(AlchemyLanguage
또는
Watson Discovery
서비스에서
사용)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e517" class="stentry">
  <p class="p">AlchemyLanguage에 배치하려면,
    유효한 AlchemyLanguage Advanced
    플랜 키 ID가 있어야 합니다. </p>
  <p class="p">Watson Discovery 서비스에
    배치하려면 서비스 {{site.data.keyword.cloud_notm}} 영역
    및 인스턴스 이름을 알고 있어야 합니다. </p>
</td>
</tr>
</table>
