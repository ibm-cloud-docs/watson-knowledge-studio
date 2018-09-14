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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/glossary.html){: new_window} aufgerufen werden.
{: tip}

# Glossar
{: #glossary}

Dieses Glossar enthält Begriffe und Definitionen für {{site.data.keyword.knowledgestudioshort}}.
{: shortdesc}

In diesem Glossar werden die folgenden Querverweise verwendet:

- *Siehe* verweist von einem Begriff auf ein bevorzugtes Synonym oder von einem Akronym bzw. einer Abkürzung auf die definierte Langform.
- *Siehe auch* kann auch auf einen verwandten oder gegensätzlichen Begriff verweisen.

[A](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) [B](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [D](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) [E](/docs/services/watson-knowledge-studio/glossary.html#gloss_E) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [H](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) [I](/docs/services/watson-knowledge-studio/glossary.html#gloss_I) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [N](/docs/services/watson-knowledge-studio/glossary.html#gloss_N) [O](/docs/services/watson-knowledge-studio/glossary.html#gloss_O) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)

## A
{: #gloss_A}

- **Richtigkeit**

    Ein Maß für die Korrektheit von Annotationen, die von einem Modell für maschinelles Lernen erstellt werden. Siehe auch [Genauigkeit](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) und [Vollständigkeit](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **Richtigkeitsanalyse**

    Analysieren der Scores von Modellen für maschinelles Lernen, um festzustellen, ob Änderungen erforderlich sind, um die Genauigkeit zu verbessern.

- **Beurteilung**

    Ein iterativer Prozess zum Auflösen von Annotationskonflikten durch das Vergleichen der Annotationen, die von verschiedenen Annotatorbenutzern hinzugefügt wurden.

- **Analyseengine**

    Ein Programm, das Artefakte (z. B. Dokumente) analysiert, Informationen zu diesen Artefakten ableitet und die Schnittstellenspezifikation der UIMA-Analyseengine implementiert. Analyseengines werden aus Bausteinen erstellt, die als Annotatoren bezeichnet werden. Eine Analyseengine kann einen einzelnen Annotator enthalten (primitive Analyseengine) oder mehrere Annotatoren (zusammengefasste Analyseengine).

- **Annotation**

    Enthält Informationen zu einem Textbereich. Eine Annotation kann beispielsweise darauf hinweisen, dass ein Textbereich einen Firmennamen darstellt.

- **Annotationsgruppe**

    Im Kontext von Annotatorbenutzern eine Sammlung von Dokumenten, die aus dem Korpus extrahiert werden, um die Workload auf mehrere Annotatorbenutzer zu verteilen. Im Kontext der maschinenbasierten Annotationen eine Sammlung von Dokumenten, die als Blinddaten, Trainingsdaten oder Testdaten verwendet werden können.

- **Prozessmanager für Annotationen**

    Eine Rolle, die für die Verwaltung der gesamten Aktivitäten im Lebenszyklus für Annotationen in einem Arbeitsbereich verantwortlich ist. Der für einen Arbeitsbereich hinzugefügte Projektleiter führt in der Regel die Aufgaben eines Prozessmanagers für Annotationen aus.

- **Annotator**

    Siehe [Annotatorbenutzer](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) und [Annotator für maschinelles Lernen](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **Attribut**

    Ein Merkmal oder eine Eigenschaft einer Entität, das bzw. die die Entität beschreibt. Beispiel: Die Telefonnummer eines Mitarbeiters ist eines der Mitarbeiterattribute.

## B
{: #gloss_B}

- **Blinddaten**

    Eine Dokumentgruppe mit Ground Truth-Annotationen (z. B. Frage/Antwort-Paare), semantischen Annotationen und Passagenbeurteilung. Blinddaten sind für Entwickler weder zugänglich noch sichtbar. Sie dienen dazu, die Systemleistung regelmäßig an unbekannten Daten zu testen. Das Testen an Blinddaten verhindert die Beeinträchtigung der Richtigkeit durch Überanpassung an bekannte Fragensets oder Annotationen. Die gemeldeten Ergebnisse sollten nur von Tests stammen, die an Blinddaten ausgeführt wurden. Siehe auch [Daten testen](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) und [Trainingsdaten](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

## C
{: #gloss_C}

- **Konkordanz**

    Mit diesem Verfahren soll sichergestellt werden, dass für dieselbe Erwähnung in einem Dokument und über Annotationsgruppen hinweg stets derselbe Entitätstyp annotiert wird. Die Konkordanz unterstützt die Gewährleistung der Konsistenz über viele Vorkommen einer Erwähnung hinweg, ohne dass der Annotatorbenutzer jedes Vorkommen einzeln beschriften muss.

- **Fehlermatrix**

    Eine Tabelle, die eine detaillierte numerische Aufgliederung der annotierten Dokumentgruppen enthält. Die Tabelle dient zum Vergleichen der Annotationen, die von einem Modell für maschinelles Lernen hinzugefügt wurden, mit den Annotationen in der Ground Truth. In der Tabelle wird die Anzahl der [falsch-positiven](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [falsch-negativen](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [wahr-positiven](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) und [wahr-negativen](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) Befunde angegeben.

- **Koreferenz**

    Eine Beziehung zwischen zwei Wörtern oder Ausdrücken, die beide auf dieselbe Person oder Sache verweisen und bei der ein Wort bzw. Ausdruck das linguistische Bezugselement des anderen Worts bzw. Ausdrucks bildet. Beispiel: Es besteht eine Koreferenz zwischen den beiden Pronomen in dem Ausdruck 'Sie brachte es sich selbst bei', jedoch nicht in dem Ausdruck 'Sie brachte es ihr bei'. Ein Korrelationswert verbindet zwei funktional entsprechende Entitäten im selben Text.

- **Koreferenzkette**

    Eine Liste der Entitäten, die als Koreferenzen annotiert wurden. Wenn Sie Erwähnungen als Koreferenzen annotieren, erstellt das System eine Koreferenzkette. Mithilfe dieser Kette können Sie alle Erwähnungen im Kontext anzeigen und überprüfen, dass alle Vorkommen demselben Entitätstyp angehören.

- **Korpus**

    Eine Sammlung von Quellendokumenten, die zu einem Arbeitsbereich hinzugefügt und zum Trainieren eines Modells für maschinelles Lernen verwendet wurden.

- **Kuratieren**

    Relevante Inhalte für ein bestimmtes Thema auswählen, sammeln, bewahren und verwalten. Durch Kuratieren wird ein Mehrwert auf der Grundlage von Daten erzeugt, verwaltet und erweitert. Auf diese Weise werden aus Daten zuverlässige Informationen und sicheres Wissen.

## D
{: #gloss_D}

- **Wörterverzeichnis**

    Eine Sammlung von Wörtern, die zum Vorannotieren von Dokumenten verwendet werden können. Für jedes Wort im Dokumenttext, das mit einem Begriff im Wörterverzeichnis übereinstimmt, wird eine neue Annotation erstellt. Ein Modell für maschinelles Lernen kann mit einem oder mehreren unabhängigen Wörterverzeichnissen konfiguriert werden, die in der Regel fachspezifisch sind (z. B. ein Wörterverzeichnis für Pharmazeutika oder für Vermögensverwaltung). Siehe auch [Lemma](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) und [Oberflächenform](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

- **Wörterverzeichnisbasierter Vorannotator**

    Eine Komponente, die Erwähnungen im Text identifiziert, die mit einer bestimmten Gruppe von Wörtern übereinstimmen. Durch die Verwendung fachspezifischer Terminologie zum Vorannotieren von Text können wörterverzeichnisbasierte Vorannotatoren die Arbeit des Annotatorbenutzers und damit das Vorbereiten einer Ground Truth-Dokumentgruppe beschleunigen.

- **Dokumentgruppe**

    Eine Sammlung von Dokumenten. Dokumente, die zusammen importiert werden, bilden eine Dokumentgruppe. Aus annotierten Dokumenten, die für Trainingszwecke gruppiert wurden (Test-, Trainings- oder Blinddaten) werden Dokumentgruppen generiert.

## E
{: #gloss_E}

- **Entität**

    1. Eine Erwähnung, die mit einem Entitätstyp annotiert wird.
    1. Eine Person, ein Objekt oder ein Konzept, zu dem Informationen gespeichert werden.
    1. Eine Gruppe von Details zu einem realen Objekt (z. B. eine Person, eine Position oder ein Bankkonto), die aufgezeichnet wurden. Eine Entität ist eine Art Element.

- **Entitätstyp**

    Der Entitätstyp, den eine Erwähnung unabhängig vom Kontext darstellt. Die Erwähnung {{site.data.keyword.IBM_notm}} kann beispielsweise mit dem Entitätstyp ORGANISATION annotiert sein.

    In einem Entitätsbeziehungsmodell ist ein Entitätstyp die Sache, die modelliert wird, oder die Sache, auf die sich eine Erwähnung bezieht (z. B. der Name einer Person oder eines Ortes). Verschiedene Entitätstypen verfügen über unterschiedliche Attributgruppen mit Attributen wie 'Nachname' oder 'Wohnort' und sind durch Beziehungen wie 'wohnt in' verknüpft. Der Entitätstyp ist ein unabhängiges Element und kann eindeutig identifiziert werden.

## F
{: #gloss_F}

- **F1-Score**

    Ein Messwert für die Richtigkeit eines Tests, der unter Berücksichtigung von Genauigkeit und Vollständigkeit (Recall) berechnet wird. Der F1-Score kann als gewichteter Durchschnitt der Genauigkeits- und Vollständigkeitswerte beschrieben werden. Der beste Wert für den F1-Score ist 1 und der schlechteste Wert ist 0.

- **Falsch-negativer Befund**

    Eine korrekte Antwort oder Annotation, die jedoch als falsch prognostiziert wurde.

- **Falsch-positiver Befund**

    Eine falsche Antwort oder Annotation, die jedoch als richtig prognostiziert wurde.

- **Merkmal**

    Ein Datenelement oder Attribut eines Typs.

- **Fleiss' Kappa-Score**

    Ein Messwert für die konsistente Anwendung derselben Annotation durch mehrere Annotatorbenutzer auf sich überschneidende Dokumente. Der beste Wert für den Fleiss' Kappa-Score ist 1 und der schlechteste Wert ist 0.

## G
{: #gloss_G}

- **Ground Truth**

    Die Gruppe der geprüften Daten (bestehend aus Annotationen, die von Annotatorbenutzern hinzugefügt wurden), die zum Anpassen eines Modells für maschinelles Lernen verwendet werden. Ground Truth-Daten werden verwendet, um Modelle für maschinelles Lernen zu trainieren, die Modellleistung (Genauigkeit und Vollständigkeit) zu messen und den Spielraum für die gezielte Weiterentwicklung und die Optimierung der Modellleistung zu ermitteln. Die Richtigkeit der Ground Truth-Daten ist von entscheidender Bedeutung, da Ungenauigkeiten in den Ground Truth-Daten zu Ungenauigkeiten in den darauf basierenden Komponenten führen.

## H
{: #gloss_H}

- **Spielraumanalyse**

    Mit diesem Prozess wird ermittelt, welche Verbesserung der Richtigkeit, der Genauigkeit oder der Vollständigkeit zu erwarten ist, wenn eine bestimmte Klasse von Problemen bearbeitet wird, die bei der Richtigkeitsanalyse ermittelt wurden.

- **Annotatorbenutzer**

    Ein Fachmann, der die Ergebnisse der Vorannotierung prüft, ändert und erweitert (durch das Identifizieren von Erwähnungen, Entitätstypbeziehungen und Koreferenzen für Erwähnungen). Durch kontextbezogene Textprüfung unterstützt der Annotatorbenutzer das Festlegen der Ground Truth und das Optimieren der Richtigkeit des Modells für maschinelles Lernen.

## I
{: #gloss_I}

- **Übereinstimmung der Annotatoren**

    Ein Messwert für den Grad der Ähnlichkeit beim Annotieren eines Dokuments in zwei oder mehr Dokumentgruppen.

## K
{: #gloss_K}

- **Wissensdiagramm**

    Ein konsolidiertes Modell der typisierten Entitäten, zugehörigen Beziehungen, zugehörigen Eigenschaften und hierarchischen Taxonomien zum Darstellen der konzeptionellen Struktur eines bestimmtes Fachgebiets. Nachdem der Speicher für das Wissensdiagramm mit Eingaben aus strukturierten und unstrukturierten Datenquellen gefüllt wurde, können Benutzer und Anwendungen auf das Wissensdiagramm zurückgreifen, um zentrale Wissenselemente für ein bestimmtes Fachgebiet zu untersuchen, Interaktionen zu untersuchen und zusätzliche Beziehungen zu erkennen.

## L
{: #gloss_L}

- **Lemma**

    Die normalisierte oder kanonische Form eines Wortes. Das Lemma ist in der Regel die Grundform eines Substantivs oder Verbs (ohne Ableitungen und Beugungen). Beispiel: Das Lemma der Begriffe 'organisierend' und 'organisiert' lautet 'organisieren'. Siehe auch [Wörterverzeichnis](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) und [Oberflächenform](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

## M
{: #gloss_M}

- **Maschinelles Lernen**

    Eine Methode der Datenanalyse, die iterativ aus bisherigen Daten lernt und sich unabhängig an neue Daten anpasst. Das mathematische Modell für maschinelles Lernen wird aus Ground Truth-Eingabedaten erstellt. Durch Training und Optimierung mithilfe von Beispieleingabedaten kann das Modell beim Analysieren neuer Daten genaue und reproduzierbare Ergebnisse liefern.

- **Annotator für maschinelles Lernen**

    Siehe [Modell für maschinelles Lernen](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **Modell für maschinelles Lernen**

    Eine Komponente, die Entitäten und Entitätsbeziehungen gemäß einem statistischen Modell identifiziert, das auf Ground Truth basiert. Das Modell wendet bisherige Erkenntnisse (z. B. Trainingsdaten) an, um auf der Grundlage der Datenmerkmale das richtige Ergebnis für zukünftige Erkenntnisse zu ermitteln und vorherzusagen. Die bisherigen Erkenntnisse werden in Form eines Modells erfasst. Dabei werden Merkmal-Scores für alle infrage kommenden Antworten oder Belege berechnet und mit vorhandenen Ergebnissen kombiniert. Diese Komponente wird auch als *Annotator für maschinelles Lernen* bezeichnet.

- **Erwähnung**

    Ein Textbereich, den Sie für die Daten in Ihrem Fachgebiet als relevant erachten. In einem Typsystem für Kraftfahrzeuge können zum Beispiel Begriffe wie 'Airbag', 'Ford Explorer' und 'Kinderrückhaltesystem' relevante Erwähnungen sein.

## N
{: #gloss_N}

- **Benannte Entität**

    Ein Konzept in einem Fachgebiet, das einer klar definierten Kategorie angehört (z. B. Namen von Organisationen, Positionen, Autoren oder Krankheiten).

- **Verarbeitung natürlicher Sprache**

    Ein Gebiet der künstlichen Intelligenz und der Sprachwissenschaft, das die Probleme untersucht, die bei der Verarbeitung natürlicher Sprache auftreten, und das Ziel verfolgt, die Fähigkeit von Computern zum Verstehen der menschlichen Sprache zu verbessern.

## O
{: #gloss_O}

- **Ontologie**

    Eine explizite und formale Spezifikation für die Darstellung der Objekte, Konzepte und anderen Entitäten, die einem Interessengebiet vorhanden sein können, und der zwischen ihnen bestehenden Beziehungen.

## P
{: #gloss_P}

- **Wortart**

    Einzelnen lexikalischen Elementen in einem Wörterverzeichnis werden Tags für die Wortart (Part Of Speech, POS) zugeordnet. Beispiel: Das Wort 'Fliegen' kann eine Verbform oder ein Substantiv sein.

- **Leistung**

    Ein Messwert für die Richtigkeit, Genauigkeit und Vollständigkeit eines {{site.data.keyword.watson}}-Systems (z. B. beim Beantworten von Fragen, beim Erkennen von Beziehungen oder beim Annotieren von Text).

- **Vorannotierung**

    Der Prozess zum Annotieren einer Dokumentgruppe als Vorbereitung für die weitere Bearbeitung durch Annotatorbenutzer. Zum Vorannotierern von Dokumenten kann ein regelbasiertes Modell, ein Modell für maschinelles Lernen, {{site.data.keyword.nlufull}} oder ein Wörterverzeichnis verwendet werden. Die Vorannotierung kann den Zeitaufwand der Annotatorbenutzer beim Vorbereiten einer Ground Truth-Dokumentgruppe reduzieren.

- **Genauigkeit**

    Ein Messwert für den Anteil der Ergebnisse, die relevant sind. Die Genauigkeit ist ein positiver Vorhersagewert und wird ermittelt, indem die Anzahl der zutreffenden positiven Ergebnisse durch die Anzahl aller positiven Ergebnisse dividiert wird. Die Richtigkeit wird am besten unter Berücksichtigung von Genauigkeit und Vollständigkeit ermittelt. Siehe auch [Richtigkeit](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) und [Vollständigkeit](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **Verarbeitungsenginearchiv (Processing Engine Archive, PEAR)**

    Eine Archivdatei `.pear`, die eine UIMA-Analyseengine (UIMA = Unstructured Information Management Architecture) und alle Ressourcen enthält, die zur Verwendung der Datei für die angepasste Analyse erforderlich sind.

## R
{: #gloss_R}

- **Vollständigkeit (Recall)**

    Ein Messwert für den Prozentsatz der relevanten Ergebnisse, die aus allen verfügbaren relevanten Ergebnissen zurückgegeben werden. Die Vollständigkeit ist ein Messwert für die Sensitivität und wird ermittelt, indem die Anzahl der zutreffenden positiven Ergebnisse durch die Anzahl der positiven Ergebnisse dividiert wird, die zurückgegeben worden sein sollten. Die Richtigkeit wird am besten unter Berücksichtigung von Genauigkeit und Vollständigkeit ermittelt. Siehe auch [Richtigkeit](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) und [Genauigkeit](/docs/services/watson-knowledge-studio/glossary.html#gloss_P).

- **Beziehung**

    In der Regel eine Bezeichnung, die die Relation zwischen Entitäten mithilfe eines Verbs angibt. Beispiel: 'Wohnt in' gibt die Beziehung zwischen einer Person und einem Ort an. Eine Beziehung verbindet zwei verschiedene Entitäten im selben Satz.

- **Beziehungstyp**

    Eine binäre, unidirektionale Beziehung zwischen zwei Entitäten. Beispiel: `Mary` `beschäftigtBei` {{site.data.keyword.IBM_notm}} ist eine gültige Beziehung. {{site.data.keyword.IBM_notm}} `beschäftigtBei` `Mary` ist keine gültige Beziehung.

- **Rolle**

    Ein Attribut, das die kontextabhängige Bedeutung einer Erwähnung angibt. Beispiel: Der Ausdruck 'Ich ging heute zu {{site.data.keyword.IBM_notm}}' enthält die Erwähnung '{{site.data.keyword.IBM_notm}}'. Der Entitätstyp ist 'Organisation' und die Rolle des Entitätstyps ist 'Einrichtung'.

- **Regelsatz**

    Eine Gruppe von Regeln, die Muster zum Annotieren von Text definieren. Wenn ein Muster zutrifft, werden die für die Regel festgelegten Aktionen auf die betreffenden Annotationen angewendet. Eine Regel gibt normalerweise die Bedingung an, die erfüllt sein muss, einen optionalen Quantor, eine Liste mit zusätzlichen Einschränkungen, die der Text erfüllen muss, und die bei Erfüllung dieser Bedingungen auszuführende Aktion (z. B. Erstellen einer neuen Annotation oder Ändern einer vorhandenen Annotation).

## S
{: #gloss_S}

- **Subtyp**

    Ein Typ der einen anderen übergeordneten Typ (Supertyp) ergänzt oder implementiert.

- **Oberflächenform**

    Die Form eines Wortes oder einer Mehrworteinheit, das bzw. die im Korpus vorkommt. Beispiel: Zwei Oberflächenformen des Lemmas 'organisieren' sind 'organisierend' und 'organisiert'. Siehe auch [Wörterverzeichnis](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) und [Lemma](/docs/services/watson-knowledge-studio/glossary.html#gloss_L).

## T
{: #gloss_T}

- **Testdaten**

    Eine Gruppe annotierter Dokumente, die verwendet werden können, um Systemmetriken nach dem Einpflegen und Trainieren auszuwerten. Siehe auch [Blinddaten](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) und [Trainingsdaten](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **Trainieren**

    Der Prozess zum Einrichten einer {{site.data.keyword.watson}}-Instanz mit Komponenten, die ein funktionierendes System für ein bestimmtes Fachgebiet bilden (z. B. Korpusinhalte, Trainingsdaten zum Generieren von Modellen für maschinelles Lernen, programmgesteuerte Algorithmen oder andere Ground Truth-Komponenten) und das anschließende Verbessern und Aktualisieren dieser Komponenten anhand von Richtigkeitsanalysen.

- **Trainingsdaten**

    Eine Gruppe annotierter Dokumente, die zum Trainieren von Modellen für maschinelles Lernen verwendet werden können. Siehe auch [Blinddaten](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) und [Testdaten](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **Wahr-negativer Befund**

    Eine falsche Antwort oder Annotation, die auch als falsch prognostiziert wurde.

- **Wahr-positiver Befund**

    Eine korrekte Antwort oder Annotation, die auch als richtig prognostiziert wurde.

- **Typsystem**

    Das Typsystem definiert die Objekttypen, die in einem Dokument erkannt werden können. Das Typsystem definiert alle möglichen Entitätstypen und die Beziehungen zwischen den Entitätstypen. In einem Typsystem kann eine beliebige Anzahl verschiedener Typen definiert werden. Typsysteme sind in der Regel fach- und anwendungsspezifisch.
