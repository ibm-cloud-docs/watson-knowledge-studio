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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}.
{: tip}

# Usando o modelo baseado em regra
{: #wks_rule_publish}

Alavanque um modelo baseado em regra que você criou com o {{site.data.keyword.knowledgestudioshort}} tornando-o disponível para outros aplicativos do {{site.data.keyword.watson}}.
{: shortdesc}

**Atenção**: é possível implementar um modelo baseado em regra para torná-lo disponível para uso nesses serviços como um recurso [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).

Antes de um modelo poder ser implementado para uso por um serviço, deve-se ter uma assinatura do serviço. Os serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} estão hospedados no {{site.data.keyword.Bluemix_notm}}, que é a plataforma de nuvem para a {{site.data.keyword.IBM_notm}}. Veja [O que é {{site.data.keyword.Bluemix_notm}}? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obter mais informações sobre a plataforma. Para assinar um dos serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crie uma conta por meio do website do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/){: new_window}.

Para alguns dos serviços, deve-se saber detalhes sobre a instância de serviço que você planeja implementar, como o nome do espaço e o nome da instância de serviço do {{site.data.keyword.Bluemix_notm}}. As informações de espaço e nome da instância estão disponíveis na página de serviços do {{site.data.keyword.Bluemix_notm}}.

Também é possível pré-anotar documentos novos com o modelo baseado em regra. Veja [Pré-anotando documentos com o modelo baseado em regra](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) para obter detalhes.

## Implementando um modelo baseado em regra para AlchemyLanguage
{: #wks_rule_bluemix}

Esse recurso permite que seus aplicativos usem o modelo baseado em regra implementado para localizar e extrair entidades de documentos em seu domínio.

**Atenção**: esse é atualmente um [recurso](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) experimental do serviço

### Antes de Começar

Deve-se ter o plano Avançado do serviço {{site.data.keyword.alchemylanguageshort}} para usar esse modelo customizado.

### Sobre essa Tarefa

Para implementar esse serviço, deve-se ter uma chave de acesso do {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

A chave deve pertencer a uma conta que está autorizada a publicar modelos customizados ou o modelo será implementado com êxito, mas você não será capaz de usá-lo.

Quando você implementa o modelo baseado em regra, você seleciona a versão dele que deseja implementar. Deve-se especificar a chave na primeira vez em que você implementar um modelo no {{site.data.keyword.alchemylanguageshort}}. É possível, então, reutilizar a chave com múltiplas versões do modelo que você implementa. Cada chave tem um número máximo de modelos que podem ser implementados ao mesmo tempo.

### Procedimento

Para implementar um modelo baseado em regra no {{site.data.keyword.alchemylanguageshort}}:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Baseado em regra**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, salve o modelo atual para implementação clicando em **Salvar para implementação**. Clicar em **Salvar para implementação** cria uma versão do modelo, que permite a você implementar uma versão e ao mesmo tempo continuar a melhorar a versão atual. Salvar a versão pode levar alguns minutos. A opção para implementar não aparece até depois que a versão é criada.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.alchemylanguageshort}} e, em seguida, clique em **Avançar**.
1. Digite a chave que você obteve por meio do {{site.data.keyword.alchemylanguageshort}} ou selecione uma versão anteriormente implementada do modelo que tem uma chave que você deseja reutilizar e clique em **Implementar**. Se a chave for válida, uma confirmação que contenha o ID do modelo será exibida. Essa confirmação não significa que o modelo esteja pronto para uso por seus aplicativos.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** ao lado da versão que você implementou. Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    As informações de status incluem o ID do modelo, os últimos quatro dígitos da chave do {{site.data.keyword.alchemyapishort}} e um log do processo de implementação. O ID do modelo (model_id) é como os seus aplicativos chamam o modelo de aprendizado de máquina. Anote esse ID do modelo porque não há maneira programática para acessá-lo mais tarde. Use a tecla {{site.data.keyword.alchemyapishort}} para acompanhar o número de implementações por chave.

### O que fazer em seguida

Para usar o modelo implementado, deve-se copiar e colar o ID do modelo em sua chamada API do aplicativo.

> **Atenção:** não é possível usar a chamada API `GET /info/models` do {{site.data.keyword.alchemylanguageshort}} para obter o ID do modelo de modelos baseados em regra programaticamente. É possível acessar o ID do modelo de modelos de aprendizado de máquina com essa chamada, mas não o ID do modelo baseado em regra.

A chamada também deve especificar o serviço {{site.data.keyword.alchemylanguageshort}} que você deseja usar com o modelo e sua chave de acesso do {{site.data.keyword.alchemyapishort}}.

O terminal a seguir é suportado:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Usa o modelo customizado que você especifica no parâmetro de modelo para extrair uma lista de menções de todos os tipos de entidade conhecidos que ele localiza na entrada que você fornece. Tipos de entrada suportados incluem texto, HTML ou uma URL pública. Veja [{{site.data.keyword.alchemylanguageshort}}&gt;Entidades ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} para obter informações adicionais sobre a API e a sintaxe a serem usadas.

## Implementando um modelo baseado em regra no IBM Watson Discovery
{: #wks_rule_discovery}

Implemente o modelo para permitir que um aplicativo que usa o serviço {{site.data.keyword.discoveryshort}} use o modelo baseado em regra para localizar e extrair as entidades durante o enriquecimento do documento.

**Atenção**: esse é atualmente um [recurso](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) experimental do serviço

### Antes de Começar

Deve-se ter acesso administrativo a uma instância de serviço do {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e saber os nomes do espaço e da instância de serviço do {{site.data.keyword.Bluemix_notm}} que estão associados com ela.

### Procedimento

Para implementar um modelo baseado em regra no {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Baseado em regra**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, salve o modelo atual para implementação clicando em **Salvar para implementação**. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. Salvar a versão pode levar alguns minutos. A opção para implementar não aparece até depois que a versão é criada.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.discoveryshort}} e, em seguida, clique em **Avançar**.
1. Forneça o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou.

    Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.discoveryshort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida

Para usar o modelo implementado, você deverá fornecer o ID do modelo quando ele for solicitado durante o processo de configuração de enriquecimento de serviço do {{site.data.keyword.discoveryshort}}.

## Implementando um modelo baseado em regra no IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Implemente o modelo baseado em regra para permitir que um aplicativo que usa o serviço {{site.data.keyword.nlushort}} use o modelo para localizar e extrair entidades que são relevantes para seu domínio.

**Atenção**: esse é atualmente um [recurso](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) experimental do serviço

### Antes de Começar

Deve-se ter acesso administrativo para uma instância de serviço do {{site.data.keyword.nlushort}} e conhecer os nomes de espaço e instância do {{site.data.keyword.Bluemix_notm}} que estão associados a ela.

### Procedimento

Para implementar um modelo baseado em regra no {{site.data.keyword.nlushort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Baseado em regra**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, salve o modelo atual para implementação clicando em **Salvar para implementação**. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. Salvar a versão pode levar alguns minutos. A opção para implementar não aparece até depois que a versão é criada.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.nlushort}} e, em seguida, clique em **Avançar**.
1. Forneça o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou.

    Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.nlushort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida

Para usar o modelo implementado, deve-se especificar o ID do modelo de seu modelo customizado no parâmetro `entities.model`.

É possível usar o modelo com a solicitação do {{site.data.keyword.nlushort}} `GET /analyze` para extrair entidades.

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

## Alavancando um modelo baseado em regra no IBM Watson Explorer
{: #wks_rule_export}

Exporte o arquivo PEAR que é produzido quando o modelo baseado em regra é criado para que possa ser usado no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimento

Para alavancar um modelo baseado em regra no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, conclua as etapas a seguir.

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Gerenciamento de modelo** > **Versões** > **Baseado em regra**.
1. Clique em **Exportar modelo atual**.

    Se você tiver uma assinatura de plano grátis, nenhuma opção de exportação estará disponível.

    O modelo é salvo como um arquivo PEAR e você é solicitado a fazer download do arquivo. Um arquivo PEAR (Processing Engine Archive) é o formato de pacote padrão UIMA para componentes UIMA. O modelo é salvo no formato PEAR para que possa ser distribuído e reutilizado em aplicativos UIMA.

1. Faça download do arquivo para o seu sistema local.
1. No aplicativo {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe o arquivo PEAR.
