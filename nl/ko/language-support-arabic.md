---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크를 클릭 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/services/knowledge-studio/language-support-arabic.html){: new_window}하십시오.
{: tip}

# 아랍어 지원 구성
{: #wks_langsupp_ar}

다음 가이드라인을 읽고 {{site.data.keyword.knowledgestudioshort}}에서 아랍어 문서의 아랍 문자 형태 변형 및 숫자 형태 변형을 어떻게 처리하는지 이해하십시오.

## 이 태스크에 대한 정보

문자 형태 변형과 관련하여, 아랍 문자에는 대문자가 없지만 텍스트 문자열 내에서의 위치 및 주변 문자에 따라 문자의 형태가 변합니다. 여러 운영 체제 및 코드 페이지 변환 프로그램은 문자 형태 변형을 서로 다른 방식으로 처리합니다. Windows 시스템에서는 원형 저장이 표준이며, {{site.data.keyword.knowledgestudioshort}}는 아랍어 텍스트가 원형으로 저장된다고 가정됩니다. {{site.data.keyword.knowledgestudioshort}}에 형태 변형된 텍스트를 업로드하려는 경우에는 먼저 ICU(International Components for Unicode) API와 같은 표준 도구를 사용하여 텍스트를 원형 형태로 변환해야 합니다([http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}의 ArabicShaping 클래스 참조).

> **중요:** 몇몇 경우에는 아랍 문자가 적절한 형태로 변형되지 않으면 컨텐츠가 기준 실제값 편집기에서 올바르지 않게 표시될 수 있습니다.

숫자 형태 변형과 관련하여, {{site.data.keyword.knowledgestudioshort}}는 숫자 형태 변형을 iOS 플랫폼에서 아랍어 컨텐츠가 처리되는 방식과 마찬가지로 저장 레벨 특성으로 취급합니다. 많은 아랍어 컨텐츠는 숫자 형태 변형을 표시 레벨 특성으로 취급하는 Windows와 같은 플랫폼에서 작성되므로, 사용자는 숫자 형태 변형을 저장 레벨 특성으로 설정하기 위해 컨텐츠를 변환하거나 {{site.data.keyword.knowledgestudioshort}}를 사용할 때 Firefox 브라우저를 사용해야 합니다. Firefox에는 브라우저 레벨에서 숫자 형태 변형 환경 설정을 설정하고 브라우저에 표시되는 모든 컨텐츠에 대해 적절한 표시를 적용하는 기능이 있습니다.

## 프로시저

Firefox 브라우저에서 숫자 형태 변형을 구성하려면 다음 작업을 수행하십시오.

1. 브라우저 URL 필드에 **about:config**를 입력하십시오. Firefox에서 경고를 표시하는 경우에는 경고를 무시하는 조치를 클릭하고 계속 진행하십시오. **about:config** 특성의 편집에 대한 정보는 [http://kb.mozillazine.org/About:config_entries ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://kb.mozillazine.org/About:config_entries){: new_window}를 참조하십시오.
1. 검색 필터 필드에 `bidi`를 입력하십시오.
1. 숫자가 표시되는 방식을 제어하는 **bidi.numeral** 특성을 선택하고 Enter를 누르십시오.
1. 이 특성의 값을 필요에 따라 변경하십시오. 예를 들면, `3`을 입력한 후 **확인**을 클릭하십시오.

    - **0**: 명목 숫자(기본값)
    - **1**: 일반 컨텍스트 숫자
    - **2**: 힌디어 컨텍스트 숫자
    - **3**: 아랍어 숫자
    - **4**: 힌디어 숫자

    > **중요:** **bidi.numeral** 특성이 사용되는 경우, Firefox는 웹 페이지의 컨텐츠에서 특정 숫자 문자의 코드 포인트를 완전히 무시합니다. 

### 관련 참조

[언어 지원](/docs/services/watson-knowledge-studio/language-support.html)
