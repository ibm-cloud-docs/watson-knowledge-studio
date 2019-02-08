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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window}.
{: tip}

# Definizione di una regola
{: #wks_rule_creation}

Utilizza l'editor della regola per definire le regole.
{: shortdesc}

## Informazioni su quest'attività

Evita la modifica simultanea di regole, classi ed espressioni regolari da parte di più utenti perché potrebbe creare duplicati o sovrascritture non previste.

## Procedura

Per definire una regola, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e fai clic su **Rule-based Model** > **Rules**.
1. Fai clic sul segno più (+) accanto all'intestazione Documents per aggiungere un documento.

    Per ulteriori informazioni, vedi [Aggiunta di documenti per la definizione delle regole](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html).

    Ad esempio, potresti aggiungere un documento denominato `My Document` che contiene questa sola riga di testo:

    ```
    A 50-year-old driver was driving the 2017 Example Horizon.
    ```
    {: screen}

1. Se pensi di definire un'espressione regolare o aggiungere un dizionario, crea una classe da associarvi.

    1. Dal pannello **Class**, fai clic sul segno più (+) accanto alla classe.
    1. Aggiungi un nome della classe.

        Se assocerai la classe a un'espressione o a un dizionario, considera di chiamarla in un modo in cui puoi identificarne l'origine. Ad esempio, se pensi di utilizzare un'espressione regolare per definire un modello per l'età nella frase di esempio, puoi creare una classe denominata `AGE_REGEX`. Se pensi di utilizzare un dizionario per annotare il produttore di automobili nella frase, puoi aggiungere una classe denominata `MANUFACTURER_DICT`.

        Tieni a mente queste regole di denominazione:
        - Il primo carattere in un nome della classe deve essere alfabetico.
        - Utilizza solo i seguenti caratteri ASCII alfanumerici e il carattere di sottolineatura nei valori che aggiungi alle classi: da `A` a `Z`, da `a` a `z`, da `0` a `9`.
        - I nomi non possono contenere spazi.
        - I nomi non possono essere più lunghi di 64 caratteri.

1. Facoltativo: per annotare velocemente le classi in un documento, puoi associare un dizionario all'editor della regola. I termini in un documento che corrispondono alle voci nel dizionario vengono automaticamente annotati nella classe che selezioni per il dizionario. 

    1. Fai clic sulla scheda **Dictionaries**.

        Vengono visualizzati tutti i dizionari che hai creato.

        Se non hai aggiunto un dizionario, apri la pagina **Assets** > **Dictionaries** dalla barra di navigazione principale per aggiungerne uno. Consulta [Creazione dei dizionari](/docs/services/watson-knowledge-studio/dictionaries.html) per ulteriori informazioni.

    1. Fai clic su un dizionario, associa una classe al dizionario e poi fai clic su **Save**.

        Ad esempio, se hai un dizionario che contiene i nomi dell'organizzazione, puoi creare una classe di regole denominata `ORGANIZATION` e associarla al dizionario. Tutti i nomi dell'organizzazione presenti nei tuoi documenti di esempio saranno annotati come istanze della classe `ORGANIZATION`.

    Se successivamente vuoi rimuovere l'associazione del dizionario dall'editor della regola, puoi rimuovere l'associazione della classe. Per far ciò, scegli l'opzione vuota all'inizio dell'elenco a discesa.

2. Facoltativo: per definire un'espressione regolare per aiutarti a creare una regola, fai clic sulla scheda **Regex**.

    1. Fai clic sul segno più (+) accanto all'intestazione Regular Expressions.
    2. Fornisci un nome all'espressione regolare. Ad esempio, `MyAgeRegex`.

        Il nome non può essere più lungo di 64 caratteri.

    3. Associa l'espressione a una classe. Ad esempio, `AGE_REGEX`.
    4. Fai clic su **Add Entry**.
    5. Aggiungi l'espressione.

        Ad esempio, per acquisire un numero che rappresenta un'età (fino a 99), puoi specificare `[0-9]{1,2}`. Per acquisire le espressioni di tempo, come *12:30 AM*, potresti specificare questa espressione della regola:

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        Puoi facoltativamente modificare il numero minimo e massimo di token della parola. In inglese, i token sono spesso equivalenti alle parole perché delimitati da spazi bianchi in una frase. Tuttavia, non sempre hanno una corrispondenza di uno a uno con le parole. Altri elementi di testo vengono considerati token in alcune situazioni. Ad esempio, i trattini nel termine *50-year-old* contano ognuno come un token, il che significa che il numero totale di token utilizzato in questo termine è 5. E il testo *12:30 PM* contiene 4 token. (`12 | : | 30 | PM`)

        Fai clic su **Add**.

    6. Ripeti i precedenti due passi se vuoi aggiungere ulteriori espressioni.
    7. Fai clic su **Save**.

    L'editor regex si chiude e viene visualizzato il documento. Dovresti vedere la classe che hai definito per l'espressione regolare applicata al testo che vuoi gli corrisponda. Se non visualizzi l'annotazione, controlla la tua espressione. Potrebbe essere necessario revisionarla perché corrisponda al testo che vuoi trovi.

    ![L'editor della regola che mostra la scheda "Regex" selezionata, un'espressione regolare della regola "Age" associata alla classe "AGE_REGEX" e un documento che mostra il testo "50" evidenziato in giallo. Il testo evidenziato corrisponde all'espressione regolare che hai creato.](images/rule_step3.jpg "L'editor della regola che mostra ")

3. Per definire una regola, fai clic su **Rules** dalla navigazione.
4. Apri il documento con il modello che vuoi acquisire come una regola. Ad esempio, se hai creato un documento intitolato `My Document` con il testo di esempio che contiene la frase `50-year-old`, apri tale documento.
5. Dal testo nel documento, seleziona i caratteri che illustrano il modello che vuoi acquisire. Ad esempio, puoi selezionare i seguenti trattini (-) e parole:

    ```
    50-year-old
    ```
    {: screen}

    Dopo aver selezionato i caratteri puoi aggiungere una regola.

6. Fai clic sul segno più (+) nel pannello **Rules**.

    L'editor della regola rappresenta il testo che hai selezionato come due livelli di celle. Le celle nel livello superiore sono dove annoti le classi dei token sottostanti. Il livello inferiore è dove definisci le condizioni in cui i token partecipano nel modello.

    ![L'editor della regola che mostra il pannello "Create a rule".](images/rule_step4.jpg "L'editor della regola che mostra come ")

7. Definisci le condizioni per le quali ciascun token partecipa al modello.

    Nel livello inferiore delle celle, fai clic sul primo token per controllarne le condizioni. Se vuoi indicare che possono essere utilizzati tutti i token nella posizione corrente nel modello, fai clic su **Open Properties** e seleziona **Allow any token**. Fai clic su **Close Properties**. Se un token è un regex, come ad esempio `AGE_REGEX` nell'esempio, **Allow any token** non è disponibile.

    > **Nota:** il numero massimo di celle del gruppo che può partecipare a un modello è 15 quando ogni cella ha un'impostazione di ripetizione di 1 o meno. Le celle del gruppo includono token singoli, annotazioni o token dove sono consentiti. Il numero massimo di token totali consentito in un modello è 20. Seleziona l'impostazione di ripetizione di ogni cella nell'account quando definisci il modello. Ad esempio, puoi definire un modello che include 15 token quando ogni cella a un'impostazione di ripetizione di 1 o meno. Ma puoi definire non più di 4 token nel modello se ciascuno ha un'impostazione di ripetizione di 1 o meno per ognuno di essi, il token può essere ripetuto fino a 5 volte. Quattro token vengono ripetuti 5 volte portandoti al massimo consentito di 20.

    Per indicare che è necessario un tipo particolare di token, puoi definire i seguenti tipi di impostazioni della condizione:
    - **Impostazione di ripetizione**: specifica quante volte il token corrente deve essere incluso nel modello. Puoi modificare l'impostazione di ripetizione ma ne può essere specificata solo una per token. Le opzioni sono descritte nella seguente tabella.

    <table summary="">
      <caption>Tabella 1. Impostazioni di ripetizione </caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e471">
          Opzione di impostazione
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e473">
          Descrizione
        </th>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Obbligatorio (esattamente 1)</p>
        </td>
        <td headers="d27028e473">
          <p>Questo token deve essere presente nel modello
            una volta. Questa opzione viene applicata per impostazione predefinita,
            ma può essere modificata.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Ripetizione di 1 o più volte</p>
        </td>
        <td headers="d27028e473">
          <p>Questo token deve essere presente nel modello
            almeno una volta e può essere ripetuto più volte.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Ripetizione di 0 o più volte</p>
        </td>
        <td headers="d27028e473">
          <p>Questo token può facoltativamente essere ripetuto nel modello
            molte volte ma non deve essere ripetuto.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Ricorrenza di 0 o 1 volta</p>
        </td>
        <td headers="d27028e473">
          <p>Questo token è facoltativo.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Avanzato: _personalizzata_</p>
        </td>
        <td headers="d27028e473">
          <p>Questo token deve essere ripetuto nel modello
            il numero di volte qui specificato. Per definire
            un'impostazione di ripetizione personalizzata, fai clic su
            <b>Open Properties</b>,
            seleziona **Advanced** e poi seleziona il numero esatto di ripetizioni o l'intervallo delle ripetizioni che vuoi definire.</p>
          <p>
            Il numero massimo di ripetizioni consentite per un token è
            5.</p>
        </td>
      </tr>
    </table>

    - **Impostazione della funzione**: deve essere definita almeno una della impostazioni della funzione. Puoi aggiungere ulteriori funzioni al numero di condizioni che deve essere soddisfatto dal testo per corrispondere a questo modello. Le opzioni sono descritte nella seguente tabella.

    <table summary="">
      <caption>Tabella 2. Impostazioni delle funzioni</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e512">
          Opzione di impostazione
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e514">
          Condizione che aggiunge
        </th>
      </tr>
      <tr>
        <td headers="d27028e512">
          <p>Testo</p>
        </td>
        <td headers="d27028e514">
          <p>Deve corrispondere al testo esatto in questo
            token. Questa opzione viene applicata per impostazione predefinita. Puoi rimuoverla
            ma solo se aggiungi un'impostazione differente come condizione
            o applichi l'impostazione token Any.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e512">
          <p>Lunghezza</p>
        </td>
        <td headers="d27028e514">
          <p>Deve corrispondere alla lunghezza dei caratteri
            di questo token. La lunghezza viene contata a partire da 0 da davanti
            al primo carattere.</p>
        </td>
      </tr>
    </table>

    Il resto delle opzioni variano a seconda del tipo di token.

    - **Token non annotati che non corrispondono a un regex o a un termine del dizionario**: queste impostazioni sono disponibili per i token che non vengono annotati e non corrispondono a un regex o a un termine del dizionario.

    <table summary="">
      <caption>Tabella 3. Impostazioni token non annotato</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e535">Opzione di impostazione</th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e537">Descrizione</th>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Parte del discorso</p>
        </td>
        <td headers="d27028e537">
          <p>Deve essere la stessa parte del discorso
            di questo token. Sono supportati i seguenti tipi:</p>
          <ul>
            <li>
              aggettivo
            </li>
            <li>
              apposizione
            </li>
            <li>
              avverbio
            </li>
            <li>
              congiunzione
            </li>
            <li>
              determinativo
            </li>
            <li>
              esclamazione
            </li>
            <li>
              nome
            </li>
            <li>
              numeri
            </li>
            <li>
              pronome
            </li>
            <li>
              residuo
            </li>
            <li>
              verbo
            </li>
          </ul>
        </td>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Lemma</p>
        </td>
        <td headers="d27028e537">
          <p>Deve avere lo stesso lemma di questo
            token.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Tipo carattere</p>
        </td>
        <td headers="d27028e537">
          <p>Deve avere lo stesso tipo di carattere di questo
            token. Sono supportati i seguenti tipi:</p>
          <ul>
            <li>
              <p>Arabo: contiene una sequenza
                di caratteri arabi</p>
            </li>
            <li>
              <p>Numeri cinesi: contiene solo
                numeri cinesi.</p>
            </li>
            <li>
              <p>Punteggiatura finale della frase:
                i caratteri di punteggiatura che separano una proposizione
                o una frase dalla successiva</p>
            </li>
            <li>
              <p>Han: contiene caratteri Han</p>
            </li>
            <li>
              <p>Hangul: contiene caratteri sillabici
                Hangul coreani</p>
            </li>
            <li>
              <p>Ebraico: contiene una sequenza di
                caratteri ebraici</p>
            </li>
            <li>
              <p>Hiragana: contiene i caratteri sillabici
                Hiragana giapponesi</p>
            </li>
            <li>
              <p>Ideografico: contiene un
                ideogramma o un simbolo che rappresenta un'idea
                o una cosa</p>
            </li>
            <li>
              <p>Katakana: contiene i caratteri sillabici
                Katakana giapponesi</p>
            </li>
            <li>
              <p>Minuscolo: contiene solo
                caratteri alfanumerici minuscoli</p>
            </li>
            <li>
              <p>Numerico: contiene solo caratteri
                numerici</p>
            </li>
            <li>
              <p>Punteggiatura: uno o più caratteri
                che forniscono la punteggiatura nel
                testo</p>
            </li>
            <li>
              <p>Sillabico: contiene caratteri
                sillabici</p>
            </li>
            <li>
              <p>Thai: contiene caratteri
                thai</p>
            </li>
            <li>
              <p>Iniziali maiuscole: inizia con un solo carattere alfabetico
                maiuscolo, seguito da uno o più
                caratteri minuscoli</p>
            </li>
            <li>
              <p>Maiuscolo: un token che contiene solo
                caratteri alfabetici maiuscoli</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **Corrispondenza della regola:**

    <table summary="">
      <caption>Tabella 4. Corrispondenza della regola</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e617">
          Opzione di impostazione</th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e619">
          Descrizione</th>
      </tr>
      <tr>
        <td headers="d27028e617">
          <p>Corrispondenza della regola</p>
        </td>
        <td headers="d27028e619">
          <p>Deve corrispondere alla classe denominata. Ricorda, una classe può essere derivata da un regex,
            un dizionario o una regola. Se la classe qui specificata
            è stata derivata da un'espressione regolare, ad esempio, questo token
            deve corrispondere al modello di ricerca
            dell'espressione.</p>
        </td>
      </tr>
    </table>

8. Per i token che hanno annotazioni aggiunte indirettamente da una corrispondenza di annotazione del dizionario o espressione regolare, puoi scegliere se il modello dovrebbe richiedere tutte le parole con lo stesso tipo di annotazione o invece le parole al momento evidenziate che sono state annotate.

    Nel livello inferiore delle celle, puoi vedere quali celle sono incluse nel modello perché una riga orizzontale le collega tra loro. Dove un'annotazione è stata applicata, c'è una suddivisione. Le celle con le parole originali sono visualizzate sotto a una cella con l'etichetta di annotazione. Puoi fare clic su una serie di celle o modificare il percorso della riga e quindi modificare le celle incluse nel modello.

    Ad esempio, potresti scegliere che il modello utilizzi 50 invece della corrispondenza all'espressione regolare dell'età.

    ![Il pannello "Create a rule" che mostra una modifica del token, "50", che utilizza l'annotazione, "AGE_REGEX", nella regola. Per impostazione predefinite, viene utilizzata l'annotazione "AGE_REGEX", ma puoi modificare il modello in modo che sia invece utilizzata la parola evidenziata, "50".](images/rule_step5.jpg)

9. Dopo aver configurato l'ordine del modello, puoi annotare i token nel testo.

    Dal livello superiore delle celle, fai clic su quelle che rappresentano i token che vuoi annotare e poi applica loro un'etichetta della classe. Per selezionare più celle, fai clic su una di esse, premi il tasto **Shift** e fai clic sulle ulteriori celle.

    Assegna una classe alle celle selezionate. Se la classe che vuoi assegnare non esiste, puoi aggiungerla. Immetti il nome della classe nel campo **Assign class** e premi **Enter**.

    > **Nota:** non puoi aggiungere più di 10 classi per regola.

    ![La sezione "Create a rule" che mostra la finestra "Assign class" che si apre quando fai clic su un token. La finestra mostra un campo in cui puoi immettere il nome della nuova classe o selezionare una classe esistente dall'elenco.](images/rule_step6.jpg)

10. Fornisci un nome alla regola.

    Il nome della regola non può essere più lungo di 64 caratteri.

11. Fai clic su **Save** nel pannello Rules per salvare la regola.
