---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-24"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window}.
{: tip}

# Creazione di un modello di machine learning
{: #wks_tutml_intro}

Questa esercitazione di aiuta a comprendere il processo di creazione di un modello di machine learning che puoi distribuire e utilizzare con altri servizi {{site.data.keyword.watson}}.
{: shortdesc}

## Obiettivi di apprendimento
{: #objectives}

Dopo aver completato le lezioni in questa esercitazione, saprai come effettuare le seguenti attività:

- Creare serie di documenti
- Pre-annotare i documenti
- Creare le attività per gli annotatori umani
- Analizzare l'accordo tra annotatori e giudicare i conflitti nei documenti annotati.
- Creare i modelli di machine learning

Lo svolgimento di questa esercitazione richiede circa 60 minuti. Se si approfondiscono altri concetti correlati a questa esercitazione, potrebbe essere necessario più tempo.

## Prima di cominciare
{: #prereqs}

- Assicurati di stare utilizzando un browser supportato. Consulta [Requisiti del browser](/docs/services/watson-knowledge-studio/system-requirements.html).
- Hai correttamente completato l'[Introduzione a {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html), che copre la creazione di uno spazio di lavoro, la creazione di un sistema tipo e l'aggiunta di un dizionario.
- Devi avere almeno un ID utente nel ruolo di gestore del progetto o di amministratore. 

    > **Nota:** se possibile, utilizza più ID utente per le attività del modello di machine learning in questa esercitazione (un ID utente gestore del progetto o amministratore e almeno due ID utente annotatore umano). L'utilizzo di più ID utente fornisce la simulazione più realistica di uno spazio di lavoro {{site.data.keyword.knowledgestudiofull}} reale, dove un gestore del progetto deve coordinare e giudicare l'annotazione effettuata da più annotatori umani. Tuttavia, se hai accesso a solo un ID utente, puoi ancora simulare molte parti del progetto.

    Per informazioni sui ruoli utente, consulta [Ruoli utente in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Risultati
{: #results}

Dopo aver completato questa esercitazione, avrai un modello di machine learning personalizzato che puoi utilizzare con gli altri servizi {{site.data.keyword.watson}}.

## Lezione 1: Aggiunta di documenti per l'annotazione
{: #tut_lessml1}

In questa lezione, apprenderai come aggiungere i documenti a uno spazio di lavoro in {{site.data.keyword.knowledgestudioshort}} che possono venire annotati dagli annotatori umani.

### Informazioni su quest'attività
{: #tut_lessml1_about}

Per ulteriori informazioni sull'aggiunta dei documenti, vedi [Aggiunta di documenti a uno spazio di lavoro](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

### Procedura
{: #tut_lessml1_procedure}

1. Scarica il file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv` <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a> sul tuo computer. Questo file contiene i documenti di esempio adatti per il caricamento.
1. All'interno del tuo spazio di lavoro, fai clic su **Assets** > **Documents**.
1. Nella pagina Documents, fai clic su **Upload Document Sets**.
1. Carica il file `documents-new.csv` dal tuo computer. Il file caricato viene visualizzato nella tabella.

### Operazioni successive
{: #tut_lessml1_next}

Puoi ora suddividere il corpus in più serie documenti e assegnarle agli annotatori umani.

## Lezione 2: Creazione delle serie di annotazioni
{: #wks_tutless_ml2}

In questa lezione, apprenderai come creare le serie di annotazioni in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml2_about}

Una *serie di annotazioni* è una sottoserie di documenti da una serie di documenti caricata che assegni a un annotatore umano. L'annotatore umano annota i documenti nella serie di annotazioni. Per utilizzare in un secondo momento i punteggi tra annotatori per confrontare le annotazioni che sono state aggiunte da ogni annotatore umano, devi assegnare almeno due annotatori umani a serie di annotazioni differenti. Devi anche specificare una percentuale di documenti che si sovrappongono tra le serie.

> **Nota:** in uno scenario realistico, potresti creare tutte le serie di annotazioni necessarie, in base al numero di annotatori umani che stanno lavorando nello spazio di lavoro. In questa esercitazione, creerai due serie di annotazioni. Se non hai accesso a più ID utente, puoi assegnare entrambe le serie allo stesso utente. 

Per ulteriori informazioni sulle serie di annotazioni, consulta [Creazione e assegnazione delle serie di annotazioni](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).

### Procedura
{: #wks_tutless_ml2_procedure}

1. All'interno del tuo spazio di lavoro, fai clic su **Assets** > **Documents**.
2. Fai clic su **Create Annotation Sets**.

    Si apre la finestra Create Annotation Sets. Per impostazione predefinita, questa finestra mostra la serie base che contiene tutti i documenti e i campi in cui puoi specificare le informazioni di una nuova serie di annotazioni.

3. Fai clic su **Add another set and human annotator** per aggiungere i campi di una serie di annotazioni aggiuntiva. Puoi fare clic per aggiungere tutte le serie di annotazioni che vuoi creare. Per questa esercitazione, hai bisogno solo di due serie di annotazioni. 

    ![Un'acquisizione schermo della pagina Create Annotation Sets.](images/wks_tutdocset2.jpg "Un'acquisizione schermo della pagina Create Annotation Sets.")

4. Nel campo **Overlap**, specifica `100`. Questo valore specifica che vuoi il 100 percento dei documenti nella serie di base inclusi in tutte le nuove serie di annotazioni in modo che possono essere annotate da tutti gli annotatori umani.
5. Per ogni nuova serie di annotazioni, specifica le informazioni obbligatorie.

    - Nel campo **Annotator**, seleziona un ID utente di un annotatore umano a cui assegnare la nuova serie di annotazioni. In uno scenario realistico, ogni serie di annotazioni viene assegnata a un annotatore umano diverso.

        > **Nota:** se hai solo un ID amministratore da utilizzare per l'esercitazione, assegna a tale utente tutte le serie di annotazioni. In uno scenario realistico, avrai più annotatori umani, ma per l'esercitazione, l'amministratore può agire come annotatore umano.

    - Nel campo **Set name**, specifica un nome descrittivo della serie di annotazioni. Per questa esercitazione, puoi utilizzare i nomi, `Set 1` e `Set 2`.

6. Fai clic su **Generate**.

### Risultati
{: #wks_tutless_ml2_results}

Vengono create le nuove serie di annotazioni.

## Lezione 3: Pre-annotazione con un annotatore basato sul dizionario
{: #wks_tutless_ml3}

In questa lezione, apprenderai come utilizzare un annotatore basato sul dizionario per pre-annotare i documenti in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml3_about}

La pre-annotazione dei documenti è un passo facoltativo. Tuttavia, è un passo importante perché rende più semplice il successivo lavoro degli annotatori umani.

Per ulteriori informazioni sulla pre-annotazione con i dizionari, consulta [Pre-annotazione dei documenti con un dizionario](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot).

### Procedura
{: #wks_tutless_ml3_procedure}

1. All'interno del tuo spazio di lavoro, fai clic su **Assets** > **Dictionaries**.

  Si apre il dizionario `Test dictionary`. La lezione [Aggiunta di un dizionario](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) dell'esercitazione *Introduzione a {{site.data.keyword.knowledgestudioshort}}* mostra come creare questo dizionario.

1. Dall'elenco **Entity type**, seleziona il tipo di entità `ORGANIZATION` e associalo al dizionario `Test dictionary`.

  La lezione [Creazione di un sistema tipo](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless3) dell'esercitazione *Introduzione a {{site.data.keyword.knowledgestudioshort}}* mostra come creare il sistema tipo che contiene il tipo di entità `ORGANIZATION`.

1. Nella scheda **Machine Learning Model** > **Pre-annotation** > **Dictionaries**, fai clic su **Apply This Pre-annotator**.
1. Seleziona le serie di annotazioni che hai creato nella [Lezione 2](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2), non includendo la serie di documenti che hai creato nella [Lezione 1](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1).
1. Fai clic su **Run**.

    ![Questa schermata mostra la pagina Run Annotator. Il pulsante Run è evidenziato.](images/wks_tutanno3.jpg "Questa schermata mostra la pagina Run Annotator. Il pulsante Run è evidenziato.")

### Risultati
{: #wks_tutless_ml3_results}

I documenti nelle serie selezionate vengono pre-annotati utilizzando il dizionario che hai creato. Se vuoi, puoi utilizzare il dizionario per pre-annotare le serie di documenti o di annotazioni che aggiungi successivamente.

## Lezione 4: Creazione di un'attività di annotazione
{: #wks_tutless_ml4}

In questa lezione, apprenderai come utilizzare le attività di annotazione per tenere traccia del lavoro degli annotatori umani in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml4_about}

Per ulteriori informazioni sulle attività di annotazione, vedi [Creazione di un'attività di annotazione](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask).

### Procedura
{: #wks_tutless_ml4_procedure}

1. All'interno del tuo spazio di lavoro, fai clic su **Machine Learning Model** > **Annotation Tasks**.
2. Nella pagina Tasks, fai clic su **Add Task**.
3. Specifica i dettagli dell'attività:

    - Nel campo **Task name**, immetti `Test`.
    - Nel campo **Deadline**, seleziona una data futura.

4. Fai clic su **Create**.
5. Seleziona le serie di annotazioni che hai creato nella [Lezione 2](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2).

 Selezionando entrambe le serie di annotazioni specifichi che devono essere annotate entrambe dai propri annotatori umani per il completamento di questa attività.

7. Fai clic su **Create Task**.
8. Quando gli annotatori umani iniziano ad annotare i documenti, puoi aprire le attività per visualizzarne i progressi.

## Lezione 5: Annotazione dei documenti
{: #wks_tutless_ml5}

In questa lezione, apprenderai come utilizzare un *editor ground truth* per annotare i documenti in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml5_about}

Per ulteriori informazioni sull'annotazione umana, vedi [Annotazione con l'editor ground truth](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte).

### Procedura
{: #wks_tutless_ml5_procedure}

1. Accedi a {{site.data.keyword.knowledgestudioshort}} come un utente a cui è assegnata l'attività di annotazione che hai creato nella [Lezione 4](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).

    > **Nota:** se hai accesso a un solo ID amministratore per questa esercitazione, puoi utilizzarlo per eseguire l'annotazione umana. Tuttavia, ricorda che in uno scenario realistico, l'annotazione umana è effettuata da utenti diversi con il ruolo di annotatore umano.

1. Apri lo spazio di lavoro `My workspace` e fai clic su **Machine Learning Model** > **Annotation Tasks**.
1. Apri l'attività di annotazione `Test` che hai creato nella [Lezione 4](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).
1. Fai clic su **Annotate** di una delle serie di annotazioni assegnate.

  A seconda di come configuri le attività di annotazione, potresti avere una o più attività di annotazione assegnate all'ID utente con cui hai eseguito l'accesso.

1. Dall'elenco dei documenti, trova il documento *Technology - gmanews.tv* e aprilo.

  Nota che il termine `IBM` è stato già annotato con il tipo di entità `ORGANIZATION`. Questa annotazione è stata aggiunta dal pre-annotatore del dizionario che è stato applicato nella [Lezione 3](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3). Questa pre-annotazione è corretta, non è necessario modificarla.

  ![Questa schermata mostra un documento aperto con una pre-annotazione esistente di "IBM".](images/wks_tut_preannotation.png "Questa schermata mostra un documento aperto con una pre-annotazione esistente di ")

1. Annota una citazione:

    1. Fai clic sulla scheda Entity.
    2. Nel corpo del documento, seleziona il testo `Thomas Watson`.
    3. Nell'elenco dei tipi di entità, fai clic su `PERSON`. Il tipo di entità `PERSON` viene applicato alla citazione selezionata.

        ![Questa schermata mostra il tipo di entità "PERSON" applicato alla citazione "Thomas Watson".](images/wks_tut_annotatemention3.png "Questa schermata mostra ")

1. Annota una relazione:

    1. Fai clic sulla scheda Relation.
    1. Seleziona le citazioni `Thomas Watson` e `IBM` (in questo ordine). Per selezionare una citazione, fai clic sull'etichetta del tipo di entità accanto al testo.
    1. Nell'elenco dei tipi di relazione, fai clic su `founderOf`. Le due citazioni vengono collegate con una relazione `founderOf`.

        ![Questa schermata mostra due citazioni collegate dl tipo di relazione, "founderOf".](images/wks_tut_annotaterelation.png "Questa schermata mostra due citazioni collegate dl tipo di relazione, ")

1. Dal menu dello stato, seleziona **Completed** e poi fai clic sul pulsante **Save**.
1. Fai clic su **Open document list** per ritornare all'elenco dei documenti di questa attività e fai clic su **Submit All Documents** per inviare i documenti per l'approvazione.

    > **Nota:** in una situazione realistica, dovresti creare molte altre annotazioni e completare tutti i documenti nella serie prima di inviarli.

1. Chiudi questa serie di annotazioni e poi apri l'altra serie di annotazioni nell'attività `Test`.

   A seconda di come configuri le attività di annotazione e di quali utenti assegni loro, potresti dover accedere a {{site.data.keyword.knowledgestudioshort}} come l'utente assegnato all'altra serie di annotazioni nell'attività di annotazione.

1. Ripeti le stesse annotazioni nel documento *Technology - gmanews.tv*, ma questa volta, utilizza la relazione `employedBy` invece di `founderOf`.

  Accedere come un altro utente permetterà di illustrare l'accordo tra annotatori nella prossima lezione. Ma se hai un solo utente, puoi ancora completare l'esercitazione per comprendere il funzionamento dell'accordo tra annotatori.

1. Dopo aver completato le annotazioni per la seconda serie di annotazioni, fai clic su **Submit All Documents**.

## Lezione 6: Analisi dell'accordo tra annotatori
{: #wks_tutless_ml6}

In questa lezione, apprenderai come confrontare il lavoro di più annotatori umani in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml6_about}

Per determinare se diversi annotatori umani stanno annotando i documenti di sovrapposizione in modo coerente, controlla i punteggi dell'*accordo tra annotatori* (IAA).

{{site.data.keyword.knowledgestudioshort}} calcola i punteggi IAA esaminando tutti i documenti di sovrapposizione in tutte le serie nell'attività, indipendentemente dallo stato delle serie di documenti. I punteggi IAA mostrano quanto differentemente gli annotatori umani annotano le citazioni, le relazioni e le catene di coreferenza. È una buona idea controllare i punteggi IAA periodicamente e verificare che gli annotatori umani siano coerenti tra loro.

In questa esercitazione, gli annotatori umani hanno inviato tutte le serie di documenti per l'approvazione. Se i punteggi dell'accordo tra annotatori sono accettabili, puoi approvare le serie di documenti. Se rifiuti una serie di documenti, viene restituita all'annotatore umano per un miglioramento.

Per ulteriori informazioni sull'accordo tra gli annotatori, consulta [Creazione di ground truth](/docs/services/watson-knowledge-studio/build-groundtruth.html).

### Procedura
{: #wks_tutless_ml6_procedure}

1. Accedi a {{site.data.keyword.knowledgestudioshort}} come amministratore, seleziona **Machine Learning Model** > **Annotation Tasks** e fai clic sull'attività `Test`.

  Nella colonna **Status**, puoi visualizzare le serie di documenti che sono state inviate.

1. Fai clic su **Calculate Inter-Annotator Agreement**.
1. Visualizza i punteggi IAA per la citazione, le relazioni e le catene di coreferenza facendo clic sul primo menu. Puoi anche visualizzare l'accordo tra una coppia di annotatori umani. Puoi anche visualizzare l'accordo tra documenti specifici. In generale, mira a un punteggio compreso tra .8 e 1, dove 1 indica l'accordo perfetto. Poiché hai annotato solo due tipi di entità in questa esercitazione, la maggior parte dei punteggi del tipo di entità sono `N/A` (non applicabile), che significa che non è disponibile alcuna informazione per fornire un punteggio.

    *Figura 1. Controllo dei punteggi tra annotatori degli utenti `dave` e `phil`*

    ![Questa schermata illustra i punteggi tra annotatori di un'attività.](images/wks_tutiaa2.gif "Questa schermata illustra i punteggi tra annotatori di un'attività.")

1. Dopo aver controllato i punteggi, puoi decidere se vuoi approvare o rifiutare le serie di documenti che sono nello stato `SUBMITTED`. Effettua una delle seguenti operazioni:

    - Se i punteggi sono accettabili per una serie di annotazioni, seleziona la casella di spunta e fai clic su **Accept**. I documenti che non si sovrappongono ad altre serie di documenti sono promossi a ground truth. I documenti che si sovrappongono devono prima essere revisionati tramite la decisione in modo che possano essere risolti i conflitti. Per questa esercitazione, accetta entrambe le serie di documenti.
    - Se i punteggi non sono accettabili per una serie di annotazioni, seleziona la casella di spunta e fai clic su **Reject**. La serie di documenti deve essere ricontrollata dall'annotatore umano per migliorare le annotazioni.

### Risultati
{: #wks_tutless_ml6_results}

Quando hai valutato i punteggi di accordo tra annotatori, hai visto come coppie di annotatori umani diversi annotano lo stesso documento. Se il punteggio di accordo tra annotatori era accettabile, hai accettato la serie documenti.

## Lezione 7: Giudicare i conflitti nei documenti annotati.
{: #wks_tutless_ml7}

In questa lezione, apprenderai come giudicare i conflitti nei documenti che si sovrappongono tra le serie di documenti in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml7_about}

Quando approvi una serie di documenti, solo i documenti che non si sovrappongono ad altre serie di documenti sono promossi a ground truth. Se un documento fa parte della sovrapposizione di più serie di documenti, devi giudicare tutti i conflitti di annotazione prima che il documento possa essere promosso a ground truth.

Per ulteriori informazioni sul giudizio, consulta [Creazione di ground truth](/docs/services/watson-knowledge-studio/build-groundtruth.html).

### Procedura
{: #wks_tutless_ml7_procedure}

1. Accedi a {{site.data.keyword.knowledgestudioshort}} come amministratore, seleziona **Machine Learning Model** > **Annotation Tasks** e fai clic sull'attività `Test`.
1. Verifica che le due serie di documenti siano nello stato approvato.
1. Fai clic su **Check Overlapping Documents for Conflicts**.

    Puoi visualizzare i documenti di sovrapposizione che sono stati annotati da più di un annotatore umano.

1. Poiché l'esercitazione ti ha indicato di creare una relazione in conflitto per il documento *Technology - gmanews.tv*, trova tale documento nell'elenco e fai clic su **Check for Conflicts**.
1. Seleziona le due serie di annotazioni in conflitto e fai clic su **Check for Conflicts**.

    Viene aperta la modalità di giudizio. Nella modalità di giudizio, puoi visualizzare i documenti di sovrapposizione, controllare i conflitti e rimuovere o sostituire le annotazioni prima di promuovere i documenti a ground truth.

1. Seleziona **Relation conflicts**, accetta la relazione `founderOf` e rifiuta `employedBy`.
1. Fai clic su **Promote to Ground Truth**.

    In alternativa, puoi promuovere un documento a ground truth facendo clic su **Accept** nella pagina Documents.

### Risultati
{: #wks_tutless_ml7_results}

Dopo aver risolto i conflitti di annotazione e promosso i documenti a ground truth, puoi utilizzarli per preparare il modello di machine learning.

## Lezione 8: Creazione di un modello di machine learning
{: #wks_tutless_ml8}

In questa lezione, apprenderai come creare un modello di machine learning in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless_ml8_about}

Quando crei un modello di machine learning, selezioni le serie di documenti che vuoi utilizzare per prepararlo. Specifichi inoltre la percentuale di documenti che devono essere utilizzati come dati di preparazione, di test e senza indicazioni. Solo i documenti che sono diventati ground truth tramite l'approvazione o il giudizio possono essere utilizzati per preparare il modello di machine learning.

Per ulteriori informazioni sul modello di machine learning, consulta [Preparazione del modello di machine learning](/docs/services/watson-knowledge-studio/train-ml.html) e [Analisi delle prestazioni del modello di machine learning](/docs/services/watson-knowledge-studio/evaluate-ml.html).

### Procedura
{: #wks_tutless_ml8_procedure}

1. Accedi a {{site.data.keyword.knowledgestudioshort}} come amministratore.
1. Fai clic su **Machine Learning Model** > **Performance** > **Train and evaluate**.
2. Seleziona **All** e poi fai clic su **Train & Evaluate**.

    > **Nota:** la preparazione può durare più di dieci minuti o anche ore, a seconda del numero di annotazioni umane e il numero di parole in tutti i documenti.

3. Dopo che il modello di machine learning è stato preparato, puoi esportarlo nella pagina Version o puoi visualizzare le informazioni dettagliate sulle sue prestazioni facendo clic sui link **Detailed Statistics** ubicati sopra ognuno dei grafici nella pagina Performance.
4. Per visualizzare la pagina Training / Test / Blind Sets, fai clic sul pulsante **Train and evaluate**.
5. Per visualizzare i documenti sui cui hanno lavorato gli annotatori umani, fai clic su **View Ground Truth**.
6. Per visualizzare le annotazioni create dal modello di machine learning preparato sulla stessa serie di documenti, fai clic su **View Decoding Results**.
7. Per visualizzare i dettagli sui punteggi di precisione, richiamo e F1 del modello di machine learning, fai clic sulla pagina Performance.
8. Fai clic sui link **Detailed Statistics** sopra ognuno dei grafici. In queste pagine delle statistiche, puoi visualizzare i punteggi delle citazioni, relazioni e catene di coreferenza utilizzando i pulsanti di opzione.

    Puoi analizzare le prestazioni visualizzando un riepilogo delle statistiche dei tipi di entità, dei tipi di relazione e delle catene di coreferenza. Puoi inoltre analizzare le statistiche presentate in una *matrice di confusione*. Per visualizzare la matrice, modifica **Summary** con **Confusion Matrix**. La matrice di confusione ti aiuta a confrontare le annotazioni che sono state aggiunte dal modello di machine learning alle annotazioni nel ground truth.

    > **Nota:** in questa esercitazione, hai annotato i documenti con un solo dizionario delle organizzazioni. Pertanto, i punteggi che vedi sono `0` o `N/A` per la maggior parte dei tipi di entità tranne per `ORGANIZATION`. I numeri sono bassi, ma è previsto, perché non hai apportato alcuna annotazione e correzione umana.

    *Figura 2. Opzioni nella pagina Statistics di un modello di machine learning*

    ![Questa schermata mostra la pagina Statistics.](images/wks_tutanno9.gif "Questa schermata mostra la pagina Statistics.")

9.  Fai clic su **Versions**. Nella pagina Versions, puoi prendere un'istantanea del modello e delle risorse che sono state utilizzate per crearlo (tranne i dizionari e le attività di annotazione). Ad esempio, potresti voler prendere un'istantanea prima di riaggiornare il modello. Se le statistiche sono basse, la prossima volta che lo prepari, puoi promuovere la precedente versione e eliminare quella che ti ha restituito risultati più bassi.

### Risultati
{: #wks_tutless_ml8_results}

Hai creato un modello di machine learning, lo hai preparato e hai valutato quanto bene viene eseguito quando annoti i dati di test e senza indicazioni. Esplorando le metriche delle prestazioni, puoi identificare i modi per migliorare l'accuratezza del modello di machine learning.

## Riepilogo esercitazione
{: #wks_tutml_sum}

Hai creato un modello di machine learning.

### Lezione imparate
{: #lessons_learned}

Completando questa esercitazione, hai imparato i seguenti concetti:

- Serie di documenti
- Modelli di machine learning
- Attività di annotazione umana
- Giudizio e accordo tra annotatori
