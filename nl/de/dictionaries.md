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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/dictionaries.html){: new_window} aufgerufen werden.
{: tip}

# Wörterverzeichnisse erstellen
{: #dictionaries}

Wörterverzeichnisse geben den Annotatoren für maschinelles Lernen in {{site.data.keyword.knowledgestudioshort}}
Einblick in den Sprachgebrauch des Fachgebiets.
{: shortdesc}

## Wörterverzeichnisse
{: #wks_dictionaries}

Beim maschinellen Lernen werden in einem Wörterverzeichnis Begriffe und Ausdrücke zusammengefasst,
die bestimmte Gemeinsamkeiten aufweisen. Die Wörter in einem Eintrag des Wörterverzeichnisses haben nicht alle
die gleiche Bedeutung, aber sie werden von einem Modell für maschinelles Lernen gleich behandelt.

In einem Wörterverzeichnis werden Wörter und Ausdrücke aufgelistet, die mit Bezug auf die Informationsextraktion äquivalent sind, d. h. sie sind im Hinblick auf das Identifizieren von Entitäts- und Beziehungserwähnungen austauschbar.

Angenommen, ein Wörterverzeichniseintrag enthält die sieben Tage der Woche. Zum Annotieren eines Dokuments ordnet der Annotatorbenutzer den Entitätstyp WOCHENTAG für Erwähnungen der Wörter 'Montag' und 'Freitag' im Text zu. Da das Wörterverzeichnis die sieben Wochentage als austauschbar einstuft, kann leichter sichergestellt werden, dass ein Modell für maschinelles Lernen das Vorkommen der Wörter 'Dienstag' und 'Mittwoch' sowie der übrigen Wochentage in neuen Dokumenten während der Laufzeit korrekt annotiert. Außerdem unterstützt die Gleichsetzung dieser Wörter auch das Extrahieren von Informationen aus dem umgebenden Text. Die Erkenntnisse, die das Modell für maschinelles Lernen aus Trainingsbeispielen des Texts gewinnt, der die Erwähnungen 'Montag' und 'Freitag' umgibt, wird auf Texte angewendet, in deren Umgebung andere Wochentage erwähnt werden, da diese Begriffe laut Wörterverzeichnis bei der Informationsextraktion als äquivalent eingestuft werden.

> **Hinweis:** Sie müssen kein Wörterverzeichnis erstellen, das Informationen zu Wochentagen enthält. Mehrere solche, vielseitig einsetzbare Wörterverzeichnisse sind in die Anwendung integriert. Andere Wörterverzeichnisse enthalten Länder- und Ortsnamen, Zahlwörter, Tiere, Pflanzen, Krankheiten, Maßeinheiten (z. B. Unze und Meter) sowie Anreden wie Herr und Frau. Integrierte Wörterverzeichnisse können weder inaktiviert noch bearbeitet werden.

Vermeiden Sie das Hinzufügen von Einträgen mit mehreren Bedeutungen. In einem Fachgebiet für Autorennen sollte der Begriff *Pilot* für den Fahrer am Steuer des Rennwagens nur eingetragen werden, wenn der Textkorpus in der Regel keine Hinweise auf die Luftfahrt enthält. Wenn beide Wortbedeutungen in den Quellendokumenten häufig vorkommen, sollte der Begriff in beide Wörterverzeichnistypen (für Autorennen und für Luftfahrt) nicht aufgenommen werden.

Sie können in {{site.data.keyword.knowledgestudioshort}} Wörterverzeichnisse erstellen, indem Sie einzelne Einträge manuell hinzufügen. {{site.data.keyword.knowledgestudioshort}} bietet auch die Möglichkeit, mehrere Typen von Wörterverzeichnisdateien hochzuladen.

### Wie werden Wörterverzeichnisse verwendet?

Wörterverzeichnisse können (optional) auf zwei verschiedene Arten verwendet werden. Entweder innerhalb des Modells für maschinelles Lernen, um Wörter oder Ausdrücke bereitzustellen, die im Sinne der Informationsextraktion als äquivalent gelten, oder beim Vorannotieren, um den Aufwand für die Vorannotation zu reduzieren.

- **Verwendung beim maschinellen Lernen**

    Der Entitätstyp, den Sie einem Wörterverzeichnis zuordnen, wird nicht verwendet, um Regeln für das Modell für maschinelles Lernen zu definieren. Beim maschinellen Lernen werden Erwähnungen in Dokumenten unabhängig ausgewertet. Dabei wird nicht vorausgesetzt, dass eine Erwähnung einen bestimmten Entitätstyp aufweist, nur weil sie mit einem Wörterverzeichniseintrag übereinstimmt, der dem betreffenden Entitätstyp zugeordnet ist. Diese Information wird zwar berücksichtigt, aber sie wird als eine von vielen Einzelinformation behandelt, die durch linguistische Analyse gesammelt werden. Tatsächlich gilt: Wenn kein Begriff aus einem Wörterverzeichnis in den Ground Truth-Dokumenten vorkommt, dann wird das betreffende Wörterverzeichnis im Modell für maschinelles Lernen nicht verwendet.

- **Verwendung der Vorannotation**

    Wörterverzeichnisse sind wichtig für die folgenden Prozesse der Vorannotation.
    - Wörterverzeichnisbasierter Vorannotator: Beim Ausführen des wörterverzeichnisbasierten Vorannotators ordnen Sie einem Wörterverzeichnis einen Entitätstyp aus dem Typsystem zu.
    - Regelbasiertes Modell: Sie können optional ein Wörterverzeichnis einer Regelklasse zuordnen. Beim Ausführen des regelbasierten Modells zum Vorannotieren von Dokumenten werden dann Klassen den Entitätstypen aus dem Typsystem zugeordnet. Dies führt dazu, dass Begriffe aus dem Wörterverzeichnis im Umlaufverfahren auch Entitätstypen für das regelbasierte Modell zugeordnet werden.

    In beiden Fällen stellen die Wörterverzeichnisse Begriffe bereit, die vom System erkannt und als Erwähnungen annotiert werden können. Jeder Erwähnung wird der Entitätstyp zugewiesen, der dem Wörterverzeichnis zugeordnet ist, das diesen Begriff enthält. Wenn ein Annotatorbenutzer mit dem Bearbeiten neuer Dokumente beginnt, die vorannotiert wurden, sind viele Erwähnungen bereits mithilfe der Wörterverzeichniseinträge annotiert. Der Annotatorbenutzer kann sich daher verstärkt auf das Zuweisen von Entitätstypen für Erwähnungen konzentrieren, die eine genauere Analyse erfordern.

### Sprachaspekte

- Für Portugiesisch (Brasilien), Englisch, Deutsch, Italienisch und Spanisch stellt {{site.data.keyword.knowledgestudioshort}} derzeit keine Option zum Aktivieren eines von Groß-/Kleinschreibung unabhängigen Wörterverzeichnisabgleichs bereit. Die Wörterverzeichniseinträge finden jedoch Textübereinstimmungen mit Großschreibung. Beispiel: Für den Eintrag 'fahrzeug' im Wörterverzeichnis werden 'fahrzeug', 'Fahrzeug' und 'FAHRZEUG' im Text als Übereinstimmungen erkannt. Für den Wörterverzeichniseintrag 'Sat' werden im Text zwar 'Sat' und 'SAT' als Übereinstimmungen erkannt, jedoch nicht 'sat'.
- Für Japanisch und Koreanisch wird beim Wörterverzeichnisabgleich während der Vorannotation die Groß-/Kleinschreibung beachtet.
- Für Arabisch setzt {{site.data.keyword.knowledgestudioshort}} voraus, dass der arabische Text ungeformt gespeichert ist. Zahlenformen werden als Eigenschaft auf der Speicherebene behandelt. Weitere Informationen zur Verarbeitung arabischer Zeichen- und Zahlenformen in {{site.data.keyword.knowledgestudioshort}}, finden Sie unter [Unterstützung für Arabisch konfigurieren](/docs/services/watson-knowledge-studio/language-support.html#wks_langsupp_ar).

### Wörterverzeichnis als CSV-Datei
{: #wks_dictionaries__cvsdict}

Ein Wörterverzeichnis in einer `CSV`-Datei (auch als Standardformat für Wörterverzeichnisse bezeichnet) besteht aus einer Datei, die Sie nach dem Hochladen bearbeiten können. Die maximale Größe einer `CSV`-Datei, die Sie hochladen können, beträgt 1 MB. Wenn Ihre Wörterverzeichnisdatei größer ist, teilen Sie sie in mehrere Dateien auf und laden Sie die Dateien einzeln nacheinander in ein einziges Wörterverzeichnis in Ihrem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich.

Zusammenfassung der Voraussetzungen: Zum Erstellen der `CSV`-Datei muss ein Texteditor verwendet werden (und keine Software wie Microsoft Excel). In der Datei muss die UTF-8-Codierung ohne Byteanordnungsmarkierung (Byte Order Mark, BOM) am Anfang des Textstroms verwendet werden. In der ersten Zeile der Datei müssen die folgenden Spaltenüberschriften angegeben werden:

```
lemma,poscode,surface
```
{: screen}

In den restlichen Zeilen der Datei werden die Wörterverzeichniseinträge angegeben. Dabei gilt Folgendes:

- **`Lemma`**

    Gibt die repräsentativste Wortform (Grundform) für den Eintrag an.

- **`poscode (Arabisch, Portugiesisch (Brasilien), Englisch, Französisch, Deutsch, Italienisch und Spanisch)`**

    Gibt einen Code an, der die Wortart identifiziert. Diese Wortartinformationen werden vom wörterverzeichnisbasierten Anotator verwendet, um Sätze in Tokens zu zerlegen.
    - 0 - Unbekannt

        > **Hinweis:** Dieser Code bietet Unterstützung zum Hochladen eines umfangreichen, maschinengenerierten Wörterverzeichnisses, das nicht in jedem Eintrag Wortartinformationen enthält. Der Code 'Unbekannt' kann standardmäßig allen Einträgen zugeordnet werden. Vermeiden Sie nach Möglichkeit die Verwendung dieses Codes.

    - 1 - Pronomen
    - 2 - Verb
    - 3 - Nomen
    - 4 - Adjektiv
    - 5 - Adverb
    - 6 - Adposition
    - 7 - Interjektion
    - 8 - Konjunktion
    - 9 - Determinator
    - 10 - Quantifizierer

    In der englischen Sprache sind Nomen (3), Verb (2) und Adjektiv (4) die häufigsten Wortarten in Wörterverzeichniseinträgen.

    > **Hinweis:** Durch die Wortart wird nicht automatisch der Typ der Erwähnung festgelegt. Gehen Sie nicht generell davon aus, dass alle Nomen Erwähnungen von Entitätstypen sind und alle Verben Erwähnungen von Beziehungstypen. Beispiel: *amerikanisch* ist ein Adjektiv, das jedoch als Entitätstyp  GPE (geopolitische Entität) oder PERSON annotiert werden sollte. Das Verb *traf* sollte mit EREIGNIS_TREFFEN annotiert werden.

    In anderen Sprachen (z. B. Deutsch), die Komposita (zusammengesetzte Wörter) verwenden, sind exakte Wortartinformationen noch wichtiger, um Wortgrenzen zu erkennen.

- **`poscode (Japanisch)`**

    Gibt einen Code an, der die Wortart identifiziert. Der Wert für die Wortart ist für die Zerlegung von Text in Tokens und für die Vorannotierung in Sprachen wie Japanisch wichtig, die Wortgrenzen nicht durch Leerzeichen kenntlich machen.
    - 19 - Nomen
    - 23 - allgemeines Präfix
    - 24 - allgemeines Suffix
    - 140 - Eigenname (Nachname)
    - 141 - Eigenname (Vorname)
    - 146 - Eigenname (Personenname)
    - 142 - Eigenname (Organisation)
    - 144 - Eigenname (Ortsname)
    - 143 - Eigenname (Region)
    - 145 - Eigenname (Andere)

- **`poscode (Koreanisch)`**

    Gibt einen Code an, der die Wortart identifiziert. Der Wert für die Wortart ist für die Zerlegung von Text in Tokens und für die Vorannotierung in Sprachen wie Koreanisch wichtig, die Wortgrenzen nicht durch Leerzeichen kenntlich machen.
    - 10010 - Nomen
    - 10300 - Eigenname (Nachname)
    - 10310 - Eigenname (Vorname)
    - 110360 - Eigenname (Personenname)
    - 10320 - Eigenname (Organisation)
    - 10340 - Eigenname (Ortsname)
    - 10330 - Eigenname (Region)
    - 10350 - Eigenname (Andere)

- **`surface`**

    Gibt äquivalente Begriffe an (auch als Oberflächenformen bezeichnet). Wiederholen Sie das Lemma als Oberflächenform und trennen Sie mehrere Oberflächenformen jeweils durch ein Komma. Wenn eine Oberflächenform ein Komma enthält, setzen Sie die Oberflächenform in Anführungszeichen.

Beispiel:

```
lemma,poscode,surface
IBM,3,IBM Corp.,IBM,"International Business Machines, Inc."
Department of Energy,3,DOE,Department of Energy
premium,4,premium,premium-grade
```
{: screen}

**Zugehörige Konzepte**:

[Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html)

**Zugehörige Tasks**:

[Dokumente mit dem wörterverzeichnisbasierten Annotator vorannotieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

## Wörterverzeichnisse zu einem Arbeitsbereich hinzufügen
{: #wks_projdictionaries}

Das Hinzufügen von Wörterverzeichnissen ist ein optionaler Schritt bei der Erstellung eines Modells. Wörterverzeichnisse sind hilfreich, da sie den Einstieg in den Annotationsprozess beschleunigen.

### Informationen zu diesem Vorgang

Wenn Sie ein Wörterverzeichnis bereitstellen, können Sie den wörterverzeichnisbasierten Vorannotator auf die Dokumente anwenden. Der Vorannotator erkennt Begriffe, die in Ihrem Wörterverzeichnis enthalten sind, und versieht diese Begriffe automatisch mit Annotationen. Diese vorbereitende Annotation (Vorannotation) erleichtert die Arbeit der Annotatorbenutzer. Die Annotatorbenutzer können die vom Vorannotator hinzugefügten Annotationen überprüfen und gegebenenfalls korrigieren oder weitere Annotationen hinzufügen (d. h. sie müssen den Annotationsprozess nicht völlig neu beginnen).

Für Wörterverzeichnisse gelten die folgenden Einschränkungen:

- Maximal 15.000 Einträge pro Wörterverzeichnis

    > **Hinweis:** Diese Begrenzung gilt nicht für Wörterverzeichnisse, die als CSV-Datei hochgeladen werden. Schreibgeschützte Wörterverzeichnisse können mehr Einträge enthalten.

- Maximal 64 Wörterverzeichnisse pro Arbeitsbereich

### Vorgehensweise

So fügen Sie in Ihrem Arbeitsbereich ein Wörterverzeichnis hinzu:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und öffnen Sie die Registerkarte **Assets & Tools** > **Vorannotatoren** > **Wörterverzeichnisse**.
1. Führen Sie eine der folgenden Tasks aus:

    - Klicken Sie auf die Schaltfläche **Wörterverzeichnis hochladen**, wählen Sie ein Wörterverzeichnis aus und klicken Sie anschließend auf **Hochladen**. Klicken Sie nach dem Hochladen eines Wörterverzeichnisses auf **Wörterverzeichnisse verwalten**, um das Wörterverzeichnis anzuzeigen und einem Entitätstyp zuzuordnen.

        - Sie können eine komprimierte Datei hochladen, die ein Wörterverzeichnis enthält und aus einem anderen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich heruntergeladen wurde. Vor dem Hochladen der Wörterverzeichnisdatei müssen Sie das aus dem anderen Arbeitsbereich heruntergeladene Typsystem im JSON-Format hochladen. In einem Wörterverzeichnis aus einem anderen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich, das Sie wiederverwenden, können Sie Einträge bearbeiten und hinzufügen. Details hierzu finden Sie unter [Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html).

        Das Hochladen einer CSV-Datei wird ebenfalls unterstützt. Wenn Sie die Datei jedoch direkt als Wörterverzeichnis hochladen, wird eine schreibgeschützte Vorschau des Wörterverzeichnisses erstellt, die Sie weder bearbeiten noch zum Vorannotieren von Dokumenten verwenden können. Um eine bearbeitbare CSV-Datei hochzuladen, die auch zum Vorannotieren verwendet werden kann, klicken Sie auf **Wörterverzeichnisse verwalten** und danach auf **Wörterverzeichnis erstellen**, damit zuerst ein Wörterverzeichnis erstellt wird, in das anschließend der Inhalt der CSV-Datei als Einträge geladen werden kann.

    - Klicken Sie auf die Schaltfläche **Wörterverzeichnisse verwalten**, um ein neues Wörterverzeichnis zu erstellen, in dem Sie anschließend Einträge hinzufügen können.

        Klicken Sie auf die Schaltfläche **Wörterverzeichnis erstellen** und geben Sie einen beschreibenden Namen für das Wörterverzeichnis an. Wählen Sie den Entitätstyp aus, der den Zweck des Wörterverzeichnisses am besten beschreibt, und klicken Sie anschließend auf **Speichern**.

1. Führen Sie eine der folgenden Tasks aus, um Einträge zum Wörterverzeichnis hinzuzufügen:

    - Klicken Sie auf **Eintrag hinzufügen**, um einen Wörterverzeichniseintrag hinzuzufügen. Geben Sie das Lemma (die Grundform des Begriffs) an.
    - Klicken Sie auf **Hochladen**, um eine `CSV`-Datei mit Wörterverzeichniseinträgen hochzuladen. Navigieren Sie anschließend zu der Datei und wählen Sie sie aus. Die CSV-Datei muss kleiner als 1 MB sein.

1. Nachdem Sie Einträge hochgeladen oder hinzugefügt haben, können Sie die Einträge bearbeiten.

    Öffnen Sie einen Eintrag, um äquivalente Begriffe (auch als Oberflächenformen bezeichnet) anzugeben. Jede Oberflächenform darf maximal 258 Zeichen lang sein. Sie können angeben, welche Oberflächenform als Lemma verwendet werden soll.

    Beispiel: Für das Lemma *{{site.data.keyword.IBM_notm}}* können Oberflächenformen wie *{{site.data.keyword.IBM_notm}} Corp.* und *International Business Machines, Inc.* vorkommen.

1. Wählen Sie die entsprechende Wortart für jedes Lemma und jede Oberflächenform im Wörterverzeichnis aus.

    Die Wortartinformationen werden vom Tokenizer und beim Vorannotieren verwendet. 

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Nächste Schritte

Führen Sie den Vorannotator aus, der die von Ihnen erstellen Wörterverzeichnisse für einen ersten Durchlauf durch die Quellendokumente verwendet und Annotationen hinzufügt.

**Zugehörige Tasks**:

[Dokumente mit dem wörterverzeichnisbasierten Vorannotator vorannotieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

**Zugehörige Referenzinformationen**:

[Unterstützung verschiedener Landessprachen](/docs/services/watson-knowledge-studio/language-support.html)
