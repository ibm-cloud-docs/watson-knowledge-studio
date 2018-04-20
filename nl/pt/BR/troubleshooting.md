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

Ao começar a descrever um problema, a pergunta mais óbvia é "Qual é o problema?" Essa pergunta pode parecer direta; entretanto, é possível dividi-la em várias perguntas mais focadas que criam uma figura mais descritiva do problema. Essas perguntas podem incluir:

- Quem, ou o que, está relatando o problema?
- Quais são os códigos de erro e mensagens?
- Como o sistema falha? Por exemplo, é um loop, interrupção, travamento, degradação de desempenho ou resultado incorreto?

### Em que local o problema ocorre?

Nem sempre é fácil determinar onde o problema se origina, mas é uma das etapas mais importantes na resolução de um problema. Muitas camadas de tecnologia podem existir entre o relatório e os componentes com falha. Redes, discos e drivers são apenas alguns dos componentes a considerar quando você estiver investigando problemas.

As perguntas a seguir o ajudam a se concentrar em onde o problema ocorre para isolar a camada do problema:

- O problema é específico a uma plataforma ou sistema operacional ou é comum entre múltiplas plataformas ou sistemas operacionais?
- O ambiente e a configuração atuais são suportados?
- Todos os usuários têm o problema?
- (Para instalações multisite.) Todos os sites têm o problema?

Se uma camada relata o problema, o problema não necessariamente se origina nessa camada. Parte de identificar a origem de um problema é entender o ambiente no qual ele existe. Dedique algum tempo para descrever completamente o ambiente do problema, incluindo o sistema operacional e a versão, todos os softwares e versões correspondentes e informações de hardware. Confirme se você está executando em um ambiente que é uma configuração suportada; muitos problemas podem ser rastreados de volta para níveis incompatíveis de software que não são destinados a executar juntos ou não foram totalmente testados juntos.

### Quando o problema ocorre?

Desenvolva uma linha de tempo detalhada de eventos que levam a uma falha, especialmente para aqueles casos que são ocorrências únicas. É possível desenvolver mais facilmente uma linha de tempo trabalhando de trás para frente: inicie no momento em que um erro foi relatado (o mais precisamente possível, mesmo em milissegundos) e trabalhe retroativamente por meio dos logs e informações disponíveis. Geralmente, é necessário observar somente até o primeiro evento suspeito que você localiza em um log de diagnósticos.

Para desenvolver uma linha de tempo detalhada de eventos, responda a estas perguntas:

- O problema acontece somente em um determinado horário do dia ou da noite?
- Com que frequência o problema ocorre?
- Qual sequência de eventos leva ao horário em que o problema é relatado?
- O problema ocorre após uma mudança de ambiente, como fazer upgrade ou instalar software ou hardware?

Responder a esses tipos de perguntas pode dar a você um quadro de referência no qual investigar o problema.

### Sob quais condições o problema ocorre?

Saber quais sistemas e aplicativos estavam em execução no momento em que o problema ocorreu é uma parte importante da resolução de problemas. Essas perguntas sobre seu ambiente podem ajudá-lo a identificar a causa raiz do problema:

- O problema sempre ocorre quando a mesma tarefa está sendo executada?
- Uma determinada sequência de eventos precisa acontecer para que o problema ocorra?
- Algum outro aplicativo falha ao mesmo tempo?

Responder a esses tipos de perguntas pode ajudá-lo a explicar o ambiente no qual o problema ocorre e correlacionar quaisquer dependências. Lembre-se de que apenas porque múltiplos problemas podem ter ocorrido ao mesmo tempo, os problemas não estão necessariamente relacionados.

### O problema pode ser reproduzido?

De um ponto de vista de resolução de problemas, o problema ideal é aquele que pode ser reproduzido. Geralmente, quando um problema pode ser reproduzido, você tem um conjunto maior de ferramentas ou procedimentos à sua disposição para ajudá-lo a investigar. Consequentemente, os problemas que podem ser reproduzidos são frequentemente mais fáceis de depurar e resolver.

Entretanto, os problemas que podem ser reproduzidos podem ter uma desvantagem: se o problema é de impacto significativo no negócio, você não deseja que ele ocorra novamente. Se possível, recrie o problema em um ambiente de teste ou de desenvolvimento, que geralmente oferece mais flexibilidade e controle durante sua investigação.

- O problema pode ser recriado em um sistema de teste?
- Múltiplos usuários ou aplicativos estão encontrando o mesmo tipo de problema?
- O problema pode ser recriado executando um único comando, um conjunto de comandos ou um aplicativo específico?

## Problemas do modelo AlchemyLanguage
{: #wks_ts_deployed_model_deleted}

### Problema

Não é possível implementar um modelo AlchemyLanguage ou a implementação foi bem-sucedida, mas o modelo não está disponível para uso.

### Sintomas

- Você implementou um modelo, mas o status mostra que um erro ocorreu.
- Você implementou um modelo e o status indicou que o modelo está disponível, mas não é possível usá-lo.
- O modelo foi implementado com êxito e funcionou antes, mas agora ele não funciona.

### Causas

Os eventos a seguir podem causar problemas com modelos implementados:

- Se você digitar incorretamente a chave do {{site.data.keyword.alchemyapishort}} ao incluí-la no parâmetro `apikey` da chamada API de REST, a chamada falhará. O mesmo é verdadeiro para o ID do modelo. É melhor copiar e colar o ID do modelo e chave API para evitar erros de digitação.
- Se você fornecer uma chave do {{site.data.keyword.alchemyapishort}} que é inválida ou não está autorizada a implementar um modelo customizado, o processo de implementação indicará que o modelo foi implementado com êxito, mas você não será capaz de usá-lo.
- Se, ao usar o {{site.data.keyword.alchemylanguageshort}} no {{site.data.keyword.Bluemix}}, você excluir todas as instâncias de serviço que estão associadas a uma chave do {{site.data.keyword.alchemyapishort}} no {{site.data.keyword.Bluemix_notm}}, quaisquer modelos implementados que referenciarem esse chave serão removidos do serviço. O {{site.data.keyword.Bluemix_notm}} verifica periodicamente se os modelos registrados estão associados com uma chave válida e quaisquer modelos que não estão são excluídos. Se o modelo é implementado com relação a uma chave que é excluída, o status do modelo muda para `error`.

### Solução do Problema

1. Verifique o status da implementação.

    Efetue login como administrador do {{site.data.keyword.knowledgestudioshort}}. Na página **Gerenciamento de modelo** > **Versões**, visualize a coluna **Status** para verificar o status do modelo que você implementou.

1. Se o status de implementação do modelo é `error` ou o status é `available`, mas o modelo não funciona quando você tenta usá-lo, retire o modelo da implementação clicando em **Remover implementação**.
1. Reimplemente o modelo.

    Use somente uma chave válida do {{site.data.keyword.alchemyapishort}} que tenha autorização para implementar modelos e copie e cole o ID do modelo e a chave API quando os incluir como parâmetros para a chamada API.

**Tarefas relacionadas**:

[Implementando um modelo de aprendizado de máquina no {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/publish-ml.html#wks_mabluemix)

## Não é possível criar uma conta grátis
{: #wks_ts_free}

### Problema

Você tenta criar uma conta grátis e vê a mensagem de erro, `Erro 331: Não é possível processar sua solicitação. Tente novamente mais tarde ou entre em contato com o help desk {{site.data.keyword.IBM_notm}}.`

### Causas

O {{site.data.keyword.knowledgestudioshort}} não permite mais de uma conta grátis por organização.

### Solução do Problema

Crie uma conta que não esteja incluída na organização.

Se você precisar usar sua conta atual para a avaliação grátis e sua conta do usuário estiver associada a uma conta paga, será possível enviar um chamado de suporte. Para obter mais informações, veja [Entrando em contato com o suporte {{site.data.keyword.IBM_notm}}](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Se você precisar usar a sua conta atual para a avaliação grátis e sua conta de usuário não estiver associada a uma conta paga, poste sua pergunta no [{{site.data.keyword.IBM_notm}} developerWorks Answers](https://developer.ibm.com/answers/topics/wks/), certificando-se de identificar a pergunta, **WKS**.

## Não é possível acessar o aplicativo
{: #wks_ts_access}

Descubra como conceder aos usuários acesso ao {{site.data.keyword.knowledgestudioshort}} e direcionar problemas de acesso comum.

Deve-se ter credenciais de registro do usuário da {{site.data.keyword.IBM_notm}} para solicitar uma instância do {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}}.

### Administrador

Cada instância do {{site.data.keyword.knowledgestudioshort}} tem uma função de administrador associada a ela. A pessoa que se inscreve originalmente para usar o aplicativo recebe a função de administrador automaticamente. O administrador pode convidar outras pessoas.

Para obter informações sobre como convidar pessoas para usar sua instância do aplicativo, veja [Montando a equipe](/docs/services/watson-knowledge-studio/team.html).

### Anotador humano

Se tiver sido convidado para a instância de alguém do {{site.data.keyword.knowledgestudioshort}} para servir como um anotador humano, você provavelmente recebeu um convite por e-mail. Primeiro, deve-se registrar com a {{site.data.keyword.IBM_notm}} se você ainda não tem as credenciais de registro do {{site.data.keyword.IBM_notm}}. Ao registrar-se com a {{site.data.keyword.IBM_notm}} e aceitar o convite, você recebe acesso à instância. No entanto, depois que você recebe acesso e antes de poder começar a anotar documentos, o administrador ou um gerente de projeto da instância deve incluí-lo em uma área de trabalho e designar uma tarefa de anotação para você. Você só pode executar qualquer ação na instância do {{site.data.keyword.knowledgestudioshort}} depois que uma tarefa é designada a você. Para anotar documentos, use o editor de verdade absoluta. Use um navegador Google Chrome para o melhor desempenho.

Para obter ajuda sobre como usar o editor de verdade absoluta, veja [Anotando documentos](/docs/services/watson-knowledge-studio/user-guide.html).

## Serviços experimentais: o que *experimental* significa?
{: #experimental}

Para obter informações sobre serviços experimentais, veja a [documentação do {{site.data.keyword.Bluemix_notm}}](/docs/services/index.html#experimental_services). Para obter detalhes completos dos serviços experimentais, veja a versão mais recente da [Descrição do serviço {{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=IBM+Bluemix+Service+Description){: new_window}.

## Problemas de espaço de armazenamento
{: #storage}

Dependendo do seu plano de assinatura, você pode atingir o limite de armazenamento especificado para seu plano e ser impedido de executar tarefas que deseja concluir.

### Sintomas

Você pode ver uma mensagem sobre ter excedido o espaço de armazenamento permitido ao tentar executar uma destas tarefas:

- Fazer upload de documentos ou dicionários
- Implementar um modelo ou versão de um modelo
- Executar um pré-anotador em documentos

### Causas

O limite de armazenamento foi atendido ou seria excedido se a ação fosse continuar.

### Solução do Problema

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

### Antes de Começar

Primeiramente, veja se uma solução está documentada para o problema que você está tendo. Procure {{site.data.keyword.knowledgestudioshort}} no [Portal de suporte {{site.data.keyword.IBM_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/home/entry/portal){: new_window}. Na página de resultados da procura, clique na guia **Suporte** para ver os resultados de notas técnicas, {{site.data.keyword.IBM_notm}} Redbooks e documentação. Clique na guia **Para desenvolvedores** para ver os resultados da comunidade do {{site.data.keyword.IBM_notm}} developerWorks, como blogs e perguntas do fórum.

Após tentar localizar sua resposta ou solução procurando no [Portal de suporte {{site.data.keyword.IBM_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/home/entry/portal){: new_window}, é possível entrar em contato com o Suporte {{site.data.keyword.IBM_notm}}. O tipo de suporte que você tem depende de seu tipo de serviço.

- **usuários do plano Grátis**

    Obtenha ajuda e respostas para perguntas por meio dos membros amigos da comunidade do desenvolvedor. Para links para as comunidades do desenvolvedor, veja a seção **Comunidade do desenvolvedor** no índice.

- **Usuários do plano Pago**

    Como um usuário do plano pago, você também pode fazer perguntas e aprender com as perguntas de outros usuários. Os fóruns são abertos a todos e são um ótimo local para começar. Para links, veja a seção **Comunidade do desenvolvedor** no índice.

    Envie um chamado de problema do [{{site.data.keyword.IBM_notm}} Cloud Service Portal ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson.service-now.com/wcp){: new_window}.

    > **Nota:** deve-se estar autorizado a enviar problemas à {{site.data.keyword.IBM_notm}}.

### Procedimento

Para entrar em contato com o Suporte {{site.data.keyword.IBM_notm}} sobre um problema:

1. Defina o problema, reúna informações de plano de fundo e determine a gravidade do problema.
1. Reúna informações de diagnóstico, se possível.
1. Envie o problema para o Suporte {{site.data.keyword.IBM_notm}}. Para obter detalhes de contato, consulte o [guia de suporte do Software como Serviço ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www-01.ibm.com/software/support/acceleratedvalue/SaaS_Handbook_V18.pdf){: new_window}.
