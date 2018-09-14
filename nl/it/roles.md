---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# Ruoli utente in {{site.data.keyword.knowledgestudioshort}}
{: #roles}

I ruoli {{site.data.keyword.knowledgestudiofull}} vengono utilizzati per organizzare un team di persone che creano i modelli basato sulla regola e di machine learning.
{: shortdesc}

## Note sui ruoli in {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- I ruoli utente in {{site.data.keyword.knowledgestudioshort}} sono gestiti ai seguenti livelli:
  - I ruoli {{site.data.keyword.cloud}} controllano l'accesso ai servizi {{site.data.keyword.cloud_notm}}. {{site.data.keyword.knowledgestudioshort}} utilizza Cloud Foundry per il controllo dell'accesso, che richiede che gli utenti {{site.data.keyword.knowledgestudioshort}} abbiano il ruolo di sviluppatore. Per ulteriori informazioni, vedi [Accesso Cloud Foundry ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - I ruoli {{site.data.keyword.knowledgestudioshort}} controllano l'accesso alla funzionalità {{site.data.keyword.knowledgestudioshort}}, come descritto in questa pagina.
- Non è necessario un ruolo {{site.data.keyword.knowledgestudioshort}} per creare un'istanza di {{site.data.keyword.knowledgestudioshort}}. Tuttavia, quando una persona crea un'istanza di {{site.data.keyword.knowledgestudioshort}}, al primo utente che avvia {{site.data.keyword.knowledgestudioshort}} viene assegnato il ruolo di amministratore di {{site.data.keyword.knowledgestudioshort}}.
- Per gestire uno spazio di lavoro, i gestori del progetto devono essere assegnati allo spazio di lavoro da un amministratore.
- Gli amministratori e i gestori del progetto possono impersonare il ruolo di annotatori umani, ma devono essere assegnati alle serie di annotazioni nello stesso modo degli annotatori umani.
- Una volta assegnati, non è possibile eseguire il downgrade dei ruoli da livelli di autorizzazioni più alti a livelli inferiori. Non è possibile eseguire il downgrade degli amministratori a gestori del progetto o annotatori umani e dei gestori del progetto ad annotatori umani. Per informazioni sull'aggiunta di utenti, l'upgrade dei ruoli e la disattivazione degli account utente, vedi [Assemblaggio di un team](/docs/services/watson-knowledge-studio/team.html).

## Descrizioni dei ruoli
{: #descriptions}
I ruoli {{site.data.keyword.knowledgestudioshort}} sono descritti nella seguente tabella. I ruoli sono elencati per ordine di livello di autorizzazioni, dal maggiore al minore.

| Ruolo | Descrizione |
|------|-------------|
| Amministratore | Responsabile delle attività di gestione, che includono la gestione degli utenti, il consumo delle risorse e gli addebiti mensili. In impostazioni di team di grandi dimensioni, gli amministratori raramente partecipano al processo di sviluppo del modello.
| Gestore progetto | Responsabile dell'organizzazione generale dello spazio di lavoro a cui viene assegnato/a. Le attività includono la creazione del sistema tipo, la gestione delle risorse, la gestione del lavoro di annotazione, la valutazione del modello di machine learning e la distribuzione dei modelli. Gli utenti in questo ruolo hanno bisogno di esperienza specifica nel settore perché creano il sistema tipo, insegnano agli annotatori umani come applicare correttamente il sistema tipo e valutano la qualità del modello. |
| Annotatore umano | Esegue l'etichettatura delle menzioni dell'entità e della relazione nei documenti di preparazione a cui è assegnato/a. Il lavoro viene assegnato agli annotatori umani e monitorato dal gestore del progetto. Gli annotatori umani possono non essere esperti del settore, a condizione che vengano correttamente preparati dal gestore del progetto ad applicare il sistema tipo. |
{:caption="Tabella 1. Descrizioni dei ruoli" caption-side="top"}

## Autorizzazioni del ruolo 
{: #permissions}

Per confrontare le autorizzazioni di ciascun ruolo, consulta la seguente tabella. Viene elencata un'autorizzazione su ogni riga. Se un ruolo dispone di tale autorizzazione, la colonna del ruolo viene contrassegnata con un segno di spunta (&checkmark;).

| Autorizzazione | Amministratore | Gestore progetto | Annotatore umano |
|------------|-------|-----------------|-----------------|
| Gestire i ruoli e l'accesso dell'utente | &checkmark; |  |  |
| Gestire gli spazi di lavoro | &checkmark; |  |  |
| Creare il sistema tipo e le linee guida di annotazione | &checkmark; | &checkmark; |  |
| Caricare i documenti di preparazione | &checkmark; | &checkmark; |  |
| Gestire le regole | &checkmark; | &checkmark; |  |
| Pre-annotare i documenti | &checkmark; | &checkmark; |  |
| Gestire le attività di annotazione | &checkmark; | &checkmark; |  |
| Risolvere i conflitti di annotazione con l'annotazione umana (*giudizio*) | &checkmark; | &checkmark; |  |
| Preparare e valutare i modelli di machine learning | &checkmark; | &checkmark; |  |
| Distribuire e annullare la distribuzione dei modelli ai servizi di runtime | &checkmark; | &checkmark; |  |
| Eseguire l'annotazione del documento | &checkmark; | &checkmark; | &checkmark; |
{:caption="Tabella 2. Autorizzazioni del ruolo" caption-side="top"}
