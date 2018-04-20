---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-14"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrando para o IBM Cloud
{: #migrate}

Em 18 de dezembro de 2017, a IBM lançou o {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud_notm}}, que marca o início do processo para migrar todas as instâncias do {{site.data.keyword.knowledgestudioshort}} do {{site.data.keyword.IBM_notm}} Marketplace para o {{site.data.keyword.cloud_notm}}.
{: shortdesc}

**Nota**: o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}} usa o termo _área de trabalho_, enquanto o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace usa o termo _projeto_. A funcionalidade é a mesma. Somente a terminologia é diferente.

## Processo e planejamento
{: #process}

O processo e planejamento de migração dos seus projetos do {{site.data.keyword.knowledgestudioshort}} dependem do seu [plano de precificação atual no {{site.data.keyword.IBM_notm}} Marketplace ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} e do tipo de conta, conforme mostrado na tabela a seguir:

| Plano e conta | Processo de migração | Planejamento de migração |
|------|-------------------|--------------------|
| Plano grátis | O cliente migra a instância e os dados | As migrações devem ser concluídas em ou antes de 1 de fevereiro de 2018. Em 2 de fevereiro de 2018, todos os planos Grátis no {{site.data.keyword.IBM_notm}} Marketplace serão limpos, incluindo dados do projeto associado. |
| Plano padrão com conta pré-paga | O cliente migra a instância e os dados | Migrações devem ser concluídas até 29 de junho de 2018. Em 30 de junho de 2018, todos os planos Padrão com contas pré-pagas no {{site.data.keyword.IBM_notm}} Marketplace serão limpos, incluindo dados do projeto associado.
| Plano padrão no contrato | O cliente migra a instância e os dados. A {{site.data.keyword.IBM_notm}} renova o contrato. | Migrações devem ser concluídas até 29 de junho de 2018. Entre em contato com o seu representante de conta {{site.data.keyword.IBM_notm}} designado ou entre em contato com [Vendas do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Plano premium no contrato | A {{site.data.keyword.IBM_notm}} migra a instância e os dados. A {{site.data.keyword.IBM_notm}} renova o contrato. | Migrações devem ser concluídas até 29 de junho de 2018. Entre em contato com o seu representante de conta {{site.data.keyword.IBM_notm}} designado ou entre em contato com [Vendas do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabela 1. Processo e planejamento para migrar o {{site.data.keyword.knowledgestudioshort}} do {{site.data.keyword.IBM_notm}} Marketplace para {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migração de planos Grátis
{: migratefree}

Se você tiver um plano Grátis do {{site.data.keyword.knowledgestudioshort}}, conclua as etapas a seguir para migrar sua instância e projetos do {{site.data.keyword.IBM_notm}} Marketplace para o {{site.data.keyword.cloud_notm}}:

1. Se você não tiver uma conta do {{site.data.keyword.cloud_notm}}, inscreva-se no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/wks_cloud){: new_window} usando seu {{site.data.keyword.ibmid}} do {{site.data.keyword.IBM_notm}} Marketplace.

   O seu {{site.data.keyword.ibmid}} é o ID que você usa para efetuar login no {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace.

1. Efetue login no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Se você não tiver uma instância do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}}, crie uma na [página do {{site.data.keyword.knowledgestudioshort}} do catálogo do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Siga o processo de [backup e restauração](/docs/services/watson-knowledge-studio/backup-restore.html) para migrar manualmente os seus projetos da instância do {{site.data.keyword.IBM_notm}} Marketplace para a sua instância no {{site.data.keyword.cloud_notm}}.

  **Nota**: se você tiver um modelo que já esteja implementado e planejar excluir a área de trabalho após fazer o backup dela, retire o modelo da implementação. É possível reconstruir e reimplementar o modelo após você restaurar a área de trabalho por meio do backup. Para obter informações sobre como remover a implementação de modelos, veja [Removendo a implementação de modelos de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Removendo a implementação de modelos baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migração de planos Padrão para contas pré-pagas
{: migratepaygo}

Se você tiver um plano Padrão e uma conta [pré-paga ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/pricing/billable.html){: new_window}, conclua as etapas a seguir para migrar sua instância e projetos do {{site.data.keyword.IBM_notm}} Marketplace para o {{site.data.keyword.cloud_notm}}:

1. Se você não tiver uma conta do {{site.data.keyword.cloud_notm}}, inscreva-se no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/){: new_window} usando seu {{site.data.keyword.ibmid}} do {{site.data.keyword.IBM_notm}} Marketplace.

   O seu {{site.data.keyword.ibmid}} é o ID que você usa para efetuar login no {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace.

1. Efetue login no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Se você não tiver uma instância do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}}, crie uma na [página do {{site.data.keyword.knowledgestudioshort}} do catálogo do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Siga o processo de [backup e restauração](/docs/services/watson-knowledge-studio/backup-restore.html) para migrar manualmente os seus projetos da instância do {{site.data.keyword.IBM_notm}} Marketplace para a sua instância no {{site.data.keyword.cloud_notm}}.

  **Nota**: se você tiver um modelo que já esteja implementado e planejar excluir a área de trabalho após fazer o backup dela, retire o modelo da implementação. É possível reconstruir e reimplementar o modelo após você restaurar a área de trabalho por meio do backup. Para obter informações sobre como remover a implementação de modelos, veja [Removendo a implementação de modelos de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Removendo a implementação de modelos baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migração de planos Padrão para contas de contrato
{: migratecontract}

Se você tiver um plano Padrão do {{site.data.keyword.knowledgestudioshort}} no contrato, conclua as etapas a seguir para renovar seu contrato e migrar sua instância e projetos do {{site.data.keyword.IBM_notm}} Marketplace para o {{site.data.keyword.cloud_notm}}:

1. Para renovar seu contrato, entre em contato com seu representante de conta designado pela {{site.data.keyword.IBM_notm}} ou entre em contato com [{{site.data.keyword.cloud_notm}} Sales ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration).
1. Depois de renovar seu contrato no {{site.data.keyword.cloud_notm}}, efetue login no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Se você não tiver uma instância do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}}, crie uma na [página do {{site.data.keyword.knowledgestudioshort}} do catálogo do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Siga o processo de [backup e restauração](/docs/services/watson-knowledge-studio/backup-restore.html) para migrar manualmente os seus projetos da instância do {{site.data.keyword.IBM_notm}} Marketplace para a sua instância no {{site.data.keyword.cloud_notm}}.

  **Nota**: se você tiver um modelo que já esteja implementado e planejar excluir a área de trabalho após fazer o backup dela, retire o modelo da implementação. É possível reconstruir e reimplementar o modelo após você restaurar a área de trabalho por meio do backup. Para obter informações sobre como remover a implementação de modelos, veja [Removendo a implementação de modelos de aprendizado de máquina](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Removendo a implementação de modelos baseados em regra](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migração de planos Premium para contas de contrato
{: migratecontract}

Se você tiver um plano Premium do {{site.data.keyword.knowledgestudioshort}} no contrato, entre em contato com seu representante de conta designado pela {{site.data.keyword.IBM_notm}} ou entre em contato com [{{site.data.keyword.cloud_notm}} Sales ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Quando o contrato for renovado no {{site.data.keyword.cloud_notm}}, seus dados serão migrados pela IBM em um planejamento que é negociado entre você e o {{site.data.keyword.cloud_notm}}.
