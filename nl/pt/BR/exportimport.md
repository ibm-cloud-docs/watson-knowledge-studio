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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}.
{: tip}

# Fazendo upload de recursos de outra área de trabalho
{: #exportimport}

Para acelerar a criação de um modelo, é possível fazer upload de recursos como documentos (com ou sem anotações de verdade absoluta), um sistema de tipos e dicionários transferidos por download de outra área de trabalho.
{: shortdesc}

A capacidade de fazer download e upload separadamente de diferentes recursos fornece flexibilidade ao projetar e criar um modelo. Por exemplo, você poderá criar uma área de trabalho para projetar o sistema de tipos e executar a anotação humana e, em seguida, criar uma área de trabalho separada, talvez em uma instância separada do {{site.data.keyword.knowledgestudioshort}} com usuários diferentes, para treinar o modelo de aprendizado de máquina. A capacidade de fazer upload dos recursos, incluindo a verdade absoluta criada por anotadores humanos, torna esse cenário possível.

Não é possível fazer download e upload de um modelo de aprendizado de máquina. Em vez disso, é possível fazer download de todos os artefatos que foram usados para criar o modelo de uma área de trabalho e fazer upload deles em uma nova área de trabalho. Na nova área de trabalho, é possível executar o treinamento novamente para recriar o modelo. O novo modelo deve produzir resultados semelhantes ao modelo original porque eles foram treinados com o mesmo conjunto de artefatos.

Os arquivos dos quais você faz download são independentes do sistema operacional. As instâncias do {{site.data.keyword.knowledgestudioshort}} nas quais você faz download e upload de arquivos não precisam executar a mesma versão do Linux.

## Sistemas de tipos
{: #wks_exportimport_expimp_type}

Para fazer download de um sistema de tipos, abra a página **Ativos e ferramentas** > **Tipos de entidade** e clique em **Fazer download de tipos**. O sistema cria um arquivo chamado `types-ID.json` e solicita que você faça download do arquivo para seu sistema local. Para usar esse sistema de tipos em uma nova área de trabalho, abra a página **Tipos de entidade** e faça upload do arquivo `JSON` transferido por download.

## Dicionários
{: #wks_exportimport_expimp_dict}

Para fazer download de um ou mais dicionários, selecione a guia **Ativos e ferramentas** > **Pré-anotadores** > **Dicionários** e clique em **Fazer download de dicionários**. Para cada dicionário transferido por download, o sistema cria um arquivo chamado `dictionary name_timestamp.csv`, combina os arquivos em um arquivo `ZIP` chamado `workspace name_dictionary_timestamp.zip` e solicita que você faça download do arquivo para seu sistema local. Também é possível fazer download de um dicionário individual abrindo o dicionário e clicando em **Fazer download**. Os dicionários somente de visualização transferidos por upload como um arquivo CSV de dicionário não podem ser transferidos por download.

Antes de fazer upload de um dicionário transferido por download para uma nova área de trabalho, deve-se fazer download do sistema de tipos da área de trabalho antiga e fazer upload dele na nova área de trabalho. O sistema de tipos e os dicionários devem se originar da mesma área de trabalho do {{site.data.keyword.knowledgestudioshort}} e o sistema de tipos deve existir na nova área de trabalho antes de fazer upload dos dicionários.

Para fazer upload de dicionários, abra a guia **Dicionários** e inclua um arquivo `CSV` transferido por download ou faça upload do arquivo `ZIP`.

## Documentos
{: #wks_exportimport_expimp_doc}

Para fazer download de documentos que você incluiu no corpus, abra a guia **Ativos e ferramentas** > **Documentos** > **Conjuntos de documentos** e clique em **Fazer download de conjuntos de documentos**. O sistema cria um arquivo chamado `corpus-ID.zip` e solicita que você faça download do arquivo para seu sistema local. O arquivo `ZIP` contém todos os documentos no corpus. As anotações que foram incluídas em conjuntos de anotações são incluídas no arquivo ZIP, mas somente após os conjuntos de anotações terem sido aprovados e promovidos para verdade absoluta.

> **Restrição:** qualquer documento que for pré-anotado será ocultado em um formato não legível quando for transferido por download. Até as anotações nesses documentos que foram incluídas por anotação humana são ilegíveis.

Antes de fazer upload de documentos que incluem verdade absoluta em uma nova área de trabalho, deve-se fazer download do sistema de tipos da área de trabalho antiga e fazer upload dele para a nova área de trabalho. O sistema de tipos e os documentos devem se originar da mesma área de trabalho do {{site.data.keyword.knowledgestudioshort}} e o sistema de tipos deve existir na nova área de trabalho antes de fazer upload das anotações de verdade absoluta.

Para fazer upload de documentos, abra a guia **Conjuntos de documentos** na nova área de trabalho, clique em **Fazer upload de conjuntos de documentos** e selecione o arquivo `ZIP` do corpus transferido por download. Especifique se você deseja que os documentos transferidos por upload incluam ou excluam as anotações de verdade absoluta antes de clicar em **Fazer upload**. Somente as anotações que foram promovidas para verdade absoluta antes de fazer download dos documentos serão transferidas por upload.

**Conceitos relacionados**:

[Sistema de tipos](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[Dicionários](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[Documentos para anotadores de aprendizado de máquina](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[Documentos para anotadores baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
