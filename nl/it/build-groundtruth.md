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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/build-groundtruth.html){: new_window}.
{: tip}

# Creazione di ground truth
{: #build-groundtruth}

L'obiettivo del progetto di annotazione è di ottenere il ground truth, la raccolta di dati controllati che viene utilizzata per adattare {{site.data.keyword.watson}} a un dominio particolare. In {{site.data.keyword.knowledgestudioshort}}, gli annotatori umani, che sono normalmente esperti nella materia del dominio di destinazione, hanno un ruolo importante nella determinazione del ground truth.
{: shortdesc}

Un flusso di lavoro tipico include i seguenti passi:

1. Gli annotatori umani inviano i documenti annotati per la revisione.
1. Il gestore del progetto (che potrebbe essere un esperto di alto livello del dominio) controlla l'accuratezza del loro lavoro e confronta la congruenza di come gli annotatori umani hanno annotato i documenti che si sovrappongono tra le serie di annotazioni.
1. Se il punteggio di accordo tra annotatori è troppo basso, il gestore del progetto respinge la serie di annotazioni e la restituisce all'annotatore umano in modo che venga migliorata. Quando una serie di annotazioni viene rifiutata, tutti i documenti nella serie vengono riportati alla modalità modificabile.
1. Se il gestore del progetto approva una serie di annotazioni, i documenti che non si sovrappongono tra le serie di annotazioni vengono promossi a ground truth in modo che le annotazioni possano essere utilizzate per preparare il modello.
1. Il gestore del progetto controlla i documenti di sovrapposizione e risolve i conflitti di annotazione. In questa fase, a cui fare riferimento come decisione, il team potrebbe controllare e rivedere le linee guida di annotazione per aiutare a chiarire i fraintendimenti che hanno portato che il testo sia incorretto o incongruente da parte di diversi annotatori umani.

    In alcuni casi, un gestore del progetto potrebbe volere una percentuale maggiore di sovrapposizione per la valutazione dell'accordo tra annotatori rispetto a quella della decisione delle differenze. Ad esempio, se l'accordo tra annotatori sembra OK, il gestore del progetto potrebbe decidere che è OK e promuovere una annotazione a ground truth.

1. Come il gestore del progetto risolve i conflitti di annotazione, le annotazioni approvate sono promosse a ground truth. 

Tieni presente che l'annotazione umana richiede sempre dei giudizi. Le linee guida di annotazione possono fare molto per garantire che il testo venga annotato in modo corretto e congruente, ma anche le migliori linee guida sono aperte all'interpretazione umana. Per ottenere il ground truth, dovrai investire del tempo nella preparazione degli annotatori umani in modo che possano fare le valutazioni migliori quando analizzano il contenuto del dominio.

## Accordo tra annotatori
{: #wks_haiaa}

Dopo che gli annotatori umani hanno annotato i documenti, devi determinare quali documenti promuovere a ground truth. Inizia controllando i punteggi dell'accordo tra annotatori. I documenti con punteggi bassi sono candidati ad essere rifiutati e restituiti all'annotatore umano per un miglioramento.

Quando calcola i punteggi di accordo tra annotatori, il sistema esamina tutti i documenti di sovrapposizione in tutte le serie di annotazioni nell'attività, indipendentemente dallo stato delle serie. Poiché non puoi accettare o rifiutare le serie di annotazioni finché non sono nello stato Submitted, potresti voler valutare l'accordo tra annotatori finché non vengono inviate tutte le serie di annotazioni o di limitare il tuo controllo solo agli annotatori umani che hanno inviato le loro serie di annotazioni complete.

I punteggi dell'accordo tra annotatori mostrano quanto differentemente gli annotatori umani annotano le citazioni, le relazioni e le catene di coreferenza. Puoi vedere i punteggi confrontando una coppia di annotatori umani (ad esempio, confronta tutte le annotazioni della citazione di John con quelle di Mary). Puoi anche vedere i punteggi confrontando documenti specifici (ad esempio, confronta le annotazioni di relazione fatte da John in un documento con quelle di Mary nello stesso documento).

Per aiutarti a identificare le aree che richiedono un controllo, i punteggi che sono sotto il valore che hai specificato per la soglia dell'accordo tra annotatori sono evidenziati in rosso. Nelle prime fasi del tuo progetto di annotazione, potresti trovare che i punteggi di relazione sono spesso peggiori rispetto a quelli della citazione perché un'annotazione di relazione perfetta richiede che siano prima in accordo le citazioni che definiscono la relazione.

Il punteggio nella colonna **All** è un *punteggio Fleiss Kappa*. Rappresenta quanto coerentemente la stessa annotazione è stata applicata da più annotatori umani tra i documenti di sovrapposizione nell'attività. Il valore, che è compreso nell'intervallo fino a 1 ma può anche essere negativo, può aiutarti a identificare i punti deboli nelle linee guida di annotazione o di annotatori umani particolari. Le seguenti linee guida (*Landis e Koch, 1977*) forniscono un punto di partenza per valutare le prestazioni generali:

<table cellpadding="4" cellspacing="0" summary="" id="wks_haiaa__table_p5s_dx1_f5" class="table" rules="rows" frame="void" border="0"><thead class="thead" align="left"><tr class="row"><th class="entry ncol thleft" align="left" valign="top" id="d12741e148">Punteggio</th>
<th class="entry ncol thleft" align="left" valign="top" id="d12741e150">Livello d'accordo</th>
</tr>
</thead>
<tbody class="tbody"><tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">&lt; 0</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Scarso</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.01 - .20</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Leggero</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.21 - .40</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Discreto</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.41 - .60</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Moderato</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.61 - .80</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Considerevole </p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.81 - 1.0</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Perfetto</p></td>
</tr>
</tbody>
</table>

Il punteggio nelle altre colonne è una *misurazione F1*. Rappresenta la coerenza dell'annotazione tra una coppia di annotatori umani. Il valore può essere compreso nell'intervallo tra 0 e 1, dove l'accordo perfetto viene indicato da 1. Cosa costituisce un livello accettabile di accordo dipende dai tuoi dati del dominio e sistema tipo. Ma per fornire un esempio, queste sono le soglie F1 che i gestori del progetto si aspettano di rispettare o superare nei progetti che si basano sul sistema tipo KLUE.

- Citazioni con tipi di entità: 0.85
- Relazioni: 0.8
- Catene di coreferenza: 0.9

L'interpretazione dei punteggi dipende dalla complessità del tuo sistema tipo, la quantità e complessità del contenuto annotato, quanto sono esperti gli annotatori umani e altri fattori. Ad esempio, se l'attività di annotazione si concentra sulle parti etichettate del discorso, potresti aspettarti di visualizzare un punteggio più alto in base a quanto sono ben definite le parti del discorso. Ma un'attività che richiede un'analisi più approfondita del testo, dove è necessaria l'interpretazione umana, potrebbe mostrare punteggi più bassi finché non fai qualcosa per chiarire le cause dell'ambiguità.

Generalmente, un sistema tipo che include molti tipi di entità e relazione è aperto a maggiore interpretazione, quindi l'accordo tra annotatori potrebbe essere più basso durante le prime fasi di sviluppo del modello. Guardando i punteggi, puoi vedere quali tipi di entità, ad esempio, hanno punteggi bassi. Questi punteggi bassi sono un'indicazione che le linee guida di annotazione devono essere migliorate. Guardando i punteggi tra le coppie di annotatori umani, puoi identificare se un annotatore particolare mostra costantemente punteggi più bassi di altri. Questo annotatore potrebbe avere problemi di comprensione delle linee guida o sull'utilizzo degli strumenti di annotazione e quindi essere un candidato a una ulteriore preparazione.

## Controllo dei punteggi dell'accordo tra annotatori
{: #wks_haaccuracy}

Quando determini quali documenti devono essere promossi a ground truth, devi controllare i punteggi dell'accordo tra annotatori. I documenti con i punteggi bassi sono candidati per essere rifiutati e restituiti all'annotatore umano per un miglioramento.

### Informazioni su quest'attività

Quando esamini l'accordo tra annotatori, esamini i documenti che sono stati annotati da più di un annotatore umano. Se un documento non è condiviso tra più serie di annotazioni e annotatori umani, non c'è un accordo tra annotatori da calcolare. Quando aggiungi le serie di annotazioni a un'attività, assicurati che le serie che vuoi confrontare contengano gli stessi documenti di sovrapposizione. Puoi vedere quali documenti sono in una serie di annotazioni aprendo la pagina **Assets & Tools** > **Documents**, facendo clic sulla scheda **Annotation Sets** e poi sui nomi delle serie.

Potresti riscontrare situazioni in cui non si trovano dei documenti di sovrapposizione. Questo potrebbe succedere, ad esempio, se crei le serie di annotazioni in due round e le aggiungi alla stessa attività. Anche se le serie di annotazioni sono state create circa nello stesso momento, non hanno alcun documento in comune. Un altro esempio, se crei le serie di annotazioni con i documenti di sovrapposizione, ma aggiungi una serie di annotazioni per attività invece di aggiungerle tutte a una sola attività, non saranno trovati i documenti di sovrapposizione e l'accordo tra annotatori non può essere calcolato.

### Procedura

Per valutare l'accordo di annotazione tra annotatori umani:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro. 
1. Seleziona la scheda **Assets & Tools** > **Documents** > **Tasks** e apri l'attività che vuoi valutare.
1. Fai clic su **Calculate Inter-Annotator Agreement**. La vista predefinita mostra i punteggi di accordo per quanto coerentemente le coppie di annotatori umani hanno annotato le citazioni. La riga più in alto mostra la coerenza generale tra ogni coppia di annotatori e la tabella di seguito mostra quanto coerentemente una coppia ha etichettato citazioni specifiche nel testo.
1. Per esplorare quanto coerentemente le coppie di annotatori umani hanno annotato le relazioni e le coreferenze, seleziona **Relation** o **Coreference** dal primo menu.
1. Per esplorare quanto coerentemente una coppia di annotatori umani ha annotato le entità, le relazioni e le coreferenze in documenti di sovrapposizione specifici, seleziona **Document** nel secondo menu e poi seleziona la coppia di annotatori che vuoi valutare.
1. Dopo aver controllato i punteggi, puoi decidere se vuoi approvare o rifiutare le serie di annotazioni che sono nello stato Submitted. Dopo che una serie di annotazioni è stata inviata, viene visualizzata una casella di spunta accanto al suo nome. Effettua una delle seguenti operazioni:

    - Se i punteggi dell'accordo tra annotatori sono accettabili per una serie di annotazioni, seleziona la casella di spunta e fai clic su **Accept**. I documenti che non si sovrappongono ad altre serie di annotazioni sono promossi a ground truth. I documenti che si sovrappongono devono prima essere revisionati tramite la decisione in modo che possano essere risolti i conflitti.
    - Se i punteggi dell'accordo tra annotatori non sono accettabili per una serie di annotazioni, seleziona la casella di spunta e fai clic su **Reject**. La serie di annotazioni deve essere ricontrollata dall'annotatore umano per migliorare le annotazioni.

## Giudizio
{: #wks_haperform}

Se più annotatori umani lavorano allo stesso documento, avrai probabilmente bisogno di risolvere le incongruenze tra le annotazioni prima di promuoverle a ground truth. Questo processo di risoluzione dei conflitti è noto come giudizio. 

Quando approvi le serie di annotazioni inviate dagli annotatori umani, i documenti che non si sovrappongono tra le serie di annotazioni vengono promossi a ground truth. Prima di promuovere i documenti che si sovrappongono, dovresti controllare le annotazioni per i conflitti. Quando trovi istanze in disaccordo, devi decidere come risolvere il conflitto, selezionando l'annotazione corretta tra quelle applicate dagli annotatori umani o selezionando un'annotazione differente da applicare.

Un documento è disponibile per il giudizio quando almeno una delle seguenti condizioni è vera:

- Il gestore del progetto approva una o più serie di annotazioni in un'attività nello stesso momento e lo stesso documento è presente in almeno due serie di annotazioni (un documento di sovrapposizione).
- Il gestore del progetto approva un'altra serie di annotazioni prima che i documenti nelle precedenti serie di annotazioni approvate siano giudicati. Se giudichi positivamente un documento che si sovrappone tra le serie di annotazioni A e B, promuovi le annotazioni a ground truth e approvi un'altra serie di annotazioni C, che ha lo stesso documento, le annotazioni nel documento appena approvato sono promosse automaticamente a ground truth perché non esistono più conflitti. Tieni presente che le annotazioni promosse nella serie di annotazioni C sovrascrivono il ground truth stabilito quando i documenti di sovrapposizione nelle serie di annotazioni A e B sono stati decisi. Se approvi la serie di annotazioni C prima di promuovere le annotazioni in A e B, i documenti di sovrapposizione nella serie C possono essere controllati per i conflitti e giudicati.

La quantità di tempo che utilizzi nella decisione potrebbe essere minore se impieghi del tempo per migliorare le linee guida di annotazione. Fornendo gli esempi e chiarendo le aree che causano confusione, puoi aiutare gli annotatori umani a imparare dai loro errori e a prevenire conflitti futuri.

Questi sono alcuni esempi di vari modi di disaccordo degli annotatori umani:

- **Citazioni**

    - Annotator_1 prende una citazione su una parte di testo; Annotator_2 no.
    - L'indice di Annotator_1 inizia e finisce prima o dopo quello di Annotator_2 (c'è un sottocampo di testo o una sovrapposizione parziale).
    - Annotator_1 assegna un tipo di entità differente da quello assegnato da Annotator_2.

- **Relazioni**

    - Annotator_1 crea una relazione tra due citazioni; Annotator_2 no.
    - Annotator_1 e Annotator_2 creano una relazione tra le stesse citazioni ma con un tipo di relazione differente.
    - Annotator_1 e Annotator_2 creano una relazione tra le stesse citazioni ma in ordine inverso (raro, perché la relazione tra la prima citazione e la seconda è vincolata dal sistema tipo).

- **Catene di coreferenza**

    - La versione di Annotator_1 di una catena di coreferenza include (o esclude) le citazioni che sono escluse (o incluse) da Annotator_2. L'allineamento delle entità tra Annotator_1 e Annotator_2 diventa una questione di calcolo.

## Risoluzione dei conflitti di annotazione
{: #wks_haadjudicate}

Il giudizio è un passo che ti consente di rivedere i conflitti di annotazione nei documenti di sovrapposizione prima di promuovere le annotazioni a ground truth. Puoi confrontare le annotazioni aggiunte da una coppia di annotatori umani o confrontare le annotazioni umane al ground truth corrente.

### Prima di cominciare 

Fai clic su [questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.youtube.com/watch?v=EbexfsuXxoQ&amp;feature=youtu.be){: new_window} per guardare un video di 3 minuti che illustra come giudicare i documenti.

### Informazioni su quest'attività

Dopo che gli annotatori umani hanno completato le loro attività di annotazione, devono inviare le proprie serie di annotazioni complete per la revisione. Quando valuti i punteggi di accordo tra annotatori, puoi vedere come coppie di annotatori diverse annotano lo stesso documento. Se il punteggio di accordo tra annotatori è accettabile, approva la serie di annotazioni. Se un documento non si sovrappone tra le serie di annotazioni nell'attività, le annotazioni nel documento approvato vengono promosse a ground truth. Se un documento si sovrappone tra le serie di annotazioni, dovrai giudicare il documento e risolvere tutti i conflitti di annotazione presenti prima di promuovere le annotazioni a ground truth.

Ad esempio, quando giudichi un documento, potresti vedere che un annotatore ha annotato la citazione `Barack Obama` con il tipo di entità `PeoplePerson`. Un altro annotatore ha annotato la stessa stringa di testo con due citazioni, assegnando il tipo di entità `Person` a `Barack` e `Person` a `Obama`. Per garantire la corretta preparazione del modello di machine learning, dovresti risolvere questa incongruenza.

{{site.data.keyword.knowledgestudioshort}} supporta la capacità di giudicare tra due serie di annotazioni alla volta o tra una serie di annotazioni e il ground truth corrente. Se un documento si sovrappone tra più di due serie di annotazioni, giudica le due serie di annotazioni con cui hai più confidenza (forse perché hai una maggiore fiducia negli annotatori umani) per determinare il ground truth del documento. E giudica quindi il resto delle serie di annotazioni in base ai risultati del giudizio iniziale.

### Procedura

Per controllare i documenti di sovrapposizione e per risolvere i conflitti:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro. 
1. Seleziona la scheda **Assets & Tools** > **Documents** > **Tasks** e apri l'attività che vuoi valutare.
1. Conferma che almeno due serie di annotazioni siano nello stato **In conflict**.
1. Fai clic su **Check Overlapping Documents for Conflicts**. I documenti che sono in conflitto vengono elencati.
1. Se vuoi ignorare i conflitti in un documento di sovrapposizione e promuovere la annotazioni a ground truth senza giudicarle, fai clic su **Accept**.
1. Per iniziare a risolvere i conflitti in un documento di sovrapposizione, fai clic su **Check for Conflicts**.
1. Se ci sono tre o più candidati per il giudizio, includi le serie di annotazioni che sono state annotate tramite l'annotazione umana e il ground truth corrente, seleziona i due candidati che vuoi giudicare e fai clic su **Check for Conflicts**. Se esistono solo due candidati, lo strumento di decisione viene avviato automaticamente.

    Lo strumento di decisione mostra quanti conflitti di citazioni, relazioni e catene di coreferenza esistono. Devi risolvere i conflitti di citazione prima di passare ai conflitti tra le relazioni e le catene di coreferenza.

1. Fai clic per evidenziare una frase che contiene i conflitti. Per rendere più facile concentrarsi sui conflitti non risolti, potresti voler deselezionare la casella di spunta **Resolved** e assicurarti che **Unresolved** sia selezionata.
1. Fai clic sulle singole annotazioni e poi su **Accept** o **Reject**. Per annullare una decisione che hai preso, premi `Ctrl+Z`.

    Puoi anche fare clic su più di una annotazione e poi fare clic per accettare o rifiutare tutte le annotazioni selezionate. Se decidi che vuoi deselezionare un'annotazione, annulla le selezioni facendo clic su uno spazio vuoto tra le frasi o premendo il tasto **Esc**.

    Se le linee guida di annotazione sono state precedentemente collegate al progetto e vuoi avere aiuto nella scelta dell'annotazione corretta da applicare, fai clic su **View Guidelines**. A seconda delle autorizzazioni di accesso configurate nel sito in cui sono ospitate le linee guida, potresti doverle aggiornare dopo averle aperte, ad esempio, per aggiungere chiarimenti ed esempi.
    {: tip}

1. Per applicare un tipo di entità diverso a una citazione, rifiuta l'annotazione corrente, seleziona la citazione, come ad esempio `Barack Obama` e quindi seleziona il tipo di entità corretto, come `Person`.
1. Continua ad accettare, rifiutare e controllare gli altri conflitti nella frase. Dopo che hai risolto tutti i conflitti in una frase, fai clic sul link **Select all annotations** e poi su **Accept**.
1. Fai clic sull'icona freccia per passare alla frase successiva. Continua finché tutti i conflitti di citazione nel documento non sono stati risolti.

    Per salvare il tuo lavoro in corso o per interrompere temporaneamente la sessione di decisione corrente, fai clic su **Save** in qualsiasi momento. Se vuoi scartare tutte le modifiche fatte, fai clic su **Discard**. Se hai salvato la precedente sessione di decisione e sei pronto per riprendere, fai clic su **Resume** per giudicare i conflitti da dove ti eri fermato l'ultima volta. Se hai eliminato la precedente sessione di decisione, devi iniziarne una nuova.
    {: tip}

1. Dopo aver risolto i conflitti di citazione, passa alla modalità di decisione per risolvere tutti i conflitti che si verificano tra le annotazioni di relazione e di catena di coreferenza.

    - La risoluzione dei conflitti nella modalità di relazione è simile a come risolvi i conflitti per le citazioni. Risolvi i conflitti in una base frase per frase.
    - Le catene di coreferenza possono essere presenti tra più frasi. Quando ti sposti alla modalità di coreferenza, il sistema elenca le catene di coreferenza che sono state create da ogni annotatore umano in un pannello a destra. Seleziona le catene che vuoi giudicare e poi fai clic su **Reject Chain** o **Accept Chain** per rifiutare o accettare le annotazioni in una catena o fai clic su **Merge Chains** per unire le due catene. Se vuoi rimuovere la citazione da una catena di coreferenza, fai clic sull'icona di eliminazione (-) nell'etichetta sopra la citazione nell'area del documento.

1. Dopo che tutti i conflitti nel documento sono stati risolti, fai clic su **Promote to Ground Truth**.
