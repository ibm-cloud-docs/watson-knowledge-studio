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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# 릴리스 정보
{: #release-notes}

{{site.data.keyword.knowledgestudiofull}}에는 다음과 같은 새로운 기능 및 변경사항이 있습니다.
{: shortdesc}

## 2018년 3월
{: #march2018}

### 새로운 기능 및 변경사항
{: #new-march2018}

- 사용자에게 액세스 권한이 있는 영역 내의 서비스에 배치된 모든 {{site.data.keyword.knowledgestudioshort}} 모델을 보여주는 **Deployed Models** 페이지를 사용할 수 있습니다. **Deployed Models** 페이지를 보려면 오른쪽 상단 메뉴 표시줄의 **Settings** 메뉴에서 **Manage deployed models**를 클릭하십시오. **Deployed Models** 페이지에서의 모델 배치 취소 및 보기에 대한 정보는 [기계 학습 모델 배치 취소](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) 및 [규칙 기반 모델 배치 취소](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)를 참조하십시오. 
- 이제 {{site.data.keyword.knowledgestudioshort}} 인터페이스의 프랑스어 번역이 사용 가능합니다. 
- 더 이상 {{site.data.keyword.alchemylanguagefull}}를 프리어노테이터(pre-annotator)로 사용할 수 없습니다. {{site.data.keyword.alchemylanguageshort}} 대신 {{site.data.keyword.nlushort}}을 사용하여 문서에 어노테이션 미리 작성을 수행할 수 있습니다. 자세한 정보는 [어노테이션 부트스트래핑](/docs/services/watson-knowledge-studio/preannotation.html)을 참조하십시오. 

## 2017년 12월
{: #december2017}

### 새로운 기능 및 변경사항
{: #new-december2017}

- {{site.data.keyword.cloud_notm}}에서 실행되는 {{site.data.keyword.knowledgestudioshort}}가 출시되었습니다. 마이그레이션 프로세스 및 스케줄에 대한 정보는 [{{site.data.keyword.cloud_notm}}로 마이그레이션](/docs/services/watson-knowledge-studio/client-migration.html)을 참조하십시오. 
- 탐색이 다시 설계되었습니다. 탐색 변경사항에 대한 세부사항은 2017년 9월 릴리스 정보의 [표 2](#september2017)를 참조하십시오. 
- 프리어노테이터로 {{site.data.keyword.nlufull}}이 추가되었습니다. 
- Service Details 페이지에 사용자 및 스토리지 관리 설정이 추가되었습니다. 사용자 추가에 대한 정보는 [팀 구성](/docs/services/watson-knowledge-studio/team.html)을 참조하십시오. 스토리지 한계 설정에 대한 정보는 [문제점 해결 > 스토리지 공간 문제](/docs/services/watson-knowledge-studio/troubleshooting.html#storage)를 참조하십시오. 
- 모델 품질 평가와 품질 개선 방법에 대한 안내를 제공하는 Performance 페이지가 추가되었습니다. 

## 2017년 11월
{: #november2017}

### 변경사항
{: #new-november2017}

- 다운로드한 말뭉치에서 일부 관계 어노테이션이 누락되는 문제를 수정했습니다. 
- 모델의 상태가 **None**인 경우 이를 배치에서 철회하지 못하는 문제를 수정했습니다. 
- 한국어에 대해 모델을 평가할 수 없는 문제를 수정했습니다. 

## 2017년 10월
{: #october2017}

### 변경사항
{: #new-october2017}

- {{site.data.keyword.Bluemix_notm}} [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스에서 브라우저 창을 새로 고쳐야 **Export** 단추를 사용할 수 있게 되는 문제를 수정했습니다. 
- {{site.data.keyword.Bluemix_notm}} [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스에서 용어 _업로드_ 및 _다운로드_에 대한 변경사항과 일치하도록 단추 레이블 및 툴팁을 수정했습니다. 유형 시스템, 문서 및 사전과 관련된 경우에는 _가져오기_ 및 _내보내기_ 대신 이러한 용어가 사용되었습니다. 
- {{site.data.keyword.Bluemix_notm}} [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스에서 {{site.data.keyword.knowledgestudioshort}} User Account Management 페이지에 있는 설명을 업데이트할 때 지연 시간이 발생하는 문제를 수정했습니다. 
- 인터페이스의 어노테이션 미리 작성 섹션에서 기계 학습 모델, 규칙 기반 모델, 사전 및 {{site.data.keyword.alchemylanguagefull}}의 기능을 명확하게 하기 위해 몇 가지 GUI가 변경되었습니다. **Run**에서 **Pre-annotate**로 단추 레이블을 변경했고, 창 제목을 **Run Annotator**에서 **Run Pre-annotation**으로 변경했으며, 사람이 문서에 어노테이션을 작성한 후에는 자동화된 어노테이션을 추가할 수 없음을 명확히 하기 위해 오류 메시지를 변경했습니다. 
- 사전 기반 토크나이저를 사용하는 프로젝트 또는 작업공간의 경우, 기준 실제값이 없는 문서를 가져오면 비어 있는 문장이 표시되는 문제를 수정했습니다. 

## 2017년 9월
{: #september2017}

### 새로운 기능 및 변경사항
{: #new-sept17}

- {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.Bluemix}}를 위한 새 프론트 엔드 사용자 경험을 [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 서비스로서 릴리스했습니다. 변경사항에는 재구성된 탐색 및 새 모델 성능 분석 페이지 등이 있습니다. 탐색 변경사항에 대한 요약은 알려진 문제의 표를 참조하십시오. 
- 중국어 및 네델란드어 지원이 추가되었습니다. 

### 알려진 문제
{: #issues-sept17}

- 규칙 기반 모델의 경우, 클래스 및 엔티티 유형을 맵핑한 후 브라우저 창을 새로 고쳐야 **Export** 단추가 사용할 수 있게 됩니다. 
- {{site.data.keyword.Bluemix_notm}} [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스의 경우 문서의 일부 용어가 새 인터페이스와 일치하지 않습니다. 이 문서의 내용은 현재 {{site.data.keyword.IBM_notm}} Marketplace의 인터페이스와 일치합니다. [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스에서는 다음 용어가 변경되었습니다. 

| {{site.data.keyword.IBM_notm}} Marketplace의 용어 | {{site.data.keyword.Bluemix_notm}}의 용어 | 참고 |
|----------|----------|----------|
| _프로젝트_ | _작업공간_ | 이 용어는 {{site.data.keyword.Bluemix_notm}}에서도 _프로젝트_라는 용어를 사용하여 변경되었습니다. |
| _가져오기_ 및 _내보내기_ | _업로드_ 및 _다운로드_ | 용어 _가져오기_ 및 _내보내기_는 이제 문서 및 엔티티 유형과 관련되어 사용되는 경우 _업로드_ 및 _다운로드_라고 합니다. 용어 _내보내기_는 모델을 {{site.data.keyword.watson}} Explorer와 같은 애플리케이션에 내보내는 경우 여전히 사용됩니다. |
{: caption="표 1. {{site.data.keyword.Bluemix_notm}} 버전의 용어 변경사항" caption-side="top"}

- {{site.data.keyword.Bluemix_notm}} [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스의 경우 문서의 일부 태스크 단계가 새 인터페이스와 일치하지 않습니다. 이 문서의 내용은 현재 {{site.data.keyword.IBM_notm}} Marketplace의 인터페이스와 일치합니다. 다음 표에는 [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스의 탐색 변경사항이 요약되어 있습니다. 

| 기능 | {{site.data.keyword.IBM_notm}} Marketplace에서의 위치 | {{site.data.keyword.Bluemix_notm}}에서의 위치
|----------|----------|----------|
|Annotator Component 탭 | 기본 탐색 | 더 이상 존재하지 않음 |
|Confusion Matrix 테이블(Statistics 탭) | Annotator Component > Details | Model Management > Performance > Detailed Statistics 링크 |
|Dictionaries 탭 | 기본 탐색 | Assets & Tools > Pre-annotators |
|Dictionary Mapping 페이지 | Annotator Component | Assets & Tools > Pre-annotators |
|Entity Types 탭 | Type System | Assets & Tools > Entity Types |
|Ground Truth Editor(기준 실제값 편집기) | Human Annotation | Document Annotation 탭 |
|Ground Truth Editor Settings 탭 | Human Annotation | Settings > Document Annotation Settings |
|모델, 실행 및 내보내기 | Annotator Component | Model Management > Versions |
|Rules 탭 | 기본 탐색 | Document Annotation > Rules |
|Statistics 탭 | Annotator Component > Details | Model Management > Performance |
|Summary 테이블(Statistics 탭) | Annotator Component > Details | Model Management > Performance > Detailed Statistics 링크 |
|Type Mapping 탭(규칙 기반 모델용) | Annotator Component > Details | Model Management > Versions > Rule-based model type mapping |
{: caption="표 2. {{site.data.keyword.Bluemix_notm}} 버전의 탐색 변경사항" caption-side="top"}

## 2017년 7월
{: #july2017}

- 일부 경우에 헤더가 사라지는 결함을 수정했습니다. 
- 인프라 컴포넌트에 대한 보안 업데이트를 적용했습니다. 

## 2017년 6월
{: #june2017}

- 특정 조건 하에서의 대규모 데이터 처리 작업의 안정성을 개선했습니다. 
- 판정 오류에 대한 결함을 수정했습니다. 

## 2017년 5월
{: #may2017}

- 프로젝트, 문서 세트와 같은 다양한 오브젝트의 이름을 바꾸는 기능을 추가했습니다. 
- 특정 {{site.data.keyword.Bluemix}} 지역에 NLU 모델을 배치하는 기능을 추가했습니다. 
- IAA에 대한 대형 테이블을 표시하는 성능을 개선했습니다. 
- 사소한 결함을 수정했습니다. 
- 보안 수정사항을 적용했습니다. 

## 2017년 4월
{: #april2017}

- {{site.data.keyword.knowledgestudioshort}} 프리미엄의 안정성을 개선했습니다. 
- 비즈니스 메트릭에 대한 사용량 분석을 추가했습니다. 

## 2017년 4월 이전 릴리스

[{{site.data.keyword.IBM_notm}} 기술 노트 #1986001 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}을 참조하십시오. 
