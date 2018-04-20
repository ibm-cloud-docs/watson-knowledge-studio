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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Notas sobre a liberação
{: #release-notes}

Os novos recursos e mudanças a seguir no {{site.data.keyword.knowledgestudiofull}} estão disponíveis.
{: shortdesc}

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
