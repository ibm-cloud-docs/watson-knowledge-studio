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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# Montando uma equipe
{: #team}

A criação de um modelo requer entrada de especialistas no assunto, gerentes de projeto e usuários que podem entender e interpretar modelos estatísticos. Deve-se incluir um usuário no {{site.data.keyword.knowledgestudioshort}} para cada pessoa que precisa efetuar login.
{: shortdesc}

**Nota**: somente planos Standard e planos Premium podem ter mais de um usuário. Os planos Lite são limitados a um usuário. Como o único usuário, essa pessoa é designada à função com a permissão mais alta, a função administrativa.

## Antes de Começar

- Certifique-se de que você esteja usando um navegador suportado. Para obter informações, veja [Requisitos do navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Crie uma instância do {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Se você se inscreveu para um plano Padrão ou Premium, na guia **Gerenciar** do {{site.data.keyword.cloud_notm}}, convide outros usuários para sua organização que você deseja incluir como usuários no {{site.data.keyword.knowledgestudioshort}}. Para obter mais informações sobre convidar usuários, veja [Convidando usuários e designando acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/iam/iamuserinv.html){: new_window}.

  **Importante**: assegure-se de que os usuários convidados tenham a função de desenvolvedor do Cloud Foundry. Para obter mais informações, veja [Acesso ao Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}.

## Sobre essa Tarefa

Geralmente, você inclui usuários para preencher as funções de anotadores humanos e gerentes de projeto. Para obter descrições, consulte  [ Funções de usuário no  {{site.data.keyword.knowledgestudioshort}} ](/docs/services/watson-knowledge-studio/roles.html).

** Nota: **

- Se você se inscreveu para um plano Lite, não será possível incluir outros em sua instância do {{site.data.keyword.knowledgestudioshort}}. Em vez disso, ao ativar o {{site.data.keyword.knowledgestudioshort}}, você será incluído na instância e a função administrativa lhe será concedida. Na função administrativa, é possível executar muitas funções que geralmente seriam executadas por pessoas diferentes que estão designadas a funções diferentes. É possível testar como especialistas de diferentes áreas de um domínio podem trabalhar juntos para construir um modelo de aprendizado de máquina ou modelo baseado em regra.
- A função administrativa é concedida ao primeiro usuário a ativar o {{site.data.keyword.knowledgestudioshort}} para a instância do {{site.data.keyword.knowledgestudioshort}}. Essa tarefa presume que você é a primeira pessoa a ativar o {{site.data.keyword.knowledgestudioshort}} depois de se inscrever para um plano, o que significa que você tem a função administrativa.

## Incluindo usuários no {{site.data.keyword.knowledgestudioshort}}

Inclua usuários de sua organização do {{site.data.keyword.cloud_notm}} no {{site.data.keyword.knowledgestudioshort}}.

Para incluir usuários em uma instância do {{site.data.keyword.knowledgestudioshort}}:

1. Efetue login no [Painel do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}){: new_window} com seu {{site.data.keyword.ibmid}} e ative o {{site.data.keyword.knowledgestudioshort}}.
1. Clique no ícone **Configurações** e, em seguida, clique em **Gerenciar detalhes do serviço**.
1. Na seção **Gerenciar usuários**, insira o {{site.data.keyword.ibmid}} para o usuário que você deseja incluir.
1. Selecione a função que você deseja fornecer ao usuário. Para descrições das funções que estão disponíveis, consulte [Funções de usuário no {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

  **Nota**: não é possível fazer downgrade de funções de usuário após designá-las, portanto, certifique-se de entender as tarefas que cada função pode executar ao designar a função administrativa e a função de gerente de projeto.

1. Clique em ** Adicionar**.

## Fazendo upgrade de funções de usuário

Depois de incluir usuários no {{site.data.keyword.knowledgestudioshort}}, é possível fazer upgrade de funções inferiores para funções superiores. Os usuários devem ser designados às funções descritas abaixo para poderem executar as respectivas tarefas.

**Nota**: somente planos Standard e planos Premium podem ter mais de um usuário. Os planos Lite são limitados a um usuário que já tenha a função mais alta, administrador.

> **Atenção: o downgrade de uma função superior para uma função inferior não é permitido.**

Para fazer upgrade de funções para usuários do {{site.data.keyword.knowledgestudioshort}}:

1. Efetue login no [Painel do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}){: new_window} com seu {{site.data.keyword.ibmid}} e ative o {{site.data.keyword.knowledgestudioshort}}.
1. No menu de navegação da direita superior, clique no ícone **Configurações** ![o ícone Configurações](images/settings.png) e, em seguida, clique em **Gerenciar detalhes do serviço**. A seção **Gerenciar Usuários** da página Detalhes do serviço lista todos os IDs de usuário que são usuários para essa instância do {{site.data.keyword.knowledgestudioshort}}.
1. Localize o nome do usuário que você deseja mudar e clique no link **Editar**.
1. Clique na função do usuário e escolha a função para a qual você deseja fazer upgrade desse usuário. Para descrições das funções que estão disponíveis, consulte [Funções de usuário no {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

  **Importante:** deve-se criar uma área de trabalho, associar um usuário a um conjunto de documentos e designar uma tarefa de anotação a um usuário antes que um usuário com a função de anotador humano possa ver qualquer espaço de trabalho listado no aplicativo {{site.data.keyword.knowledgestudioshort}}. Configure a área de trabalho assim que possível depois que os usuários se registrarem para ver sua área de trabalho quando eles acessam pela primeira vez o aplicativo. Você pode desejar notificar os usuários depois de configurar a área de trabalho para permitir que eles saibam que podem começar a anotar documentos.

1. Opcional: quando você terminar de administrar usuários no {{site.data.keyword.knowledgestudioshort}}, saia da sessão fechando o navegador da web. A interface com o usuário do {{site.data.keyword.knowledgestudioshort}} não fornece uma ação para efetuar logout explicitamente.

## Desativando contas de usuário

Posteriormente, se você desejar remover usuários, siga as etapas anteriores para abrir a página Detalhes do serviço. Na lista de IDs de usuário, localize o usuário que você deseja remover e clique em **Desativar**.

> **Atenção**: se os usuários forem designados a documentos para anotar e você desativar suas contas, suas anotações serão afetadas. Se as anotações feitas por usuários desativados não forem promovidas para verdade absoluta, essas anotações serão excluídas.

### Tarefas relacionadas

[Criando e designando conjuntos de anotações](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
