---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}.
{: tip}

# Pré-anotação de documentos
{: #wks_tutboot_intro}

Este tutorial ajuda você a entender como pré-anotar documentos, que autoinicializa o processo de anotação de anotação humana.
{: shortdesc}

## Aprendendo objetivos
{: #objectives}

Depois de concluir o tutorial, você saberá como pré-anotar documentos com um modelo de aprendizado de máquina.

A conclusão do tutorial deve levar aproximadamente 5 minutos. Se você explorar outros conceitos relacionados a este tutorial, ele poderá levar mais tempo para ser concluído.

## Antes de Começar
{: #prereqs}

- Você está usando um navegador suportado. Para obter informações, veja [Requisitos do navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- Você concluiu com sucesso a [Introdução ao {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html), que abrange a criação de uma área de trabalho, a criação de um sistema de tipos e a inclusão de um dicionário.
- Você concluiu com êxito [Criando um modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Deve-se ter pelo menos um ID do usuário na função Administrador ou Gerente de projeto. Para obter informações sobre funções de usuário, consulte [Funções de usuário no {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Resultados
{: #results}

Depois de concluir este tutorial, você terá um conjunto de documentos parcialmente anotados. Em seguida, será possível designar os documentos aos anotadores humanos para concluir o trabalho de anotação.

## Lição 1: pré-anotando novos documentos com um modelo de aprendizado de máquina
{: #wks_tutboot_ml}

Nesta lição, você aprenderá como usar modelo de aprendizado de máquina para pré-anotar documentos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa
{: #wks_tutboot_ml_about}

Depois de treinar um modelo de aprendizado de máquina, é possível usá-lo para pré-anotar novos documentos que você inclui no corpus.

> **Atenção:** não execute um pré-anotador em documentos que foram anotados por humanos, mas não foram incluídos na verdade absoluta ainda. Se fizer isso, todas as anotações atuais serão removidas dos documentos.

Neste tutorial, é possível incluir um segundo conjunto de documentos usando o arquivo `documents-ml.csv`. Não inclua novamente o arquivo `documentos-new.csv`, pois essa adição resultaria em documentos duplicados na verdade absoluta. A duplicação causa os problemas a seguir:

- Se as anotações em cada documento não correspondem, elas diminuem a qualidade do modelo de aprendizado de máquina.
- Se as anotações em cada documento correspondem, elas treinam em excesso o modelo de aprendizado de máquina nos arquivos duplicados.

Para obter mais informações sobre a pré-anotação de documentos, veja [Autoinicializando a anotação](/docs/services/watson-knowledge-studio/preannotation.html), que abrange métodos adicionais de pré-anotação.

### Procedimento
{: #wks_tutboot_ml_procedure}

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como o administrador.
1. Faça upload de mais documentos na área de trabalho. É possível usar o arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.

    Para obter mais informações sobre a inclusão de documentos em uma área de trabalho, veja [Incluindo documentos para anotação](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Crie um conjunto de anotações que use o arquivo `documents-ml.csv` como o conjunto de base e designe-o para si mesmo, o administrador.

    Depois de concluir as etapas a seguir para pré-anotar os novos documentos, é possível visualizar o conjunto de anotações para ver como o modelo de aprendizado de máquina anotou os documentos. Geralmente, você designa conjuntos de anotações a um ou mais anotadores humanos. Para obter mais informações sobre como criar e designar conjuntos de anotações, veja [Incluindo documentos para anotação](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Para pré-anotar os novos documentos, clique em **Modelo de aprendizado de máquina** > **Versões** e, em seguida, clique em **Executar este modelo**.
1. Selecione o conjunto de documentos que você incluiu no corpus, `documentos-ml.csv`, e clique em **Executar**.
1. Após a conclusão da pré-anotação, crie uma tarefa de anotação humana que inclua o conjunto de anotações que você criou.

    Para obter mais informações sobre a criação de uma tarefa de anotação, veja [Configuração de anotação](/docs/services/watson-knowledge-studio/annotate-documents.html).

1. Para visualizar as anotações que foram aplicadas pelo modelo de aprendizado de máquina para os novos documentos, abra a tarefa de anotação.

    Como os novos documentos foram pré-anotados com o modelo de aprendizado de máquina, a anotação humana requer menos tempo. Para obter mais informações sobre como incluir anotações por anotadores humanos, veja [Anotando documentos](/docs/services/watson-knowledge-studio/user-guide.html).

### Resultados
{: #wks_tutboot_ml_results}

Usando seu modelo de aprendizado de máquina para pré-anotar novos conjuntos de documentos, é possível expedir as tarefas de anotação humana para esses documentos.
