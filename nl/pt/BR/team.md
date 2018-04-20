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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# Montando uma equipe
{: #team}

A criação de um modelo requer entrada de especialistas no assunto, gerentes de projeto e usuários que podem entender e interpretar modelos estatísticos. Deve-se incluir um usuário no {{site.data.keyword.knowledgestudioshort}} para cada pessoa que precisa efetuar login.
{: shortdesc}

**Nota**: apenas planos Standard e planos Premium podem incluir usuários. Planos grátis são limitados a um usuário. Como o único usuário, essa pessoa é designada à função com a permissão mais alta, a função Administrador.

## Antes de Começar

- Certifique-se de que você esteja usando um navegador suportado. Para obter informações, veja [Requisitos do navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Crie uma instância do {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Se você se inscreveu para um plano Padrão ou Premium, na guia **Gerenciar** do {{site.data.keyword.cloud_notm}}, convide outros usuários para sua organização que você deseja incluir como usuários no {{site.data.keyword.knowledgestudioshort}}. Para obter mais informações sobre convidar usuários, veja [Convidando usuários e designando acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Importante**:

  - Assegure-se de que os usuários convidados tenham a função Cloud Foundry de **Desenvolvedor**. Para obter mais informações, veja [Acesso ao Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - O primeiro usuário a ativar o {{site.data.keyword.knowledgestudioshort}} recebe a função Administrador para a instância do {{site.data.keyword.knowledgestudioshort}}. Esta tarefa supõe que você é a primeira pessoa a ativar o {{site.data.keyword.knowledgestudioshort}} depois de se inscrever para um plano, o que significa que tem a função Administrador.

## Sobre essa Tarefa

Geralmente, você inclui usuários para preencher as funções a seguir.

**Nota:** se você se inscreveu para um plano Grátis, não é possível incluir outros em sua instância do {{site.data.keyword.knowledgestudioshort}}. Em vez disso, ao ativar o {{site.data.keyword.knowledgestudioshort}}, você é incluído na instância com a função Administrador. Na função Administrador, é possível executar muitas funções que normalmente seriam executadas por pessoas diferentes que estão designadas a funções diferentes. É possível testar como os especialistas de diferentes áreas de um domínio podem trabalhar juntos para construir um modelo de aprendizado de máquina ou modelo baseado em regras.

- **HumanAnnotator**

    Os anotadores humanos normalmente são especialistas no assunto que revisam documentos de um domínio específico para identificar entidades e relacionamentos de interesse do domínio. Esses usuários interagem com o aplicativo em um modo limitado. Eles usam o editor de verdade absoluta para anotar um conjunto de documentos que foram designados a eles.

- **ProjectManager**

    Os gerentes de projeto são pessoas que ajudam a facilitar a criação de modelos, executando tarefas como criar artefatos de área de trabalho e treinando, criando e implementando modelos. Para áreas de trabalho que são usadas para construir anotadores de aprendizado de máquina, os gerentes de projeto também gerenciam o processo de anotação de documento, designando tarefas de revisão de documento para anotadores humanos, adjudicando conflitos de anotação e aprovando documentos para incluir na verdade absoluta.

## Incluindo usuários no {{site.data.keyword.knowledgestudioshort}}

Inclua usuários de sua organização do {{site.data.keyword.cloud_notm}} no {{site.data.keyword.knowledgestudioshort}}.

**Nota**: apenas planos Standard e planos Premium podem incluir usuários. Planos grátis são limitados a um usuário.

Para incluir usuários em uma instância do {{site.data.keyword.knowledgestudioshort}}:

1. Efetue login no Painel do [{{site.data.keyword.cloud_notm}}![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard/apps/){: new_window} com o seu {{site.data.keyword.ibmid}} e ative o {{site.data.keyword.knowledgestudioshort}}.
1. Clique no ícone **Configurações** e, em seguida, clique em **Visualizar/modificar detalhes do serviço**.
1. Na seção **Gerenciar usuários**, insira o {{site.data.keyword.ibmid}} para o usuário que você deseja incluir.
1. Selecione a função que você deseja fornecer ao usuário.

   Nota: não é possível fazer downgrade de funções de usuário depois de designá-las, então certifique-se de que você entenda as tarefas que cada função pode executar ao designar a função Administrador e função ProjectManager.

1. Clique em ** Adicionar**.

## Fazendo upgrade de funções de usuário

Depois de incluir usuários no {{site.data.keyword.knowledgestudioshort}}, é possível fazer upgrade de funções inferiores para funções superiores. Os usuários devem ser designados às funções descritas abaixo para poderem executar as respectivas tarefas.

**Nota**: somente planos Padrão e Premium podem fazer upgrade de usuários. Os planos Grátis são limitados a um usuário que já tem a função mais alta, Administrador.

> **Atenção: o downgrade de uma função superior para uma função inferior não é permitido.**

Para fazer upgrade de funções para usuários do {{site.data.keyword.knowledgestudioshort}}:

1. Efetue login no Painel do [{{site.data.keyword.cloud_notm}}![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard/apps/){: new_window} com o seu {{site.data.keyword.ibmid}} e ative o {{site.data.keyword.knowledgestudioshort}}.
1. No menu de navegação superior direito, clique no ícone **Configurações** ![o ícone Configurações](images/settings.png) e, em seguida, clique em **Visualizar/Modificar detalhes do serviço**. A seção **Gerenciar Usuários** da página Detalhes do serviço lista todos os IDs de usuário que são usuários para essa instância do {{site.data.keyword.knowledgestudioshort}}.
1. Localize o nome do usuário que você deseja mudar e clique no link **Editar**.

    O {{site.data.keyword.knowledgestudioshort}} tem as funções a seguir, que são listadas do nível mais alto ao nível mais baixo de privilégios:
    - **Administrador**

      Os usuários nesta função podem executar as tarefas a seguir:

        - Gerenciar uma assinatura, como incluir recursos, armazenamento e mais usuários
        - Conceda aos usuários acesso a uma assinatura na página Detalhes do serviço
        - Criar e gerenciar todas as áreas de trabalho em sua assinatura
        - Designar pessoas às funções de gerente de projeto ou anotador humano para todas as áreas de trabalho

    - **ProjectManager**

      Os usuários com essa função podem executar as tarefas a seguir:

      - Gerenciar áreas de trabalho nas quais eles são incluídos
      - Designar anotadores humanos a uma área de trabalho

      Os usuários com essa função não podem executar as tarefas a seguir:

      - Criar áreas de trabalho
      - Gerenciar acesso de usuário e funções na página Detalhes do serviço

    - **HumanAnnotator**

      Os usuários com essa função podem anotar documentos que estão em áreas de trabalho nas quais eles são designados à função de anotador humano e em um conjunto de documentos que está associado com tarefas de anotação designadas a eles.

      **Importante:** deve-se criar uma área de trabalho, associar um usuário com um conjunto de documentos e designar uma tarefa de anotação para um usuário antes de um usuário com a função **HumanAnnotator** poder ver as áreas de trabalho listadas no aplicativo {{site.data.keyword.knowledgestudioshort}}. Configure a área de trabalho assim que possível depois que os usuários se registrarem para ver sua área de trabalho quando eles acessam pela primeira vez o aplicativo. Você pode desejar notificar os usuários depois de configurar a área de trabalho para permitir que eles saibam que podem começar a anotar documentos.

1. Clique na função do usuário e escolha a função para a qual você deseja fazer upgrade desse usuário.
1. Opcional: quando você terminar de administrar usuários no {{site.data.keyword.knowledgestudioshort}}, saia da sessão fechando o navegador da web. A interface com o usuário do {{site.data.keyword.knowledgestudioshort}} não fornece uma ação para efetuar logout explicitamente.

## Desativando contas de usuário

Posteriormente, se você desejar remover usuários, siga as etapas anteriores para abrir a página Detalhes do serviço novamente. Na lista de IDs de usuário, localize o usuário que você deseja remover e clique em **Desativar**.

> **Atenção**: se os usuários forem designados a documentos para anotar e você desativar suas contas, suas anotações serão afetadas. Se as anotações feitas por usuários desativados não forem promovidas para verdade absoluta, essas anotações serão excluídas.

### Tarefas relacionadas

[Criando e designando conjuntos de anotações](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
