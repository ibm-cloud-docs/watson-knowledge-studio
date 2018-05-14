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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/glossary.html){: new_window}.
{: tip}

# Glossario
{: #glossary}

Questo glossario contiene i termini e le definizioni relativi a {{site.data.keyword.knowledgestudioshort}}.
{: shortdesc}

In questo glossario vengono utilizzati i seguenti riferimenti incrociati:

- Consulta, associa un termine ad un sinonimo preferito oppure un acronimo o un'abbreviazione a una forma completa definita. 
- Consulta anche, rinvia l'utente ad un termine correlato o contrario. 

Per visualizzare i glossari di altri prodotti {{site.data.keyword.IBM}}, vai a [www.ibm.com/software/globalization/terminology ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/software/globalization/terminology/){: new_window}.

[A](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) [B](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [D](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) [E](/docs/services/watson-knowledge-studio/glossary.html#gloss_E) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [H](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) [I](/docs/services/watson-knowledge-studio/glossary.html#gloss_I) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [N](/docs/services/watson-knowledge-studio/glossary.html#gloss_N) [O](/docs/services/watson-knowledge-studio/glossary.html#gloss_O) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)

## A
{: #gloss_A}

- **accuratezza**

    Una misura della correttezza delle annotazioni prodotte da un modello di machine learning. Consulta anche [precisione](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) e [richiamo](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **analisi dell'accuratezza**

    Analizza i punteggi del modello di machine learning per determinare se sono necessarie delle modifiche per migliorare l'accuratezza.

- **giudizio**

    Un processo iterativo per risolvere i conflitti di annotazione confrontando le annotazioni aggiunte allo stesso documento da diversi annotatori umani.

- **motore di analisi**

    Un programma che analizza le risorse, come i documenti, ne deduce le informazioni e che implementa la specifica dell'interfaccia del motore di analisi UIMA. I motori di analisi sono creati da elementi fondamentali chiamati annotatori. Un motore di analisi può contenere un solo annotatore, a cui si fa riferimento come a un motore di analisi primitivo o più annotatori, a cui si fa riferimento come a un motore di analisi aggregato.

- **annotazione**

    Le informazioni su una parte di testo. Ad esempio, un'annotazione potrebbe indicare che una parte di testo rappresenta un nome aziendale.

- **serie di annotazioni**

    Nell'annotazione umana, una raccolta di documenti che viene estratta da un corpus che consente al carico di lavoro di essere condiviso tra più annotatori umani. Nell'annotazione automatica, una raccolta di documenti che può essere utilizzata come dati senza indicazioni, di preparazione o di test.

- **gestore del processo di annotazione**

    Un ruolo che è responsabile della gestione di tutte le attività del ciclo di vita dell'annotazione all'interno di uno spazio di lavoro. Il gestore del progetto che viene aggiunto a uno spazio di lavoro normalmente esegue le attività di un gestore del processo di annotazione.

- **annotatore**

    Consulta [annotatore umano](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) e [annotatore machine learning](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **attributo**

    Una caratteristica o un tratto di un'entità che descrive l'entità stessa, ad esempio il numero di telefono di un impiegato è uno degli attributi dell'impiegato. 

## B
{: #gloss_B}

- **dati senza indicazioni**

    Una serie di documenti annotati con ground truth, come coppie di domanda e risposta, annotazione semantica e giudizio del passaggio. I dati senza indicazioni non vengono mai rilasciati o visti dagli sviluppatori e sono utilizzati per verificare il sistema periodicamente per valutare le prestazioni dei dati non visti. La verifica sui dati senza indicazioni previene all'accuratezza di essere corrotta dall'eccessivo inserimento di annotazioni o serie di domande note. I risultati riportati dovrebbero provenire solo dai test che vengono eseguiti sui dati senza indicazioni. Consulta anche [dati di test](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) e [dati di preparazione](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

## C
{: #gloss_C}

- **concordanza**

    Fornisce un modo di verificare che la stessa citazione sia annotata con lo stesso tipo di entità in un documento e tra le serie di annotazioni. La concordanza aiuta ad assicurare la coerenza tra più ricorrenze di una citazione senza richiedere all'annotatore umano di etichettare manualmente ogni ricorrenza.

- **matrice di confusione**

    Una tabella che fornisce una suddivisione numerica dettagliata di serie di documenti annotate. La tabella viene utilizzata per confrontare le annotazioni che sono state aggiunte da un modello di machine learning e quelle ground truth. La tabella riporta il numero di [falsi positivi](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [falsi negativi](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [veri positivi](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) e [veri negativi](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **coreferenza**

    Una relazione tra due parole o frasi che fanno entrambe riferimento alla stessa persona o cosa e una si posiziona come un antecedente linguistico dell'altra. Ad esempio, esiste una coreferenza tra due pronomi nella frase "She taught herself" ma non in "She taught her". Una coreferenza collega due entità equivalenti nello stesso testo.

- **catena di coreferenza**

    Un elenco di entità che sono state annotate come coreferenze. Quando annoti le citazioni come coreferenze, il sistema crea una catena di coreferenza. La catena fornisce un modo per visualizzare tutte le citazioni nel contesto e di verificare che tutte le ricorrenze  appartengano allo stesso tipo di entità.

- **corpus**

    Una raccolta di documenti di origine che sono stati aggiunti a uno spazio di lavoro e utilizzati per preparare un modello di machine learning.

- **conservazione**

    Per selezionare, raccogliere, conservare e mantenere il contenuto rilevante per un argomento specifico. La conservazione stabilisce, mantiene e aggiunge valore ai dati; li trasforma in informazioni attendibili. 

## D
{: #gloss_D}

- **dizionario**

    Una raccolta di parole che può essere utilizzata per pre-annotare i documenti. Viene creata una nuova annotazione per ogni parola nel testo del documento che corrisponde a un termine nel dizionario. Un modello di machine learning può essere configurato con uno o più dizionari indipendenti, che sono normalmente specifici del dominio, come un dizionario per i prodotti farmaceutici e uno per l'amministrazione patrimoniale. Consulta anche [lemma](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) e [formato di superficie](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

- **pre-annotatore del dizionario**

    Un componente che identifica le citazioni nel testo che corrispondono a una serie di parole specifica. Utilizzando la terminologia specifica del dominio per pre-annotare il testo, i pre-annotatori del dizionario possono accelerare la capacità di un annotatore umano di preparare una serie di documenti ground truth.

- **serie di documenti**

    Una raccolta di documenti. I documenti che vengono importati insieme diventano una serie di documenti. I documenti annotati che vengono raggruppati insieme per scopi di preparazione (test, preparazione, senza indicazioni) vengono generati come serie di documenti.

## E
{: #gloss_E}

- **entità**

    1. Una citazione che viene annotata da un tipo di entità.
    1. Una persona, un oggetto o un concetto su cui sono state archiviate delle informazioni.
    1. Una serie di dettagli che vengono conservati su un oggetto reale come una persona, un luogo o un conto bancario. Un'entità è un tipo di elemento.

- **tipo di entità**

    Il tipo di entità che una citazione rappresenta senza considerare il contesto. Ad esempio, la citazione {{site.data.keyword.IBM_notm}} potrebbe essere annotata dal tipo di entità ORGANIZATION.

    In un modello di relazione e entità, un tipo di entità è la cosa che sta venendo creata a cui fa riferimento una citazione, come ad esempio il nome di una persona o di un luogo. Diversi tipi di entità hanno diverse serie di attributi come "surname" o "home town" e sono collegati tramite le relazioni come "lives in". Un tipo di entità esiste in modo indipendente e può essere identificato in modo univoco.

## F
{: #gloss_F}

- **Punteggio F1**

    Una misura che considera sia la precisione che il richiamo per calcolare il punteggio. Il punteggio F1 può essere interpretato come una media ponderata dei valori di precisione e richiamo. Un punteggio F1 raggiunge il suo migliore valore con 1 e il peggiore con 0. 

- **falso negativo**

    Una risposta o un'annotazione corretta ma che era previsto non lo fosse.

- **falso positivo**

    Una risposta o un'annotazione non corretta ma che era previsto lo fosse.

- **funzione**

    Un attributo o un membro di dati di un tipo.

- **punteggio Fleiss Kappa**

    Una misura di quanto coerentemente la stessa annotazione è stata applicata da più annotatori umani tra i documenti di sovrapposizione. Il punteggio Fleiss Kappa raggiunge il suo migliore valore con 1 e il peggiore con 0.

## G
{: #gloss_G}

- **ground truth**

    Una serie di dati controllati, composta da annotazioni aggiunte dagli annotatori umani, che viene utilizzata per adattare un modello di machine learning a un dominio particolare. Ground truth viene utilizzato per preparare i modelli di machine learning, misurare le prestazioni del modello (precisione e richiamo) e calcolare la capacità per decidere dove concentrare il lavoro di sviluppo per migliorare le prestazioni. L'accuratezza di ground truth è essenziale poiché le imprecisioni nel ground truth si collegheranno a quelle nei componenti che lo utilizzano.

## H
{: #gloss_H}

- **analisi della capacità**

    Il processo di determinazione di quanti miglioramenti nell'accuratezza, precisione o richiamo possono essere previsti risolvendo alcune classi di problemi che sono stati identificati durante l'analisi dell'accuratezza.

- **annotatore umano**

    Un esperto in materia che controlla, modifica e incrementa i risultati della pre-annotazione identificando citazioni, relazioni di tipo di entità e coreferenze della citazione. Esaminando il testo nel contesto, un annotatore umano aiuta a determinare il ground truth e migliora l'accuratezza del modello di machine learning.

## I
{: #gloss_I}

- **accordo tra annotatori**

    Una misura di quanto analogamente viene annotato un documento in due o più serie di documenti.

## K
{: #gloss_K}

- **grafo della conoscenza**

    Un modello che consolida le entità immesse, le rispettive relazioni e proprietà e le tassonomie cronologiche per rappresentare un'organizzazione di concetti di un determinato dominio. Dopo che il negozio del grafo della conoscenza viene caricato con gli input dalle origini di dati strutturate e non strutturare, gli utenti e le applicazioni possono accedere al grafo della conoscenza per esplorare gli elementi chiave di conoscenza di un dominio specifico, esplorare le interazioni e rilevare ulteriori relazioni.

## L
{: #gloss_L}

- **lemma**

    Il formato di una parola canonico o normalizzato. Normalmente, il lemma è un formato originale e non derivato di un nome o un verbo. Ad esempio, il lemma dei termini 'organizing' e 'organized' è 'organize'. Consulta anche [dizionario](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) e [formato di superficie](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

## M
{: #gloss_M}

- **machine learning**

    Un metodo di analisi dei dati che iterattivamente impara dai dati passati e si adatta in modo indipendente quando esposto a nuovi dati. Il modello matematico al centro di machine learning viene creato dagli input ground truth. Tramite la preparazione e la rifinitura dei dati di input di esempio, il modello può fornire risultati accurati e ripetibili quando analizza dei nuovi dati.

- **annotatore machine learning**

    Consulta [modello di machine learning](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **modello di machine learning**

    Un componente che identifica le entità e le relazioni tra entità in base a un modello statistico basato su ground truth. Il modello applica le esperienze passate, come i dati di preparazione, per determinare o predire il risultato corretto di esperienze future in base a caratteristiche di dati. Queste esperienze passate vengono acquisite nel formato di un modello calcolando i punteggi della funzione di ogni controllo o risposta canditati e li combina con i risultati conosciuti. A volte indicato come *annotatore machine learning*.

- **citazione**

    Una parte di testo che consideri rilevante nei tuoi dati del dominio. Ad esempio, in un sistema tipo di veicoli automobilistici, le ricorrenze dei termini "airbag", "Ford Explorer" e "child restraint system" potrebbero essere citazioni importanti.

## N
{: #gloss_N}

- **entità denominata**

    Un concetto in un dominio che rientra in una categoria ben definita, come i nomi delle organizzazioni, ubicazioni, autori o malattie.

- **elaborazione del linguaggio naturale**

    Un campo di intelligenza artificiale e linguistica che studia i problemi inerenti all'elaborazione e alla manipolazione del linguaggio naturale, con l'obiettivo di incrementare l'abilità dei computer di comprendere i linguaggi umani.

## O
{: #gloss_O}

- **ontologia**

    Una specifica formale esplicita della rappresentazione di oggetti, concetti e altre entità presenti in determinate aree di interesse con le relative relazioni. 

## P
{: #gloss_P}

- **parte del discorso (POS)**

    In un dizionario, oggetti lemma individuali vengono assegnati a tag di parti del discorso (POS). Ad esempio, la parola 'fly' può essere identificata come un verbo o un nome.

- **prestazioni**

    La misurazione di un sistema {{site.data.keyword.watson}} in termini di accuratezza, precisione e richiamo, ad esempio, quando rispondi alle domane, rilevi le relazioni o annoti il testo.

- **pre-annotazione**

    Il processo di annotazione di una serie di documenti prima dell'annotazione umana. I documenti possono essere pre-annotati utilizzando un modello basato sulla regola, un modello di machine-learning, {{site.data.keyword.nlufull}} o un dizionario. La pre-annotazione può aiutare gli annotatori umani a preparare più velocemente una serie di documenti ground truth.

- **precisione**

    Una misurazione che specifica la proporzione dei risultati che sono rilevanti. La precisione, che è un valore predittivo positivo, viene determinata dal numero di risultati positivi corretti diviso il numero di tutti i risultati positivi. L'accuratezza viene meglio misurata utilizzando sia la precisione che il richiamo. Consulta anche [accuratezza](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) e [richiamo](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **processing engine archive (PEAR)**

    Un file di archiviazione `.pear` che include un motore di analisi Unstructured Information Management Architecture (UIMA) e tutte le risorse necessarie per utilizzarlo per l'analisi personalizzata.

## R
{: #gloss_R}

- **richiamo**

    Una misurazione che specifica la percentuale di risultati importanti riportati, rispetto a tutti i risultati importanti disponibili. Il richiamo, che è una misurazione della sensibilità, viene determinato dal numero di risultati positivi corretti diviso il numero di risultati positivi che dovrebbero essere restituiti. L'accuratezza viene meglio misurata utilizzando sia la precisione che il richiamo. Consulta anche [accuratezza](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) e [precisione](/docs/services/watson-knowledge-studio/glossary.html#gloss_P).

- **relazione**

    Normalmente un verbo che riflette come le entità sono correlate tra loro. Ad esempio, "lives in" è una relazione tra una città e una persona. Una relazione collega due differenti entità nella stessa frase.

- **tipo di relazione**

    Una relazione binaria e unidirezionale tra due entità. Ad esempio, Mary employedBy {{site.data.keyword.IBM_notm}} è una relazione valida; {{site.data.keyword.IBM_notm}} employedBy Mary non lo è.

- **ruolo**

    Un attributo che fornisce un significato sensibile al contesto di una citazione. Ad esempio, nella frase "I went to {{site.data.keyword.IBM_notm}} today", {{site.data.keyword.IBM_notm}} è la citazione, Organization è il tipo di entità e Facility è il ruolo del tipo di entità.

- **serie di regole**

    Una serie di regole che definisce i modelli per l'annotazione del testo. Se un modello viene applicato, le azioni della regola sono eseguite nelle annotazioni corrispondenti. Una regola normalmente specifica la condizione che deve corrispondere, un quantificatore facoltativo, un elenco di ulteriori vincoli che deve rispettare il testo di corrispondenza e le azioni da eseguire quando si verifica una corrispondenza, come la creazione di una nuova annotazione o la modifica di una esistente.

## S
{: #gloss_S}

- **sottotipo**

    Un tipo che estende o implementa un altro tipo; il supertipo.

- **formato di superficie**

    Il formato di una parola o un'unità di più parole che viene trovato nel corpus. Ad esempio, alcuni formati di superficie del lemma 'organize' sono i termini 'organizing' e 'organized'. Consulta anche [dizionario](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) e [lemma](/docs/services/watson-knowledge-studio/glossary.html#gloss_L).

## T
{: #gloss_T}

- **dati di test**

    Una serie di documenti annotati che può essere utilizzata per valutare le metriche del sistema dopo l'inserimento e la preparazione. Consulta anche [dati senza indicazioni](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) e [dati di preparazione](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **preparazione**

    Il processo di configurazione di un'istanza di {{site.data.keyword.watson}} con i componenti che abilitano il sistema a funzionare in un dominio particolare (ad esempio: il contenuto del corpus, i dati di preparazione che generano i modelli di machine learning, gli algoritmi programmatici, gli annotatori o altri componenti ground truth) e poi effettua miglioramenti e aggiornamenti di questi componenti in base all'analisi dell'accuratezza.

- **dati di preparazione**

    Una serie di documenti annotati che può essere utilizzata per preparare gli annotatori machine learning. Consulta anche [dati senza indicazioni](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) e [dati di test](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **vero negativo**

    Una risposta o un'annotazione che al momento non è corretta e che era previsto non lo fosse. 

- **vero positivo**

    Una risposta o un'annotazione che al momento è corretta e che era previsto lo fosse. 

- **sistema tipo**

    Il sistema tipo definisce i tipi di oggetti che possono essere rilevati in un documento. Il sistema tipo definisce tutti i tipi di entità e le relazioni possibili tra i tipi di entità. Puoi definire un qualsiasi numero di tipi differenti in un sistema tipo. I sistemi tipi sono generalmente specifici del dominio e dell'applicazione.
