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

이 문서는 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}에 대한 문서입니다. 이전 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 버전에 대한 문서를 보려면 [이 링크 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")를 클릭하십시오](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}.
{: tip}

# 다른 작업공간의 리소스 업로드
{: #exportimport}

더욱 빠르게 모델을 작성하기 위해, 사용자는 다른 작업공간에서 다운로드한 문서(기준 실제값 어노테이션이 있거나 없는), 유형 시스템 및 사전과 같은 리소스를 업로드할 수 있습니다.
{: shortdesc}

여러 리소스를 개별적으로 다운로드하고 업로드하는 기능은 모델을 유연하게 디자인하고 작성할 수 있게 해 줍니다. 예를 들면, 유형 시스템을 디자인하고 사람에 의한 어노테이션 작성을 수행하기 위해 한 작업공간을 작성한 후, 다른 사용자가 있는 별도의 {{site.data.keyword.knowledgestudioshort}} 인스턴스에 별도의 작업공간을 작성하여 기계 학습 모델을 훈련시킬 수 있습니다. 리소스(사람 어노테이터가 작성한 기준 실제값 포함)를 업로드하는 기능은 이러한 시나리오를 가능하게 해 줍니다. 

기계 학습 모델은 다운로드하거나 업로드할 수 없습니다. 대신 한 작업공간에서 모델을 작성하는 데 사용된 모든 아티팩트를 다운로드하여 새 작업공간에 업로드할 수 있습니다. 새 작업공간에서 훈련을 다시 실행하여 모델을 다시 작성할 수 있습니다. 새 모델은 동일한 아티팩트 세트로 훈련되었으므로 원본 모델과 유사한 결과를 작성합니다. 

다운로드하는 파일은 운영 체제로부터 독립적입니다. 파일을 다운로드하고 업로드하는 {{site.data.keyword.knowledgestudioshort}} 인스턴스에서 서로 다른 Linux 버전을 사용해도 괜찮습니다. 

## 유형 시스템
{: #wks_exportimport_expimp_type}

유형 시스템을 다운로드하려면 **Assets & Tools** > **Entity Types** 페이지를 열고 **Download Types**를 클릭하십시오. 시스템이 `types-ID.json`이라는 파일을 작성하고 이 파일을 로컬 시스템으로 다운로드할지 묻는 프롬프트를 표시합니다. 이 유형 시스템을 새 작업공간에서 사용하려면 **Entity Types** 페이지를 열고 다운로드한 `JSON` 파일을 업로드하십시오. 

## 사전
{: #wks_exportimport_expimp_dict}

하나 이상의 사전을 다운로드하려면 **Assets & Tools** > **Pre-annotators** > **Dictionaries** 탭을 선택하고 **Download Dictionaries**를 클릭하십시오. 다운로드하는 각 사전에 대해, 시스템은 `dictionary name_timestamp.csv`라는 파일을 작성하고 이러한 파일을 `workspace name_dictionary_timestamp.zip`이라는 `ZIP` 파일로 결합한 후 이 파일을 로컬 시스템으로 다운로드할지 묻는 프롬프트를 표시합니다. 사전을 열고 **Download**를 클릭하여 개별 사전을 다운로드할 수도 있습니다. 사전 CSV 파일로 업로드한 미리보기 전용 사전은 다운로드할 수 없습니다. 

다운로드한 사전을 새 작업공간에 업로드하려면 먼저 이전 작업공간에서 유형 시스템을 다운로드하여 새 작업공간에 업로드해야 합니다. 유형 시스템 및 사전의 소스는 같은 {{site.data.keyword.knowledgestudioshort}} 작업공간이어야 하며, 사전을 업로드하기 전에 먼저 유형 시스템이 새 작업공간에 있어야 합니다. 

사전을 업로드하려면 **Dictionaries** 탭을 열고 다운로드한 `CSV` 파일을 추가하거나 `ZIP` 파일을 업로드하십시오. 

## 문서
{: #wks_exportimport_expimp_doc}

말뭉치에 추가한 문서를 다운로드하려면 **Assets & Tools** > **Documents** > **Document Sets** 탭을 열고 **Download Document Sets**를 클릭하십시오. 시스템이 `corpus-ID.zip`이라는 파일을 작성하고 이 파일을 로컬 시스템으로 다운로드할지 묻는 프롬프트를 표시합니다. 이 `ZIP` 파일은 말뭉치 내의 모든 문서를 포함하고 있습니다. 어노테이션 세트에 추가된 어노테이션은 해당 어노테이션 세트가 승인되어 기준 실제값으로 승격된 후에만 이 ZIP 파일에 포함됩니다. 

> **제한사항:** 어노테이션 미리 작성이 수행된 문서는 다운로드될 때 읽을 수 없는 형식으로 숨겨집니다. 이러한 문서의 사람에 의한 어노테이션 작성을 통해 추가된 어노테이션 또한 읽을 수 없습니다. 

기준 실제값을 포함하는 문서를 새 작업공간에 업로드하려면 먼저 이전 작업공간에서 유형 시스템을 다운로드하여 새 작업공간에 업로드해야 합니다. 유형 시스템 및 문서의 소스는 같은 {{site.data.keyword.knowledgestudioshort}} 작업공간이어야 하며, 기준 실제값 어노테이션을 업로드하려기 전에 먼저 유형 시스템이 새 작업공간에 있어야 합니다. 

문서를 업로드하려면 새 작업공간의 **Document Sets** 탭을 열고 **Upload Document Sets**를 클릭한 후 다운로드한 말뭉치 `ZIP` 파일을 선택하십시오. **Upload**를 클릭하기 전에 업로드되는 문서의 기준 실제값 어노테이션 포함 또는 제외 여부를 지정하십시오. 문서를 다운로드하기 전에 기준 실제값으로 승격된 어노테이션만 업로드됩니다. 

**관련 개념**:

[유형 시스템](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[사전](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[기계 학습 어노테이터를 위한 문서](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[규칙 기반 어노테이터를 위한 문서](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
