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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Usando o modelo de aprendizado de máquina
{: #publish-ml}

Alavanque um modelo de aprendizado uma máquina que você treinou com {{site.data.keyword.knowledgestudioshort}} tornando-o disponível para outros aplicativos do {{site.data.keyword.watson}}.
{: shortdesc}

É possível implementar ou exportar um modelo de aprendizado de máquina. Um dicionário ou pré-anotador do {{site.data.keyword.nlushort}} pode ser usado somente para pré-anotar documentos no {{site.data.keyword.knowledgestudioshort}}.

Antes de um modelo poder ser implementado para uso por um serviço, deve-se ter uma assinatura do serviço. Os serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} estão hospedados no {{site.data.keyword.Bluemix_short}}, que é a plataforma de nuvem para a {{site.data.keyword.IBM_notm}}. Veja [O que é {{site.data.keyword.Bluemix_notm}}? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obter mais informações sobre a plataforma. Para assinar um dos serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crie uma conta por meio do website do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/){: new_window}.

Para alguns dos serviços, deve-se saber detalhes sobre a instância de serviço que você planeja implementar, como o nome do espaço e o nome da instância de serviço do {{site.data.keyword.Bluemix_notm}}. As informações de espaço e nome da instância estão disponíveis na página de serviços do {{site.data.keyword.Bluemix_notm}}.

Também é possível pré-anotar documentos novos com o modelo de aprendizado de máquina. Veja [Pré-anotando documentos com o modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire) para obter detalhes.

## Implementando um modelo de aprendizado de máquina no IBM Watson Discovery
{: #wks_madiscovery}

Quando você está satisfeito com o desempenho do modelo, é possível implementar uma versão dele no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Esse recurso permite que seus aplicativos usem o modelo de aprendizado de máquina implementado para enriquecer os insights que você obtém de seus dados para incluir o reconhecimento de conceitos e relações que são relevantes para seu domínio.

### Antes de Começar
{: #wks_madiscovery_prereqs}

Deve-se ter acesso administrativo a uma instância de serviço do {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e saber os nomes do espaço e da instância de serviço do {{site.data.keyword.Bluemix_notm}} que estão associados com ela.

### Sobre essa Tarefa
{: #wks_madiscovery_about}

Quando você implementar o modelo de aprendizado de máquina, você selecionará a versão dele que deseja implementar.

### Procedimento
{: #wks_madiscovery_procedure}

Para implementar um modelo de aprendizado de máquina no {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione  ** Modelo de Aprendizado de Máquina **  >  ** Versões **.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, crie uma captura instantânea do modelo atual. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. A opção para implementar não aparece até que você crie pelo menos uma versão.

    **Nota**: cada versão pode ser implementada em somente uma instância de serviço. Se você desejar implementar o mesmo modelo em mais de uma instância, crie uma versão para cada instância.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.discoveryshort}} e, em seguida, clique em **Avançar**.
1. Selecione o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou.

    Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.discoveryshort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida
{: #wks_madiscovery_next}

Para usar o modelo implementado, você deverá fornecer o ID do modelo quando ele for solicitado durante o processo de configuração de enriquecimento de serviço do {{site.data.keyword.discoveryshort}}. Para obter mais detalhes, veja a [documentação do serviço {{site.data.keyword.discoveryshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/discovery/integrate-wks.html){: new_window}.

## Implementando um modelo de aprendizado de máquina no IBM Watson Natural Language Understanding
{: #wks_manlu}

Quando você está satisfeito com o desempenho do modelo, é possível implementar uma versão dele no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Esse recurso permite que seus aplicativos usem o modelo de aprendizado de máquina implementado para analisar os recursos de semântica de entrada de texto, incluindo entidades e relações.

### Antes de Começar
{: #wks_manlu_prereqs}

Deve-se ter um serviço {{site.data.keyword.nlushort}} no qual implementar. Além disso, deve-se saber os nomes de espaço e instância do {{site.data.keyword.Bluemix_notm}} que estão associados ao serviço. Se você não se lembra dos nomes de espaço ou instância, localize-os efetuando login no {{site.data.keyword.Bluemix_notm}}. Se você não tem uma conta do {{site.data.keyword.Bluemix_notm}}, inscreva-se para obter uma conta.

### Sobre essa Tarefa
{: #wks_manlu_about}

Quando você implementar o modelo de aprendizado de máquina, você selecionará a versão dele que deseja implementar.

### Procedimento
{: #wks_manlu_procedure}

Para implementar um modelo de aprendizado de máquina no serviço {{site.data.keyword.nlushort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione  ** Modelo de Aprendizado de Máquina **  >  ** Versões **.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, crie uma captura instantânea do modelo atual. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. A opção para implementar não aparece até que você crie pelo menos uma versão.

    **Nota**: cada versão pode ser implementada em somente uma instância de serviço. Se você desejar implementar o mesmo modelo em mais de uma instância, crie uma versão para cada instância.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.nlushort}} e, em seguida, clique em **Avançar**.
1. Selecione o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou. Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.nlushort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida
{: #wks_manlu_next}

Para usar o modelo implementado, deve-se especificar o ID do modelo de seu modelo customizado no parâmetro `entities.model`.

É possível usar o modelo com a solicitação do {{site.data.keyword.nlushort}} `GET /analyze`o para extrair os recursos a seguir:

- **entidades            **

    O comando a seguir localiza as entidades presentes na sentença que é passada usando o parâmetro de texto:

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG" -d "version=2016-05-17" -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    O serviço retorna um objeto JSON de instâncias que ele localiza de tipos de entidade que são definidos no modelo customizado:

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ], "language": "en" }
    ```
    {: codeblock}

- **relações**

    O comando a seguir localiza os relacionamentos que estão presentes na sentença que é passada usando o parâmetro de texto:

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG" -d "version=2016-05-17" -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    O serviço retorna um objeto JSON de instâncias que ele localiza de tipos de relação que estão definidos no modelo customizado:

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ], "language": "en" }
    ```
    {: codeblock}

Consulte a [Documentação do {{site.data.keyword.nlushort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window} para obter mais detalhes.

## Removendo a implementação de modelos
{: #undeploy-view-model}

Se você desejar remover a implementação de um modelo ou localizar um ID do modelo, visualize a página **Modelos implementados**.

### Sobre essa Tarefa
{: #wks_undeploy_about}

O que você vê na página Modelos implementados depende da [região ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} que hospeda sua instância do {{site.data.keyword.knowledgestudioshort}}. Se a região suportar instâncias gerenciadas pelos métodos de gerenciamento de acesso [IAM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} e [Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}, você verá uma guia para cada método. Os modelos de instâncias gerenciadas pelo IAM estão listados na guia **Grupos de recursos**. Os modelos de instâncias gerenciadas pelo Cloud Foundry estão listados na guia **Organizações**.

Se a região suportar instâncias gerenciadas somente por um dos métodos de gerenciamento de acesso, você verá apenas uma lista de modelos, pois apenas um método de gerenciamento de acesso será aplicável.

### Procedimento
{: #wks_deploy_procedure}

Para remover a implementação de modelos ou localizar IDs de modelo:

1. Ative o {{site.data.keyword.knowledgestudioshort}}.
1. No menu **Configurações** na barra de menus superior direita, selecione **Gerenciar modelos implementados**.
1. Na lista de modelos implementados, localize o modelo que você deseja visualizar ou do qual deseja remover a implementação.
1. Para remover a implementação do modelo, na última coluna dessa linha, clique em **Remover a implementação do modelo**.
1. Para localizar o ID do modelo, veja a coluna **ID do modelo**.

Como alternativa, é possível remover a implementação de modelos de páginas de Versões para modelos baseados em regras e modelos de aprendizado de máquina.

## Alavancando um modelo de aprendizado de máquina no IBM Watson Explorer
{: #wks_maexport}

Exporte o modelo de aprendizado de máquina treinado para que possa ser usado no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Antes de Começar
{: #wks_maexport_prereqs}

Se você escolhe identificar os tipos de relação e anotá-los, deve-se definir pelo menos dois tipos de relação e anotar as instâncias dos relacionamentos na verdade absoluta antes de exportar o modelo. A definição e anotação de somente um tipo de relação podem causar problemas subsequentes no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, liberação 11.0.1.0.

### Sobre essa Tarefa
{: #wks_maexport_about}

Agora que o modelo de aprendizado de máquina está treinado para reconhecer entidades e relacionamentos para um domínio específico, é possível alavancá-lo no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Clique [neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} para assistir a um vídeo de menos de 2 minutos que ilustra como exportar um modelo e usá-lo no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimento
{: #wks_maexport_procedure}

Para alavancar um modelo de aprendizado de máquina no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, conclua as etapas a seguir.

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione  ** Modelo de Aprendizado de Máquina **  >  ** Versões **.
1. Clique em **Exportar modelo atual**.

    Se você tiver uma assinatura do plano Lite, nenhuma opção de exportação estará disponível.

    O modelo é salvo como um arquivo ZIP e você é solicitado a fazer download do arquivo.

1. Faça download do arquivo para o seu sistema local.
1. No aplicativo {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe o modelo.

    É possível então mapear o modelo para um modelo de aprendizado de máquina no {{site.data.keyword.watson}} Explorer Content Analytics. Depois de executar a etapa de mapeamento, quando você efetua crawl dos documentos, o modelo localiza instâncias das entidades e relações que seu modelo entende. Para saber como importar e configurar o modelo no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, veja o documento técnico que descreve a integração: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Tarefas relacionadas
{: #wks_maexport_related}

[Exportando documentos analisados do {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
