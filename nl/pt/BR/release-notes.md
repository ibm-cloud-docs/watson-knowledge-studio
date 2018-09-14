---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Notas sobre a liberação
{: #release-notes}

Os novos recursos e mudanças a seguir no {{site.data.keyword.knowledgestudiofull}} estão disponíveis.
{: shortdesc}

## Agosto de 2018
{: #august2018}

### Novos recursos e mudanças
{: #new-august2018}

- Introduzida uma nova opção para migração automatizada de instâncias do plano Padrão da plataforma {{site.data.keyword.IBM_notm}} Marketplace descontinuada para a plataforma [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}. Se tiver uma instância Padrão na plataforma descontinuada, você terá a opção de migrar. Para obter mais informações, consulte  [ Migrando para o  {{site.data.keyword.cloud_notm}} ](/docs/services/watson-knowledge-studio/client-migration.html).

## Julho de 2018
{: #july2018}

### Novos recursos e mudanças
{: #new-july2018}

- A página **Modelos implementados** foi atualizada para incluir modelos de instâncias do {{site.data.keyword.knowledgestudioshort}} que são gerenciadas por [*grupos de recursos* do IAM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window}, além de modelos que são gerenciados por [*organizações* Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.

   O que você vê na página Modelos implementados depende da [região ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} que hospeda sua instância do {{site.data.keyword.knowledgestudioshort}}. Se a região suportar instâncias gerenciadas por ambos os métodos de gerenciamento de acesso, você verá uma guia para cada método. Os modelos de instâncias gerenciadas pelo IAM estão listados na guia **Grupos de recursos**. Os modelos de instâncias gerenciadas pelo Cloud Foundry estão listados na guia **Organizações**.

  Se a região suportar instâncias gerenciadas somente por um dos métodos de gerenciamento de acesso, você verá apenas uma lista de modelos, pois apenas um método de gerenciamento de acesso será aplicável.

   Para visualizar a página **Modelos implementados**, no menu **Configurações** na barra de menus superior direita, clique em **Gerenciar modelos implementados**. Para obter informações sobre como remover a implementação de modelos na página **Modelos implementados**, veja [Removendo a implementação de modelos de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Removendo a implementação de modelos baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

- A navegação foi mudada para melhor se alinhar com o fluxo de trabalho do {{site.data.keyword.knowledgestudioshort}}. Além disso, a seguinte funcionalidade foi reorganizada:

    - Na versão anterior, o gerenciamento de dicionários foi incluído como parte da página Pré-anotadores. Agora, o gerenciamento de dicionários está localizado na página Dicionários na seção Ativos da navegação.
    - Na versão anterior, a funcionalidade de anotação humana foi distribuída entre as guias Menções, Relações e Correferências na seção Anotação de documento da navegação. Agora, a funcionalidade é mesclada sob a página Tarefas de anotação na seção Modelo de aprendizado de máquina da navegação.
    - Para gerenciar as tarefas de anotação humana, na versão anterior, você localizou a guia Tarefas na página Ativos e Ferramentas > Documentos. Agora, você inclui tarefas e gerencia tarefas existentes na página Tarefas de anotação na seção Modelo de aprendizado de máquina da navegação.
    - Na versão anterior, as páginas Regras, Regex e Dicionários eram páginas separadas na seção Anotação de documento da navegação. Agora, a funcionalidade é mesclada na página Regras na seção Modelo baseado em regra da navegação.

    Para obter mais detalhes sobre as mudanças de navegação, veja a Figura 1 e a Tabela 3.

![Capturas de tela da navegação anterior (lado esquerdo) e da nova navegação (lado direito).](images/nav3-0718.svg "Capturas de Tela da navegação anterior e nova navegação. Os detalhes sobre as mudanças estão listados na Tabela 3 e no texto anterior.") Figura 1. Capturas de tela da navegação anterior (lado esquerdo) e da nova navegação (lado direito).

| Recurso | Local anterior |Local atual |
|---------|--------------------------|----------------------|
| Tarefas de anotação | Ativos & Ferramentas > Documentos > Tarefas | Modelo de Aprendizagem de Máquina > Tarefas de Anotação |
| Guia Coreferences | Anotação do Documento | Modelo de aprendizado de máquina > Tarefas de anotação > tarefa > conjunto de anotação > documento |
| Página Dicionários (Gerenciamento) | Ativos & Tools > Pré-annotators > Gerenciar Dicionários | Ativos |
| Guia Dicionários (mapeamento para classes para modelo baseado em regra) | Anotação do Documento | Modelo Baseado em Regra > Regras |
| Página Documentos | Ativos & Ferramentas | Ativos |
| Página Tipos de Entidade | Ativos & Ferramentas | Ativos |
| Guia Menções | Anotação do Documento | Modelo de aprendizado de máquina > Tarefas de anotação > tarefa > conjunto de anotação > documento |
| Página Desempenho | Gerenciamento de modelo | Modelo de Aprendizagem |
| Página de pré-anotadores | Ativos & Ferramentas | Modelo de Aprendizado de Máquina > Pré-anotação |
| Guia Regex | Anotação do Documento | Modelo Baseado em Regra > Regras |
| Página Tipos de Relação | Ativos & Ferramentas | Ativos |
| Guia Relações | Anotação do Documento | Modelo de aprendizado de máquina > Tarefas de anotação > tarefa > conjunto de anotação > documento |
| Guia Regras | Anotação do Documento | Modelo baseado em regra |
| Guia Tarefas | Ativos & Ferramentas > Documentos | Modelo de Aprendizagem de Máquina > Tarefas de Anotação |
| Página Versões (modelo de aprendizado de máquina) | Gerenciamento de modelo | Modelo de Aprendizagem |
| Página Versões (modelo baseado em regra) | Gerenciamento de modelo | Modelo baseado em regra |
{: caption="Tabela 3. Mudanças na navegação (julho de 2018)" caption-side="top"}

## Maio de 2018
{: #may2018}

### Novos recursos e mudanças
{: #new-may2018}

- Um problema de configuração foi corrigido que fazia com que as instâncias de serviço na região Sydney não aparecessem na região Sul dos EUA.
- Na janela Implementar Modelo, se a região na qual você está implementando suportar os *grupos de recursos* do {{site.data.keyword.iamlong}} e os *espaços* do Cloud Foundry, para ver a lista, será necessário escolher o método de gerenciamento de acesso que sua instância de serviço usa. Para obter mais informações sobre o Cloud Foundry e o {{site.data.keyword.iamshort}}, veja [Grupos de recursos e gerenciamento de acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}.
- Incluída a configuração de coleta de dados na página Detalhes do serviço. Para obter mais informações sobre coleta de dados, veja [Resolução de problemas, suporte e FAQs](/docs/services/watson-knowledge-studio/troubleshooting.html#content)
- Suporte ao idioma chinês (tradicional) incluído.
- Os usuários que têm a função Administrador agora podem ver o número de áreas de trabalho que são usadas. Essas informações estão disponíveis na página Detalhes do serviço.
- O {{site.data.keyword.alchemylanguagefull}} não está mais disponível para implementar modelos. Para obter informações, veja [Retirada do serviço {{site.data.keyword.alchemyapishort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}.
- Agora, se você excluir uma área de trabalho, será solicitado que confirme sua ação. Esperamos que essa confirmação evite exclusões acidentais.
- A documentação inclui alguns novos detalhes sobre privacidade de dados. Leia mais em  [ Segurança de Informações ](/docs/services/watson-knowledge-studio/information-security.html).

## Abril de 2018
{: #april2018}

### Novos recursos e mudanças
{: #new-april2018}

- O plano Grátis do {{site.data.keyword.knowledgestudioshort}} foi substituído pelo plano Lite. Para obter mais informações, veja [Acessar Lite com o Watson {{site.data.keyword.knowledgestudioshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}.

## Março de 2018
{: #march2018}

### Novos recursos e mudanças
{: #new-march2018}

- Uma página **Modelos implementados** está disponível na qual é possível visualizar todos os modelos do {{site.data.keyword.knowledgestudioshort}} que são implementados para serviços nos espaços aos quais você tem acesso. Para visualizar a página **Modelos implementados**, no menu **Configurações** na barra de menus superior direita, clique em **Gerenciar modelos implementados**. Para obter informações sobre remoção de implementação e visualização de modelos na página **Modelos implementados**, veja [Removendo a implementação de modelos de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Removendo a implementação de modelos baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
- Uma tradução francesa da interface do {{site.data.keyword.knowledgestudioshort}} está agora disponível.
- O {{site.data.keyword.alchemylanguagefull}} não está mais disponível como uma pré-anotador. Em vez do {{site.data.keyword.alchemylanguageshort}}, é possível usar o {{site.data.keyword.nlushort}} para pré-anotar seus documentos. Para obter mais informações, veja [Autoinicializando a anotação](/docs/services/watson-knowledge-studio/preannotation.html).

## Dezembro de 2017
{: #december2017}

### Novos recursos e mudanças
{: #new-december2017}

- {{site.data.keyword.knowledgestudioshort}} ativado no {{site.data.keyword.cloud_notm}}. Para obter informações sobre processo e planejamento de migração, veja [Migrando para o {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).
- Navegação projetada novamente. Para obter detalhes sobre as mudanças de navegação, veja [Tabela 2](#september2017) nas notas sobre a liberação de setembro de 2017.
- Incluído {{site.data.keyword.nlufull}} como um pré-anotador.
- Incluídas configurações de gerenciamento de usuário e de armazenamento para a página Detalhes do serviço. Para obter informações sobre como incluir usuários, veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html). Para obter informações sobre como configurar limites de armazenamento, veja [Resolução de problemas > Problemas de espaço de armazenamento](/docs/services/watson-knowledge-studio/troubleshooting.html#storage).
- Incluída uma página de desempenho para avaliação e orientação de qualidade do modelo sobre como melhorar a qualidade.

## Novembro de 2017
{: #november2017}

### Mudanças
{: #new-november2017}

- Corrigido um problema em que algumas anotações de relação ficavam ausentes no corpus transferido por download.
- Corrigido um problema em que um modelo não podia ser retirado da implementação se seu status fosse **Nenhum**.
- Corrigido um problema em que o modelo não podia ser avaliado para coreano.

## Outubro de 2017
{: #october2017}

### Mudanças
{: #new-october2017}

- Corrigido o problema com o botão **Exportar** não sendo ativado até que você atualizasse a janela do navegador na liberação do {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).
- Corrigidos os rótulos de botões e as dicas de ferramenta para corresponder às mudanças para os termos _upload_ e _download_ na liberação do {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental). Esses termos são usados em vez de _importar_ e _exportar_ ao se referir a sistemas de tipos, documentos e dicionários.
- Corrigido o atraso na atualização das descrições na página Gerenciamento de conta do usuário do {{site.data.keyword.knowledgestudioshort}} na liberação do {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).
- Na seção de pré-anotação da interface, foram feitas algumas mudanças da GUI para esclarecer a funcionalidade do modelo de aprendizado de máquina, do modelo baseado em regra, do dicionário e do {{site.data.keyword.alchemylanguagefull}}. Mudado o rótulo do botão de **Executar** para **Pré-anotar**, mudado o título da janela de **Executar anotador** para **Executar pré-anotação** e mudada a mensagem de erro para esclarecer que não é possível incluir anotações automatizadas depois que os humanos anotaram os documentos.
- Para projetos ou áreas de trabalho que usam tokenizers baseados em dicionário, corrigido um problema que mostrava sentenças vazias se você importasse documentos sem verdade absoluta.

## Setembro de 2017
{: #september2017}

### Novos recursos e mudanças
{: #new-sept17}

- Liberada uma nova experiência do usuário de front-end para o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.Bluemix}} como um serviço [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental). As mudanças incluem uma navegação reorganizada e uma nova página de análise de desempenho do modelo. Para um resumo das mudanças de navegação, veja a tabela nos problemas conhecidos.
- Incluído o suporte ao idioma chinês (simplificado) e holandês.

### Problemas conhecidos
{: #issues-sept17}

- Para um modelo baseado em regra, depois de mapear classes e tipos de entidade, o botão **Exportar** não é ativado até que você atualize a janela do navegador.
- Para a liberação do {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental), algumas terminologias da documentação não correspondem à nova interface. A documentação corresponde à interface no {{site.data.keyword.IBM_notm}} Marketplace. Os termos a seguir foram mudados na liberação [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental):

| Termo no {{site.data.keyword.IBM_notm}} Marketplace | Termo no {{site.data.keyword.Bluemix_notm}} | Notas |
|----------|----------|----------|
| _projeto_ | _área de trabalho_ | Esse termo mudou porque o {{site.data.keyword.Bluemix_notm}} também usa o termo _projeto_ |
| _importação_ e _exportação_ | _upload_ e _download_ | Os termos _importação_ e _exportação_ agora são referidos como _upload_ e _download_ quando usados em termos de documentos e tipos de entidade. O termo _exportação_ ainda é usado ao se referir a exportar um modelo para aplicativos como {{site.data.keyword.watson}} Explorer. |
{: caption="Tabela 1. Mudanças de terminologia para a versão do {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

- Para a liberação do {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental), algumas das etapas da tarefa documentação não correspondem à nova interface. A documentação corresponde à interface no {{site.data.keyword.IBM_notm}} Marketplace. A tabela a seguir resume as mudanças de navegação para a liberação [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental):

| Recurso | Local do {{site.data.keyword.IBM_notm}} Marketplace | Local do {{site.data.keyword.Bluemix_notm}}
|----------|----------|----------|
|Guia Componente do anotador | Navegação principal | Não existe mais |
|Tabela Matriz de confusão (da guia Estatísticas) | Componente do anotador > Detalhes | Link de Gerenciamento de modelo > Desempenho > Estatísticas detalhadas |
|Guia Dicionários | Navegação principal | Recursos e ferramentas > Pré-anotadores |
|Página Mapeamento de dicionário | Componente do anotador | Recursos e ferramentas > Pré-anotadores |
|Guia Tipos de entidade | Sistema de tipos | Ativos e ferramentas > Tipos de entidade |
|Editor de verdade absoluta | Anotação humana | Guia Anotação de documento |
|Guia Configurações do editor de verdade absoluta | Anotação humana | Configurações > Configurações de anotação de documento |
|Modelos, em execução e exportação | Componente do anotador | Gerenciamento de modelo > Versões |
|Guia Regras | Navegação principal | Anotação de documento > Regras |
|Guia Estatísticas | Componente do anotador > Detalhes | Gerenciamento de modelo > Desempenho |
|Tabela Resumo (da guia Estatísticas) | Componente do anotador > Detalhes | Link de Gerenciamento de modelo > Desempenho > Estatísticas detalhadas |
|Guia Mapeamento de tipo (para o modelo baseado em regra) | Componente do anotador > Detalhes | Gerenciamento de modelo > Versões > Mapeamento de tipo de modelo baseado em regra |
{: caption="Tabela 2. Mudanças de navegação muda para a versão do {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

## Julho de 2017
{: #july2017}

- Corrigido um defeito que, em alguns casos, fazia o cabeçalho desaparecer
- Aplicadas atualizações de segurança para componentes de infraestrutura

## Junho de 2017
{: #june2017}

- Melhorada a estabilidade para manipular dados grandes sob determinadas condições
- Corrigido um defeito para um erro de adjudicação

## Maio de 2017
{: #may2017}

- Incluída a capacidade para renomear vários objetos, como projetos, conjuntos de documentos e assim por diante
- Incluída a capacidade para implementar modelos NLU em regiões específicas do {{site.data.keyword.Bluemix}}
- Melhorado o desempenho para exibir tabela grande para IAA
- Corrigidos defeitos menores
- Aplicadas correções de segurança

## Abril de 2017
{: #april2017}

- Melhorada a estabilidade para o {{site.data.keyword.knowledgestudioshort}} Premium
- Incluída análise de uso para métricas de negócios

## Liberações antes de abril de 2017

Veja a nota técnica #1986001 do [{{site.data.keyword.IBM_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}.
