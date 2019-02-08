---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator.html){: new_window}.
{: tip}

# Regole
{: #rule-annotator}

Crea un modello basato sulla regola che può riconoscere i pattern nei tuoi documenti. Utilizza le regole per acquisire i pattern che si verificano nei documenti e comunicare le informazioni sui tipi di entità evidenziati.
{: shortdesc}

## Panoramica sulla classe

Quando crei una regola, utilizza le classi che rappresentano i tipi di informazioni. Queste classi sono simili ai tipi di entità. Quindi, perché non usiamo semplicemente i tipi di entità quando definiamo le regole? Perché quando crei le regole, puoi definire le classi intermedie che sono utilizzate solo per creare altre classi più complesse. Queste classi intermedie sono solo per convenienza. Non sono utili per se stesse. Le classi intermedie collaborano con le altre classi intermedie per definire una classe più completa e utile. Una classe intermedia è necessaria, ma non qualcosa da esporre come parte di un sistema tipo. Per abilitare il modello basato sulla regola a fare cose utili come pre-annotare i documenti con le citazioni di entità, devi associare le classi complesse che utilizzi durante la creazione della regola ai loro tipi di entità equivalenti dal sistema tipo.

Ad esempio, vuoi un modello che riconosca i nomi delle persone. Per preparare un modello di machine learning in modo che riconosca i nomi delle persone, dovresti annotare molti nomi diversi che sono scritti in vari formati nei documenti in una serie di annotazioni con il tipo di entità `PERSON` e preparare un modello che riconosca i nomi delle persone. Per creare un modello basato sulla regola che riconosca i nomi delle persone, definisci una regola che descrive i modelli di testo utilizzati per scrivere i nomi delle persone. Quindi, potresti creare una classe `FirstName` e una `LastName` e utilizzare queste classi intermedie per definire una classe `FullName`. Potresti definire le condizioni che determinano il posizionamento della classe `FullName` in relazione ai prefissi comuni, come `Dr.` e ai suffissi comuni, come `Jr.`. Quando viene utilizzato il modello basato sulla regola, la classe `FullName` viene associata al tipo di entità `PERSON`.

Un altro motivo per evitare l'associazione delle classi intermedie alle entità nel tuo sistema tipo è che se pre-annoti i documenti con il modello basato sulla regola e poi li aggiungi al tuo ground truth per la preparazione di un modello di machine learning, non vuoi definire le regole in un modo tale che produrranno la sovrapposizione delle citazioni di entità. Ad esempio, se stavi associando la classe intermedia `FirstName` e la classe complessa `FullName` all'entità `PERSON`, una ricorrenza di `John Doe, Jr.` creerà una citazione di sovrapposizione.

## Strumenti dell'editor della regola

L'editor della regola fornisce alcuni strumenti che ti aiutano a definire le regole.

- Dizionario

    Aggiungi un dizionario e assegnagli un nome della classe. Tutte le parole che vengono trovate che corrispondono alle voci nel dizionario vengono automaticamente annotate con la classe assegnata.

- Espressione regolare 

    Un'espressione regolare (regex) è una sequenza di caratteri che definisce un modello di ricerca. Lo strumento regex incluso nell'editor della regola riconosce le espressioni che seguono la sintassi `java.util.regex.Pattern`. Questo è un esempio di base:
    `[A-Z][a-z]*`: trova le parole in maiuscolo.

    `[A-Z]` fa corrispondere tutte le lettere alfabetiche maiuscole (da A a Z) e `[a-z]*` alle minuscole (da a a z) zero o più volte. L'asterisco (*) è un carattere che definisce l'impostazione di ripetizione (zero o più volte).

    Considera di utilizzare un programma di utilità regex basato sul web gratuito per aiutarti a determinare l'espressione giusta da utilizzare per acquisire il modello che vuoi trovare.

    Ad esempio, i tuoi documenti potrebbero avere molti riferimenti simili alle seguenti frasi:

    ```
    35-year-old driver
    16-year-old learner
    ```
    {: screen}

    La sintassi `n-year-old x` è un modello che normalmente rappresenta una persona. Puoi definire una regola di espressione regolare per trovare le frasi che corrispondono al modello `n-year-old x` e le annota come citazioni dell'entità `PERSON`.
