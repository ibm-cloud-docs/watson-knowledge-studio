---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# Funções de usuário no  {{site.data.keyword.knowledgestudioshort}}
{: #roles}

As funções do {{site.data.keyword.knowledgestudiofull}} são usadas para organizar uma equipe de pessoas que criam aprendizado de máquina ou modelos baseados em regra.
{: shortdesc}

## Notas sobre funções no  {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- As funções de usuário no {{site.data.keyword.knowledgestudioshort}} são gerenciadas nos níveis a seguir:
  - {{site.data.keyword.cloud}}  funções controlam o acesso aos serviços  {{site.data.keyword.cloud_notm}} . O {{site.data.keyword.knowledgestudioshort}} usa o Cloud Foundry para controle de acesso, que requer que os usuários do {{site.data.keyword.knowledgestudioshort}} tenham a função de desenvolvedor. Para obter mais informações, veja [Acesso ao Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - As funções do {{site.data.keyword.knowledgestudioshort}} controlam o acesso à funcionalidade do {{site.data.keyword.knowledgestudioshort}}, conforme descrito nesta página.
- Uma função do {{site.data.keyword.knowledgestudioshort}} não é necessária para criar uma instância do {{site.data.keyword.knowledgestudioshort}}. No entanto, quando uma pessoa cria uma instância do {{site.data.keyword.knowledgestudioshort}}, o primeiro usuário a ativar o {{site.data.keyword.knowledgestudioshort}} é designado à função de administrador do {{site.data.keyword.knowledgestudioshort}}.
- Para gerenciar uma área de trabalho, os gerentes de projeto precisam ser designados à área de trabalho por um administrador.
- Os administradores e gerentes de projeto podem executar a função de anotadores humanos, mas devem ser designados a conjuntos de anotações da mesma maneira que os anotadores humanos devem ser designados a conjuntos de anotações.
- Depois de designadas, não é possível fazer downgrade das funções de usuário de níveis de permissões mais altos para mais baixos. Não é possível fazer downgrade de administradores para gerentes de projeto ou anotadores humanos e não é possível fazer downgrade dos gerentes de projeto para anotadores humanos. Para obter informações sobre a inclusão de usuários, o upgrade de funções e a desativação de contas do usuário, veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html).

## Descrições da Função
{: #descriptions}
As funções do {{site.data.keyword.knowledgestudioshort}} são descritas na tabela a seguir. As funções são listadas na ordem do nível mais alto para o nível mais baixo de permissões.

| Papel | Descrição |
|------|-------------|
| Administrador | Responsável pelas tarefas administrativas, que incluem o gerenciamento de usuários, o consumo de recursos e os encargos mensais. Em configurações de equipes grandes, os administradores raramente participam do processo de desenvolvimento do modelo.
| Gerente de projeto | Responsável pela organização geral da área de trabalho à qual ela ou ele está designado. As tarefas incluem a criação do sistema de tipos, o gerenciamento de ativos, o gerenciamento do trabalho de anotação, a avaliação do modelo de aprendizado de máquina e a implementação de modelos. Os usuários nessa função precisam de conhecimento do assunto do segmento de mercado porque eles criam o sistema de tipos, ensinam aos anotadores humanos como aplicar corretamente o sistema de tipos e avaliam a qualidade do modelo. |
| Anotador humano | Executa a rotulagem das menções de entidade e menções de relacionamento nos documentos de treinamento aos quais ele ou ela está designado. O trabalho é designado a anotadores humanos e monitorado pelo gerente de projeto. Os anotadores humanos podem não ter conhecimento do assunto do segmento de mercado, desde que sejam ensinados pelo gerente de projeto como aplicar corretamente o sistema de tipos. |
{:caption="Tabela 1. Descrições de função" caption-side="top"}

## Permissões de função
{: #permissions}

Para comparar as permissões de cada função, veja a tabela a seguir. Uma permissão é listada em cada linha. Se uma função tiver essa permissão, a coluna de função será marcada com uma marca de seleção (&checkmark;).

| Permissão | Administrador | Gerente de projeto | Anotador humano |
|------------|-------|-----------------|-----------------|
| Gerenciar o acesso e as funções do usuário | &checkmark; |  |  |
| Gerenciar áreas de trabalho | &checkmark; |  |  |
| Criar o sistema de tipos e as diretrizes de anotação | &checkmark; | &checkmark; |  |
| Upload de documentos de treinamento | &checkmark; | &checkmark; |  |
| Gerenciar regras | &checkmark; | &checkmark; |  |
| Pré-anotar documentos | &checkmark; | &checkmark; |  |
| Gerenciar tarefas de anotação | &checkmark; | &checkmark; |  |
| Resolver conflitos de anotação com a anotação humana (*adjudicação*) | &checkmark; | &checkmark; |  |
| Treinar e avaliar modelos de aprendizado de máquina | &checkmark; | &checkmark; |  |
| Implementar e remover a implementação de modelos para serviços de tempo de execução | &checkmark; | &checkmark; |  |
| Executar anotação do documento | &checkmark; | &checkmark; | &checkmark; |
{:caption="Tabela 2. Permissões de função" caption-side="top"}
