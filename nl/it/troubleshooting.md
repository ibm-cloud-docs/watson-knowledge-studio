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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window}.
{: tip}

# Risoluzione dei problemi, supporto e FAQ
{: #troubleshooting}

Per isolare e risolvere i problemi con i tuoi prodotti {{site.data.keyword.IBM_notm}}, puoi utilizzare le informazioni sulla risoluzione dei problemi e sul supporto. Queste informazioni contengono le istruzioni sull'utilizzo delle risorse di determinazione del problema fornite con i tuoi prodotti {{site.data.keyword.IBM_notm}}, incluso {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Tecniche per la risoluzione dei problemi  
{: #ts_overview}

La *risoluzione dei problemi* è un approccio sistematico alla risoluzione di un problema. L'obiettivo della risoluzione dei problemi è determinare il motivo per cui
qualcosa non funziona nel modo previsto e come risolvere il problema.
Alcune tecniche comuni possono essere utili per l'attività di risoluzione
dei problemi.


Il primo passo per la risoluzione dei problemi è la descrizione dettagliata del problema. La descrizione del problema aiuta l'utente e il rappresentante del supporto tecnico {{site.data.keyword.IBM_notm}} a identificare la possibile causa scatenante del problema. In questa fase bisogna porsi le seguenti domande basilari:

- Quali sono i sintomi del problema? 
- Dove si evidenzia il problema? 
- Quando si presenta il problema?
- Sotto quali condizioni si presenta il problema?
- È possibile riprodurre il problema? 

Rispondendo a queste domande si ottiene una descrizione chiara del problema che può agevolarne la risoluzione.

### Quali sono i sintomi del problema? 

Quando si comincia a descrivere un problema, la domanda
più ovvia è "Qual è il problema?". Questa domanda potrebbe sembrare diretta, tuttavia è possibile scomporla
in alcune domande più precise che creano un quadro più descrittivo
del problema. Queste domande possono includere.

- Chi o cosa notifica il problema?
- Quali sono i codici errore e i messaggi?
- Qual è il malfunzionamento del sistema? Ad esempio, si tratta di un loop, di una sospensione, di un'interruzione, di un peggioramento delle prestazioni o di risultato non corretto?

### Dove si evidenzia il problema? 

La determinazione del punto di origine del problema non è sempre facile, ma è uno dei passi più importanti della risoluzione di un problema. Tra i componenti
che segnalano il malfunzionamento e i componenti malfunzionanti possono
esistere molti livelli di tecnologia. Reti, dischi e driver sono solo alcuni dei componenti da considerate quando si esaminano i problemi.

Le domande seguenti aiutano a individuare il punto esatto in cui si verifica il problema e a isolare il livello del problema:

- Il problema è specifico di una piattaforma o sistema operativo o si verifica su più piattaforme o sistemi operativi?
- La configurazione e l'ambiente correnti sono supportati?
- Il problema viene rilevato da tutti gli utenti? 
- (Per le installazioni su più siti). Tutti i siti presentano il problema?

Seppure un livello segnali un problema, ciò non presuppone che esso sia necessariamente l'origine. Parte dell'identificazione dell'origine di un problema è conoscere l'ambiente in cui
il problema è presente. È sempre utile dedicare tempo alla descrizione completa dell'ambiente del problema indicando sistema operativo e versione, tutti i software corrispondenti e relative versioni e le informazioni sull'hardware. Verificare che si utilizzi un ambiente che ha una configurazione supportata: molti problemi possono essere tracciati a livelli non compatibili di software che magari non possono essere eseguiti insieme o che non sono stati testati completamente insieme. 

### Quando si presenta il problema?

Sviluppare una scala del tempo dettagliata degli eventi che si sono verificati
fino ad un errore, soprattutto per i casi che rappresentano ricorrenze univoche. Il modo più facile per sviluppare una linea temporale consiste nel
lavorare a ritroso: iniziare all'ora in cui è stato notificato un errore
(il più precisamente possibile, anche al millisecondo) e procedere al
contrario nei log e nelle informazioni disponibili. In genere è necessario tornare indietro solo fino al primo evento
sospetto individuato in un log diagnostico.

Per sviluppare una cronologia dettagliata degli eventi, rispondere alla seguenti domande:

- Il problema si verifica solo a una particolare ora del giorno o della notte?
- Con che frequenza si verifica?
- Qual è la sequenza di eventi che porta al momento in cui si rileva
il problema?
- Il problema si verifica dopo una modifica dell'ambiente, ad esempio un aggiornamento o l'installazione di un
software o hardware?

La
risposta a questi tipi di domande può fornire un quadro di riferimento
in cui ricercare il problema.

### Sotto quali condizioni si presenta il problema?

Sapere quali sistemi e applicazioni sono in esecuzione nel momento in cui si verifica un problema è un aspetto importante della risoluzione dei problemi. Le domande relative al proprio ambiente possono aiutare a identificare la causa principale del problema:

- Il problema si verifica sempre quando viene eseguita la stessa attività?
- Affinché si verifichi il problema, è necessario che venga eseguita una
specifica sequenza di eventi?
- Altre applicazioni vanno in errore nello stesso momento?

Rispondere a questo tipo di domande può facilitare l'illustrazione dell'ambiente in cui si verifica il problema e a correlare eventuali dipendenze. Tenere presente che se più problemi si sono verificati più o meno contemporaneamente questo da solo
non significa che i problemi siano necessariamente correlati.

### È possibile riprodurre il problema? 

Da un punto di
vista della risoluzione dei problemi, il problema ideale è un problema che
è possibile riprodurre. Di solito, quando è possibile riprodurre
un problema, si dispone di un maggior numero di strumenti o procedure per effettuare le opportune
verifiche. Di conseguenza, i problemi che possono essere riprodotti sono spesso più facili da risolvere.

Tuttavia, questi problemi hanno uno svantaggio: se il problema ha un impatto aziendale notevole, non si desidera che venga riprodotto. Se possibile, ricreare il problema in un ambiente di test o di sviluppo che offre in genere una maggiore flessibilità e un maggiore controllo durante l'analisi. 

- È possibile ricreare il problema in un sistema di test?
- Più utenti o applicazioni riscontrano lo stesso tipo di problema?
- È possibile ricreare il problema eseguendo un unico comando, una serie di comandi o una particolare applicazione?

## Problemi con il modello AlchemyLanguage
{: #wks_ts_deployed_model_deleted}

### Problema

Non puoi distribuire un modello AlchemyLanguage oppure la distribuzione ha avuto esito positivo ma il modello non è disponibile per l'utilizzo.

### Sintomi

- Hai distribuito un modello ma lo stato mostra che si è verificato un errore.
- Hai distribuito un modello e lo stato indica che il modello era disponibile ma non puoi utilizzarlo.
- Il modello è stato distribuito correttamente e funzionava precedentemente ma non ora non più.

### Cause

I seguenti eventi possono causare problemi con i modelli distribuiti:

- Se hai sbagliato a immettere la chiave {{site.data.keyword.alchemyapishort}} quando la aggiungi al parametro `apikey` della chiamata API REST, la chiamata avrà esito negativo. Lo stesso vale per l'ID del modello. È meglio copiare e incollare l'ID del modello e la chiave API per evitare errori di battitura.
- Se fornisci una chiave {{site.data.keyword.alchemyapishort}} non valida o se non sei autorizzato a distribuire un modello personalizzato, il processo di distribuzione indicherà che il modello è stato distribuito correttamente ma non potrai utilizzarlo.
- Se, mentre utilizzi {{site.data.keyword.alchemylanguageshort}} in {{site.data.keyword.Bluemix}}, elimini tutte le istanze del servizio associate a una chiave {{site.data.keyword.alchemyapishort}} in {{site.data.keyword.Bluemix_notm}}, tutti i modelli distribuiti che fanno riferimento a tale chiave saranno rimossi dal servizio. {{site.data.keyword.Bluemix_notm}} controlla periodicamente se i modelli registrati sono associati a una chiave valida e tutti quelli che non lo sono vengono eliminati. Se il tuo modello è stato distribuito con una chiave che è stata eliminata, lo stato si modificherà in `error`.

### Risoluzione del problema

1. Controlla lo stato della distribuzione.

    Accedi come amministratore {{site.data.keyword.knowledgestudioshort}}. Nella pagina **Model Management** > **Versions**, visualizza la colonna **Status** per controllare lo stato del modello che hai distribuito.

1. Se lo stato della distribuzione del modello è `error` o `available` ma il modello non funziona quando provi ad utilizzarlo, ritiralo dalla distribuzione facendo clic su **Undeploy**.
1. Ridistribuisci il modello.

    Utilizza solo una chiave {{site.data.keyword.alchemyapishort}} valida che ha l'autorizzazione a distribuire i modelli e copia e incolla l'ID del modello e la chiave API quando li aggiungi come parametri alla chiamata API.

**Attività correlate**:

[Distribuzione di un modello di machine learning a {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/publish-ml.html#wks_mabluemix)

## Impossibile creare un account gratuito
{: #wks_ts_free}

### Problema

Provi a creare un account gratuito e visualizzi il messaggio di errore, `Error 331: We are unable to process your request. Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### Cause

{{site.data.keyword.knowledgestudioshort}} non consente più di un account gratuito per organizzazione.

### Risoluzione del problema

Crea un account che non sia incluso nell'organizzazione.

Se devi utilizzare il tuo account corrente per la prova gratuita ed è associato a un account a pagamento, puoi inviare un ticket di supporto. Per ulteriori informazioni, vedi [Come contattare il supporto {{site.data.keyword.IBM_notm}}](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Se devi utilizzare il tuo account corrente per la prova gratuita e non è associato a un account a pagamento, inserisci il tuo problema in [{{site.data.keyword.IBM_notm}} developerWorks Answers](https://developer.ibm.com/answers/topics/wks/), assicurandoti di contrassegnare la domanda, **WKS**.

## Impossibile accedere all'applicazione
{: #wks_ts_access}

Scopri come concedere l'accesso utenti a {{site.data.keyword.knowledgestudioshort}} e risolvi i problemi di accesso comuni.

Devi avere le credenziali di registrazione dell'utente {{site.data.keyword.IBM_notm}} per richiedere un'istanza di {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}}.

### Amministratore

Ogni istanza di {{site.data.keyword.knowledgestudioshort}} ha un ruolo di amministratore associato. Alla persona che originariamente si è registrata per utilizzare l'applicazione viene automaticamente assegnato il ruolo di amministratore. L'amministratore può invitare altre persone.

Per le informazioni su come invitare le persone ad utilizzare la tua istanza dell'applicazione, consulta [Assemblaggio del team](/docs/services/watson-knowledge-studio/team.html).

### Annotatore umano

Se sei stato invitato nell'istanza di {{site.data.keyword.knowledgestudioshort}} di qualcuno, per coprire il ruolo di annotatore umano, probabilmente hai ricevuto un invito email. Per prima cosa, devi registrarti con {{site.data.keyword.IBM_notm}} se non hai già le credenziali di registrazione di {{site.data.keyword.IBM_notm}}. Una volta registrato con {{site.data.keyword.IBM_notm}} e accettato l'invito, ti viene fornito l'accesso all'istanza. Tuttavia, dopo che ti è stato fornito l'accesso e prima di poter iniziare ad annotare i documenti, l'amministratore o un gestore del progetto dell'istanza deve aggiungerti a uno spazio di lavoro e assegnarti un'attività di annotazione. Finché non vieni assegnato a un'attività non puoi effettuare alcuna azione nell'istanza di {{site.data.keyword.knowledgestudioshort}}. Per annotare i documenti utilizza l'editor ground truth. Utilizza un browser Google Chrome per prestazioni migliori.

Per l'utilizzo dell'editor ground truth, consulta [Annotazione dei documenti](/docs/services/watson-knowledge-studio/user-guide.html).

## Servizi sperimentali: cosa significa *sperimentale*?
{: #experimental}

Per informazioni sui servizi sperimentali, consulta la [documentazione {{site.data.keyword.Bluemix_notm}}](/docs/services/index.html#experimental_services). Per i dettagli completi sui servizi sperimentali, consulta l'ultima versione di [{{site.data.keyword.Bluemix_notm}} Service Description ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=IBM+Bluemix+Service+Description){: new_window}.

## Problemi con lo spazio di archiviazione
{: #storage}

A seconda del tuo piano di sottoscrizione, potresti raggiungere il limite di archiviazione specificato per il tuo piano e non poter eseguire le attività che vuoi completare.

### Sintomi

Potresti visualizzare un messaggio sull'aver superato lo spazio di archiviazione consentito quando provi ad eseguire una di queste attività:

- Caricare i documenti o i dizionari
- Distribuire un modello o una versione del modello
- Eseguire un pre-annotatore sui documenti

### Cause

Il limite di archiviazione è stato raggiunto o potrebbe essere superato se l'azione dovesse procedere.

### Risoluzione del problema

I più grandi consumatori di spazio di archiviazione sono i modelli di machine learning e basati sulla regola. Per liberare spazio, puoi effettuare le seguenti azioni: 

- Elimina l'istantanea delle versioni di ogni modello che non prevedi sia necessario ripristinare.
- Elimina tutti i modelli di cui non hai bisogno.
- Se i tuoi modelli sono troppo importanti per essere eliminati, considera di eseguire l'upgrade del tuo piano a uno che fornisce una quantità maggiore di spazio di archiviazione.

Dopo aver rimosso i modelli o le versioni del modello, attendi un'ora prima di riprovare l'azione che ha creato il messaggio di errore. È necessaria fino a un'ora perché lo spazio di archiviazione che hai liberato sia disponibile per l'utilizzo.

Per gestire la tua fatturazione mensile, se ti è stato assegnato il ruolo di amministratore e hai un account standard o premium, puoi impostare un limite di archiviazione nella pagina Service Details in {{site.data.keyword.knowledgestudioshort}}. Per visualizzare la pagina Service Details e impostare il limite di archiviazione, dalla barra di navigazione principale in {{site.data.keyword.knowledgestudioshort}}, fai clic sull'icona **Settings**, sul link **View/modify service details** e poi sul link **Set storage limit**.
{: tip}

## Come contattare il supporto IBM 
{: #ts_contactingibmsupport}

Il supporto {{site.data.keyword.IBM_notm}} fornisce assistenza con i difetti del prodotto, le risposte alle FAQ e aiuta gli utenti a risolvere i problemi con il prodotto.

### Prima di cominciare

Per prima cosa, cerca se una soluzione del problema che stai avendo è documentata. Cerca {{site.data.keyword.knowledgestudioshort}} nel [{{site.data.keyword.IBM_notm}} Support Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/home/entry/portal){: new_window}. Nella pagina dei risultati della ricerca, fai clic sulla scheda **Support** per visualizzare i risultati dalle tech note, {{site.data.keyword.IBM_notm}} Redbooks e dalla documentazione. Fai clic sulla scheda **For developers** per visualizzare i risultati dalla community {{site.data.keyword.IBM_notm}} developerWorks, come blog e domande sul forum.

Dopo aver tentato di trovare la tua risposta o soluzione cercando nel [{{site.data.keyword.IBM_notm}} Support Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/home/entry/portal){: new_window}, puoi contattare il supporto {{site.data.keyword.IBM_notm}}. Il tipo di supporto che hai dipende dal tuo tipo di servizio.

- **Utenti del piano gratuito**

    Richiedi assistenza e risposte alle domande chiedendo ai colleghi della community di sviluppatori. Per i link alle community di sviluppatori, consulta la sezione **Developer community** nella tabella dei contenuti.

- **Utenti del piano a pagamento**

    Come utente di un piano a pagamento, anche tu puoi fare domande e imparare dalle domande di altri utenti. I forum sono aperti a chiunque e sono un buon punto di partenza. Per i link, consulta la sezione **Developer community** nella tabella dei contenuti.

    Invia un ticket del problema dal [{{site.data.keyword.IBM_notm}} Cloud Service Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson.service-now.com/wcp){: new_window}.

    > **Nota:** devi essere autorizzato per inviare i problemi a {{site.data.keyword.IBM_notm}}.

### Procedura

Per contattare il supporto {{site.data.keyword.IBM_notm}} per un problema:

1. Definisci il problema, raccogli le informazioni di background e determina la gravità del problema.
1. Raccogli le informazioni di diagnostica, se possibile.
1. Invia il problema al supporto {{site.data.keyword.IBM_notm}}. Per i dettagli di contatto, fai riferimento a [Software as a Service support guide ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www-01.ibm.com/software/support/acceleratedvalue/SaaS_Handbook_V18.pdf){: new_window}.
