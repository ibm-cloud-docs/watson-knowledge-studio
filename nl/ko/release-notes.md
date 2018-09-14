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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}하십시오.
{: tip}

# 릴리스 정보
{: #release-notes}

{{site.data.keyword.knowledgestudiofull}}에는 다음과 같은 새로운 기능 및 변경사항이 있습니다.
{: shortdesc}

## 2018년 8월
{: #august2018}

### 새로운 기능 및 변경사항
{: #new-august2018}

- 더 이상 사용되지 않는 {{site.data.keyword.IBM_notm}} Marketplace 플랫폼에서 [{{site.data.keyword.cloud_notm}} 플랫폼 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}으로 표준 플랜 인스턴스의 자동화된 마이그레이션을 위한 새 옵션이 도입되었습니다.
더 이상 사용되지 않는 플랫폼에 표준 인스턴스가 있는 경우에는 마이그레이션하는 옵션이 있습니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}}로 마이그레이션](/docs/services/watson-knowledge-studio/client-migration.html)을 참조하십시오. 

## 2018년 7월
{: #july2018}

### 새로운 기능 및 변경사항
{: #new-july2018}

- [Cloud Foundry *조직* ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}에 의해 관리되는 모델에 추가하여, [IAM *리소스 그룹* ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window}에 의해 관리되는 {{site.data.keyword.knowledgestudioshort}} 인스턴스의 모델을 포함하도록 **Deployed Models** 페이지가 업데이트되었습니다. 

   배치된 모델 페이지에서 보는 내용은 {{site.data.keyword.knowledgestudioshort}} 인스턴스를 호스팅하는 [지역 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/resources/services_region.html){: new_window}에 따라 다릅니다. 해당 지역에서 두 액세스 관리 방법 모두로 관리되는 인스턴스를 지원하는 경우에는 각 방법마다 탭이 표시됩니다. IAM에 의해 관리되는 인스턴스의 모델은 **Resource Groups** 탭에 나열되어 있습니다. Cloud Foundry에 의해 관리되는 인스턴스의 모델은 **Organizations** 탭에 나열되어 있습니다. 

  해당 지역에서 액세스 관리 방법 중 하나로만 관리되는 인스턴스를 지원하면 하나의 액세스 관리 방법만 적용되므로 하나의 모델 목록만 표시됩니다. 

   **Deployed Models** 페이지를 보려면 오른쪽 상단 메뉴 표시줄의 **Settings** 메뉴에서 **Manage deployed models**를 클릭하십시오. **Deployed Models** 페이지에서 모델 배치 취소에 대한 정보는 [기계 학습 모델 배치 취소](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) 및 [규칙 기반 모델 배치 취소](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)를 참조하십시오. 

- 탐색이 {{site.data.keyword.knowledgestudioshort}} 워크플로우와 보다 잘 맞도록 변경되었습니다. 또한 다음 기능이 재구성되었습니다.

    - 이전 버전에서 사전의 관리는 프리어노테이터 페이지의 일부로서 포함되었습니다. 이제 사전의 관리는 탐색의 자산 섹션에 있는 사전 페이지에 있습니다. 
    - 이전 버전에서는 사람 어노테이션 기능이 탐색의 문서 어노테이션 섹션에 있는 멘션, 관계 및 상호 참조 탭 간에 분배되었습니다. 이제 이 기능은 탐색의 기계 학습 모델 섹션에서 어노테이션 태스크 페이지 아래에 병합되었습니다. 
    - 이전 버전에서 사람 어노테이션 태스크를 관리하려면 자산 & 도구 > 문서 페이지 아래의 태스크 탭을 찾았습니다. 이제는 탐색의 기계 학습 모델 섹션에 있는 어노테이션 태스크 페이지에서 태스크를 추가하고 기존 태스크를 관리합니다. 
    - 이전 버전에서는 규칙, 정규식 및 사전 페이지가 탐색의 문서 어노테이션 섹션에서 별도의 페이지였습니다. 이제 이 기능은 탐색의 규칙 기반 모델 섹션에서 규칙 페이지 아래에 병합되었습니다. 

    탐색 변경사항에 대한 자세한 내용은 그림 1과 표 3을 참조하십시오. 

![이전 탐색(왼쪽) 및 새 탐색(오른쪽)의 화면 캡처입니다.](images/nav3-0718.svg "이전 탐색 및 새 탐색의 화면 캡처입니다. 변경 세부사항은 표 3과 이전 텍스트에 나열되어 있습니다.") 그림 1. 이전 탐색(왼쪽) 및 새 탐색(오른쪽)의 화면 캡처.

|기능 |이전 위치|현재 위치|
|---------|--------------------------|----------------------|
|어노테이션 작성 태스크 |자산 & 도구 > 문서 > 태스크 | 기계 학습 모델 > 어노테이션 태스크|
| 상호 참조 탭 |문서 어노테이션| 기계 학습 모델 > 어노테이션 태스크 > 태스크 > 어노테이션 세트 > 문서 |
|사전 페이지(관리)| 자산 & 도구 > 프리어노테이터 > 사전 관리|자산 |
| 사전 탭 (규칙 기반 모델의 클래스로 맵핑) |문서 어노테이션|규칙 기반 모델 > 규칙|
|문서 페이지|자산 & 도구 |자산 |
|엔티티 유형 페이지 |자산 & 도구 |자산 |
|멘션 탭 |문서 어노테이션| 기계 학습 모델 > 어노테이션 태스크 > 태스크 > 어노테이션 세트 > 문서 |
|성능 페이지|모델 관리|기계 학습 모델 |
|프리어노테이터 페이지 |자산 & 도구 | 기계 학습 모델 > 어노테이션 미리 작성|
| Regex 탭|문서 어노테이션|규칙 기반 모델 > 규칙|
|관계 유형 페이지 |자산 & 도구 |자산 |
|관계 탭 |문서 어노테이션| 기계 학습 모델 > 어노테이션 태스크 > 태스크 > 어노테이션 세트 > 문서 |
|Rules 탭 |문서 어노테이션|규칙 기반 모델|
|태스크 탭|자산 & 도구 > 문서| 기계 학습 모델 > 어노테이션 태스크|
| 버전 페이지(기계 학습 모델) |모델 관리|기계 학습 모델 |
| 버전 페이지(규칙 기반 모델) |모델 관리|규칙 기반 모델|
{: caption="표 3. 탐색 변경사항(2018년 7월)" caption-side="top"}

## 2018년 5월
{: #may2018}

### 새로운 기능 및 변경사항
{: #new-may2018}

- 시드니 지역의 서비스 인스턴스가 미국 남부 지역에 나타나지 않도록 하는 구성 문제가 해결되었습니다.
- 모델 배치 창에서 배치할 지역이 {{site.data.keyword.iamlong}} *리소스 그룹* 및 Cloud Foundry *영역*을 둘 다 지원하는 경우, 목록을 보려면 서비스 인스턴스가 사용하는 액세스 관리 방법을 선택해야 합니다. Cloud Foundry 및 {{site.data.keyword.iamshort}}에 대한 자세한 정보는 [리소스 그룹 및 액세스 관리 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}를 참조하십시오. 
- 서비스 세부사항 페이지에서 데이터 콜렉션 설정이 추가되었습니다. 데이터 콜렉션에 대한 자세한 정보는 [문제점 해결, 지원 및 FAQ](/docs/services/watson-knowledge-studio/troubleshooting.html#content)를 참조하십시오. 
- 대만어 지원이 추가되었습니다. 
- Admin 역할이 있는 사용자는 이제 사용되는 작업공간의 수를 확인할 수 있습니다. 이 정보는 서비스 세부사항 페이지에서 사용 가능합니다.
- {{site.data.keyword.alchemylanguagefull}}의 경우는 더 이상 모델 배치에 사용될 수 없습니다. 자세한 정보는 [{{site.data.keyword.alchemyapishort}} 서비스 폐기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}를 참조하십시오. 
- 이제 작업공간을 삭제하는 경우 조치를 확인하는 단계가 있습니다. 이 확인 단계를 이용하여 실수로 삭제하는 일이 없기를 바랍니다.
- 문서에 데이터 개인정보처리방침에 대한 일부 새 세부사항이 포함되었습니다. [정보 보안](/docs/services/watson-knowledge-studio/information-security.html)에서 자세히 읽어보십시오. 

## 2018년 4월
{: #april2018}

### 새로운 기능 및 변경사항
{: #new-april2018}

- {{site.data.keyword.knowledgestudioshort}} 무료 사용제가 라이트 플랜으로 대체되었습니다. 자세한 정보는 [{{site.data.keyword.knowledgestudioshort}}에서 라이트 플랜 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}을 참조하십시오. 

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

|{{site.data.keyword.IBM_notm}} Marketplace의 용어 |{{site.data.keyword.Bluemix_notm}}의 용어 |참고 |
|----------|----------|----------|
|_프로젝트_ |_작업공간_ |이 용어는 {{site.data.keyword.Bluemix_notm}}에서도 _프로젝트_라는 용어를 사용하여 변경되었습니다. |
|_가져오기_ 및 _내보내기_ |_업로드_ 및 _다운로드_ |용어 _가져오기_ 및 _내보내기_는 이제 문서 및 엔티티 유형과 관련되어 사용되는 경우 _업로드_ 및 _다운로드_라고 합니다. 용어 _내보내기_는 모델을 {{site.data.keyword.watson}} Explorer와 같은 애플리케이션에 내보내는 경우 여전히 사용됩니다. |
{: caption="표 1. {{site.data.keyword.Bluemix_notm}} 버전의 용어 변경사항" caption-side="top"}

- {{site.data.keyword.Bluemix_notm}} [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스의 경우 문서의 일부 태스크 단계가 새 인터페이스와 일치하지 않습니다. 이 문서의 내용은 현재 {{site.data.keyword.IBM_notm}} Marketplace의 인터페이스와 일치합니다. 다음 표에는 [시범](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) 릴리스의 탐색 변경사항이 요약되어 있습니다.

|기능 |{{site.data.keyword.IBM_notm}} Marketplace에서의 위치 |{{site.data.keyword.Bluemix_notm}}에서의 위치
|----------|----------|----------|
|Annotator Component 탭 |기본 탐색 |더 이상 존재하지 않음 |
|Confusion Matrix 테이블(Statistics 탭) |Annotator Component > Details |Model Management > Performance > Detailed Statistics 링크 |
|Dictionaries 탭 |기본 탐색 |Assets & Tools > Pre-annotators |
|Dictionary Mapping 페이지 |Annotator Component |Assets & Tools > Pre-annotators |
|Entity Types 탭 |Type System |Assets & Tools > Entity Types |
|Ground Truth Editor(기준 실제값 편집기) |Human Annotation |Document Annotation 탭 |
|Ground Truth Editor Settings 탭 |Human Annotation |Settings > Document Annotation Settings |
|모델, 실행 및 내보내기 |Annotator Component |Model Management > Versions |
|Rules 탭 |기본 탐색 |Document Annotation > Rules |
|Statistics 탭 |Annotator Component > Details |Model Management > Performance |
|Summary 테이블(Statistics 탭) |Annotator Component > Details |Model Management > Performance > Detailed Statistics 링크 |
|Type Mapping 탭(규칙 기반 모델용) |Annotator Component > Details |Model Management > Versions > Rule-based model type mapping |
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
