---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-20"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/backup-restore.html){: new_window}.
{: tip}

# Backup e ripristino dei dati
{: #backup-restore}

Se hai bisogno di eseguire il backup o di ripristinare uno spazio di lavoro di {{site.data.keyword.knowledgestudioshort}}, esegui queste attività. Inoltre, se devi eseguire una migrazione manuale dei dati da un'istanza {{site.data.keyword.knowledgestudioshort}} a un altra, come quando migri da un'istanza sul {{site.data.keyword.IBM_notm}} Marketplace a una in {{site.data.keyword.cloud_notm}}, esegui queste attività.
{: shortdesc}

La _Migrazione dei dati manuale_ è il processo di backup dei tuoi dati da un'istanza e del ripristino di essi su un'altra.

**Nota**: {{site.data.keyword.knowledgestudioshort}} su {{site.data.keyword.cloud_notm}} utilizza il termine _spazio di lavoro_, mentre {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace utilizza _progetto_. La funzionalità è la stessa. È diversa soltanto la terminologia.

Per eseguire il backup e ripristinare i dati completa la seguente procedura:

1. [Comprendi di quali dati è possibile eseguire il backup](#data)
1. [Prepara il backup](#prepare)
1. [Scarica le risorse dall'istanza corrente](#export)
1. [Ricrea gli spazi di lavoro nella nuova istanza](#recreateproj)
1. [Ripristina i dati dello spazio di lavoro](#restoredata)
1. [Ripristina i modelli](#restoremodels)
1. [Ripristina tutte le attività di annotazione incomplete](#restoretasks)

## È possibile eseguire il backup dei dati
{: #data}

Le seguenti risorse possono essere sottoposte a backup e migrate manualmente:

- Dizionari modificabili.
- Sistema tipo
- Serie di documenti ground truth approvati

I seguenti tipi di risorse non possono essere sottoposti a backup e migrati manualmente:

- Documenti di annotazione umana in corso
- Attività di annotazione
- Modelli e istantanee
- Dizionari in sola lettura

## Preparazione del backup
{: #prepare}

Per preparare il backup e il ripristino dei tuoi dati, completa la seguente procedura:

1. Completa tutti i lavori in corso nel tuo spazio di lavoro.

    - > **Importante:** termina qualsiasi attività di annotazione in corso. È possibile eseguire il backup solo dei documenti che sono stati annotati, giudicati, approvati e promossi a ground truth. Se non termini il lavoro di annotazione, perderai tutte le attività di annotazione che sono in corso ma non ancora completate.

    - Se hai creato delle attività di annotazione per tracciare il lavoro che vuoi fare, ma nessuna di queste è iniziata e non avrà luogo fino a dopo che lo spazio di lavoro è stato ripristinato, fai un elenco di attività di annotazione in sospeso. Assicurati di prendere nota delle serie di documenti che hai importato, ma che non sono ancora stati aggiunti a ground truth. Inoltre, prendi nota di chi hai assegnato per l'annotazione di ogni documento. Dovrai ricaricare queste serie di documenti e ricreare le attività di annotazione dopo il ripristino dello spazio di lavoro.

1. Comprensione dell'utilizzo del tokenizer.

    Per i modelli di machine learning, gli spazi di lavoro utilizzano il tokenizer basato sul machine learning per impostazione predefinita. Se stai utilizzando un tokenizer basato sul dizionario e hai un bisogno specifico di continuare in questo modo, puoi configurare lo spazio di lavoro per utilizzare il tokenizer basato sul dizionario quando lo ripristini. Per ulteriori informazioni, vedi [Tokenizer](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Gestisci le risorse del modello.

    Il tuo modello, i dati delle istantanee e le sue versioni, non possono essere migrati. Le risorse (tranne i dizionari di sola lettura) che hai utilizzato per preparare queste risorse possono essere migrate. Pertanto, dopo la migrazione, puoi ricreare il modello. Il modello che sarà prodotto sarà eseguito nello stesso modo dei modelli che hai generato prima della migrazione perché le risorse che sono state utilizzate per la preparazione saranno le stesse.

    **ATTENZIONE**: se hai un modello che è già stato distribuito e pensi di eliminare lo spazio di lavoro dopo il backup, ritira il modello dalla distribuzione. Puoi ricreare e ridistribuire il modello dopo il ripristino dello spazio di lavoro dal backup. Per informazioni sui modelli di distribuzione, consulta [Annullamento della distribuzione dei modelli di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Annullamento della distribuzione dei modelli basati sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

    **Tieni presente che se non riesci a ritirare il modello dalla distribuzione, il risultato è un modello di distribuzione _orfano_. I modelli di distribuzione orfani continueranno a generare addebiti nelle tue fatture mensili.**

1. Gestisci le informazioni del dizionario in sola lettura

    I dizionari in sola lettura non possono essere migrati. Trova da dove è stato importato il dizionario in sola lettura, in modo da poterlo ricaricare nel tuo spazio di lavoro dopo la migrazione.

1. Fai un elenco dei ruoli utente correnti.

    **NOTA**: questo passo è facoltativo. Viene normalmente eseguito quando uno spazio di lavoro viene migrato tra le istanze e il nuovo spazio di lavoro deve essere identico all'originale. Se vuoi migrare solo i dati dello spazio di lavoro in un nuovo spazio, puoi saltare questo passo.

    Se stai migrando gli spazi di lavoro tra istanze differenti, considera di fare un elenco degli utenti e dei rispettivi ruoli dell'istanza di cui stati eseguendo il backup. Qualcuno con il ruolo di amministratore può stampare l'elenco dalla pagina User Account Management. Dopo che sono stati ricreati gli spazi di lavoro nella nuova istanza, qualcuno con il ruolo di amministratore deve aggiungere gli utenti e assegnarne i ruoli.

    Per ulteriori informazioni sui ruoli, consulta [Ruoli utente in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Prendi nota delle informazioni dello spazio di lavoro.

    Mentre hai ancora accesso all'istanza corrente, per ogni spazio di lavoro che vuoi migrare, prendi nota delle seguenti informazioni:
    - Nome dello spazio di lavoro
    - Descrizione dello spazio di lavoro
    - Proprietario dello spazio di lavoro
    - Lingua
    - Se hai attività di annotazione incomplete, poiché non è possibile eseguirne il backup o migrarle, prendi nota degli annotatori umani che sono assegnati alle attività incomplete nello spazio di lavoro. Prendi anche nota dei dettagli dell'attività, come il nome, la data di scadenza e quali serie di documenti sono assegnate a quali utenti.

## Scaricamento delle risorse
{: #export}

Per ogni spazio di lavoro che vuoi migrare, scarica le seguenti risorse. Archiviale in un'ubicazione sicura da cui potrai caricarle nella nuova istanza in un secondo momento.

- Sistema tipo
- Dizionari

  **Nota**:
    - Saranno scaricati solo i dizionari modificabili. Non puoi scaricare i dizionari in sola lettura.
    - Per i dizionari, le associazioni dei tipi di entità non vengono migrate. Dopo che hai ripristinato queste risorse, dovrai associare i dizionari ai tipi di entità, se necessario.

- Documenti

  Consulta [Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html) per le informazioni su come scaricare queste risorse in modo che possano essere importate in un nuovo spazio di lavoro.

## Ricreazione degli spazi di lavoro
{: #recreateproj}

**NOTA**: in questo passo, l'unica impostazione che deve corrispondere a quella dello spazio di lavoro originale (scaricato) è la lingua. Il resto delle impostazioni possono essere diverse rispetto alle originali.

Ricrea ogni spazio di lavoro copiando le seguenti informazioni dall'istanza precedente a quella nuova:

- Nome dello spazio di lavoro
- Descrizione dello spazio di lavoro
- Lingua dei documenti (questa impostazione deve corrispondere all'impostazione nello spazio di lavoro originale)
- Se hai precedentemente utilizzato un tokenizer basato sul dizionario nello spazio di lavoro e hai un motivo valido per continuare ad utilizzarlo, devi specificare che vuoi utilizzare il tokenizer basato sul dizionario invece del predefinito nel momento in cui crei lo spazio di lavoro. Per ulteriori informazioni sulle opzioni, vedi [Tokenizer](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

  Per utilizzare un tokenizer basato sul dizionario, espandi la sezione Advanced Options della finestra Create Workspace (nel {{site.data.keyword.IBM_notm}} Marketplace, la finestra Create Workspace) e modifica le impostazioni del tokenizer.

## Ripristino dei dati dello spazio di lavoro
{: #restoredata}

Dopo aver ricreato gli spazi di lavoro, carica le risorse scaricate precedentemente:

1. Carica il sistema tipo dal backup creato precedentemente.
   Per i dettagli, vedi [Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html).

  **Nota**: devi caricare il sistema tipo prima di poter caricare le altre risorse che stai spostando dallo spazio di lavoro di backup.

1. Carica i dizionari dal backup del dizionario creato precedentemente.
   Per i dettagli, vedi [Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html).

  Se hai utilizzato i dizionari in sola lettura nella versione precedente dello spazio di lavoro, ricaricali in questo spazio di lavoro dalla loro sorgente originale.

1. Per i pre-annotatori del dizionario, associa i dizionari a un tipo di entità. I dizionari che non hanno associazioni ai tipi di entità non applicheranno le annotazioni quando pre-annoti i documenti.

1. Carica i documenti che hai scaricato dalla versione precedente dello spazio di lavoro in questa versione.
   Per i dettagli, vedi [Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html).

## Ripristino dei modelli
{: #restoremodels}

A questo punto, tutte le risorse che sono state utilizzate per preparare il modello nella versione (di backup) precedente dello spazio di lavoro, sono ora disponibili in questa nuova istanza.

Per ridistribuire un modello di machine learning che hai distribuito nell'istanza precedente, completa la seguente procedura:

1. [Prepara il modello di machine learning](/docs/services/watson-knowledge-studio/train-ml.html).

  **Nota**: non eseguire i pre-annotatori sui documenti annotati che hai migrato a questo spazio di lavoro perché perderanno le annotazioni che sono state aggiunte dagli annotatori umani.

1. Dopo aver creato il modello, ridistribuiscilo. Per i dettagli, vedi [Utilizzo di un modello di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html).

Per ridistribuire un modello basato sulla regola che hai distribuito nell'istanza precedente, completa la seguente procedura:

1. [Crea il modello basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html).
1. [Distribuisci il modello basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html).

## Ripristino delle attività di annotazione incomplete
{: #restoretasks}

Se hai delle attività di annotazione che hai creato ma non completato nello spazio di lavoro precedente, completa la seguente procedura per ricrearle.

1. [Carica tutti i documenti](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd) che non sono ancora stati annotati ma che vuoi aggiungere a ground truth per continuare a migliorare il modello.
1. Dai documenti appena importati e non annotati, [crea le serie di annotazioni](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).
1. [Ricrea le attività di annotazione](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask). Fornisci all'attività lo stesso nome, una data di scadenza appropriata e assegna le serie di annotazioni agli annotatori umani appropriati.
