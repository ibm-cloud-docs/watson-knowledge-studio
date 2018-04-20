---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}.
{: tip}

# Anotação de autoinicialização
{: #wks_tutboot_intro}

Este tutorial ajuda a entender como pré-anotar documentos, que simplifica a tarefa de anotação de anotadores humanos.
{: shortdesc}

## Aprendendo objetivos

Depois de concluir o tutorial, você saberá como pré-anotar documentos com um modelo de aprendizado de máquina.

A conclusão do tutorial deve levar aproximadamente 5 minutos. Se você explorar outros conceitos relacionados a este tutorial, ele poderá levar mais tempo para ser concluído.

## Antes de Começar

- Você está usando um navegador suportado. Para obter informações, veja [Requisitos do navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- Você concluiu com êxito o [Tutorial: criando uma área de trabalho](/docs/services/watson-knowledge-studio/tutorials-create-project.html) e [Tutorial: criando um modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Deve-se ter pelo menos um ID do usuário na função de Administrador ou de ProjectManager. Para obter informações sobre funções de usuário, veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html).

## Resultados

Após concluir este tutorial, você terá um conjunto de documentos parcialmente anotados. Em seguida, será possível designar os documentos aos anotadores humanos para concluir o trabalho de anotação.

## Lição 1: pré-anotando novos documentos com um modelo de aprendizado de máquina
{: #wks_tutboot_ml}

Nesta lição, você aprenderá como usar modelo de aprendizado de máquina para pré-anotar documentos no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa

Depois de treinar um modelo de aprendizado de máquina, é possível usá-lo para pré-anotar novos documentos que você inclui no corpus.

> **Atenção:** não execute um pré-anotador em documentos que foram anotados por humanos, mas não foram incluídos na verdade absoluta ainda. Se fizer isso, todas as anotações atuais serão removidas dos documentos.

Neste tutorial, é possível incluir um segundo conjunto de documentos usando o arquivo `documents-ml.csv`. Não inclua novamente o arquivo `documentos-new.csv`, pois essa adição resultaria em documentos duplicados na verdade absoluta. A duplicação causa os problemas a seguir:

- Se as anotações em cada documento não correspondem, elas diminuem a qualidade do modelo de aprendizado de máquina.
- Se as anotações em cada documento correspondem, elas treinam em excesso o modelo de aprendizado de máquina nos arquivos duplicados.

### Procedimento

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} como o administrador.
1. Faça upload de mais documentos na área de trabalho. É possível usar o arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv`<img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.

    Para obter detalhes sobre como fazer upload de documentos, veja [Criando um modelo de aprendizado de máquina > Incluindo documentos para anotação](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1).

1. Crie uma anotação configurada com o arquivo `documentos-ml.csv`.

    Para este tutorial, designe o conjunto de anotações para si mesmo, o administrador. Depois de executar o modelo de aprendizado de máquina para pré-anotar os novos documentos, será possível visualizar o conjunto de anotações para ver como o modelo de aprendizado de máquina os pré-anotou. Geralmente, você designa os conjuntos de anotações a um ou mais anotadores humanos. Para obter mais informações sobre como criar conjuntos de anotações, veja [Criando um modelo de aprendizado de máquina > Criando Conjuntos de anotações](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2).

1. Na barra lateral **Gerenciamento de modelo** > **Versões**, selecione a guia **Aprendizado de máquina** e clique em **Executar este modelo**.
1. Selecione o conjunto de documentos que você incluiu no corpus, `documentos-ml.csv`, e clique em **Executar**.
1. Após a pré-anotação ser concluída, é possível criar uma tarefa de anotação humana e anotar os novos documentos pré-anotados.

    Para obter detalhes sobre como criar uma tarefa e anotar documentos, veja [Criando um modelo de aprendizado de máquina > Criando uma tarefa de anotação](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4) e [Criando um modelo de aprendizado de máquina > Anotando documentos](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5).

    Nessa situação, a anotação humana requer menos tempo porque você usou modelo de aprendizado da máquina para pré-anotar os documentos.

### Resultados

Usando seu modelo de aprendizado de máquina para pré-anotar novos conjuntos de documentos, é possível expedir as tarefas de anotação humana para esses documentos.
