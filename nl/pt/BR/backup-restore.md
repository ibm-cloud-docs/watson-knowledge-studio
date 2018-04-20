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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/backup-restore.html){: new_window}.
{: tip}

# Backup e restauração de dados
{: #backup-restore}

Se você precisar fazer backup e restaurar uma área de trabalho para o {{site.data.keyword.knowledgestudioshort}}, execute estas tarefas. Além disso, se você precisa executar uma migração manual de dados de uma instância do {{site.data.keyword.knowledgestudioshort}} para outra, como quando migrar de uma instância no {{site.data.keyword.IBM_notm}} Marketplace para uma instância no {{site.data.keyword.cloud_notm}}, execute estas tarefas.
{: shortdesc}

_Migração manual de dados_ é o processo de fazer backup de seus dados de uma instância e restaurá-los em outra instância.

**Nota**: o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}} usa o termo _área de trabalho_, enquanto o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace usa o termo _projeto_. A funcionalidade é a mesma. Somente a terminologia é diferente.

Para fazer backup e restaurar seus dados, conclua as etapas a seguir:

1. [Entender quais dados podem ser submetidos a backup](#data)
1. [Preparar para o backup](#prepare)
1. [Exportar artefatos da instância atual](#export)
1. [Recriar espaços na nova instância](#recreateproj)
1. [Restaurar os dados da área de trabalho](#restoredata)
1. [Restaurar os modelos](#restoremodels)
1. [Restaurar quaisquer tarefas de anotação incompletas](#restoretasks)

## Os dados que podem ser submetidos a backup
{: #data}

Os artefatos a seguir podem ser submetidos a backup e migrados manualmente:

- Dicionários editáveis
- Sistema de tipos
- Conjuntos de documentos de verdade absoluta aprovados

Os tipos de artefatos a seguir não podem ser submetidos a backup e migrados manualmente:

- Documentos de anotação humana em andamento
- Tarefas de anotação
- Modelos e capturas instantâneas
- Dicionários somente leitura

## Preparando para backup
{: #prepare}

Para preparar para fazer backup e restaurar seus dados, conclua as etapas a seguir:

1. Conclua qualquer trabalho que está em andamento em sua área de trabalho.

    - > **Importante:** conclua quaisquer tarefas de anotação em andamento. Somente documentos que foram anotados, adjudicados e aprovados e promovidos para verdade absoluta podem ser submetidos a backup. Se você não concluir o trabalho de anotação, perderá qualquer esforço de anotação que estiver em andamento, mas não completamente pronto.

    - Se você criou tarefas de anotação para controlar o trabalho que deseja fazer, mas nenhum trabalho de anotação começou e não ocorrerá até que a área de trabalho seja restaurada, faça uma lista das tarefas de anotação pendentes. Certifique-se de anotar os conjuntos de documentos que você importou, mas que não foram incluídos na verdade absoluta ainda. Além disso, faça uma nota de quem você designou para anotar cada conjunto de documentos. Você precisará fazer um novo upload desses conjuntos de documentos e recriar as tarefas de anotação depois que a área de trabalho for restaurada.

1. Entenda o tokenizer usado.

    Para modelos de aprendizado de máquina, as áreas de trabalho usam o tokenizer baseado em aprendizado de máquina por padrão. Se você estiver usando um tokenizer baseado em dicionário e tiver uma necessidade específica de continuar fazendo isso, será possível configurar a área de trabalho para usar o tokenizer baseado em dicionário quando restaurá-la. Para obter mais informações, veja [Tokenizers](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Gerencie recursos de modelo.

    Não é possível migrar seu modelo, suas versões e os dados de captura instantânea. Os recursos (exceto dicionários somente leitura) que você usou para treinar esses artefatos podem ser migrados. Portanto, após a migração, será possível recriar o modelo. O modelo que será produzido executará de forma idêntica aos modelos que você gerou antes da migração porque os recursos usados para treinamento serão os mesmos.

    **ATENÇÃO**: se você tiver um modelo que já está implementado e planeja excluir a área de trabalho após fazer backup, retirar o modelo da implementação. É possível reconstruir e reimplementar o modelo após você restaurar a área de trabalho por meio do backup. Para obter informações sobre como remover a implementação de modelos, veja [Removendo a implementação de modelos de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Removendo a implementação de modelos baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

    **Esteja ciente de que se você não retirar o modelo da implementação, o resultado será um modelo implementado _órfão_. Os modelos implementados órfãos continuarão a gerar encargos em suas contas mensais.**

1. Gerencie informações do dicionário somente leitura.

    Os dicionários somente leitura não podem ser migrados. Descubra qual é o local de onde o dicionário somente leitura foi importado, assim é possível fazer upload dele para sua área de trabalho após a migração.

1. Faça uma lista de funções de usuário atuais.

    **NOTA**: esta etapa é opcional. Ela é normalmente executada quando uma área de trabalho é migrada entre instâncias e a nova área de trabalho deve ser idêntica à área de trabalho original. Se deseja migrar somente os dados da área de trabalho para uma nova área de trabalho, é possível ignorar esta etapa.

    Se você está migrando áreas de trabalho entre instâncias diferentes, considere fazer uma lista de usuários e suas funções para a instância que está sendo submetida a backup. Alguém com a função de Administrador pode imprimir a lista na página Gerenciamento de conta do usuário. Após as áreas de trabalho serem recriadas na nova instância, alguém com função de Administrador deve incluir os usuários e designar suas funções.

    Veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html) para obter mais informações sobre as funções.

1. Anote as informações de área de trabalho.

    Enquanto você ainda tem acesso à instância atual, para cada área de trabalho que deseja migrar, faça uma nota das informações a seguir:
    - Nome da área de trabalho
    - Descrição da área de trabalho
    - Proprietário da área de trabalho
    - Linguagem
    - Se você tiver quaisquer tarefas de anotação incompletas, porque elas não podem ser submetidas a backup ou migradas, anote os anotadores humanos que estão designados a tarefas incompletas na área de trabalho. Além disso, anote os detalhes da tarefa de anotação, como o nome da tarefa, data de vencimento e quais conjuntos de documentos estão designados a quais usuários.

## Fazendo download de artefatos
{: #export}

Para cada área de trabalho que você deseja migrar, faça download dos artefatos a seguir. Armazene-os em um local seguro do qual você será capaz de fazer upload deles para a nova instância mais tarde.

- Sistema de tipos
- Dicionários

  **Nota**: somente dicionários editáveis serão transferidos por download. Não é possível fazer download de dicionários somente leitura.

- Documentos

  Veja [Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html) para obter informações sobre como fazer download desses artefatos para que eles possam ser importados para uma nova área de trabalho.

## Recriando áreas de trabalho
{: #recreateproj}

**NOTA**: nesta etapa, a única configuração que deve corresponder à configuração da área de trabalho original (transferida por download) é a linguagem. O restante das configurações pode diferir das configurações da área de trabalho original.

Recrie cada área de trabalho copiando as informações a seguir da instância anterior para a nova:

- Nome da área de trabalho
- Descrição da área de trabalho
- Linguagem de documentos (essa configuração deve corresponder à configuração na área de trabalho original)
- Se você usou anteriormente um tokenizer baseado em dicionário na área de trabalho e tem uma necessidade válida de continuar a usá-lo, deve-se especificar que deseja usar o tokenizer baseado em dicionário em vez do tokenizer padrão no momento ao criar a área de trabalho. Para obter mais informações sobre as opções, veja [Tokenizers](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

  Para usar um tokenizer baseado em dicionário, expanda a seção Opções avançadas da janela Criar área de trabalho (no {{site.data.keyword.IBM_notm}} Marketplace, a janela Criar área de trabalho) e mude a configuração de tokenizer.

## Restaurando dados da área de trabalho
{: #restoredata}

Depois de recriar as áreas de trabalho, faça upload dos artefatos transferidos por download anteriormente:

1. Faça upload do sistema de tipos por meio do backup do sistema de tipos criado anteriormente.
   Para obter detalhes, veja [Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html).

  **Nota**: deve-se fazer upload do sistema de tipos para poder fazer upload de qualquer outro artefato que você está movendo da área de trabalho submetida a backup.

1. Faça upload dos dicionários por meio do backup de dicionário criado anteriormente.
   Para obter detalhes, veja [Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html).

  Se você usou os dicionários somente leitura na versão anterior da área de trabalho, faça upload deles nessa área de trabalho por meio de sua fonte original.

  **Nota**: quando você inclui dicionários, o pré-anotador de dicionário é criado automaticamente. Você associa o dicionário com um tipo de entidade no momento em que executa o pré-anotador.

1. Faça upload dos documentos que você transferiu por download da versão anterior da área de trabalho para esta versão da área de trabalho.
   Para obter detalhes, veja [Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html).

## Restaurando modelos
{: #restoremodels}

Neste ponto, todos os artefatos que foram usados para treinar o modelo na versão anterior (submetida a backup) da área de trabalho agora estão disponíveis nessa nova instância.

Para reimplementar um modelo de aprendizado de máquina que você implementou na instância anterior, conclua as etapas a seguir:

1. Treine o modelo de aprendizado de máquina. Para obter detalhes, veja [Criando um modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/train-ml.html).

  **Nota**: não execute nenhum pré-anotador em documentos anotados que você migrou para essa área de trabalho porque eles perderão quaisquer anotações neles que foram incluídas por anotadores humanos.

1. Depois de criar o modelo, implemente-o novamente. Para obter detalhes, veja [Usando o modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html).

Para reimplementar um modelo baseado em regra que você implementou na instância anterior, conclua as etapas a seguir:

1. [Crie o modelo baseado em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html).
1. [Implemente o modelo baseado em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html).

## Restaurando tarefas de anotação incompletas
{: #restoretasks}

Se você tinha quaisquer tarefas de anotação que foram criadas, mas não concluídas na área de trabalho anterior, conclua as etapas a seguir para recriar as tarefas de anotação incompletas:

1. Faça upload de quaisquer documentos que não foram anotados ainda, mas que você deseja incluir na verdade absoluta para continuar a melhorar o modelo.
1. Dos documentos recentemente importados e não anotados, crie conjuntos de documentos para anotação. Esses conjuntos são agora chamados de _conjuntos de anotações_. Para obter detalhes, veja [Criando e designando conjuntos de anotações](/docs/services/watson-knowledge-studio/document-for-annotation.html).
1. Recrie as tarefas de anotação. Dê à tarefa o mesmo nome, uma data de vencimento apropriada e designe conjuntos de anotações aos anotadores humanos apropriados.
