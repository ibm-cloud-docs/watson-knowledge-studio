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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Usando o modelo de aprendizado de máquina
{: #publish-ml}

Alavanque um modelo de aprendizado uma máquina que você treinou com {{site.data.keyword.knowledgestudioshort}} tornando-o disponível para outros aplicativos do {{site.data.keyword.watson}}.
{: shortdesc}

É possível implementar ou exportar um modelo de aprendizado de máquina. Um dicionário ou pré-anotador do {{site.data.keyword.nlushort}} pode ser usado somente para pré-anotar documentos no {{site.data.keyword.knowledgestudioshort}}.

Antes de um modelo poder ser implementado para uso por um serviço, deve-se ter uma assinatura do serviço. Os serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} estão hospedados no {{site.data.keyword.Bluemix_short}}, que é a plataforma de nuvem para a {{site.data.keyword.IBM_notm}}. Veja [O que é {{site.data.keyword.Bluemix_notm}}? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obter mais informações sobre a plataforma. Para assinar um dos serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crie uma conta por meio do website do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/){: new_window}.

Para alguns dos serviços, deve-se saber detalhes sobre a instância de serviço que você planeja implementar, como o nome do espaço e o nome da instância de serviço do {{site.data.keyword.Bluemix_notm}}. As informações de espaço e nome da instância estão disponíveis na página de serviços do {{site.data.keyword.Bluemix_notm}}.

Também é possível pré-anotar documentos novos com o modelo de aprendizado de máquina. Veja [Pré-anotando documentos com um modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire) para obter detalhes.

## Implementando modelo de aprendizado de máquina para AlchemyLanguage
{: #wks_mabluemix}

Quando você está satisfeito com o desempenho do modelo, é possível implementar uma versão dele no {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}. Esse recurso, que requer que você forneça uma chave de acesso do {{site.data.keyword.alchemyapishort}}, permite que seus aplicativos usem o modelo de aprendizado a máquina implementado para anotar documentos em seu domínio.

### Antes de Começar

Deve-se ter o plano Avançado do serviço {{site.data.keyword.alchemylanguageshort}} para poder implementar e usar o modelo.
>Nota: o serviço {{site.data.keyword.alchemylanguageshort}} foi descontinuado. Não será possível implementar esse modelo no serviço, a menos que você tenha um plano existente.

### Sobre essa Tarefa

Quando você implementar o modelo de aprendizado de máquina, você selecionará a versão dele que deseja implementar. Para implementar esse serviço, deve-se ter uma chave de acesso do {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

A chave deve pertencer a uma conta que está autorizada a publicar modelos customizados ou o modelo será implementado com êxito, mas você não será capaz de usá-lo.

Deve-se especificar a chave na primeira vez em que você implementar um modelo no {{site.data.keyword.alchemylanguageshort}}. É possível, então, reutilizar a chave com múltiplas versões do modelo que você implementa. Cada chave tem um número máximo de modelos que podem ser implementados ao mesmo tempo.

### Procedimento

Para implementar um modelo de aprendizado de máquina no {{site.data.keyword.alchemylanguageshort}}:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Aprendizado de máquina**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, crie uma captura instantânea do modelo atual. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. A opção para implementar não aparece até que você crie pelo menos uma versão.

1. Clique em **Implementar** e escolher implementá-lo no serviço {{site.data.keyword.alchemylanguageshort}} e, em seguida, clique em **Avançar**.
1. Digite a chave que você obteve por meio do {{site.data.keyword.alchemylanguageshort}} ou selecione uma versão anteriormente implementada do modelo que tem uma chave que você deseja reutilizar e clique em **Implementar**. Se a chave for válida, uma confirmação que contenha o ID do modelo será exibida. Essa confirmação não significa que o modelo esteja pronto para uso por seus aplicativos.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** ao lado da versão que você implementou. Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    As informações de status incluem o ID do modelo, os últimos quatro dígitos da chave do {{site.data.keyword.alchemyapishort}} e um log do processo de implementação. O ID do modelo (model_id) é como os seus aplicativos chamam o modelo de aprendizado de máquina. Use a tecla {{site.data.keyword.alchemyapishort}} para acompanhar o número de implementações por chave.

### O que fazer em seguida

Para usar o modelo implementado, deve-se copiar e colar o ID do modelo em sua chamada API do aplicativo. A chamada também deve especificar o serviço de plano Avançado do {{site.data.keyword.alchemylanguageshort}} que você deseja usar com o modelo e sua chave de acesso do {{site.data.keyword.alchemyapishort}} associada. Os terminais a seguir são suportados:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Usa o modelo customizado que você especifica no parâmetro de modelo para extrair uma lista de menções de todos os tipos de entidade conhecidos que ele localiza na entrada que você fornece. Tipos de entrada suportados incluem texto, HTML ou uma URL pública. Veja [{{site.data.keyword.alchemylanguageshort}}&gt;Entidades ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} para obter informações adicionais sobre a API e a sintaxe a serem usadas.

- **&lt;*input-type*&gt;GetTypedRelations**

    Usa o modelo customizado que você especifica no parâmetro de modelo para extrair uma lista de instâncias de relacionamentos conhecidos que ele localiza na entrada fornecida. Veja [{{site.data.keyword.alchemylanguageshort}}&gt;TypedRelations ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#typed-relations){: new_window} para obter mais informações sobre a API e a sintaxe a ser usada.

#### Exemplos

- A chamada API a seguir procura tipos de entidade conhecidos na sequência de texto que é passada no corpo de POST. A solicitação especifica o ID do modelo que foi criado e uma chave API Alchemy que tem direitos para executar modelos customizados.

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetRankedNamedEntities?
    showSourceText=1&
 model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
 apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
 outputMode=json"
    ```
    {: pre}

    A resposta retorna `Mary` e `lamb` se essas são menções reconhecidas pelo seu modelo de aprendizado de máquina.

- A chamada API a seguir procura relacionamentos conhecidos na sequência de texto que é passada no corpo de POST. A solicitação especifica o ID do modelo que foi criado e uma chave API Alchemy que tem direitos para executar modelos customizados.

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetTypedRelations?
    showSourceText=1&
 model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
 apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
 outputMode=json"
    ```
    {: pre}

    A resposta retorna `ownedBy` se esse relacionamento é reconhecido pelo seu modelo de aprendizado de máquina.

> **Nota:** os retornos de linha são incluídos para formatar melhor os exemplos para a tela. Não inclua retornos de linha na sintaxe da API.

Para obter mais informações, veja a documentação do [{{site.data.keyword.alchemylanguageshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/doc/alchemylanguage/customizing.shtml){: new_window}.

#### Informações relacionadas

[Problemas de modelo do {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/troubleshooting.html#wks_ts_deployed_model_deleted)

## Implementando um modelo de aprendizado de máquina no IBM Watson Discovery
{: #wks_madiscovery}

Quando você está satisfeito com o desempenho do modelo, é possível implementar uma versão dele no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Esse recurso permite que seus aplicativos usem o modelo de aprendizado de máquina implementado para enriquecer os insights que você obtém de seus dados para incluir o reconhecimento de conceitos e relações que são relevantes para seu domínio.

### Antes de Começar

Deve-se ter acesso administrativo a uma instância de serviço do {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e saber os nomes do espaço e da instância de serviço do {{site.data.keyword.Bluemix_notm}} que estão associados com ela.

### Sobre essa Tarefa

Quando você implementar o modelo de aprendizado de máquina, você selecionará a versão dele que deseja implementar.

### Procedimento

Para implementar um modelo de aprendizado de máquina no {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Aprendizado de máquina**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, crie uma captura instantânea do modelo atual. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. A opção para implementar não aparece até que você crie pelo menos uma versão.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.discoveryshort}} e, em seguida, clique em **Avançar**.
1. Selecione o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou.

    Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.discoveryshort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida

Para usar o modelo implementado, você deverá fornecer o ID do modelo quando ele for solicitado durante o processo de configuração de enriquecimento de serviço do {{site.data.keyword.discoveryshort}}. Para obter mais detalhes, veja a documentação do serviço [{{site.data.keyword.discoveryshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/watson/developercloud/doc/discovery/integrate-wks.shtml){: new_window}.

## Implementando um modelo de aprendizado de máquina no IBM Watson Natural Language Understanding
{: #wks_manlu}

Quando você está satisfeito com o desempenho do modelo, é possível implementar uma versão dele no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Esse recurso permite que seus aplicativos usem o modelo de aprendizado de máquina implementado para analisar os recursos de semântica de entrada de texto, incluindo entidades e relações.

### Antes de Começar

Deve-se ter um serviço {{site.data.keyword.nlushort}} no qual implementar. Além disso, deve-se saber os nomes de espaço e instância do {{site.data.keyword.Bluemix_notm}} que estão associados ao serviço. Se você não se lembra dos nomes de espaço ou instância, localize-os efetuando login no {{site.data.keyword.Bluemix_notm}}. Se você não tem uma conta do {{site.data.keyword.Bluemix_notm}}, inscreva-se para obter uma conta.

### Sobre essa Tarefa

Quando você implementar o modelo de aprendizado de máquina, você selecionará a versão dele que deseja implementar.

### Procedimento

Para implementar um modelo de aprendizado de máquina no serviço {{site.data.keyword.nlushort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Aprendizado de máquina**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, crie uma captura instantânea do modelo atual. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. A opção para implementar não aparece até que você crie pelo menos uma versão.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.nlushort}} e, em seguida, clique em **Avançar**.
1. Selecione o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou. Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.nlushort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida

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

Veja a documentação do [{{site.data.keyword.nlushort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window} para obter mais detalhes.

## Removendo a implementação de modelos
{: #undeploy-view-model}

Se você desejar remover a implementação de um modelo ou localizar um ID do modelo, visualize a página **Modelos implementados**. A página **Modelos implementados** mostra todos os modelos do {{site.data.keyword.knowledgestudioshort}} que são implementados em serviços nos espaços aos quais você tem acesso.

Para remover a implementação de modelos ou localizar IDs de modelo:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. No menu **Configurações** na barra de menus superior direita, selecione **Gerenciar modelos implementados**.
1. Na lista de modelos implementados, localize o modelo que você deseja visualizar ou do qual deseja remover a implementação.
1. Para remover a implementação do modelo, na última coluna dessa linha, clique em **Remover a implementação do modelo**.
1. Para localizar o ID do modelo, veja a coluna **ID do modelo**.

## Alavancando um modelo de aprendizado de máquina no IBM Watson Explorer
{: #wks_maexport}

Exporte o modelo de aprendizado de máquina treinado para que possa ser usado no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Antes de Começar

Se você escolhe identificar os tipos de relação e anotá-los, deve-se definir pelo menos dois tipos de relação e anotar as instâncias dos relacionamentos na verdade absoluta antes de exportar o modelo. A definição e anotação de somente um tipo de relação podem causar problemas subsequentes no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, liberação 11.0.1.0.

### Sobre essa Tarefa

Agora que o modelo de aprendizado de máquina está treinado para reconhecer entidades e relacionamentos para um domínio específico, é possível alavancá-lo no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Clique [neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} para assistir a um vídeo de menos de 2 minutos que ilustra como exportar um modelo e usá-lo no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimento

Para alavancar um modelo de aprendizado de máquina no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, conclua as etapas a seguir.

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Aprendizado de máquina**.
1. Clique em **Exportar modelo atual**.

    Se você tiver uma assinatura de plano grátis, nenhuma opção de exportação estará disponível.

    O modelo é salvo como um arquivo ZIP e você é solicitado a fazer download do arquivo.

1. Faça download do arquivo para o seu sistema local.
1. No aplicativo {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe o modelo.

    É possível então mapear o modelo para um modelo de aprendizado de máquina no {{site.data.keyword.watson}} Explorer Content Analytics. Depois de executar a etapa de mapeamento, quando você efetua crawl dos documentos, o modelo localiza instâncias das entidades e relações que seu modelo entende. Para saber como importar e configurar o modelo no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, veja o documento técnico que descreve a integração: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Tarefas relacionadas

[Exportando documentos analisados do {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
