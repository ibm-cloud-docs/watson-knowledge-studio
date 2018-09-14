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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window}.
{: tip}

# Resolução de problemas, suporte e FAQs
{: #troubleshooting}

Para isolar e resolver problemas com os produtos {{site.data.keyword.IBM_notm}}, é possível usar a resolução de problemas e as informações de suporte. Essas informações contêm instruções para usar os recursos de determinação de problema que são fornecidos com seus produtos {{site.data.keyword.IBM_notm}}, incluindo o {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Técnicas para resolução de problemas
{: #ts_overview}

*Resolução de problemas* é uma abordagem sistemática para resolver um problema. O objetivo da resolução de problemas é determinar por que algo não funciona conforme o esperado e como resolver o problema. Determinadas técnicas comuns podem ajudar com a tarefa de resolução de problemas.

A primeira etapa no processo de resolução de problemas é descrever o problema completamente. As descrições do problema ajudam você e o representante de suporte técnico {{site.data.keyword.IBM_notm}} saber onde começar a localizar a causa do problema. Esta etapa inclui fazer a si mesmo perguntas básicas:

- Quais são os sintomas do problema?
- Em que local o problema ocorre?
- Quando o problema ocorre?
- Sob quais condições o problema ocorre?
- O problema pode ser reproduzido?

As respostas a essas perguntas geralmente levam a uma boa descrição do problema, o que pode levar você a uma resolução de problema.

### Quais são os sintomas do problema?
{: #ts_overview_symptoms}

Ao começar a descrever um problema, a pergunta mais óbvia é "Qual é o problema?" Essa pergunta pode parecer direta; entretanto, é possível dividi-la em várias perguntas mais focadas que criam uma figura mais descritiva do problema. Essas perguntas podem incluir:

- Quem, ou o que, está relatando o problema?
- Quais são os códigos de erro e mensagens?
- Como o sistema falha? Por exemplo, é um loop, interrupção, travamento, degradação de desempenho ou resultado incorreto?

### Em que local o problema ocorre?
{: #ts_overview_where}

Nem sempre é fácil determinar onde o problema se origina, mas é uma das etapas mais importantes na resolução de um problema. Muitas camadas de tecnologia podem existir entre o relatório e os componentes com falha. Redes, discos e drivers são apenas alguns dos componentes a considerar quando você estiver investigando problemas.

As perguntas a seguir o ajudam a se concentrar em onde o problema ocorre para isolar a camada do problema:

- O problema é específico a uma plataforma ou sistema operacional ou é comum entre múltiplas plataformas ou sistemas operacionais?
- O ambiente e a configuração atuais são suportados?
- Todos os usuários têm o problema?
- (Para instalações multisite.) Todos os sites têm o problema?

Se uma camada relata o problema, o problema não necessariamente se origina nessa camada. Parte de identificar a origem de um problema é entender o ambiente no qual ele existe. Dedique algum tempo para descrever completamente o ambiente do problema, incluindo o sistema operacional e a versão, todos os softwares e versões correspondentes e informações de hardware. Confirme se você está executando em um ambiente que é uma configuração suportada; muitos problemas podem ser rastreados de volta para níveis incompatíveis de software que não são destinados a executar juntos ou não foram totalmente testados juntos.

### Quando o problema ocorre?
{: #ts_overview_when}

Desenvolva uma linha de tempo detalhada de eventos que levam a uma falha, especialmente para aqueles casos que são ocorrências únicas. É possível desenvolver mais facilmente uma linha de tempo trabalhando de trás para frente: inicie no momento em que um erro foi relatado (o mais precisamente possível, mesmo em milissegundos) e trabalhe retroativamente por meio dos logs e informações disponíveis. Geralmente, é necessário observar somente até o primeiro evento suspeito que você localiza em um log de diagnósticos.

Para desenvolver uma linha de tempo detalhada de eventos, responda a estas perguntas:

- O problema acontece somente em um determinado horário do dia ou da noite?
- Com que frequência o problema ocorre?
- Qual sequência de eventos leva ao horário em que o problema é relatado?
- O problema ocorre após uma mudança de ambiente, como fazer upgrade ou instalar software ou hardware?

Responder a esses tipos de perguntas pode dar a você um quadro de referência no qual investigar o problema.

### Sob quais condições o problema ocorre?
{: #ts_overview_conditions}

Saber quais sistemas e aplicativos estavam em execução no momento em que o problema ocorreu é uma parte importante da resolução de problemas. Essas perguntas sobre seu ambiente podem ajudá-lo a identificar a causa raiz do problema:

- O problema sempre ocorre quando a mesma tarefa está sendo executada?
- Uma determinada sequência de eventos precisa acontecer para que o problema ocorra?
- Algum outro aplicativo falha ao mesmo tempo?

Responder a esses tipos de perguntas pode ajudá-lo a explicar o ambiente no qual o problema ocorre e correlacionar quaisquer dependências. Lembre-se de que apenas porque múltiplos problemas podem ter ocorrido ao mesmo tempo, os problemas não estão necessariamente relacionados.

### O problema pode ser reproduzido?
{: #ts_overview_reproduce}

De um ponto de vista de resolução de problemas, o problema ideal é aquele que pode ser reproduzido. Geralmente, quando um problema pode ser reproduzido, você tem um conjunto maior de ferramentas ou procedimentos à sua disposição para ajudá-lo a investigar. Consequentemente, os problemas que podem ser reproduzidos são frequentemente mais fáceis de depurar e resolver.

Entretanto, os problemas que podem ser reproduzidos podem ter uma desvantagem: se o problema é de impacto significativo no negócio, você não deseja que ele ocorra novamente. Se possível, recrie o problema em um ambiente de teste ou de desenvolvimento, que geralmente oferece mais flexibilidade e controle durante sua investigação.

- O problema pode ser recriado em um sistema de teste?
- Múltiplos usuários ou aplicativos estão encontrando o mesmo tipo de problema?
- O problema pode ser recriado executando um único comando, um conjunto de comandos ou um aplicativo específico?

## Não é possível criar uma instância no plano Lite
{: #wks_ts_lite}

### Problema
{: #wks_ts_lite_problem}

Você tenta criar uma instância do {{site.data.keyword.knowledgestudioshort}} no plano Lite e vê a mensagem de erro, `Error 331: We are unable to process your request. Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### Causas
{: #wks_ts_lite_causes}

O {{site.data.keyword.knowledgestudioshort}} não permite mais de um plano Lite por organização.

### Solução do Problema
{: #wks_ts_lite_resolve}

Crie uma conta que não esteja incluída na organização.

Se você precisar usar a sua conta atual para uma instância do {{site.data.keyword.knowledgestudioshort}} em um plano Lite e a sua conta do usuário estiver associada a uma conta paga, será possível criar um caso. Para obter mais informações, veja [Entrando em contato com o suporte {{site.data.keyword.IBM_notm}}](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Se for necessário usar sua conta atual para uma instância do {{site.data.keyword.knowledgestudioshort}} em um plano Lite e sua conta do usuário não estiver associada a uma conta paga, poste seu problema no [{{site.data.keyword.IBM_notm}} developerWorks Answers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/topics/watson-knowledge-studio/){: new_window}. Identifique a questão,  ** WATSON-KNOWLEDGE-STUDIO **.

## Não é possível acessar o aplicativo
{: #wks_ts_access}

Descubra como conceder aos usuários acesso ao {{site.data.keyword.knowledgestudioshort}} e direcionar problemas de acesso comum.

Deve-se ter credenciais de registro do usuário da {{site.data.keyword.IBM_notm}} para solicitar uma instância do {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}}.

### Administrador
{: #wks_ts_access_administrator}

Cada instância do {{site.data.keyword.knowledgestudioshort}} tem uma função de administrador associada a ela. A pessoa que se inscreve originalmente para usar o aplicativo recebe a função de administrador automaticamente. O administrador pode convidar outras pessoas.

Para obter informações sobre como convidar pessoas para usar sua instância do aplicativo, veja [Montando a equipe](/docs/services/watson-knowledge-studio/team.html).

### Anotador humano
{: #wks_ts_access_annotator}

Se tiver sido convidado para a instância de alguém do {{site.data.keyword.knowledgestudioshort}} para servir como um anotador humano, você provavelmente recebeu um convite por e-mail. Primeiro, deve-se registrar com a {{site.data.keyword.IBM_notm}} se você ainda não tem as credenciais de registro do {{site.data.keyword.IBM_notm}}. Ao registrar-se com a {{site.data.keyword.IBM_notm}} e aceitar o convite, você recebe acesso à instância. No entanto, depois que você recebe acesso e antes de poder começar a anotar documentos, o administrador ou um gerente de projeto da instância deve incluí-lo em uma área de trabalho e designar uma tarefa de anotação para você. Você só pode executar qualquer ação na instância do {{site.data.keyword.knowledgestudioshort}} depois que uma tarefa é designada a você. Para anotar documentos, use o editor de verdade absoluta. Use um navegador Google Chrome para o melhor desempenho.

Para obter ajuda sobre como usar o editor de verdade absoluta, veja [Anotando documentos](/docs/services/watson-knowledge-studio/user-guide.html).

## Coleta de dados
{: #content}

Para planos Padrão (Lite, Standard, Pro), por padrão, o {{site.data.keyword.knowledgestudioshort}} usa dados do cliente para melhorar o serviço. Esses dados são usados somente em agregação. Os dados do cliente não são compartilhados nem tornados públicos.

Se você tiver a função Administrativa, será possível mudar esse comportamento padrão selecionando a configuração de coleta de dados na página Detalhes do serviço.

Para planos Premium e contas Dedicadas, o {{site.data.keyword.knowledgestudioshort}} não usa dados do cliente para melhorar o serviço.

Para obter mais informações, veja a [descrição do serviço {{site.data.keyword.knowledgestudioshort}} mais recente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=Knowledge+Studio){: new_window}.

## Serviços e recursos experimentais: o que *experimental* significa?
{: #experimental}

A {{site.data.keyword.IBM_notm}} libera serviços experimentais e recursos para você experimentar. Esses serviços podem ser instáveis, mudar frequentemente de maneiras que não são compatíveis com versões anteriores e podem ser descontinuados com pouca antecedência. Esses serviços e recursos não são recomendados para uso em ambientes de produção.

Para obter mais informações sobre serviços experimentais, veja a [documentação do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/get-support/servicessupport.html#s-services-exporcont){: new_window}. Para obter os detalhes integrais dos serviços experimentais, veja a versão mais recente da [Descrição do serviço do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){: new_window}.

## Problemas de espaço de armazenamento
{: #storage}

Dependendo do seu plano de assinatura, você pode atingir o limite de armazenamento especificado para seu plano e ser impedido de executar tarefas que deseja concluir.

### Sintomas
{: #storage_symptoms}

Você pode ver uma mensagem sobre ter excedido o espaço de armazenamento permitido ao tentar executar uma destas tarefas:

- Fazer upload de documentos ou dicionários
- Implementar um modelo ou versão de um modelo
- Executar um pré-anotador em documentos

### Causas
{: #storage_causes}

O limite de armazenamento foi atendido ou seria excedido se a ação fosse continuar.

### Solução do Problema
{: #storage_resolve}

Os maiores consumidores de espaço de armazenamento são modelos de aprendizado de máquina e baseados em regra. Para liberar espaço, é possível tomar as ações a seguir:

- Exclua versões de captura instantânea de quaisquer modelos para os quais você não espera precisar reverter.
- Exclua quaisquer modelos que você não precisa.
- Se seus modelos são muito importantes para excluir, considere fazer upgrade de seu plano para um que forneça uma dotação maior de espaço de armazenamento.

Depois de remover modelos ou versões do modelo, aguarde uma hora antes de tentar novamente a ação que resultou na mensagem de erro. Pode levar até uma hora para o espaço de armazenamento que você liberou estar disponível para uso.

Para gerenciar sua conta mensal, se a função Administrador é designada para você e sua conta é Premium ou Padrão, é possível configurar um limite de armazenamento na página Detalhes do serviço no {{site.data.keyword.knowledgestudioshort}}. Para ver a página Detalhes do serviço e configurar o limite de armazenamento, na barra de navegação superior no {{site.data.keyword.knowledgestudioshort}}, clique no ícone **Configurações**, clique no link **Visualizar/modificar detalhes do serviço** e, em seguida, clique no link **Configurar limite de armazenamento**.
{: tip}

## Entrando em contato com o suporte IBM
{: #ts_contactingibmsupport}

O Suporte {{site.data.keyword.IBM_notm}} fornece assistência a defeitos do produto, responde às perguntas frequentes e ajuda os usuários a resolver problemas com o produto.

- **Clientes do plano Lite não associados a uma conta paga**

    Obtenha ajuda e respostas para perguntas por meio dos membros amigos da comunidade do desenvolvedor. Para links, consulte a seção "Comunidade do desenvolvedor" na parte inferior do índice.

- ** Clientes associados a uma conta paga **

    Como um cliente associado a uma conta paga, também é possível fazer perguntas e aprender com as perguntas de outros usuários. As comunidades de desenvolvedores estão abertas a todos e são um ótimo lugar para começar. Para links, consulte a seção "Comunidade do desenvolvedor" na parte inferior do índice.

    ** Para entrar em contato com o  {{site.data.keyword.IBM_notm}}  Suporte: **

    Deve-se estar autorizado a criar casos de suporte no Portal de serviço do {{site.data.keyword.cloud_notm}}.

    1. Defina o problema, reúna informações de plano de fundo e determine a gravidade do problema.
    1. Reúna informações de diagnóstico, se possível.
    1. Crie um caso no Portal de serviço do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson.service-now.com/wcp){: new_window}.
