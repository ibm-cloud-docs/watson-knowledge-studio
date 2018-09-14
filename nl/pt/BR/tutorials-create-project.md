---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}.
{: tip}

# Introdução ao {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

Este tutorial do {{site.data.keyword.knowledgestudiofull}} ajuda você a executar tarefas de pré-requisito que devem ser concluídas antes que possa iniciar qualquer um dos outros tutoriais.
{: shortdesc}

## Antes de Começar
{: #prereq}

- Confirme se você está usando um navegador suportado. Para obter informações, veja [Requisitos do navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
-  Para concluir este tutorial, deve-se ter pelo menos um ID do usuário que seja possível usar no {{site.data.keyword.knowledgestudioshort}}. Esse ID do usuário deve ter a função Administrador. Se você se inscrever para um plano Lite, como o único usuário, você terá a função Administrativa. Para obter informações sobre funções de usuário, veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html).

## Criando uma instância de serviço
{: #instance}

1. Caso ainda não tenha feito isso, [inscreva-se para um {{site.data.keyword.ibmid}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net){: new_window} e efetue login no {{site.data.keyword.cloud_notm}}.
1. Na página de serviços do {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/developer/watson/services){: new_window}, clique no tile {{site.data.keyword.knowledgestudioshort}} e inscreva-se para um plano.
1. Depois de se inscrever para um plano, na lista de serviços existentes, ative o {{site.data.keyword.knowledgestudioshort}}.

## Lição 1: designando funções de usuário
{: #wks_tutless1}

Nesta lição, você aprenderá sobre as diferentes funções que podem ser designadas aos usuários no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa
{: #wks_tutless1_about}

A criação de um modelo de aprendizado de máquina requer entrada de especialistas no assunto, gerentes de projeto e usuários que podem entender e interpretar modelos estatísticos. Os administradores designam funções a cada usuário, de modo que eles tenham autoridade apropriada para suas tarefas. Para obter mais informações sobre funções de usuário, veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html).

### Procedimento
{: #wks_tutless1_procedure}

1. Efetue login no {{site.data.keyword.knowledgestudioshort}} com seu ID de administrador. Se você tiver uma instância existente do {{site.data.keyword.knowledgestudioshort}}, será possível localizá-la na página de serviços do {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/developer/watson/services){: new_window}.
1. Clique no ícone Configurações para abrir a página Detalhes do serviço. A página lista todos os IDs do usuário que estão registrados como usuários do {{site.data.keyword.knowledgestudioshort}}. Cada ID do usuário tem uma das funções a seguir (em ordem decrescente de permissões incluídas):

    - Administrador
    - Gerente de projeto
    - Anotador humano

    Para obter informações sobre funções de usuário, consulte [Funções de usuário no {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Verifique se há pelo menos um usuário com a função Administrador. Um ID do usuário com essa função pode criar áreas de trabalho e agir como um gerente de projeto ou anotador humano.
1. Se você tiver acesso a IDs de usuário adicionais, verifique se há pelo menos dois usuários com a função Anotador Humano.

    > **Nota:** criando um modelo real geralmente envolve múltiplos anotadores humanos, além um administrador ou gerente de projeto. No entanto, para propósitos do tutorial, é possível continuar com um único ID do usuário.

1. Opcional: mude a função que está designada a um ID do usuário. Na coluna **Ação** da tabela, clique no link **Editar**, em seguida, mude a função de usuário designada.

    > **Nota:** é possível fazer upgrade de um ID de usuário para uma função com permissões superiores, mas não é possível fazer downgrade de um usuário com uma função Administrativa ou de Gerente de Projeto para a função Anotador Humano.

## Lição 2: criando uma área de trabalho
{: #wks_tutless2}

Nesta lição, você aprenderá a criar uma área de trabalho no {{site.data.keyword.knowledgestudioshort}}.

### Sobre essa Tarefa
{: #wks_tutless2_about}

Uma área de trabalho define todos os recursos que são necessários para criar um modelo de aprendizado de máquina, incluindo documentos de treinamento, o sistema de tipos, dicionários e anotações que são incluídos por anotadores humanos. Para obter mais informações sobre a criação de área de trabalho, veja [Criando uma área de trabalho](/docs/services/watson-knowledge-studio/create-project.html).

### Procedimento
{: #wks_tutless2_procedure}

1. Como um administrador do {{site.data.keyword.knowledgestudioshort}}, em seu painel do {{site.data.keyword.cloud_notm}} [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net){:new_window}, ative o serviço {{site.data.keyword.knowledgestudioshort}}.
1. Clique em **Criar área de trabalho**.
1. Especifique os detalhes para a nova área de trabalho:

    - No campo **Nome da área de trabalho**, digite `Minha área de trabalho`.
    - No campo **Descrição da área de trabalho**, digite `Área de trabalho do tutorial do Watson Knowledge Studio`.
    - No campo **Linguagem de documentos**, use o valor padrão, **Inglês**. Os arquivos de amostra que você usará para este tutorial estarão em inglês.

1. Clique em **Criar**.

### Resultados
{: #wks_tutless2_results}

A área de trabalho é criada e aberta automaticamente.

### O que fazer em seguida
{: #wks_tutless2_next}

Agora é possível começar a configurar os recursos da área de trabalho, como o sistema de tipos.

## Lição 3: criando um sistema de tipos
{: #wks_tutless3}

Nesta lição, você aprenderá como fazer upload e modificar um sistema de tipos no {{site.data.keyword.knowledgestudioshort}}. Deve-se criar ou fazer upload de um sistema de tipos antes de começar qualquer tarefa de anotação.

### Sobre essa Tarefa
{: #wks_tutless3_about}

Para obter mais informações sobre sistemas de tipos, veja [Sistemas de tipos](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem).

### Procedimento
{: #wks_tutless3_procedure}

1. Faça download do arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> para seu computador. Esse arquivo contém um sistema de tipos KLUE de exemplo.
1. Clique em  ** Ativos ** >  ** Tipos de Entidades **.
1. Na página Tipos de entidade, clique em **Fazer upload**.
1. Faça upload do arquivo `en-klue2-types.json` de seu computador. O sistema de tipos transferido por upload é exibido na tabela.
1. Procure o sistema de tipos para que seja possível ver os dados que foram transferidos por upload.
1. Edite um tipo de entidade:

    1. Localize o tipo de entidade MONEY.
    1. Clique duas vezes em qualquer lugar na linha da tabela para editar o tipo de entidade.
    1. Na coluna **Funções**, clique no ícone **Excluir uma função** ![O ícone "Excluir uma função".](images/wks_delete.jpg "O ") próximo à função AWARD.

        ![Uma captura de tela de exclusão de uma função de um tipo de entidade.](images/wks_tut_delete_role.jpg "Uma captura de tela que mostra o cursor passando sobre o ")

    1. Clique em **Salvar**.

### O que fazer em seguida
{: #wks_tutless3_next}

Depois de terminar de fazer mudanças no sistema de tipos, é possível começar a incluir documentos em sua área de trabalho.

## Lição 4: incluindo um dicionário
{: #wks_tutless4}

Nesta lição, você aprenderá como incluir um dicionário em uma área de trabalho no {{site.data.keyword.knowledgestudioshort}}. Os dicionários são usados para pré-anotar texto ao criar um modelo de aprendizado de máquina.

### Sobre essa Tarefa
{: #wks_tutless4_about}

Para obter mais informações sobre dicionários, veja [Incluindo dicionários em uma área de trabalho](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Procedimento
{: #wks_tutless4_procedure}

1. Faça download do arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> para seu computador. Esse arquivo contém termos de dicionário em formato CSV, adequados para fazer upload em um dicionário do {{site.data.keyword.knowledgestudioshort}}.
1. Clique em  ** Ativos **  >  ** Dicionários **.
1. Clique em **Criar dicionário** para incluir um dicionário.

    > **Nota:** não clique em **Fazer upload de dicionário**, que é usado para fazer upload de um dicionário que você deseja usar no estado em que se encontra. Para o tutorial, você criará um novo dicionário editável e, em seguida, fará upload de termos nele.

1. No campo **Nome**, digite `Test dictionary` e clique em **Salvar** para criar o dicionário (vazio).

    O novo dicionário é criado e automaticamente aberto para edição.

1. Na área de janela de dicionário, clique em **Fazer upload**.
1. Faça upload do arquivo `dictionary-items-organization.csv` de seu computador. Os termos no arquivo são transferidos por upload para o dicionário.
1. Clique em **Incluir entrada** para criar um novo termo. Uma linha editável é incluída na parte superior da tabela.
1. Na coluna **Formas superficiais**, digite `IBM` e `International Business Machines Corporation` em linhas separadas. (Quando você começa a digitar uma nova forma superficial, um espaço é incluído abaixo para uma forma superficial adicional.) Deixe o botão de opções próximo a `IBM` selecionado, que indica que `IBM` é o lema.
1. Na coluna **Parte do discurso**, selecione **Substantivo**.
1. Clique em **Salvar**.

    ![Uma captura de tela da página Dicionários. A entrada de dicionário "IBM" é selecionada e suas formas superficiais e a parte do discurso são destacadas.](images/wks_tutdict4.jpg "Uma captura de tela da página Dicionários. A ")

### O que fazer em seguida
{: #wks_tutless4_next}

Depois de criar um dicionário, é possível usá-lo para acelerar tarefas de anotação humana pré-anotando os documentos.

## Resumo do tutorial
{: #wks_tutsum}

Ao aprender sobre o {{site.data.keyword.knowledgestudioshort}}, você criou uma área de trabalho e incluiu artefatos nela.

### Lições aprendidas
{: #lessons_learned}

Ao concluir este tutorial, você terá aprendido sobre os conceitos a seguir:

- Áreas de trabalho
- Sistemas de tipos
- Dicionários
