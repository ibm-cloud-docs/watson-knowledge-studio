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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window} aufgerufen werden.
{: tip}

# Regel definieren
{: #wks_rule_creation}

Verwenden Sie den Regeleditor, um Regeln zu definieren.
{: shortdesc}

## Informationen zu diesem Vorgang

Vermeiden Sie die gleichzeitige Bearbeitung von Regeln, Klassen und regulären Ausdrücken durch mehrere Benutzer, da dies zu unerwarteten Überschreibungen oder Duplizierung führen kann.

## Vorgehensweise

Führen Sie die folgenden Schritte aus, um eine Regel zu definieren:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und klicken Sie auf **Regelbasiertes Modell** > **Regeln**.
1. Klicken Sie auf das Pluszeichen (+) neben der Dokumentüberschrift, um ein Dokument hinzuzufügen.

    Weitere Informationen finden Sie in [Dokumente zum Definieren von Regeln hinzufügen](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html).

    Sie können beispielsweise ein Dokument mit dem Namen  `Mein Dokument` hinzufügen, das die folgende einzelne Textzeile enthält:

    ```
    Ein 50-jähriger Fahrer saß am Steuer des Example Horizon, Baujahr 2017.
    ```
    {: screen}

1. Wenn Sie einen regulären Ausdruck definieren oder ein Wörterverzeichnis hinzufügen möchten, erstellen Sie eine Klasse, die dem Ausdruck oder dem Wörterverzeichnis zugeordnet werden soll.

    1. Klicken Sie in der Anzeige **Klasse** auf das Pluszeichen (+) neben 'Klasse'.
    1. Fügen Sie einen Klassennamen hinzu.

        Wenn Sie die Klasse einem regulären Ausdruck oder einem Wörterverzeichnis zuordnen möchten, wählen Sie einen Klassennamen, aus dem der Ursprung der Klasse hervorgeht. Beispiel: Wenn Sie einen regulären Ausdruck verwenden möchten, um ein Muster für das in dem Beispielsatz erwähnte Alter zu definieren, können Sie Klasse mit dem Namen `ALTER_REGEX` erstellen. Falls Sie ein Wörterverzeichnis verwenden möchten, um den Automobilhersteller in dem Satz zu annotieren, können Sie eine Klasse mit dem Namen `HERSTELLER_WVZ` hinzufügen.

        Beachten Sie die folgenden Namenskonventionen:
        - Das erste Zeichen in einem Klassennamen muss ein Buchstabe sein.
        - Verwenden Sie nur die folgenden alphanumerischen ASCII-Zeichen und das Unterstreichungszeichen in Werten, die Sie zu den Klassen hinzufügen: `A` bis `Z`, `a` bis `z`, `0` bis `9`.
        - Namen dürfen keine Leerzeichen enthalten.
        - Namen dürfen nicht länger als 64 Zeichen sein.

1. Optional: Um das Annotieren von Klassen in einem Dokument zu beschleunigen, können Sie dem Regeleditor ein Wörterverzeichnis zuordnen. Begriffe in einem Dokument, die den Einträgen im Wörterverzeichnis entsprechen, werden automatisch mit der entsprechenden Klasse annotiert, die Sie für das Wörterverzeichnis auswählen.

    1. Klicken Sie auf die Registerkarte **Wörterverzeichnisse**.

        Alle Wörterverzeichnisse, die Sie erstellt haben, werden angezeigt.

        Wenn Sie noch kein Wörterverzeichnis hinzugefügt haben, öffnen Sie die Seite **Assets** > **Wörterverzeichnisse** über die Hauptnavigationsleiste, um ein Wörterverzeichnis hinzuzufügen. Siehe [Wörterverzeichnisse erstellen](/docs/services/watson-knowledge-studio/dictionaries.html).

    1. Klicken Sie auf ein Wörterverzeichnis, ordnen Sie dem Wörterverzeichnis eine Klasse zu und klicken Sie anschließend auf **Speichern**.

        Wenn Sie zum Beispiel ein Wörterverzeichnis haben, das Organisationsnamen enthält, können Sie eine Regelklasse mit dem Namen `ORGANISATION` erstellen und die Klasse dem Wörterverzeichnis zuordnen. Alle Organisationsnamen, die in Ihrem Beispieldokument vorkommen, werden als Instanzen der Klasse `ORGANISATION` annotiert.

    Wenn Sie die Wörterverzeichniszuordnung im Regeleditor später rückgängig machen möchten, können Sie die Klassenzuordnung entfernen. Wählen Sie dazu die leere Option oben in der Dropdown-Liste aus.

2. Optional: Wenn Sie einen regulären Ausdruck definieren möchten, um das Erstellen einer Regel zu vereinfachen, klicken Sie auf die Registerkarte **RegEx**.

    1. Klicken Sie auf das Pluszeichen (+) neben der Überschrift 'Reguläre Ausdrücke'.
    2. Ordnen Sie einen Namen für den regulären Ausdruck zu Beispiel: `MeinAlterRegEx`.

        Der Name darf nicht länger als 64 Zeichen sein.

    3. Ordnen Sie den Ausdruck einer Klasse zu Beispiel: `ALTER_REGEX`.
    4. Klicken Sie auf **Eintrag hinzufügen**.
    5. Fügen Sie den Ausdruck hinzu.

        Wenn Sie beispielsweise eine Zahl erfassen möchten, die eine Altersangabe (bis 99 Jahre) ist, können Sie `[0-9]{1,2}` angeben. Um Ausdrücke mit Zeitangaben wie *12:30 AM* zu erfassen, können Sie den folgenden regulären Ausdruck angeben:

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        Optional können Sie die minimale und die maximale Anzahl der Worttokens ändern. In der englischen Sprache werden Tokens oft mit Wörtern gleichgesetzt, die in einem Satz durch Leerzeichen begrenzt sind. Token stimmen jedoch nicht immer eins-zu-eins mit Wörtern überein. In manchen Fällen werden andere Textelemente als Token eingestuft. Beispiel: Der Bindestrich in dem Begriff *50-jähriger* ist ein Token, d. h. in diesem Begriff sind insgesamt 3 Token enthalten. Die Textzeichenfolge *12:30 PM* enthält 4 Tokens (`12 | : | 30 | PM`).

        Klicken Sie auf **Hinzufügen**.

    6. Wiederholen Sie die beiden vorherigen Schritte, wenn Sie weitere Ausdrücke hinzufügen möchten.
    7. Klicken Sie auf **Speichern**.

    Der Editor für reguläre Ausdrücke wird geschlossen und das Dokument wird angezeigt. Sie sollten nun die Klasse sehen, die Sie für den regulären Ausdruck definiert haben, der auf den entsprechenden Text angewendet werden soll. Wenn die Annotation nicht angezeigt wird, überprüfen Sie Ihren Ausdruck. Der Ausdruck muss gegebenenfalls so angepasst werden, dass er mit dem Text übereinstimmt, den Sie finden möchten.

    ![Der Regeleditor mit der ausgewählten Registerkarte "Regex" einem regulären Ausdruck namens "Alter", dem die Klasse "ALTER_REGEX" zugeordnet ist, und einem Dokument, in dem der Text "50" gelb hervorgehoben ist. Der hervorgehobene Text stimmt mit dem erstellten regulären Ausdruck überein.](images/rule_step3.jpg "Der Regeleditor mit der ")

3. Wenn Sie eine Regel definieren möchten, klicken Sie im Navigationsbereich auf  **Regeln**.
4. Öffnen Sie das Dokument mit dem Muster, das Sie durch eine Regel erfassen möchten. Wenn Sie zum Beispiel ein Dokument namens `Mein Dokument` mit dem Beispieltext, der den Ausdruck `50-jähriger` enthält, erstellt haben, öffnen Sie das Dokument.
5. Wählen Sie im Text des Dokuments die Zeichen aus, die das Muster darstellen, das Sie erfassen möchten. Sie können zum Beispiel die beiden folgenden Wörter mit dem Bindestrich dazwischen auswählen:

    ```
    50-jähriger
    ```
    {: screen}

    Nachdem Sie die gewünschten Zeichen ausgewählt haben, können Sie eine Regel hinzufügen.

6. Klicken Sie auf das Pluszeichen (+) in der Anzeige **Regeln**.

    Der Regeleditor stellt den von Ihnen ausgewählten Text durch zwei Ebenen mit Zellen dar. In den Zellen der oberen Ebene können Sie die Klassen der zugrunde liegenden Tokens annotieren. In der unteren Ebene definieren Sie die Bedingungen für die Beteiligung der Tokens an dem Muster.

    ![Der Regeleditor zeigt, wie die Anzeige "Regel erstellen" aussieht.](images/rule_step4.jpg "Der Regeleditor zeigt, wie ")

7. Definieren Sie die Bedingungen für die Mitwirkung des Tokens an dem Muster.

    Klicken Sie in der unteren Zellenebene auf das erste Token, um die zugehörigen Bedingungen zu überprüfen. Wenn Sie angeben möchten, dass jedes Token an der aktuellen Position im Muster verwendet werden kann, klicken Sie auf **Eigenschaften öffnen** und wählen Sie **Jedes Token zulassen** aus. Klicken Sie auf **Eigenschaften schließen**. Wenn ein Token ein regulärer Ausdruck ist (wie `ALTER_REGEX` im vorliegenden Beispiel) steht die Option **Jedes Token zulassen** nicht zur Verfügung.

    > **Hinweis:** Die maximale Anzahl der Gruppenzellen, die an einem Muster beteiligt sein können, beträgt 15, wenn die Wiederholungseinstellung für jede Zelle kleiner-gleich 1 ist. Gruppenzellen schließen einzelne Tokens sowie Annotationen oder Tokens ein, für die jedes beliebige Token zulässig ist. Die maximale Anzahl der in einem Muster zulässigen Gesamtzahl von Token beträgt 20. Berücksichtigen Sie beim Definieren des Musters die Wiederholungseinstellung für jede Zelle. Sie können zum Beispiel ein Muster definieren, das 15 Tokens enthält, wenn die Wiederholungseinstellung für jede Zelle kleiner-gleich 1 ist. Sie können jedoch maximal 4 Tokens in dem Muster definieren, wenn die Wiederholungseinstellung für jede Zelle definieren, wenn die Wiederholungseinstellung jeweils größer-gleich 1 ist, da das Token für jede Zelle bis zu fünf Mal wiederholt werden kann. Vier Tokens, die fünfmal wiederholt werden, ergeben den zulässigen Maximalwert 20.

    Um anzugeben, dass ein bestimmter Tokentyp erforderlich ist, können Sie die folgenden Typen von Bedingungseinstellungen definieren:
    - **Wiederholungseinstellung**: Gibt an, wie oft das aktuelle Token in dem Muster enthalten sein muss. Die Wiederholungseinstellung kann geändert werden; für jedes Token darf jedoch nur eine einzige Wiederholungseinstellung angegeben werden. Die Optionen sind in der folgenden Tabelle beschrieben.

    <table summary="">
      <caption>Tabelle 1. Sich wiederholende Einstellungen</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e471">
          Einstellungsoption
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e473">
          Beschreibung
        </th>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Erforderlich (genau 1)</p>
        </td>
        <td headers="d27028e473">
          <p>Dieses Token muss im Muster einmal
            vorhanden sein. Diese Option wird standardmäßig angewendet,
            kann jedoch geändert werden.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Mindestens 1 Wiederholung</p>
        </td>
        <td headers="d27028e473">
          <p>Dieses Token muss in dem Muster
            mindestens einmal oder öfter vorhanden sein.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Mindestens 0 Wiederholungen</p>
        </td>
        <td headers="d27028e473">
          <p>Dieses Token kann in dem Muster optional
            beliebig oft wiederholt werden, aber es muss nicht wiederholt werden.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Kommt null- oder einmal vor</p>
        </td>
        <td headers="d27028e473">
          <p>Dieses Token ist optional.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e471">
          <p>Erweitert: _benutzerdefiniert_</p>
        </td>
        <td headers="d27028e473">
          <p>Dieses Token muss im Muster so oft vorkommen
            wie hier angegeben. Um eine benutzerdefinierte
            Wiederholungseinstellung zu definieren, klicken Sie
            auf <b>Eigenschaften öffnen</b>, wählen Sie
            **Erweitert** aus und geben Sie anschließend
            die Anzahl der Wiederholungen oder den Bereichswert für Wiederholungen an, die bzw. den Sie definieren möchten.</p>
          <p>
            Die maximale Anzahl der zulässigen Wiederholungen für ein Token ist
            5.</p>
        </td>
      </tr>
    </table>

    - **Featureeinstellung**: Mindestens eine der Featureeinstellungen muss definiert werden. Sie können weitere Features hinzufügen, um die Anzahl der Bedingungen hinzuzufügen, die erfüllt werden müssen, damit Text mit diesem Muster übereinstimmt. Die Optionen sind in der folgenden Tabelle beschrieben.

    <table summary="">
      <caption>Tabelle 2. Feature-Einstellungen</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e512">
          Einstellungsoption
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e514">
          Hinzugefügte Bedingung
        </th>
      </tr>
      <tr>
        <td headers="d27028e512">
          <p>Text</p>
        </td>
        <td headers="d27028e514">
          <p>Genaue Übereinstimmung mit dem Text in diesem
            Token erforderlich. Diese Option wird standardmäßig angewendet. Sie kann
            entfernt werden, sofern Sie eine andere Einstellung als Bedingung hinzufügen
            oder die Einstellung für jedes beliebige Token anwenden.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e512">
          <p>Länge</p>
        </td>
        <td headers="d27028e514">
          <p>Muss mit der Zeichenanzahl in diesem
            Token übereinstimmen. Die Länge wird ab der Position 0 vor dem
            ersten Zeichen gezählt.</p>
        </td>
      </tr>
    </table>

    Die übrigen Optionen variieren je nach Typ des Tokens.

    - **Nicht annotiertes Token, das keinem regulären Ausdruck oder Wörterverzeichnisbegriff entspricht**: Diese Einstellungen sind für Tokens verfügbar, die nicht annotiert sind und keinem Begriff aus einem regulären Ausdruck oder Wörterverzeichnis entsprechen.

    <table summary="">
      <caption>Tabelle 3. Nicht annotiertes, regelbasiertes Modell</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e535">Einstellungsoption</th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e537">Beschreibung</th>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Wortart</p>
        </td>
        <td headers="d27028e537">
          <p>Muss mit der Wortart dieses
            Tokens übereinstimmen. Folgende Typen werden unterstützt:</p>
          <ul>
            <li>
              Adjektiv
            </li>
            <li>
              Adposition
            </li>
            <li>
              Adverb
            </li>
            <li>
              Konjunktion
            </li>
            <li>
              Determinator
            </li>
            <li>
              Interjektion
            </li>
            <li>
              Nomen
            </li>
            <li>
              Numeral
            </li>
            <li>
              Pronomen
            </li>
            <li>
              Residuum
            </li>
            <li>
              Verb
            </li>
          </ul>
        </td>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Lemma</p>
        </td>
        <td headers="d27028e537">
          <p>Muss das gleiche Lemma wie dieses
            Token haben.</p>
        </td>
      </tr>
      <tr>
        <td headers="d27028e535">
          <p>Zeichentyp</p>
        </td>
        <td headers="d27028e537">
          <p>Muss den gleichen Zeichentyp wie dieses
            Token haben. Folgende Typen werden unterstützt:</p>
          <ul>
            <li>
              <p>Arabisch: Enthält eine
                Zeichenfolge mit arabischen Zeichen.</p>
            </li>
            <li>
              <p>ChinesischeZahl: Enthält nur
                chinesische Ziffern.</p>
            </li>
            <li>
              <p>Satzendezeichen:
                Interpunktionszeichen, die einen Teilsatz oder Satz
                vom nächsten trennen.</p>
            </li>
            <li>
              <p>Han: Enthält Han-Zeichen.</p>
            </li>
            <li>
              <p>Hangul: Enthält koreanische
                Hangul-Silbenzeichen.</p>
            </li>
            <li>
              <p>Hebräisch: Enthält eine
                Zeichenfolge mit hebräischen Zeichen.</p>
            </li>
            <li>
              <p>Hiragana: Enthält japanische
                Hiragana-Silbenzeichen.</p>
            </li>
            <li>
              <p>Ideografisch: Enthält ein
                Ideogramm oder Symbol, das eine Idee oder
                ein Ding darstellt.</p>
            </li>
            <li>
              <p>Katakana: Enthält japanische
                Katakana-Silbenzeichen.</p>
            </li>
            <li>
              <p>Kleinbuchstaben: Enthält nur
                alphabetische Zeichen in Kleinschreibung.</p>
            </li>
            <li>
              <p>Ziffern: Enthält nur
                numerische Zeichen.</p>
            </li>
            <li>
              <p>Interpunktion: Ein oder mehrere
                Interpunktionszeichen für Text.</p>
            </li>
            <li>
              <p>Silben: Enthält
                Silbenzeichen.</p>
            </li>
            <li>
              <p>Thailändisch: Enthält thailändische
                Zeichen</p>
            </li>
            <li>
              <p>Überschrift: Beginnt mit einem einzelnen
                Großbuchstaben, gefolgt von einem oder mehreren Kleinbuchstaben.</p>
            </li>
            <li>
              <p>Großschreibung: Ein Token, das
                ausschließlich Großbuchstaben enthält.</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **Regelabgleich:**

    <table summary="">
      <caption>Tabelle 4. Regelabgleich</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d27028e617">
          Einstellungsoption</th>
        <th style="vertical-align:bottom; text-align:left" id="d27028e619">
          Beschreibung</th>
      </tr>
      <tr>
        <td headers="d27028e617">
          <p>Regelabgleich</p>
        </td>
        <td headers="d27028e619">
          <p>Muss mit der benannten Klasse übereinstimmen. Beachten Sie, dass eine Klasse aus einem regulären Ausdruck,
            einem Wörterverzeichnis oder einer Regel abgeleitet werden kann. Wenn die hier angegebene Klasse zum Beispiel aus einem
            regulären Ausdruck abgeleitet wurde, muss dieses Token mit
            dem Suchmuster des Ausdrucks übereinstimmen.</p>
        </td>
      </tr>
    </table>

8. Für Token mit Annotationen, die indirekt über eine Wörterverzeichnisannotation oder einen übereinstimmenden regulären Ausdruck hinzugefügt wurden, können Sie auswählen, ob das Muster ein Wort mit demselben Annotationstyp oder den konkreten zugrunde liegenden Wörtern erfordert, die stattdessen annotiert wurden.

    In der unteren Zellenebene wird angezeigt, welche Zellen in das Muster einbezogen werden. Die betreffenden Zellen sind durch eine horizontale Linie verbunden. Wenn eine Annotation angewendet wurde, ist eine Teilung zu sehen. Zellen mit den ursprünglichen Wörtern werden unter eine Zelle mit der Annotationsbezeichnung angezeigt. Durch Klicken auf die eine oder die andere Zellengruppe können Sie den Linienverlauf ändern und damit auch die Zellen, die in das Muster einbezogen werden.

    Sie können beispielsweise angeben, dass im Muster das Token '50' enthalten sein soll, anstatt einer Übereinstimmung mit dem regulären Ausdruck für das Alter.

    ![Die Anzeige "Regel erstellen" mit einer Bearbeitung des Tokens "50", in der die Annotation "ALTER_REGEX" für die Regel verwendet wird. Die Annotation "ALTER_REGEX" wird standardmäßig verwendet. Sie können das Muster jedoch so anpassen, dass stattdessen das zugrunde liegende Wort "50" verwendet wird.](images/rule_step5.jpg)

9. Nachdem Sie die Musterreihenfolge festgelegt haben, können Sie Token im Text annotieren.

    Klicken Sie in der oberen Zellenebene auf die Zellen für die Token, die Sie annotieren möchten, und wenden Sie anschließend ein Klassenbezeichnung darauf an. Wenn Sie mehrere Zellen auswählen möchten, klicken Sie auf eine Zelle, drücken Sie die **Umschalttaste** und klicken Sie danach auf weitere Zellen.

    Ordnen Sie der bzw. den ausgewählte(n) Zelle(n) eine Klasse zu. Wenn die gewünschte Klasse nicht vorhanden ist, können Sie sie hinzufügen. Geben Sie den Namen der Klasse in das Feld **Klasse zuordnen** ein und drücken Sie die **Eingabetaste**.

    > **Hinweis:** Sie können nicht mehr als 10 Klassen für die Regel hinzufügen.

    ![Die Anzeige "Regel erstellen" mit dem Fenster "Klasse hinzufügen", das geöffnet wird, wenn Sie auf ein Token klicken. Das Fenster enthält ein Feld, in dem Sie den Namen der neuen Klasse eingeben oder eine vorhandene Klasse aus der Liste auswählen können.](images/rule_step6.jpg)

10. Ordnen Sie einen Namen für die Regel zu.

    Der Regelname darf nicht länger als 64 Zeichen sein.

11. Klicken Sie in der Anzeige 'Regeln' auf **Speichern**, um die Regel zu speichern.
