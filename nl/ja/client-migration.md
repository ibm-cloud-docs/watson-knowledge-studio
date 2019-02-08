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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/services/knowledge-studio/client-migration.html){: new_window}。
{: tip}

# IBM Cloud へのマイグレーション
{: #migrate}

IBM は、2017 年 12 月 18 日に {{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.knowledgestudiofull}} を発表し、すべての {{site.data.keyword.knowledgestudioshort}} インスタンスを {{site.data.keyword.IBM_notm}} マーケットプレイスから [{{site.data.keyword.cloud_notm}} プラットフォーム ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window} へマイグレーションするプロセスが開始されることになりました。
{: shortdesc}

**注:** {{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.knowledgestudioshort}} では_ワークスペース_ という用語が使われていますが、{{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} では_プロジェクト_ という用語が使われています。 機能は同じです。 用語が違うだけです。

**重要**: GDPR に準拠する必要がある場合は、{{site.data.keyword.cloud_notm}} プラットフォームにマイグレーションする必要があります。{{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} は廃止されました。これは、欧州連合 (EU) の一般データ保護規則 (GDPR) (EU) 2016/679 に準拠する必要があるクライアントには適していません。

## プロセス
{: #process}

{{site.data.keyword.knowledgestudioshort}} プロジェクトのマイグレーション・プロセスは、以下の表に示すように、{{site.data.keyword.IBM_notm}} マーケットプレイスでのサブスクリプションによって異なります。

| サブスクリプション | マイグレーション・プロセス | 詳細 |
|------|-------------------|--------------------|
| セルフサービス・サブスクリプションを使用する標準プラン | お客様がインスタンスおよびデータをマイグレーションします。 | {{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.knowledgestudioshort}} の最新バージョンにアクセスできるようにできるだけ早くマイグレーションしてください。
| サブスクリプション契約を使用する標準プラン | {{site.data.keyword.IBM_notm}} はサブスクリプション契約をマイグレーションします。お客様がインスタンスおよびデータをマイグレーションします。 | {{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。 |
| サブスクリプション契約を使用するプレミアム・プラン | {{site.data.keyword.IBM_notm}} はサブスクリプション契約をマイグレーションします。{{site.data.keyword.IBM_notm}} がインスタンスおよびデータをマイグレーションします。 | {{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。 |
{: caption="表 1. {{site.data.keyword.knowledgestudioshort}} を {{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へマイグレーションするプロセスおよびスケジュール" caption-side="top"}

## 標準プラン・インスタンスの自己マイグレーション
{: migratestandard}

標準プランをご使用の場合、以下のステップを実行して、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} へインスタンスをマイグレーションします。

1. {{site.data.keyword.cloud_notm}} アカウントをお持ちでない場合は、{{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.ibmid}} を使用して [{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/registration/){: new_window} に登録します。

   {{site.data.keyword.ibmid}} は、{{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} へのログインに使用する ID です。

2. [{{site.data.keyword.cloud_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}){: new_window} にログインします。
3. ご使用の {{site.data.keyword.cloud_notm}} アカウントがライト・アカウントである場合、有料アカウントにアップグレードします。有料アカウントのタイプについて詳しくは、[アカウント・タイプ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/account/index.html){: new_window} を参照してください。
4. [{{site.data.keyword.cloud_notm}} コンソール ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/knowledge-studio){: new_window} から、{{site.data.keyword.knowledgestudioshort}} 標準プランを作成します。
5. 画面上の指示に従って、インスタンスを {{site.data.keyword.IBM_notm}} マーケットプレイスから {{site.data.keyword.cloud_notm}} にマイグレーションすることを指定します。
6. 複数のインスタンスをマイグレーションする場合は、処理を繰り返してください。

## プレミアム・プラン・インスタンスのマイグレーション
{: migratesubscription}

{{site.data.keyword.knowledgestudioshort}} プレミアム・プランをご使用の場合、{{site.data.keyword.IBM_notm}} から指定されたアカウント担当者に連絡するか、[{{site.data.keyword.cloud_notm}} 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration) にお問い合わせください。サブスクリプションが {{site.data.keyword.cloud_notm}} にマイグレーションされると、お客様のデータは IBM によって、お客様と {{site.data.keyword.IBM_notm}} で折衝したスケジュールに従ってマイグレーションされます。
