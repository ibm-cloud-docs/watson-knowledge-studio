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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/language-support.html){: new_window}.
{: tip}

# Supporto per la lingua
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} fornice il supporto per preparare un modello in diverse lingue.

Il supporto per più lingue non significa che il prodotto stesso sia tradotto. La documentazione, i messaggi e le interfacce utente di {{site.data.keyword.knowledgestudioshort}} sono disponibili solo in inglese.
{: shortdesc}

Puoi preparare un modello nelle seguenti lingue:

- Inglese (la lingua predefinita)
- Arabo
- Portoghese brasiliano
- Cinese (semplificato)
- Olandese
- Francese
- Tedesco
- Italiano
- Giapponese
- Coreano
- Spagnolo

Il supporto include la capacità di aggiungere i documenti in queste lingue a uno spazio di lavoro, aggiungere i dizionari, eseguire la pre-annotazione, utilizzare l'editor ground truth per annotare i documenti e preparare un modello di machine learning. Quando selezioni una lingua, il sistema applica i modelli specifici della lingua per gestire le voci del dizionario, la suddivisione in token del testo e la segmentazione della frase. Per le informazioni su come il sistema gestisce i dizionari in lingue differenti, consulta [Dizionari](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries).

> **Nota:** l'editor delle regole e il modello basato sulla regola non possono gestire il testo bidirezionale, per cui non possono essere utilizzati con i documenti in arabo.

> **Limitazioni:**
>
> A causa delle limitazioni nella tecnologia machine learning sottostante, le voci nel sistema tipo non possono contenere gli spazi e possono includere solo i seguenti caratteri ASCII:
>
> - Da A a Z e da a a z
> - Da 0 a 9
> - Il carattere di sottolineatura: _
>
> Vengono applicate anche le seguenti regole:
>
> - Il primo carattere nel nome deve essere alfabetico.
> - Il nome del tipo di entità non può superare i 64 caratteri.
> - La lunghezza del nome del tipo di relazione non può superare i 128 caratteri.
>
> Pertanto, ad esempio, quando un annotatore umano annota del testo in giapponese nell'editor ground truth, i nomi del tipo di entità e di relazione che possono venire applicati non saranno in giapponese.

### Attività correlate

[Configurazione del supporto per l'arabo](/docs/services/watson-knowledge-studio/language-support-arabic.html)
