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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}。
{: tip}

# IBM Cloud へのマイグレーション
{: #migrate}

IBM は、2017 年 12 月 18 日に {{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.knowledgestudiofull}} を発表し、すべての {{site.data.keyword.knowledgestudioshort}} インスタンスを {{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へマイグレーションするプロセスが開始されることになりました。
{: shortdesc}

**注:** {{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.knowledgestudioshort}} では_ワークスペース_ という用語が使われていますが、{{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} では_プロジェクト_ という用語が使われています。機能は同じです。用語が違うだけです。

## プロセスおよびスケジュール
{: #process}

{{site.data.keyword.knowledgestudioshort}} プロジェクトのマイグレーション・プロセスおよびスケジュールは、以下の表に示すように、現在の [{{site.data.keyword.IBM_notm}} マーケットプレイスの料金プラン ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} およびアカウント・タイプによって異なります。

| プランおよびアカウント| マイグレーション・プロセス| マイグレーションのスケジュール|
|------|-------------------|--------------------|
| 無料プラン| お客様がインスタンスおよびデータをマイグレーションします。| 2018 年 2 月 1 日以前にマイグレーションを完了する必要があります。2018 年 2 月 2 日に、{{site.data.keyword.IBM_notm}} マーケットプレイス上の無料プランは、関連するプロジェクト・データも含めてすべて消去されます。|
| 従量課金アカウントの標準プラン | お客様がインスタンスおよびデータをマイグレーションします。| 2018 年 6 月 29 日以前にマイグレーションを完了する必要があります。2018 年 6 月 30 日に、{{site.data.keyword.IBM_notm}} マーケットプレイス上の従量課金アカウント標準プランは、関連するプロジェクト・データも含めてすべて消去されます。
| 標準プラン契約 | お客様がインスタンスおよびデータをマイグレーションします。 {{site.data.keyword.IBM_notm}} は契約を更新します。| 2018 年 6 月 29 日以前にマイグレーションを完了する必要があります。{{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。|
| プレミアム・プラン契約 | {{site.data.keyword.IBM_notm}} がインスタンスおよびデータをマイグレーションします。{{site.data.keyword.IBM_notm}} は契約を更新します。| 2018 年 6 月 29 日以前にマイグレーションを完了する必要があります。{{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。|
{: caption="表 1. {{site.data.keyword.knowledgestudioshort}} を {{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へマイグレーションするプロセスおよびスケジュール" caption-side="top"}

## 無料プランのマイグレーション
{: migratefree}

{{site.data.keyword.knowledgestudioshort}} 無料プランをご使用の場合、以下のステップを実行して、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へインスタンスおよびプロジェクトをマイグレーションします。

1. {{site.data.keyword.cloud_notm}} アカウントをお持ちでない場合は、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.ibmid}} を使用して [{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/wks_cloud){: new_window} に登録します。

   {{site.data.keyword.ibmid}} は、{{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} へのログインに使用する ID です。

1. [{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps/){: new_window} にログインします。
1. {{site.data.keyword.cloud_notm}} 上に {{site.data.keyword.knowledgestudioshort}} インスタンスがない場合は、[{{site.data.keyword.cloud_notm}} カタログ {{site.data.keyword.knowledgestudioshort}} ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} で作成します。
1. 『[バックアップおよびリストア](/docs/services/watson-knowledge-studio/backup-restore.html)』のプロセスに従って、{{site.data.keyword.IBM_notm}} マーケットプレイス・インスタンスから {{site.data.keyword.cloud_notm}} 上のインスタンスにプロジェクトを手動でマイグレーションします。

  **注:** 既にデプロイ済みのモデルがあり、バックアップしてからワークスペースを削除する予定の場合、そのモデルをアンデプロイしてください。ワークスペースをバックアップからリストアした後に、そのモデルを再作成し、再デプロイすることができます。モデルのアンデプロイについて詳しくは、『[機械学習モデルのアンデプロイ](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)』および『[ルール・ベース・モデルのアンデプロイ](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)』を参照してください。

## 従量課金アカウントの標準プランのマイグレーション
{: migratepaygo}

標準プランと [従量課金 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/pricing/billable.html){: new_window} アカウントをご使用の場合、以下のステップを実行して、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へインスタンスおよびプロジェクトをマイグレーションします。

1. {{site.data.keyword.cloud_notm}} アカウントをお持ちでない場合は、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.ibmid}} を使用して [{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/){: new_window} に登録します。

   {{site.data.keyword.ibmid}} は、{{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} へのログインに使用する ID です。

1. [{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps/){: new_window} にログインします。
1. {{site.data.keyword.cloud_notm}} 上に {{site.data.keyword.knowledgestudioshort}} インスタンスがない場合は、[{{site.data.keyword.cloud_notm}} カタログ {{site.data.keyword.knowledgestudioshort}} ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} で作成します。
1. 『[バックアップおよびリストア](/docs/services/watson-knowledge-studio/backup-restore.html)』のプロセスに従って、{{site.data.keyword.IBM_notm}} マーケットプレイス・インスタンスから {{site.data.keyword.cloud_notm}} 上のインスタンスにプロジェクトを手動でマイグレーションします。

  **注:** 既にデプロイ済みのモデルがあり、バックアップしてからワークスペースを削除する予定の場合、そのモデルをアンデプロイしてください。ワークスペースをバックアップからリストアした後に、そのモデルを再作成し、再デプロイすることができます。モデルのアンデプロイについて詳しくは、『[機械学習モデルのアンデプロイ](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)』および『[ルール・ベース・モデルのアンデプロイ](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)』を参照してください。

## 契約アカウントの標準プランのマイグレーション
{: migratecontract}

{{site.data.keyword.knowledgestudioshort}} 標準プランを契約している場合、以下のステップを実行して、契約を更新し、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へインスタンスおよびプロジェクトをマイグレーションします。

1. 契約を更新するには、{{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。
1. {{site.data.keyword.cloud_notm}} 上で契約を更新した後、[{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps/){: new_window} にログインします。
1. {{site.data.keyword.cloud_notm}} 上に {{site.data.keyword.knowledgestudioshort}} インスタンスがない場合は、[{{site.data.keyword.cloud_notm}} カタログ {{site.data.keyword.knowledgestudioshort}} ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} で作成します。
1. 『[バックアップおよびリストア](/docs/services/watson-knowledge-studio/backup-restore.html)』のプロセスに従って、{{site.data.keyword.IBM_notm}} マーケットプレイス・インスタンスから {{site.data.keyword.cloud_notm}} 上のインスタンスにプロジェクトを手動でマイグレーションします。

  **注:** 既にデプロイ済みのモデルがあり、バックアップしてからワークスペースを削除する予定の場合、そのモデルをアンデプロイしてください。ワークスペースをバックアップからリストアした後に、そのモデルを再作成し、再デプロイすることができます。モデルのアンデプロイについて詳しくは、『[機械学習モデルのアンデプロイ](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)』および『[ルール・ベース・モデルのアンデプロイ](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)』を参照してください。

## 契約アカウントのプレミアム・プランのマイグレーション
{: migratecontract}

{{site.data.keyword.knowledgestudioshort}} プレミアム・プランを契約している場合、{{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。{{site.data.keyword.cloud_notm}} 上で契約が更新されたら、お客様のデータは IBM によって、お客様と {{site.data.keyword.cloud_notm}} で折衝したスケジュールに従ってマイグレーションされます。
