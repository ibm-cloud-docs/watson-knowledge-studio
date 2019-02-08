---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}.
{: tip}

# Usando o modelo baseado em regra
{: #wks_rule_publish}

Alavanque um modelo baseado em regra que você criou com o {{site.data.keyword.knowledgestudioshort}} tornando-o disponível para outros aplicativos do {{site.data.keyword.watson}}.
{: shortdesc}

**Atenção**: é possível implementar um modelo baseado em regra para torná-lo disponível para uso nesses serviços como um recurso [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).

Antes de um modelo poder ser implementado para uso por um serviço, deve-se ter uma assinatura do serviço. Os serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} estão hospedados no {{site.data.keyword.Bluemix_notm}}, que é a plataforma de nuvem para a {{site.data.keyword.IBM_notm}}. Veja [O que é {{site.data.keyword.Bluemix_notm}}? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obter mais informações sobre a plataforma. Para assinar um dos serviços do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crie uma conta por meio do website do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/){: new_window}.

Para alguns dos serviços, deve-se saber detalhes sobre a instância de serviço que você planeja implementar, como o nome do espaço e o nome da instância de serviço do {{site.data.keyword.Bluemix_notm}}. As informações de espaço e nome da instância estão disponíveis na página de serviços do {{site.data.keyword.Bluemix_notm}}.

Também é possível pré-anotar documentos novos com o modelo baseado em regra. Veja [Pré-anotando documentos com o modelo baseado em regra](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) para obter detalhes.

## Implementando um modelo baseado em regra no IBM Watson Discovery
{: #wks_rule_discovery}

Implemente o modelo para permitir que um aplicativo que usa o serviço {{site.data.keyword.discoveryshort}} use o modelo baseado em regra para localizar e extrair as entidades durante o enriquecimento do documento.

**Atenção**: esse é atualmente um [recurso](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) experimental do serviço

### Antes de Começar
{: #wks_rule_discovery_prereqs}

Deve-se ter acesso administrativo a uma instância de serviço do {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e saber os nomes do espaço e da instância de serviço do {{site.data.keyword.Bluemix_notm}} que estão associados com ela.

### Procedimento
{: #wks_rule_discovery_procedure}

Para implementar um modelo baseado em regra no {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Modelo baseado em regra** > **Versões** > **Modelo baseado em regra**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, salve o modelo atual para implementação clicando em **Salvar para implementação**. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. Salvar a versão pode levar alguns minutos. A opção para implementar não aparece até depois que a versão é criada.

    **Nota**: cada versão pode ser implementada em somente uma instância de serviço. Se você desejar implementar o mesmo modelo em mais de uma instância, crie uma versão para cada instância.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.discoveryshort}} e, em seguida, clique em **Avançar**.
1. Forneça o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou.

    Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.discoveryshort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida
{: #wks_rule_discovery_next}

Para usar o modelo implementado, você deverá fornecer o ID do modelo quando ele for solicitado durante o processo de configuração de enriquecimento de serviço do {{site.data.keyword.discoveryshort}}.

## Implementando um modelo baseado em regra no IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Implemente o modelo baseado em regra para permitir que um aplicativo que usa o serviço {{site.data.keyword.nlushort}} use o modelo para localizar e extrair entidades que são relevantes para seu domínio.

**Atenção**: esse é atualmente um [recurso](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) experimental do serviço

### Antes de Começar
{: #wks_rule_prereqs}

Deve-se ter acesso administrativo a uma instância de serviço do {{site.data.keyword.nlushort}} e saber os nomes do espaço e da instância de serviço do {{site.data.keyword.Bluemix_notm}} que estão associados com ela.

### Procedimento
{: #wks_rule_procedure}

Para implementar um modelo baseado em regra no {{site.data.keyword.nlushort}}, conclua as etapas a seguir:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Modelo baseado em regra** > **Versões** > **Modelo baseado em regra**.
1. Escolha a versão do modelo que você deseja implementar.

    Se houver apenas uma versão de trabalho do modelo, salve o modelo atual para implementação clicando em **Salvar para implementação**. Isso provê versões ao modelo, o que permite que você implemente uma versão, enquanto continua a melhorar a versão atual. Salvar a versão pode levar alguns minutos. A opção para implementar não aparece até depois que a versão é criada.

    **Nota**: cada versão pode ser implementada em somente uma instância de serviço. Se você desejar implementar o mesmo modelo em mais de uma instância, crie uma versão para cada instância.

1. Clique em **Implementar**, escolha implementá-lo no {{site.data.keyword.nlushort}} e, em seguida, clique em **Avançar**.
1. Forneça o espaço e a instância do {{site.data.keyword.Bluemix_notm}}. Se necessário, selecione uma região diferente.
1. Clique em **Implementar**.
1. O processo de implementação pode levar alguns minutos. Para verificar o status da implementação, clique em **Status** na guia **Versões** ao lado da versão que você implementou.

    Se o modelo ainda estiver sendo implementado, o status indicará "publicando". Após a implementação ser concluída, o status mudará para "disponível", se a implementação foi bem-sucedida, ou para "erro", se ocorreram problemas.

    Quando disponível, anote o ID do modelo (model_id). Você fornecerá esse ID para o serviço do {{site.data.keyword.nlushort}} para ativar o serviço para usar o seu modelo customizado.

### O que fazer em seguida
{: #wks_rule_next}

Para usar o modelo implementado, deve-se especificar o ID do modelo de seu modelo customizado no parâmetro `entities.model`.

É possível usar o modelo com a solicitação do {{site.data.keyword.nlushort}} `GET /analyze` para extrair entidades.

Consulte a [Documentação do {{site.data.keyword.nlushort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/natural-language-understanding/index.html){: new_window} para obter mais detalhes.

## Removendo a implementação de modelos
{: #undeploy-view-model}

Se você desejar remover a implementação de um modelo ou localizar um ID do modelo, visualize a página **Modelos implementados**.

### Sobre essa Tarefa
{: #wks_undeploy_about}

O que você vê na página Modelos implementados depende da [região ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/resources/services_region.html){: new_window} que hospeda sua instância do {{site.data.keyword.knowledgestudioshort}}. Se a região suportar instâncias gerenciadas pelos métodos de gerenciamento de acesso [IAM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/iam/users_roles.html){: new_window} e [Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}, você verá uma guia para cada método. Os modelos de instâncias gerenciadas pelo IAM estão listados na guia **Grupos de recursos**. Os modelos de instâncias gerenciadas pelo Cloud Foundry estão listados na guia **Organizações**.

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

## Alavancando um modelo baseado em regra no IBM Watson Explorer
{: #wks_rule_export}

Exporte o arquivo PEAR que é produzido quando o modelo baseado em regra é criado para que possa ser usado no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimento
{: #wks_rule_export_procedure}

Para alavancar um modelo baseado em regra no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, conclua as etapas a seguir.

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Modelo baseado em regra** > **Versões** > **Modelo baseado em regra**.
1. Clique em **Exportar modelo atual**.

    Se você tiver uma assinatura do plano Lite, nenhuma opção de exportação estará disponível.

    O modelo é salvo como um arquivo PEAR e você é solicitado a fazer download do arquivo. Um arquivo PEAR (Processing Engine Archive) é o formato de pacote padrão UIMA para componentes UIMA. O modelo é salvo no formato PEAR para que possa ser distribuído e reutilizado em aplicativos UIMA.

1. Faça download do arquivo para o seu sistema local.
1. No aplicativo {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe o arquivo PEAR.
