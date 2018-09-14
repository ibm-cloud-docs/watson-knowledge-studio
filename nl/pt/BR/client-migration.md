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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrando para o IBM Cloud
{: #migrate}

Em 18 de dezembro de 2017, a IBM ativou o {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud_notm}}, que marca o início do processo para migrar todas as instâncias do {{site.data.keyword.knowledgestudioshort}} do {{site.data.keyword.IBM_notm}} Marketplace para a [plataforma {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}.
{: shortdesc}

**Nota**: o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}} usa o termo _área de trabalho_, enquanto o {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace usa o termo _projeto_. A funcionalidade é a mesma. Somente a terminologia é diferente.

**Atenção**: caso seja necessário obedecer ao GDPR, deve-se migrar para a plataforma {{site.data.keyword.cloud_notm}}. O {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace tornou-se obsoleto e não é adequado para clientes que requerem conformidade com o Regulamento Geral sobre a Proteção de Dados (GDPR) da União Europeia (UE) 2016/679.

## Processo
{: #process}

O processo de migração para os seus projetos do {{site.data.keyword.knowledgestudioshort}} depende de sua assinatura do {{site.data.keyword.IBM_notm}} Marketplace, conforme mostrado na tabela a seguir.

| Inscrição | Processo de migração | Detalhes |
|------|-------------------|--------------------|
| Plano padrão com uma assinatura de autoatendimento | O cliente migra a instância e os dados | Migre o mais rápido possível para obter acesso à versão mais atualizada do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.cloud_notm}}.
| Plano padrão com um contrato de assinatura | A {{site.data.keyword.IBM_notm}} migra o contrato de assinatura. O cliente migra a instância e os dados. | Entre em contato com o seu representante de conta {{site.data.keyword.IBM_notm}} designado ou entre em contato com [Vendas do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Plano Premium com contrato de assinatura | A {{site.data.keyword.IBM_notm}} migra o contrato de assinatura. {{site.data.keyword.IBM_notm}}  migra a instância e os dados. | Entre em contato com o seu representante de conta {{site.data.keyword.IBM_notm}} designado ou entre em contato com [Vendas do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabela 1. Processo e planejamento para migrar o {{site.data.keyword.knowledgestudioshort}} do {{site.data.keyword.IBM_notm}} Marketplace para {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Auto-migração de instâncias de plano padrão
{: migratestandard}

Se você tiver um plano Padrão, conclua as etapas a seguir para migrar sua instância do {{site.data.keyword.IBM_notm}} Marketplace para o {{site.data.keyword.cloud_notm}}:

1. Se você não tiver uma conta do {{site.data.keyword.cloud_notm}}, inscreva-se no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/registration/){: new_window} usando seu {{site.data.keyword.ibmid}} do {{site.data.keyword.IBM_notm}} Marketplace.

   O seu {{site.data.keyword.ibmid}} é o ID que você usa para efetuar login no {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace.

2. Efetue login no [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net){: new_window}.
3. Se a sua conta do {{site.data.keyword.cloud_notm}} for uma conta Lite, faça upgrade para uma conta paga. Para obter mais informações sobre os tipos de contas pagas, veja [Tipos de conta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/account/index.html){: new_window}.
4. No [console do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}, crie um plano Padrão do {{site.data.keyword.knowledgestudioshort}}.
5. Siga as instruções na tela, indicando que você deseja migrar uma instância do {{site.data.keyword.IBM_notm}} Marketplace para o {{site.data.keyword.cloud_notm}}.
6. Se você tiver mais de uma instância para migrar, repita o processo.

## Migração de Instâncias de Plano Premium
{: migratesubscription}

Se você tiver um plano Premium do {{site.data.keyword.knowledgestudioshort}}, entre em contato com o representante de conta designado pela {{site.data.keyword.IBM_notm}} ou entre em contato com o [{{site.data.keyword.cloud_notm}} Sales ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Depois que a assinatura for migrada para o {{site.data.keyword.cloud_notm}}, seus dados serão migrados pela IBM em um planejamento que é negociado entre você e a {{site.data.keyword.IBM_notm}}.
