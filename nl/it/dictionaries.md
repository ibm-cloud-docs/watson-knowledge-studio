---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/dictionaries.html){: new_window}.
{: tip}

# Creazione dei dizionari
{: #dictionaries}

I dizionari aiutano i modelli di machine learning {{site.data.keyword.knowledgestudioshort}} a comprendere la lingua del dominio.
{: shortdesc}

## Dizionari
{: #wks_dictionaries}

Nel machine learning, un dizionario raggruppa tra loro le parole e le frasi condivise in comune da qualcuno. Una voce nel dizionario non significa che tutte le parole nella voce significano la stessa cosa, ma che le parole devono essere trattate in modo equivalente da un modello.

Un dizionario è un elenco di parole o frasi che sono equivalenti per scopi di estrazione delle informazioni, il che significa che sono interscambiabili per gli scopi di identificazione delle citazioni di entità e relazione.

Considera questo esempio: una voce del dizionario contiene i sette giorni della settimana. Per annotare un documento, un annotatore umano assegna il tipo di entità `DAY_OF_WEEK` per le citazioni *Monday* e *Friday* nel testo. Poiché il dizionario mette sullo stesso livello i sette giorni della settimana, aiuta a garantire che un modello di machine learning annoti in modo corretto le ricorrenze di *Tuesday*, *Wednesday* e degli altri giorni della settimana nei documenti non visti al runtime. In aggiunta, mettendo allo stesso livello queste parole si hanno vantaggi nell'estrazione delle informazioni nel testo circostante. Quello che il modello di machine learning impara per la preparazione degli esempi sui testi vicino a *Monday* e *Friday* viene applicato ai testi che il modello di machine learning vede accanto agli altri giorni della settimana perché il dizionario afferma che questi giorni sono equivalenti per scopi di estrazione delle informazioni.

> **Nota:** non hai bisogno di creare un dizionario che contiene le informazioni sui giorni della settimana. Molti dizionari di scopo generale come questo sono integrati nell'applicazione. Altri dizionari integrati includono paesi, nomi di luoghi, numeri, animali, piante, malattie, misurazioni (come *ounce* e *meter*) titoli di saluto (come *Mr.* e *Mrs.*). Non puoi disabilitare o modificare i dizionari integrati.

Evita di aggiungere voci che hanno più significati. Ad esempio, in un dominio di auto da corsa, ha senso includere *bank*, che fa riferimento agli elementi della strada, solo se non vengono frequentemente anche discusse nel testo le istituzioni finanziare. Se entrambi i sensi della parola di verificano spesso nei documenti di origine, è meglio non inserire entrambi i tipi di dizionari: il dizionario associato agli elementi stradali e quello alle istituzioni finanziarie.

Puoi creare i dizionari in {{site.data.keyword.knowledgestudioshort}} aggiungendo manualmente voci individuali. {{site.data.keyword.knowledgestudioshort}} supporta anche la possibilità di caricare diversi tipi di file del dizionario.

### Come vengono utilizzati i dizionari?

I dizionari sono utilizzati in un paio di modi, tutti facoltativi. Sono utilizzati dal modello di machine learning per fornire le parole o le frasi equivalenti per scopi di estrazione delle informazioni e durante la pre-annotazione per avviare l'attività di annotazione.

- **Utilizzo del machine learning**

    Il tipo di entità associato a un dizionario non viene utilizzato per definire le regole del modello di machine learning. Il machine learning valuta le citazioni nei documenti indipendentemente. Non assume che una citazione abbia un tipo di entità specifico solo perché corrisponde a una voce nel dizionario associata a tale tipo di entità. Prende le informazioni nell'account ma le tratta come una parte delle informazioni insieme alle altre parti raccolte tramite l'analisi linguistica. Infatti, se nessuno dei termini in un dizionario è presente nei documenti ground truth, il dizionario non viene utilizzato dal modello di machine learning.

- **Utilizzo della pre-annotazione**

    I dizionari sono importanti per i seguenti processi di pre-annotazione.

    - Pre-annotatore del dizionario: associ un dizionario a un tipo di entità dal sistema tipo quando esegui il pre-annotatore del dizionario.
    - Modello basato sulla regola: puoi facoltativamente associare un dizionario a una classe di regole. Le classi sono poi associate ai tipi di entità dal sistema tipo quando esegui il modello basato sulla regola per pre-annotare i documenti. Di conseguenza, i termini del dizionario sono, anche se indirettamente, associati ai tipi di entità anche per il modello basato sulla regola.

    In entrambi i casi, i dizionari forniscono i termini che il sistema può trovare e annotare come citazioni. Assegna a ogni citazione il tipo di entità associato al dizionario che contiene il termine. Quando un annotatore umano inizia a lavorare sui nuovi documenti che sono stati pre-annotati, molte citazioni sono già annotate in base alle voci del dizionario. L'annotatore umano quindi ha più tempo per concentrarsi sull'assegnazione dei tipi di entità alle citazioni che richiedono un'analisi più approfondita.

### Considerazioni sulla lingua

- Per portoghese brasiliano, inglese, francese, tedesco, italiano e spagnolo, {{site.data.keyword.knowledgestudioshort}} non fornisce al momento un'opzione per specificare la corrispondenza del dizionario per casi non sensibili al maiuscolo/minuscolo, ma le voci del dizionario corrispondono al testo con più maiuscole. Ad esempio, *vehicle* nel dizionario corrisponde a *vehicle*, *Vehicle* o *VEHICLE* nel testo, mentre *Sat* nel dizionario corrisponde a *Sat* o *SAT* nel testo ma non a *sat*.
- Per giapponese e coreano, la corrispondenza del dizionario durante la pre-annotazione è sensibile al maiuscolo/minuscolo.
- Per l'arabo {{site.data.keyword.knowledgestudioshort}} presuppone che il testo in arabo sia archiviato senza forma e che tratti la forma numerica come una proprietà al livello di archiviazione. Per i dettagli su come {{site.data.keyword.knowledgestudioshort}} gestisce la forma dei caratteri e dei numeri arabi, consulta [Configurazione del supporto per l'arabo](/docs/services/watson-knowledge-studio/language-support-arabic.html).

### Dizionario file CSV
{: #wks_dictionaries__cvsdict}

Noto anche come il formato di dizionario standard, un dizionario nel formato del valore separato da virgole (`CSV`) è un file che puoi modificare dopo averlo caricato. La dimensione massima di un file `CSV` che puoi caricare è 1 MB. Se hai un file dizionario più grande, suddividilo in più parti e caricale una alla volta in un solo dizionario nel tuo spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

Per riepilogare i requisiti, devi utilizzare un editor di testo per creare il file `CSV`, non software come Microsoft Excel e il file deve utilizzare la codifica UTF-8 che non include il contrassegno di ordine di byte (BOM) all'inizio del flusso di testo. La prima riga nel file deve specificare le seguenti intestazioni di colonna:

```
lemma,poscode,surface
```
{: screen}

Le righe rimanenti nel file specificano le voci del dizionario, dove:

- **lemma**

    Specifica la parola più rappresentativa per la voce.

- **poscode** (arabo, portoghese brasiliano, inglese, francese, tedesco, italiano e spagnolo)

    Specifica un codice che identifica la parte del discorso. Queste informazioni sulla parte del discorso sono utilizzate dall'annotatore del dizionario per la suddivisione in token della frase.
    - `0` - Sconosciuto

        > **Nota:** questo codice supporta lo scenario in cui vuoi caricare un dizionario generato automaticamente molto grande che non include le informazioni sulla parte della frase in ogni voce. Puoi assegnare *unknown* a tutte le voci per impostazione predefinita. Evita di utilizzare questo codice, se possibile.

    - `1` - Pronome
    - `2` - Verbo
    - `3` - Nome
    - `4` - Aggettivo
    - `5` - Avverbio
    - `6` - Apposizione
    - `7` - Esclamazione
    - `8` - Congiunzione
    - `9` - Determinante
    - `10` - Qualificatore

    In inglese, nome (`3`), verbo (`2`) e aggettivo (`4`) sono le parti del discorso più comuni utilizzate per le voci del dizionario.

    > **Nota:** la parte del discorso non determina automaticamente il tipo di una citazione. Non assume che tutti i nomi equivalgono alle citazioni del tipo di entità e tutti i verbi alle citazioni del tipo di relazione. Ad esempio, *American* è un aggettivo ma potrebbe essere annotato come tipo di entità **GPE** (geopolitical entity) o `PERSON`. *Met* è un verbo, ma potrebbe essere annotato come un `EVENT_MEETING`.

    In altre lingue, come il tedesco, che utilizza parole composte, l'accuratezza delle informazioni sulla parte del discorso è ancora più importante per determinare i limiti della parola.

- **poscode** (cinese)

    Specifica un codice che identifica la parte del discorso. Il valore della parte del discorso è importante per la suddivisione in token e la pre-annotazione nelle lingue come il cinese (semplificato e tradizionale) che non utilizzano spazi vuoti per denotare i limiti della parola.
    - `32` - Nome
    - `31` - Nome (cognome)
    - `35` - Nome (organizzazione)
    - `34` - Nome (altro)
    - `33` - Nome (nome di persona)

- **poscode** (giapponese)

    Specifica un codice che identifica la parte del discorso. Il valore della parte del discorso è importante per la suddivisione in token e la pre-annotazione nelle lingue come il giapponese che non utilizzano spazi vuoti per denotare i limiti della parola.
    - `19` - Nome
    - `23` - Prefisso comune
    - `24` - Suffisso comune
    - `140` - Nome proprio (cognome)
    - `141` - Nome proprio (nome)
    - `146` - Nome proprio (nome di persona)
    - `142` - Nome proprio (organizzazione)
    - `144` - Nome proprio (nome di un luogo)
    - `143` - Nome proprio (regione)
    - `145` - Nome proprio (altro)

- **poscode** (coreano)

    Specifica un codice che identifica la parte del discorso. Il valore della parte del discorso è importante per la suddivisione in token e la pre-annotazione nelle lingue come il coreano che non utilizzano spazi vuoti per denotare i limiti della parola.
    - `10010` - Nome
    - `10300` - Nome proprio (cognome)
    - `10310` - Nome proprio (nome)
    - `110360` - Nome proprio (nome di persona)
    - `10320` - Nome proprio (organizzazione)
    - `10340` - Nome proprio (nome di un luogo)
    - `10330` - Nome proprio (regione)
    - `10350` - Nome proprio (altro)

- **surface**

    Specifica i termini equivalenti, denominati anche formati di superficie. Ripeti il lemma come un formato di superficie per separare più formati di superficie. Se un formato di superficie include una virgola, racchiudilo tra virgolette.

Ad esempio:

```
lemma,poscode,surface
IBM,3,IBM Corp.,IBM,"International Business Machines, Inc."
Department of Energy,3,DOE,Department of Energy
premium,4,premium,premium-grade
```
{: screen}

**Concetti correlati**:

[Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html)

**Attività correlate**:

[Pre-annotazione dei documenti con un dizionario](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

## Aggiunta di dizionari a uno spazio di lavoro
{: #wks_projdictionaries}

L'aggiunta di dizionari è un passo facoltativo nella creazione di un modello. I dizionari sono utili perché ti permettono di iniziare subito il processo di annotazione.

### Informazioni su quest'attività

Se fornisci un dizionario, puoi eseguire il pre-annotatore del dizionario nei documenti. Il pre-annotatore trova i termini presenti nel tuo dizionario e li annota automaticamente. Questo passo iniziale nei documenti semplifica il lavoro dell'annotatore umano perché può controllare le annotazioni che sono state aggiunte dal pre-annotatore e correggerle o aggiungerle. Non deve iniziare tutto da zero.

La seguente limitazione si applica ai dizionari:

- Massimo 15.000 voci per dizionario

    > **Nota:** questo limite non si applica ai dizionari che carichi come un file `CSV` del dizionario. I dizionari in sola lettura possono contenere più voci.

- Massimo 64 dizionari per spazio di lavoro

### Procedura

Per aggiungere un dizionario al tuo spazio di lavoro:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e apri la pagina **Assets** > **Dictionaries**.
1. Completa una delle seguenti attività:

    - Accanto al pulsante **Create Dictionary**, fai clic sull'icona **Menu** e seleziona **Upload Dictionary**. Seleziona un dizionario e fai poi clic su **Upload**. Dopo aver caricato un dizionario, selezionalo per visualizzarlo e associarlo a un tipo di entità.

    Puoi caricare un file ZIP che contiene un dizionario che hai scaricato da un altro spazio di lavoro {{site.data.keyword.knowledgestudioshort}}. Devi caricare il sistema tipo che è stato scaricato dall'altro spazio di lavoro nel formato JSON prima di poter caricare il file del dizionario corrispondente. Puoi modificare e aggiungere le voci di un dizionario che riutilizzi da un altro spazio di lavoro {{site.data.keyword.knowledgestudioshort}}. Consulta [Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html) per ulteriori dettagli.

    È supportato anche il caricamento di un file CSV, caricarlo direttamente come un dizionario crea un dizionario di sola anteprima che non puoi modificare o utilizzare per pre-annotare i documenti. Per caricare un file CSV che puoi modificare e utilizzare per la pre-annotazione, fai clic su **Create Dictionary** per creare prima un dizionario e poi caricare il contenuto CSV come voci nel dizionario appena creato.

    - Fai clic sul pulsante **Create Dictionary** per creare un dizionario vuoto in cui successivamente aggiungere le voci del dizionario. Specifica un nome descrittivo per il dizionario e poi fai clic su **Save**.

2. Per aggiungere le voci al dizionario, completa una delle seguenti attività:

    - Fai clic su **Add Entry** per aggiungere una voce del dizionario. Specifica il *lemma* (la parola più rappresentativa per termine).
    - Fai clic su **Upload** per caricare un file `CSV` che contiene le voci del dizionario e quindi sfoglia per selezionare il file. Il file `CSV` deve essere più piccolo di 1MB.

3. Dopo aver caricato o aggiunto le voci, puoi modificarle.

    Apri una voce per specificare termini equivalenti, denominati *formati di superficie*. Ogni formato di superficie deve avere una lunghezza di 256 caratteri o meno. Puoi modificare quale formato di superficie viene utilizzato come lemma. Ad esempio, il lemma *{{site.data.keyword.IBM_notm}}* potrebbe avere formati di superficie come *{{site.data.keyword.IBM_notm}} Corp.* e *International Business Machines, Inc.*.

4. Seleziona la pare del discorso appropriata di ogni lemma e formato di superficie nel dizionario.

    Le informazioni sulla parte del discorso sono utilizzate dal tokenizer e durante la pre-annotazione.

5. Fai clic su **Salva** per applicare le modifiche.

### Operazioni successive

Esegui il pre-annotatore, che utilizza i dizionari che hai creato per eseguire un passo preliminare dei documenti di origine e aggiunge le annotazioni ad essi.

**Attività correlate**:

[Pre-annotazione dei documenti con un dizionario](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

**Riferimento correlato**:

[Supporto per la lingua](/docs/services/watson-knowledge-studio/language-support.html)
