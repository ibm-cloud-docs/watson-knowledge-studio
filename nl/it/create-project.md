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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/create-project.html){: new_window}.
{: tip}

# Creazione di uno spazio di lavoro
{: #create-project}

Il primo passo nella creazione di un modello personalizzato è di creare uno spazio di lavoro.
{: shortdesc}

## Informazioni su quest'attività

Per ogni modello che vuoi creare ed utilizzare, crea un solo spazio di lavoro che contiene le risorse necessaria alla creazione del modello. Poi prepara il modello per produrre un modello personalizzato che può essere distribuito a un servizio esterno da utilizzare.

Prima di creare uno spazio di lavoro, rispondi a queste domande:

- **Quale tipo di modello vuoi creare?**

    - Modello di machine learning: utilizza un approccio statistico per trovare le entità e le relazioni nei documenti. Questo tipo di modello può adattarsi se la quantità di dati cresce.
    - Modello basato sulla regola: utilizza un approccio dichiarativo per trovare le entità nei documenti. Questo tipo di modello è più prevedibile ed è più facile da comprendere e mantenere. Tuttavia, non impara dai nuovi dati. Può solo trovare i modelli per cui è stato preparato.

    > **Nota:** puoi anche creare uno spazio di lavoro che contiene sia il modello basato sulla regola che il machine learning.

- **Quali servizi utilizzerà il modello?**

    Consulta i [servizi di integrazione {{site.data.keyword.watson}}](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg) per le informazioni sugli altri servizi {{site.data.keyword.watson}} con cui possono essere utilizzati i modelli personalizzati.

## Procedura

Per creare uno spazio di lavoro, completa la seguente procedura:

1. Accedi come amministratore {{site.data.keyword.knowledgestudioshort}} e fai clic su **Create Workspace**.

    > **Nota:** le persone con il ruolo di gestore del progetto possono eseguire quasi tutte le attività tranne la creazione di uno spazio di lavoro. Un amministratore deve creare lo spazio di lavoro inizialmente e assegnare i gestori del progetto ad esso.

1. Fornisci un nome allo spazio di lavoro. Scegli un nome breve che rifletta il tuo contenuto del dominio o lo scopo del modello. Se ne hai bisogno, puoi cambiare il nome dello spazio di lavoro successivamente.
1. Identifica la lingua dei documenti nel tuo spazio di lavoro. I documenti che aggiungi allo spazio di lavoro e i dizionari che crei o carichi, devono essere nella lingua che specifichi.
1. Facoltativo: se vuoi modificare il tokenizer utilizzato dall'applicazione dal tokenizer basato su machine learning predefinito, puoi espandere la sezione **Advanced Options** e scegliere **Dictionary-based tokenizer**.

    Il tokenizer predefinito è più avanzato del tokenizer basato sul dizionario; utilizza il machine learning per identificare i token nei documenti di origine basati sull'apprendimento statistico fatto nella lingua dei documenti di origine. Identifica i token con più precisione perché comprende i modelli di linguaggio più naturali e con più sfumature. Il tokenizer basato sul dizionario identifica i token in base alle regole della lingua. Consulta [Tokenizer](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer) per ulteriori dettagli.

1. Facoltativo: se vuoi aggiungere i gestori del progetto allo spazio di lavoro, espandi la sezione **Advanced Options** e seleziona i nomi delle persone che vuoi aggiungere come gestori del progetto dall'elenco. L'amministratore può aggiungere o rimuovere i gestori del progetto successivamente, modificando lo spazio di lavoro.

    Vengono visualizzati solo i nomi delle persone a cui hai assegnato il ruolo di gestore del progetto dalla pagina User Account Management dell'istanza. Consulta [Assemblaggio del team](/docs/services/watson-knowledge-studio/team.html) per ulteriori informazioni sull'aggiunta degli utenti.

    > **Nota:** se hai una sottoscrizione di piano gratuito, salta questo passo. Non puoi aggiungere altri utenti, per cui non puoi assegnare a nessuno il ruolo di gestore del progetto. Non hai bisogno di un gestore del progetto separato. Come amministratore, puoi eseguire tutte le attività normalmente eseguite da un gestore del progetto.

1. Fai clic su **Create**.

## Operazioni successive

Dopo aver creato lo spazio di lavoro, puoi iniziare a configurare le risorse dello spazio di lavoro.

Per modificare la descrizione o il nome dello spazio di lavoro o per aggiungere o rimuovere i gestori del progetto successivamente, un amministratore può modificare lo spazio di lavoro. Dalla homepage {{site.data.keyword.knowledgestudioshort}}, fai clic sull'icona **Show menu** nel tile dello spazio di lavoro e scegli l'opzione di menu **Edit**.

**Concetti correlati**:

[Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html)

**Riferimento correlato**:

[Supporto di più lingue](/docs/services/watson-knowledge-studio/language-support.html)

## Tokenizer
{: #wks_tokenizer}

Un tokenizer raggruppa i caratteri in token e i token in frasi. Un token è approssimativamente simile a una parola.

Le azioni che un tokenizer deve effettuare per identificare i token di un documento dipendono dalla lingua del documento. In inglese, i token sono spesso equivalenti alle parole perché delimitati da spazi bianchi in una frase. Tuttavia, non sempre hanno una corrispondenza di uno a uno con le parole; altri elementi di testo vengono considerati token in alcune situazioni. Ad esempio, la punteggiatura alla fine di una frase è considerata un token e le contrazioni sono spesso espanse in due token. Nelle lingue che non utilizzano gli spazi bianchi, come il cinese, vengono utilizzati algoritmi statistici più complicati per identificare i token.

Il processo di suddivisione in token è importante perché determina i gruppi di caratteri che gli utenti possono evidenziare per l'annotazione nell'editor ground truth. Le annotazioni delle citazioni di entità e relazione sono generalmente allineate con i limiti del token e devono essere etichettate in una frase; non possono estendersi oltre i limiti della frase.

### Tipi supportati

{{site.data.keyword.knowledgestudioshort}} supporta i seguenti tokenizer:

- **Tokenizer basato sul machine learning (predefinito)**

    Questo è il tokenizer più avanzato che identifica i token nei documenti di origine basati sull'apprendimento statistico fatto sulla lingua dei documenti di origine. Questo tokenizer trova i token che acquisiscono i modelli di linguaggio più naturali e con più sfumature. Non puoi personalizzare questo tokenizer.

- **Tokenizer basato sul dizionario**

    Questo tokenizer è basato sui dizionari linguistici. Trova i token che seguono le regole della lingua del documento di origine. Solo gli utenti esperti possono personalizzare questo token.

Devi scegliere il tokenizer che vuoi utilizzare quando crei lo spazio di lavoro. Non puoi passare a un tokenizer diverso in un secondo momento. Per i migliori risultati, utilizza il tokenizer predefinito. Solo gli utenti esperti che vogliono modificare il comportamento del tokenizer tramite un meccanismo di dizionario deterministico possono scegliere il tokenizer basato sul dizionario. Possono quindi personalizzarlo aggiungendo nuove voci al dizionario. Tuttavia, la personalizzazione deve essere fatta attentamente perché quando aggiungi nuove parole al dizionario, le modifiche possono influenzare il modello di machine learning in modi non voluti.

## Riepilogo di input, output e limitazioni
{: #wks_formats}

Fasi diverse dello sviluppo del modello richiedono input diversi e producono output diversi.

Per ogni tipo di processo di sviluppo del modello, questa tabella riepiloga le attività tipiche che esegui, i formati del file di input supportati, gli output che possono essere prodotti e tutti i limiti di dimensione o altri requisiti.

### Tutti i tipi di modello

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e252" class="stentry thleft thbot">Attività</th>
<th valign="bottom" align="left" id="d25459e254" class="stentry thleft thbot">Utilizzo tipico</th>
<th valign="bottom" align="left" id="d25459e256" class="stentry thleft thbot">Formati di input supportati</th>
<th valign="bottom" align="left" id="d25459e258" class="stentry thleft thbot">Formati di output supportati</th>
<th valign="bottom" align="left" id="d25459e260" class="stentry thleft thbot">Limiti e requisiti</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">Gestione sistema tipo</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">Crea un sistema tipo o carica e modifica un sistema tipo esistente.</p><p class="p">Definisci i tipi di entità
e relazione del tuo dominio.</p>
<p class="p">Non puoi vedere una visualizzazione del sistema
tipo.</p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Il file JSON che hai scaricato da
uno spazio di lavoro
Watson Knowledge
Studio</p></li>
<li class="li"><p class="p wrapper">Il file ZIP che hai scaricato da Human Annotation Tool (HAT)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">JSON</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">Per evitare il sovraccarico visivo dell'annotazione umana, definisci non più di 50 tipi di entità e
50 di relazione.</p><p class="p">Limite della dimensione del file per il caricamento di un sistema tipo: 20 MB</p>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">Gestione del dizionario</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">Carica un file dizionario CSV nella modalità di sola lettura o uno ZIP di dizionari che hai scaricato
da un altro spazio di lavoro.</p><p class="p">Crea un nuovo dizionario e poi carica un file CSV dei termini o aggiungi
un termine ad esso.</p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><p class="p wrapper">File dizionario:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">File CSV nel formato UTF-8</p></li>
<li class="li"><p class="p wrapper">ZIP di dizionari scaricato da un altro spazio di lavoro</p></li>
</ul><p class="p wrapper">
File del termine:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">File CSV nel formato UTF-8</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">File CSV nel formato UTF-8</p></li>
<li class="li"><p class="p wrapper">ZIP di dizionari da utilizzare in un altro spazio di lavoro</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">Limiti dimensione file:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">1 MB per file del termine CSV</p></li>
<li class="li"><p class="p wrapper">16 MB per i file del dizionario in sola lettura CSV</p></li>
<li class="li"><p class="p wrapper">15.000 voci per dizionario, eccetto un dizionario in sola lettura</p></li>
<li class="li"><p class="p wrapper">64 dizionari per spazio di lavoro</p></li>
</ul>
</td>
</tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Modello di machine learning

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e331" class="stentry thleft thbot">Attività</th>
<th valign="bottom" align="left" id="d25459e333" class="stentry thleft thbot">Utilizzo tipico</th>
<th valign="bottom" align="left" id="d25459e335" class="stentry thleft thbot">Formati di input supportati</th>
<th valign="bottom" align="left" id="d25459e337" class="stentry thleft thbot">Formati di output supportati</th>
<th valign="bottom" align="left" id="d25459e339" class="stentry thleft thbot">Limiti e requisiti</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Gestione documento </p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Carica una piccola e rappresentativa sottoserie di documenti. </p><p class="p">Carica i documenti che contengono
le annotazioni precedentemente aggiunte da un annotatore umano, un modello di machine learning o
motore di analisi
 UIMA.</p>
<p class="p">Non puoi
inserire l'intero corpus da
IBM Watson Explorer
 per il calcolo di documenti di elevato valore
dell'annotazione. </p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">File CSV nel formato UTF-8</p></li>
<li class="li"><p class="p wrapper">File DOCXML nel formato UTF-8</p></li>
<li class="li"><p class="p wrapper">Testo nel formato UTF-8</p></li>
<li class="li"><p class="p wrapper">File ZIP che contiene i documenti scaricati da un altro corpus</p></li>
<li class="li"><p class="p wrapper">File ZIP che contiene i documenti nel formato
UIMA
 CAS XMI</p></li>
</ul>
</td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">File di archivio ZIP dei documenti</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">40.000 caratteri per documento</p></li>
<li class="li"><p class="p wrapper">10.000 documenti per spazio di lavoro</p></li>
<li class="li"><p class="p wrapper">1.000 serie di documenti (incluse le serie di annotazioni) per spazio di lavoro.</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Pre-annotazione</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Utilizza un dizionario o un
{{site.data.keyword.nlushort}}
pre-annotatore
per fornire un punto di partenza per l'annotazione umana.</p><p class="p">Non puoi annotare nuovamente un corpus da
IBM Watson Discovery Advisor
 o
IBM Watson Explorer
.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Documenti non elaborati. </p><p class="p wrapper"><b>Nota:</b> non pre-annotare i documenti che un annotatore umano ha già
annotato o perderai il lavoro fatto dall'annotatore umano.</p>
</td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Documenti parzialmente annotati</p></td>
<td valign="top" headers="d25459e339" class="stentry"><p class="p wrapper">Nessuno</p></td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Annotazione documento</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Gestisci l'annotazione umana</p><p class="p">Annota entità, relazioni e catene di coreferenza per creare il
ground truth</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Attività di annotazione</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Ground truth</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">256 attività di annotazione attive per spazio di lavoro</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Preparazione e rifinitura</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Prepara un modello di machine learning con supervisione per estrarre le informazioni specifiche del dominio dal
testo non strutturato.</p><p class="p">Valuta e migliora un modello di machine learning con supervisione.</p>
<p class="p">Non puoi
creare un modello di machine learning senza supervisione o fatta in parte.</p>
<p class="p">Non puoi
effettuare feature engineering estesa.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Non applicabile</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Modello di machine learning</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">1 modello di machine learning dello spazio di lavoro</p></li>
<li class="li"><p class="p wrapper">10 versioni del modello per spazio di lavoro</p></li>
<li class="li"><p class="p wrapper">Il numero massimo di spazi di lavoro è determinato dal tuo piano di sottoscrizione.</p></li>
<li class="li"><p class="p wrapper">Il numero massimo di azioni di preparazione che puoi eseguire al mese è determinato dal tuo piano di sottoscrizione. </p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Pubblicazione</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Pubblica un modello di machine learning da utilizzare per l'estrazione del testo in altri

Applicazioni
 Watson. </p></td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Non applicabile</p></td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ID modello (per l'utilizzo nei servizi
AlchemyLanguage
 o
Watson Discovery) </p></li>
<li class="li"><p class="p wrapper">File ZIP (per l'utilizzo in
IBM Watson Explorer
)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry">
  <p class="p">Per distribuire a AlchemyLanguage,
    devi avere un ID chiave del piano AlchemyLanguage
    Advanced valido.</p>
  <p class="p">Per distribuire al servizio Watson Discovery,
    devi conoscere lo spazio e i nomi dell'istanza {{site.data.keyword.cloud_notm}}
    del servizio.</p>
</td>
</tr>
</table>

### Modello basato sulla regola

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e509" class="stentry thleft thbot">Attività</th>
<th valign="bottom" align="left" id="d25459e511" class="stentry thleft thbot">Utilizzo tipico</th>
<th valign="bottom" align="left" id="d25459e513" class="stentry thleft thbot">Formati di input supportati</th>
<th valign="bottom" align="left" id="d25459e515" class="stentry thleft thbot">Formati di output supportati</th>
<th valign="bottom" align="left" id="d25459e517" class="stentry thleft thbot">Limiti e requisiti</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">Editor delle regole</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p">Crea o carica i documenti nell'editor delle regole da cui definire classi, espressioni regolari
e regole.</p>
</td>
<td valign="top" headers="d25459e513" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Testo semplice (aggiunto nell'editor)</p></li>
<li class="li"><p class="p wrapper">File CSV nel formato UTF-8</p></li>
<li class="li"><p class="p wrapper">Copiato dalla serie di documenti All</p></li>
</ul>
</td>
<td valign="top" headers="d25459e515" class="stentry"><p class="p wrapper">Nessuno</p></td>
<td valign="top" headers="d25459e517" class="stentry"><ul class="ul bullets">
<li class="li"><p class="p wrapper">1 modello basato sulla regola dello spazio di lavoro</p></li>
<li class="li"><p class="p wrapper">5.000 caratteri per documento</p></li>
<li class="li"><p class="p wrapper">100 documenti per spazio di lavoro</p></li>
<li class="li"><p class="p wrapper">La dimensione massima del titolo del documento è 256 caratteri</p></li>
<li class="li"><p class="p wrapper">200 regole per spazio di lavoro</p></li>
<li class="li"><p class="p wrapper">400 classi per spazio di lavoro </p></li>
<li class="li"><p class="p wrapper">100 gruppi di espressione regolare per spazio di lavoro </p></li>
<li class="li"><p class="p wrapper">100 voci di espressione regolare per gruppo di espressione regolare </p></li>
<li class="li"><p class="p wrapper">1.000 caratteri voce di espressione regolare</p></li>
<li class="li"><p class="p wrapper">5 versioni del modello basato sulle regole per spazio di lavoro</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">Pubblicazione</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p wrapper">Pubblica un modello basato sulle regole da utilizzare per l'esecuzione del riconoscimento del modello nelle altre
applicazioni
 Watson.</p></td>
<td valign="top" headers="d25459e513" class="stentry"><p class="p wrapper">Non applicabile</p></td>
<td valign="top" headers="d25459e515" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ID modello (per l'utilizzo nei servizi
AlchemyLanguage
 o
Watson Discovery) </p></li>
</ul>
</td>
<td valign="top" headers="d25459e517" class="stentry">
  <p class="p">Per distribuire a AlchemyLanguage,
    devi avere un ID chiave del piano AlchemyLanguage
    Advanced valido.</p>
  <p class="p">Per distribuire al servizio Watson Discovery,
    devi conoscere lo spazio e i nomi dell'istanza {{site.data.keyword.cloud_notm}}
    del servizio.</p>
</td>
</tr>
</table>
