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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/improve-ml.html){: new_window}.
{: tip}

# Apportare i miglioramenti al modello di machine learning
{: #improve-ml}

Dopo aver determinato le aree in cui il modello sta avendo problemi, effettua delle azioni per migliorarne le prestazioni.
{: shortdesc}

## Creazioni delle versioni del modello
{: #wks_maversions}

Dopo aver creato un modello di machine learning, puoi prendere un'istantanea per conservare una versione di backup delle risorse correnti nel caso vuoi ripristinarle in una iterazione futura.

### Informazioni su quest'attività
{: #wks_maversions_about}

Il punteggio F1 fornisce un'indicazione della qualità del modello. Se i risultati delle prestazioni del modello sono buoni, potresti voler archiviare una versione del componente prima di modificare qualcuna delle risorse. Se le modifiche che apporti comportano una qualità inferiore, puoi ripristinare una versione che hai archiviato. Quando ripristini una versione precedente, tutte le attività di annotazione vengono archiviate perché non sono più valide.

Puoi avere un massimo di 10 versioni di uno spazio di lavoro. Se raggiungi tale limite, elimina le versioni più vecchie o quelle di cui non hai più bisogno prima di crearne una nuova.

Quando crei una nuova versione, vengono acquisite le seguenti risorse:

- Sistema tipo
- Corpus
- Ground truth
- Modello di machine learning
- Risultati della valutazione del modello di machine learning

Le seguenti risorse vengono escluse:

- Attività di annotazione, perché, come progettato, sono temporali, utilizzate solo per la determinazione del ground truth
- Dizionari, perché possono essere grandi e vari tipi di dizionari sono gestiti in modi diversi.

### Procedura
{: #wks_maversions_procedure}

Per creare e ripristinare le versioni del modello di machine learning:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona **Machine Learning Model** > **Performance**.Vengono visualizzate le statistiche della versione corrente, etichettata versione 1.0.
1. Per prendere un'istantanea della versione corrente, fai clic su **Machine Learning Model** > **Versions** e poi su **Take Snapshot**. Le risorse nella versione 1.0 vengono bloccate e la nuova versione, etichettata 1.1, diventa la corrente. Per ogni nuova versione che crei, viene incrementato il numero minore di versione, ad esempio, 1.0 diventa 1.1 che poi diventa 1.2.
1. Rivedi le risorse dello spazio di lavoro se necessario, riprepara e rivaluta il modello.
1. Se sei soddisfatto dei risultati delle prestazioni e vuoi archiviare la nuova versione prima di effettuare altre modifiche, crea un'altra versione. Continua a revisionare le risorse e riprepara il modello se necessario, creando una nuova versione per ogni iterazione che vuoi conservare.
1. Se i risultati delle prestazioni sono peggiori e vuoi ripristinare una versione precedente prima di ulteriori test:

    1. Apri la pagina **Assets** > **Dictionaries** e scarica tutti i dizionari che vuoi riutilizzare nel modello ripristinato.
    1. Fai clic su **Machine Learning Model** > **Versions** e su **Promote** della versione che vuoi ripristinare. La versione che promuovi diventa la versione corrente e il numero di versione viene modificato con 2.0. Quando promuovi una versione, viene incrementato il numero di versione maggiore e il minore diventa 0, ad esempio, 1.1 diventa 2.0.
    1. Apri la pagina **Dictionaries** e carica i dizionari che hai scaricato.
    1. Se il test della nuova versione richiede modifiche al ground truth, apri la pagina **Machine Learning Model** > **Annotation Tasks** e crea una nuova attività di annotazione.

## Modifica di un sistema tipo senza perdere le annotazioni umane
{: #wks_projtypesysmod}

Potresti dover effettuare delle modifiche mentre prepari un modello, in base alle statistiche delle prestazioni. Ma, generalmente, vuoi che il sistema tipo sia il più vicino possibile a quello finale prima di iniziare attività di annotazione su larga scala. Se modifichi il sistema tipo dopo che gli annotatori umani hanno iniziato il loro lavoro, devi rivedere i documenti che hanno annotato. Devono valutare l'applicabilità delle modifiche del sistema tipo.

### Informazioni su quest'attività
{: #wks_projtypesysmod_about}

Questo processo propaga il sistema tipo corrente, i tasti di scelta rapida dell'editor ground truth e le impostazioni sul colore a tutte le serie di documenti in un'attività.

### Procedura
{: #wks_projtypesysmod_procedure}

Per modificare il sistema tipo senza perdere il lavoro fatto dagli annotatori umani:

1. Modifica il sistema tipo. Ad esempio, puoi aggiungere o rimuovere i tipi di entità e di relazione.
1. Decidi se vuoi propagare le modifiche alle attività di annotazione umana esistenti.
1. Nella pagina **Machine Learning Model** > **Annotation Tasks**, apri ogni attività che vuoi aggiornare e fai clic su **Apply Type System Updates**.

    Se hai rimosso i tipi di entità o di relazione dal sistema tipo, tute le ricorrenze di questi tipi vengono evidenziate in grigio nei documenti. Questi tipi non validi vengono ignorati dal modello di machine learning. Non ti impediscono di inviare e approvare le serie di documenti.

1. Fornisci i dettagli agli annotatori umani su cosa è stato modificato nel sistema tipo.
1. Chiedi agli annotatori umani di aggiornare i loro documenti per riflettere le modifiche nel sistema tipo. Ad esempio, se hai aggiunto nuovi tipi di entità o di relazione, devono rivedere i loro documenti e annotarli in modo appropriato.

    > **Nota:** se l'attività contiene documenti completati, gli annotatori umani non possono modificarli per valutare le modifiche al sistema tipo finché non tornano in uno stato modificabile. Per diventare modificabili, chiedi agli annotatori umani di inviare le serie di documenti in modo che puoi rifiutarle.

**Concetti correlati**:
{: #wks_projtypesysmod_related}

[Sistemi tipo](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)

## Gestione della serie di documenti
{: #wks_mamanagedata}

Utilizza le serie di dati corrette per verificare e preparare il modello al momento giusto.

I documenti che aggiungi al sistema devono essere assegnati alle seguenti serie di dati al livello del sistema quando crei un modello di machine learning:

- **Serie di preparazione**

    Una serie di documenti che sono stati annotati tramite la pre-annotazione o dagli annotatori umani che viene utilizzata per preparare il modello. L'obiettivo della serie di preparazione è di istruire il modello di machine learning sulle annotazioni corrette, che include insegnare al modello tramite il testo che non è stato annotato.

- **Serie di test**

    Una serie di documenti annotati che viene utilizzata per verificare il modello preparato. Dopo aver eseguito una serie di test, esegui un'analisi dell'errore a scopi diagnostici dettagliata dei risultati. Un'attenta analisi ti aiuta a trovare le debolezze del modello corrente che possono essere risolte.

- **Serie senza indicazioni**

    Una serie di documenti annotati che viene messa da parte e utilizzata per verificare il sistema periodicamente dopo che si sono verificate molte iterazioni di test è miglioramenti. Per evitare che l'accuratezza venga contaminata (ad esempio, effettuando modifiche basate solo sulle annotazioni nei documenti noti), i dati senza indicazioni che potrebbero essere i dati che non sono stati precedentemente visualizzati dagli utenti, vengono coinvolti nella creazione del modello. I risultati riportati dovrebbero provenire solo dai test che vengono eseguiti sui dati senza indicazioni. Dopo aver eseguito un test sulla serie senza indicazioni, cerca solo i punteggi di più alto livello, come i punteggi F1 della citazione e della relazione generali. Non vuoi imparare troppi dettagli sulle prestazioni o potrebbe influenzare i miglioramenti che scegli di  apportare al modello.

L'obiettivo di {{site.data.keyword.knowledgestudioshort}} è di abilitare grandi team a lavorare insieme per creare i modelli. In quanto tale, assume che i modelli siano stati prodotti da un team che include un gruppo di annotatori umani e una persona o un gruppo di persone separato che crea e verifica il modello e apportano miglioramenti ad esso. A causa di questa ipotesi, l'applicazione viene configurata per eseguire il push di un raggruppamento di documenti proporzionato in ugual modo da una sola serie di documenti nelle serie di test, preparazione e senza indicazioni. Tuttavia, se il tuo team non viene suddiviso - ad esempio, se le persone che eseguono l'annotazione umana stanno anche revisionando i risultati del test del modello nel dettaglio - potresti dover modificare l'assegnazione dei documenti a queste serie per separare più esplicitamente i documenti che stanno venendo utilizzati da ognuna di esse.

### Perché ho bisogno di una serie senza indicazioni?
{: #wks_mamanagedata_why}

Poiché utilizzi i dati di test per valutare l'accuratezza in dettaglio, devi conoscere i documenti e le loro funzioni dopo un po' di tempo. Ad esempio, inizi a capire quali tipi di entità, di relazione e di test nei documenti vengono meglio riconosciuti dal modello di machine learning e quali meno. Queste informazioni sono importanti perché ti aiutano a concentrarti sull'eseguire i miglioramenti corretti - ad esempio, rifinendo il sistema tipo, integrando i dati di preparazione per colmare le lacune o aggiungendo i dizionari. Poiché i documenti di test vengono utilizzati ripetutamente per migliorare il modello, possono iniziare ad influenzare indirettamente la preparazione del modello. Questo è il motivo per cui la serie di documenti "senza indicazioni" è così importante.

### Come controllo quali documenti vengono assegnati a una serie?
{: #wks_mamanagedata_how}

Quando crei un modello di machine learning, devi specificare il rapporto di documenti dalla serie da assegnare alle serie di preparazione, test o senza indicazioni. {{site.data.keyword.knowledgestudioshort}} automaticamente applica un rapporto di 70/23/7 alle serie di documenti che utilizzi per creare un modello di machine learning. Puoi modificare questi valori.

- Per aggiungere una serie che è stata annotata da umani alla serie di preparazione, specifica un rapporto di suddivisione di 100/0/0.
- Dopo aver preparato una serie, puoi utilizzarla per il test. Per utilizzare una serie solo per il test, specifica un rapporto di suddivisione di 0/100/0.
- Aggiungi solo una serie di documenti che non è mai stata utilizzata per la preparazione o il test alla serie senza indicazioni. Per far ciò, specifica un rapporto di suddivisione di 0/0/100 per la serie di documenti.

Pensa di interrompere l'utilizzo di una serie senza indicazioni dopo alcune iterazioni. Più utilizzi una serie senza indicazioni e meno lo rimane. Lo stesso vale per i tuoi dati di test. Anziché eliminare le serie, puoi migrarle e utilizzarle per un nuovo scopo. Segui questo flusso di migrazione:

```
blind --> test --> train
```
{: screen}

Mentre le serie migrano, puoi aggiungere serie di documenti nuove e mai viste come dati senza indicazioni e di test. Ma assicurati di conservare un metodo per la valutazione tra più versioni del modello. Un modo di stabilire una linea di base è di eseguire una versione precedente del modello nelle nuove serie di documenti. I risultati di questa esecuzione ti forniscono le basi per il confronto con le esecuzioni dei modelli più recenti in quelle stesse serie.
