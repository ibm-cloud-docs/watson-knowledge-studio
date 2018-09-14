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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window} aufgerufen werden.
{: tip}

# Typsystem einrichten
{: #typesystem}

Das Typsystem steuert, wie der Inhalt annotiert werden kann.
{: shortdesc}

## Typsysteme
{: #wks_typesystem}

Ein Typsystem definiert Inhalte in Ihrem Fachgebiet, die von Interesse sind, und die Sie mit einer Annotation kenntlich machen möchten. Das Typsystem steuert, wie der Inhalt annotiert werden kann. Dies geschieht durch das Definieren von Entitätstypen, die beschriftet werden können, und durch das Definieren der Beschriftungen für die Beziehungen zwischen verschiedenen Entitäten. Der Prozessmanager für Modelle definiert das Typsystem in der Regel zusammen mit Fachleuten des jeweiligen Fachgebiets.

In {{site.data.keyword.knowledgestudioshort}} können Sie ein Typsystem entweder völlig neu erstellen oder ein vorhandenes Typsystem kopieren. Als Schnelleinstieg in einen Arbeitsbereich können Sie ein Typsystem hochladen, das für einen ähnlichen Fachbereich erstellt wurde. Anschließend können Sie das Typsystem bearbeiten, um Entitätstypen hinzuzufügen bzw. zu entfernen oder die Beziehungstypen neu zu definieren.

Ein Beispieltypsystem auf der Basis des Typsystems *KLUE* für die Verwendung mit {{site.data.keyword.knowledgestudioshort}}-Lernprogrammen wird bereitgestellt. Die Abkürzung KLUE steht für Knowledge from Language Understanding and Extraction und wurde von {{site.data.keyword.IBM_notm}} Research aus einer Analyse von Nachrichtenartikelsammlungen abgeleitet. Das Beispieltypsystem KLUE steht <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>hier<img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> zum Download bereit.

Viele Branchen, z. B. in den Fachgebieten Metallurgie, Geologie, Marktforschung, Biowissenschaften, elektronische Patientenakten und Onkologie veröffentlichen Wörterlisten oder Ontologien mit fachspezifischer Terminologie. Ziehen Sie das Referenzieren dieses Ressourcentyps in Betracht, um eine Vorstellung davon zu bekommen, welche Entitätstypen Sie in Ihrem eigenen Typsystem definieren sollten.

### Erwähnungen
{: #wks_typesystem__wks_typesystemS2}

Eine Erwähnung ist ein beliebiger Textbereich mit Daten, die Sie in Ihrem Fachgebiet als relevant erachten. In einem Typsystem für Kraftfahrzeuge können Begriffe wie `Airbag`, `Ford Explorer` und `Kinderrückhaltesystem` relevante Erwähnungen sein.

### Entitätstypen
{: #wks_typesystem__wks_typesystemS3}

Ein Entitätstyp gibt an, wie Sie ein Ding aus der realen Welt kategorisieren. Eine Entitätserwähnung ist ein Beispiel für ein Ding dieses Typs. Beispiel: Die Erwähnung `Bundeskanzlerin Merkel` kann als Entitätstyp `PERSON` annotiert werden. Die Erwähnung `{{site.data.keyword.IBM_notm}}` kann als Entitätstyp `ORGANISATION` annotiert werden. Entitäten sind häufig Substantive, aber sie können auch Verben sein, sofern die Erfassung des Verbs für die Zwecke der Anwendung, die das Typsystem verwenden wird, von Bedeutung ist. Beispiel: `EREIGNIS_UNFALL` kann ein gültiger Entitätstyp in einem Typsystem für Kraftfahrzeuge sein, mit dem das Wort `kollidierte` aus dem Satz `Das Fahrzeug kollidierte mit der Absperrung` annotiert werden kann.

Das Ziel Ihres Annotationsarbeitsbereichs besteht darin, jede Erwähnung in einem Dokument mit dem entsprechenden Objekttyp zu annotieren. Wenn eine Erwähnung nach Entitätstyp klassifiziert ist, wird der mit der Annotation beschriftete Textbereich als Entität bezeichnet.

Ein Typsystem, das Sie mit {{site.data.keyword.knowledgestudioshort}} erstellen, kann die folgenden Entitätstypattribute enthalten. Die Attribute unterstützen das Klassifizieren der Erwähnungen im Text, aber sie werden von einem Modell für maschinelles Lernen nicht als Entitätstypen markiert. Wenn der Entitätstyp `ORGANISATION` beispielsweise über einen Subtyp `KOMMERZIELL` verfügt, wird `KOMMERZIELL` nicht als eigenständiger Entitätstyp markiert.

- **Rolle**

    Qualifiziert die Erwähnung anhand des Kontexts, in dem sie vorkommt. Beispiel: Die Erwähnung `Frankreich` in der Aussage `die Studenten gingen nach Frankreich` wird mit dem Entitätstyp `GPE` markiert, da `Frankreich` eine geopolitische Entität ist. Da `Frankreich` in diesem Kontext aber auch ein Reiseziel der reisenden Studenten ist, wird der Entitätstyp zusätzlich durch ein Attribut (in diesem Fall `POSITION`) qualifiziert. Ein weiteres Beispiel: Die Erwähnung `Anwälte` kann mit dem Entitätstyp `MENSCHEN` und mit der Rolle `BERUF` markiert werden.

- **Entitätssubtyp**

    Ermöglicht die genauere Klassifizierung des Entitätstyps. Beispiel: Der Entitätstyp `ORGANISATION` kann die untergeordneten Subtypen `KOMMERZIELL`, `REGIERUNG`, `MILITÄR` und `BILDUNG` enthalten. 

- **Erwähnungstyp**

    Qualifiziert die Erwähnung nach bestimmten Wortarten:
    - **NAM**: Die Erwähnung ist ein Eigenname (z. B. der Name einer Person oder einer Organisation).
    - **NOM**: Die Erwähnung ist ein Nomen (allgemein gebräuchliches Substantiv) wie *Unternehmen* oder *Präsident*.
    - **PRO**: Die Erwähnung ist ein Pronomen, wie z. B. *er*, *wir* oder *es*.
    - **OHNE**: Keiner der drei anderen Erwähnungstypen ist zutreffend.

- **Erwähnungsklasse**

    Qualifiziert die Erwähnung durch die Angabe, ob es sich um eine spezifische, generische oder negierte Erwähnung handelt.
    - **SPC**: Es handelt sich um eine spezifische Erwähnung (im Deutschen häufig am Artikel *der/die/das* erkennbar, z. B. *das Buch* oder *der Hurricane wütete im September*). In diesen Beispielen würden die Erwähnungen *Buch* und *Hurricane* mit dem Attribut **SPC** annotiert.
    - **GEN**: Es handelt sich um eine generische Erwähnung wie *ein Buch* oder *Hurricanes treten meist im Herbst auf*. In diesen Beispielen würden die Erwähnungen *Buch* und *Hurricanes* mit dem Attribut **GEN** annotiert.
    - **NEG**: Es handelt sich um eine negierte (verneinte) Erwähnung wie *kein Buch*. Beim Trainieren eines Modells kann der Algorithmus aus negativen und aus positiven Beispielen lernen, daher ist es wichtig, beide Arten von Erwähnungen zu markieren.

### Beziehungstypen
{: #wks_typesystem__wks_typesystemS4}

Ein Beziehungstyp definiert eine binäre, geordnete Beziehung zwischen zwei Entitäten. Eine Beziehungserwähnung liegt vor, wenn im Text die Beziehung und die Bindung der beiden erwähnten Entitäten in einem einzigen Satz explizit definiert werden. Beispiel: `Mary arbeitet bei {{site.data.keyword.IBM_notm}}` ist ein Textbeleg für den Beziehungstyp `beschäftigtBei`.

Bei einigen Beziehungstypen ist die Reihenfolge der Entitätserwähnungen von Bedeutung. Beispiel: Im Beziehungstyp `beschäftigtBei` kann der Entitätstyp `PERSON` oder `MENSCHEN` an erster Stelle der Beziehung erwähnt werden und `ORGANISATION` oder **GPE** an zweiter Stelle, jedoch nicht umgekehrt. `Mary` `beschäftigtBei` `{{site.data.keyword.IBM_notm}}` ist eine gültige Beziehung. `{{site.data.keyword.IBM_notm}}` `beschäftigtBei` `Mary` ist keine gültige Beziehung. Bei manchen Beziehungstypen wie `EhepartnerVon`, `Kollege` oder `Geschwister` ist die Reihenfolge nicht von Bedeutung. Beim Definieren eines Beziehungstyps, bei dem die Reihenfolge nicht von Bedeutung ist, hat es sich bewährt, in den Annotationsrichtlinien Informationen hinzuzufügen, die die Verwendung des Beziehungstyps regeln. Eine Konvention zum Beschreiben einer solchen symmetrischen Beziehung ist der Hinweis darauf, dass die im Text zuerst erwähnte Entität auch die erste Entität in der Beziehung sein sollte.

**Zugehörige Konzepte**:

[Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html)

## Typsystem zum Arbeitsbereich hinzufügen
{: #wks_projtypesys}

Vor dem Ausführen von Annotationstasks müssen Sie ein Typsystem erstellen oder hochladen.

### Informationen zu diesem Vorgang

Für Typsystemeinträge gelten die folgenden Benennungsregeln:

- Namen dürfen keine Leerzeichen enthalten.
- Verwenden Sie nur die folgenden alphanumerischen ASCII-Zeichen und das Unterstreichungszeichen in Werten, die Sie zum System hinzufügen: `A` bis `Z`, `a` bis `z`, `0` bis `9`.
- Das erste Zeichen in einem Entitäts- oder Beziehungstypnamen muss ein Buchstabe sein.
- Entitätstypnamen dürfen nicht länger als 64 Zeichen sein.
- Beziehungstypnamen dürfen nicht länger als 128 Zeichen sein.

Namenskonvention: Entitätstypnamen werden in Großbuchstaben angegeben (z. B. `ORGANISATION`) und Beziehungstypnamen in Kamelschreibweise (`beschäftigtBei`). Diese Konvention ist optional.

### Vorgehensweise

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und öffnen Sie die Seite **Assets** > **Entitätstypen**.
1. Wählen Sie eine der folgenden Methoden aus, um ein Typsystem zu erstellen:

    - Laden Sie ein vorhandenes Typsystem hoch:

        1. Klicken Sie auf der Registerkarte **Entitätstypen** auf **Hochladen**.

            Wenn Sie zuvor ein Typsystem aus einem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich heruntergeladen haben, wird das Typsystem im `JSON`-Format heruntergeladen. Sie können dieses Typsystem hochladen, um die Erstellung eines Arbeitsbereichs zu beschleunigen. Details hierzu finden Sie unter [Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html).

            > **Hinweis:** Unabhängig von der Herkunft des Typsystems müssen die in dem System enthaltenen Einträge die oben angegebenen Namenskonventionen einhalten.

        1. Sie können Entitätstypen und Beziehungstypen auf die gleiche Weise hinzufügen, bearbeiten und löschen, wie bei der Neuerstellung eines Typsystems.

    - Erstellen Sie ein Typsystem völlig neu:

        1. Klicken Sie auf der Registerkarte **Entitätstypen** auf **Entitätstyp hinzufügen**.
        1. Geben Sie einen beschreibenden Namen für den Entitätstyp an. Beachten Sie dabei, dass ein Entitätstyp eine Bezeichnung zum Annotieren wichtiger Textabschnitte (Erwähnungen) in Ihrem fachspezifischen Inhalt ist. Wählen Sie einen kurzen und aussagefähigen Namen, den sich Annotatorbenutzer leicht merken können.

            Sie können optional auch Rollen und Subtypen für den Entitätstyp definieren.
            - Eine Rolle qualifiziert einen Entitätstyp im jeweiligen Kontext, in dem die Erwähnung vorkommt. Beispiel: Die Erwähnung `Softwareentwickler` kann mit dem Entitätstyp `MENSCHEN` und im vorliegenden Kontext mit der Rolle `BERUF` bezeichnet werden. Siehe [Wann sollten Rollen definiert werden?](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles).
            - Ein Subtyp ermöglicht die genauere Klassifizierung des Entitätstyps. Beispiel: Der Entitätstyp `REGIERUNG` kann über die Subtypen `MILITÄRISCH` und `ZIVIL` verfügen.

            > **Hinweis:** Durch das Definieren einer Rolle oder eines Subtyps für eine Entität geben Sie der Person, die Typinformationen für Erwähnungen zuordnen wird, zusätzliche Optionen für Annotationen. Der Annotatorbenutzer kann eine Annotation anwenden, die nur den Entitätstyp angibt, oder zusätzlich die Rolle oder den Subtyp, die bzw. den Sie jetzt definieren.

            Achten Sie darauf, genügend Entitätstypen zu definieren, um die zentralen Konzepte zu erfassen, die Sie annotieren möchten. Es sollten jedoch nicht so viele Entitätstypen sein, dass es für Annotatorbenutzer mühsam wird, die Bezeichnungen präzise anzuwenden.

        1. Klicken Sie auf **Erwähnungsklassen** und **Erwähnungstypen**, um die Standardklassen und -typen für Erwähnungen anzuzeigen. Sie können diese Werte nicht bearbeiten.

            Der Zweck eines Attributs besteht darin, jede Erwähnung mit dem Objekttyp zu beschriften, den sie repräsentiert. Ein Erwähnungstyp gibt an, ob die Erwähnung ein Name, ein Substantiv oder ein Pronomen ist, und eine Erwähnungsklasse gibt an, ob es sich um eine spezifische, generische oder negierte (verneinte) Erwähnung handelt.

        1. Öffnen Sie die Seite **Assets** > **Beziehungstypen** und geben Sie an, in welcher Beziehung zwei Erwähnungen zueinanderstehen können.

            In der Regel ist die Reihenfolge zwischen der ersten und der zweiten Entität in einem Beziehungstyp von Bedeutung. Beispiel: Eine Entität `PERSON` kann Mitarbeiter einer Entität `ORGANISATION` oder eine geopolitische Entität (**GPE**) sein, wie z. B. `Mary` `beschäftigtBei` `{{site.data.keyword.IBM_notm}}`. Aber Organisationen und geopolitische Entitäten können nicht Mitarbeiter einer Person sein. Wenn ein Annotatorbenutzer im Ground Truth-Editor auf eine Entität klickt, wird die Liste der verfügbaren Beziehungstypen durch das definierte Typsystem gesteuert.

            Definieren Sie keine Beziehungsattribute. Sie werden vom Modell für maschinelles Lernen nicht verwendet. Das Modell verwendet nur den Beziehungstyp und die Beziehungsreihenfolge; Beziehungsattribute werden ignoriert.

        1. Verwenden Sie die Symbole **Bearbeiten** und **Löschen**, um Entitätstypen und die zugehörigen Beziehungstypen zu ändern oder um einen Entitäts- oder Beziehungstyp im Typsystem zu löschen.

            Beim Löschen einer Entität, die in einer Beziehungstypdefinition verwendet wird, wird auch die Beziehungstypdefinition gelöscht.

**Zugehörige Tasks**:

[Typsystem ändern, ohne von Annotatorbenutzern erstellte Annotationen zu verlieren](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Richtlinien für die Erstellung von Typsystemen
{: #wks_typesys_guidelines}

Der Zweck eines Typsystems in {{site.data.keyword.knowledgestudioshort}} besteht darin, zu definieren, wie Textbereiche annotiert werden können. Wenn Sie ein Typsystem völlig neu erstellen möchten, halten Sie sich an die folgenden Richtlinien:

Konzentrieren Sie sich auf die Erstellung eines Bestands von Entitäts- und Beziehungstypen, die die Informationen abdecken, die von der Anwendung benötigt werden, in der das Typsystem verwendet wird. Beziehen Sie keine Dinge ein, die nicht benötigt werden. Teilen Sie die einzelnen Typen nicht weiter auf und verwenden Sie keine Unterscheidungen, die für die Anwendung nicht erforderlich sind. Angenommen, das Quellendokument enthält den Satz `Mord im Orient Express machte Schlagzeilen`. Welche Entitätstypen definiert werden, um die zentralen Informationen aus diesem Satz zu erfassen, hängt davon ab, von welchem Anwendungstyp das Modell genutzt wird, das Sie anhand des Typsystems erstellen.

- Für eine literarische Anwendung können Sie Typen erstellen, die folgende Informationen erfassen:

    ```
               [ROMAN][CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Mord im Orient-Express][made headlines]
    ```
    {: screen}

- Für eine Anwendung für die öffentliche Sicherheit können Sie die folgenden Typen erstellen:

    ```
    [EREIGNIS_VERBRECHEN][LOCATION]
    ```
    {: screen}

    ```
      [Mord] im [Orient Express] machte Schlagzeilen
    ```
    {: screen}

Die Struktur wird häufig durch die Merkmale der Dokumente bestimmt, aus denen Informationen extrahiert werden. Sie sollte jedoch stets darauf abgestimmt werden, welche Informationen aus den Dokumenten tatsächlich in der Anwendung genutzt werden. Angenommen, Sie erstellen eine Anwendung, die Erkenntnisse aus Patientendatensätzen gewinnt. Beim Erstellen des Typsystems suchen Sie zunächst in Patientendatensätzen danach, welche Arten von Informationen erfasst werden müssen. Möglicherweise enthalten alle Patientendatensätze ein Feld, in dem angegeben ist, was der Patient am Mittag gegessen hat. Wenn diese Informationen für die Anwendung nicht erforderlich sind, fügen Sie sie nicht zum Typsystem hinzu. Diese Entscheidung bedeutet zugleich, dass die betreffenden Abschnitte aus den Dokumenten mit Patientendatensätzen nicht annotiert werden müssen. Das ist völlig in Ordnung und soll auch so sein.

Erwähnungen sind Annotationen für einen Textbereich; sie ersetzen nicht den Textbereich. Ein Typsystem ist keine Ontologie für ein Fachgebiet. Sie sollten allgemeine Entitätstypen wie `MEDIKATIONSNAME` verwenden und nicht spezielle Entitätstypen für die einzelnen Medikamenttypen. Der Name des jeweiligen Medikaments ist schließlich im Dokumenttext aufgeführt. Die hinzugefügte Annotation identifiziert nur den Typ des Medikaments, um das programmgesteuerte Erkennen und Extrahieren dieser Informationen zu vereinfachen.

Definieren Sie zunächst 10 bis 40 Entitäts- und Beziehungstypen. Bleiben Sie im unteren Teil des Bereichs, wenn die Annotatorbenutzer, die den Arbeitsbereich bearbeiten, keine erfahrenen Fachleute sind. Definieren Sie nicht mehr als 50 Typen.

Nehmen Sie sich viel Zeit und planen Sie das Typsystem gründlich, bevor Ihr Team mit den Annotatorbenutzertasks beginnt. Wenn das Team die ersten Dokumente annotiert, sollte zunächst eine kleine Gruppe von Typen (möglichst nicht mehr als 50) verfügbar sein. Annotieren Sie anfangs nur Erwähnungen, prüfen Sie die Ergebnisse und optimieren Sie die Annotationsrichtlinien und das Typsystem entsprechend. Wenn die Ergebnisse der Annotationen für Erwähnungen Ihre Erwartungen erfüllen, können Sie mit dem Annotieren von Beziehungen und Koreferenzen fortfahren.

Während der grundlegenden Definitionsphase für Entitätstypen und für Annotationsrichtlinien für Erwähnungen sollte der Aufwand für das Annotieren von Beziehungserwähnungen möglichst gering gehalten werden. Änderungen von Erwähnungen können die in das Annotieren von Beziehungen investierte Arbeit zunichte machen. Nehmen Sie sich ausreichend Zeit zum Definieren einer Gruppe von Beziehungstypen und der dafür zulässigen Entitätstyppaare, damit die relevanten Beziehungstypen berücksichtigt werden, bevor der Entitätstypbestand abgeschlossen wird.

Gehen Sie davon aus, dass das Typsystem mit zunehmender Erfahrung der Annotatorbenutzer weiterentwickelt wird. Wenn Sie das Typsystem nach dem Erstellen von Annotationsbenutzertasks überarbeiten, müssen Sie entscheiden, ob die Änderungen auf jede einzelne Task angewendet werden sollen. Wenn Sie die Änderungen anwenden, müssen Annotatorbenutzer die zuvor von ihnen annotierten Dokumente erneut bearbeiten.

Beim Testen des Modells können Sie auf Statistikdaten zurückgreifen, die zeigen, wie häufig die Entitäts- und Beziehungstypen in Ihren Beispieldokumenten vorkommen. Diese Statistikdaten sollten unbedingt geprüft werden. Um sicherzustellen, dass Ihre Anwendung genügend Kontext erhält, um große Dokumentsammlungen präzise zu annotieren, müssen Ihre Testdaten eine umfangreiche Stichprobe der wichtigsten Entitäts- und Beziehungstypen enthalten.

> **Wichtig:** Nach dem Trainieren Ihres ersten Modells müssen Sie wahrscheinlich Änderungen gemäß der Leistungsstatistik vornehmen. Um ein zuverlässiges statistisches Modell für maschinelle Annotationen zu erstellen, sollte das Typsystem einen möglichst finalen Stand erreicht haben, bevor es für umfangreiche Annotationstasks eingesetzt wird.

## Wann sollten Rollen definiert werden?
{: #wks_typesystem_roles}

Durch die Verwendung von Rollen können Sie präzisere Entitätstypen definieren.

Jede Entität, die Sie hinzufügen, verfügt über eine Rolle. Sofern Sie keine Änderung vornehmen, stimmt der Rollenname mit dem Entitätsnamen überein. Sie können eine andere Rolle für eine Entität definieren, um die Verwendung der Erwähnung stärker zu differenzieren. Das Wort oder der Ausdruck, auf das bzw. den die Rolle angewendet wird, ist im Grunde ein bestimmter Entitätstyp, der in dem betreffenden Satz jedoch die Rolle eines anderen Entitätstyps übernimmt. Beispiel: In dem Ausdruck `das Weiße Haus legte sein Veto gegen den Gesetzesentwurf ein` kann die Bedeutung von `Weißes Haus` besser erfasst werden, wenn es mit dem Entitätstyp `EINRICHTUNG` und der Rolle `ORGANISATION` oder `PERSON` annotiert wird. Das Weiße Haus ist ein Gebäude (`EINRICHTUNG`), das in diesem Ausdruck die Regierung (`ORGANISATION`) oder den Präsidenten der Vereinigten Staaten (`PERSON`) repräsentiert. Das Zuordnen eines Entitätstyps und einer Rolle führt zu einer genaueren Klassifizierung der Erwähnung in dem Text.

Rollen bieten außerdem die Möglichkeit zum Erfassen von Beziehungsinformationen, ohne auf sich überschneidende Erwähnungen zurückzugreifen. Beispiel: Sie möchten den Text `31-jähriger, männlich` so annotieren, dass sie als Verweis auf eine Person mit dem Alter '31 Jahre' und dem Geschlecht 'Mann' erfasst wird. Beim Untersuchen des Texts stellen Sie fest, dass `31-jährig` eine Altersangabe ist, `männlich` eine Geschlechtsangabe und dass beide Angaben zusammen eine Person bezeichnen. Sie haben es also mit den drei Entitätstypen `ALTER`, `GESCHLECHT` und `PERSON` zu tun. Ein Ansatz zum Erfassen dieser Typen besteht darin, `31-jährig` mit `ALTER` und `männlich` mit `GESCHLECHT` zu annotieren. Da die ausdrückliche Erwähnung einer `PERSON` fehlt, aber `männlich` als Person interpretiert wird, kann dem Wort `männlich` die Rolle `PERSON` zugeordnet werden. Anschließend können Sie Beziehungen zwischen der Rolle `PERSON` und allen gewünschten Attributen einer Person erfassen. Sie können zum Beispiel eine Beziehung `hatAttribut` zwischen der Rolle `PERSON` und der Erwähnung `ALTER` definieren. Da Sie sowohl den Entitätstyp `GESCHLECHT` als auch den Rollentyp `PERSON` demselben `männlich` zugewiesen haben, können Sie keine Beziehung `hatAttribut` zwischen beiden Typen definieren. Da die beiden Bezeichnungen jedoch derselben Erwähnung zugeordnet wurden, sind beide miteinander verknüpft. Diese Verknüpfung wird von dem Modell für maschinelles Lernen berücksichtigt, und Sie müssen keinen Beziehungstyp 'hatAttribut' definieren, um die Beziehung ausdrücklich hervorzuheben.

Ein ähnliches Beispiel ist die Verwendung des Ausdrucks `Ford F-150, 2008` als Kurzform für `Lastkraftwagen Ford F-150, Baujahr 2008`. In diesem Beispiel wird `2008` als Entitätstyp `BAUJAHR` annotiert, `Ford` als Entitätstyp `HERSTELLER` und `F-150` als Entitätstyp `MODELL`. Da das Wort `Lastwagen` fehlt, bezeichnet `F-150` außerdem ein Fahrzeug. Der Ausdruck `der F-150` ist gleichbedeutend mit `der Lastkraftwagen`. Sie können diese Verwendung erfassen, indem Sie eine Rolle `FAHRZEUG` zum Entitätstyp `MODELL` für die Erwähnung hinzufügen. Anschließend können Sie die Beziehung `hatAttribut` zwischen der Rolle `FAHRZEUG` und den Entitätstypen `HERSTELLER` und `BAUJAHR` für die Erwähnung definieren.

### Worin unterscheiden sich Rollen und Subtypen?

Entitätssubtypen formen aus einem Bestand von Entitätstypen eine hierarchische Struktur. Wenn Sie beispielsweise 40 Objekte unterscheiden möchten, die logisch betrachtet 10 Gruppen mit je 4 Objekten bilden (`VITALZEICHEN_BLUTDRUCK`, `VITALZEICHEN_HERZFREQUENZ`, `MEDIKATION_DOSIERUNG`, `MEDIKATION_HÄUFIGKEIT`), können Sie die Objekte in Typen und Subtypen aufteilen. Dies führt zu kompakten Menüs und ermöglicht zugleich mehr Bedeutungstiefe und Diversifizierung bei der Verarbeitung der Bezeichnungen. Aus der Perspektive der Informationsextraktion kann eine Kombination aus Typen und Subtypen gegen beliebig viele gleichgeordnete Typen ohne Subtypen ausgetauscht werden. Im Gegensatz dazu ist ein Wort oder Ausdruck ein Beispiel für einen bestimmten Entitätstyp, der zwar die Rolle eines anderen Entitätstyps übernimmt, aber kein Subtyp des anderen Entitätstyps ist.

### Wie werden Rollen verarbeitet?

Das {{site.data.keyword.knowledgestudioshort}}-Modell für maschinelles Lernen definiert Klassifikationsbezeichnungen für jede Erwähnung einer Entität, die in den Quellendokumenten gefunden wird. Dabei werden die Werte für den Entitätstyp und die Rolle verknüpft. Wenn Sie Rollenwerte angeben, können präzisere Bezeichnungen erstellt werden. Jede Gruppe mit Instanzen eines Bezeichnungstyps, die in den Trainingsdaten gefunden werden, trägt zu einer gleichmäßigeren Gruppe der Erwähnungen bei. Um eine höhere Genauigkeit zu erzielen, müssen Sie jedoch ein größere Menge an Trainingsdaten bereitstellen, damit das Modell gut funktioniert. Je mehr Trainingsdaten Sie bereitstellen, umso besser wird das Modell. Wenn Sie den zusätzlichen Aufwand für weitere Annotationen in Kauf nehmen, können Sie durch die Verwendung von Rollen bessere Ergebnisse erzielen.

Angenommen, ein Quellendokument enthält die folgenden Sätze und die Bezeichnungen `Acme` (`Acme` ist ein bekannter Hersteller von Lastkraftwagen), `Limousine` und `Lastwagen` sollen als ähnliche Entitäten erfasst werden, da sie alle bestimmte Fahrzeugtypen bezeichnen:

- a) `Der Acme krachte in die Betonmauer.`
- b) `Die Limousine krachte in die Betonmauer.`
- c) `Der Lastwagen Acme A-160 krachte in die Betonmauer.`

Das zugehörige Typsystem kann auf zwei Arten erstellt werden:

1. Definieren Sie die beiden Entitätstypen `HERSTELLER` und `FAHRZEUG`. Definieren Sie für die Entität `HERSTELLER` eine Rolle `FAHRZEUG`, die als Ergänzung zur Standardrolle `HERSTELLER` verwendet werden kann.

    Mit diesem Typsystem werden die Sätze wie folgt annotiert:
    - a) Die Erwähnung `Acme` wird mit der Entität `HERSTELLER` annotiert und mit der Rolle `FAHRZEUG`, da sie auf ein konkretes Fahrzeug verweist. Die entsprechende interne Bezeichnung lautet daher `HERSTELLER-FAHRZEUG`.
    - b) Die Erwähnung `Limousine` wird mit dem Entitätstyp `FAHRZEUG` annotiert.Da keine andere Rolle definiert ist, wird automatisch die Rolle `FAHRZEUG` zugeordnet.
    - c) Die Erwähnung `Acme` wird mit dem Entitätstyp `HERSTELLER` annotiert und `Lastwagen` mit dem Entitätstyp `FAHRZEUG`. Da keine Rollen zugeordnet sind, werden die Standardrollen verwendet.

1. Definieren Sie nur die beiden Entitätstypen `HERSTELLER` und `FAHRZEUG` ohne Rollen.

    Mit diesem Typsystem werden die Sätze wie folgt annotiert:
    - a) Die Erwähnung `Acme` wird mit dem Entitätstyp `FAHRZEUG` annotiert.
    - b) Die Erwähnung `Limousine` wird mit dem Entitätstyp `FAHRZEUG` annotiert.
    - c) Die Erwähnung `Acme` wird mit dem Entitätstyp `HERSTELLER` annotiert und `Lastwagen` mit dem Entitätstyp `FAHRZEUG`. 

Wie funktionieren die beiden verschiedenen Typsysteme? Angenommen eine Dokumentgruppe wird von Annotatorbenutzern bearbeitet. Nach dem Annotieren sind im Trainingskorpus die folgenden manuell beschrifteten Ereignisse als Trainingsereignisse identifiziert:

- **Typsystem 1**

    ```
    HERSTELLER-HERSTELLER, 800 Ereignisse
    HERSTELLER-FAHRZEUG, 200 Ereignisse
    FAHRZEUG-FAHRZEUG, 400 Ereignisse
    ```
    {: screen}

- **Typsystem 2**

    ```
    HERSTELLER, 800 Ereignisse
    FAHRZEUG, 200 + 400 = 600 Ereignisse
    ```
    {: screen}

Wenn das Modell neue Dokumente verarbeitet, wird die Erwähnung `Acme` wahrscheinlich in den meisten Fällen als `HERSTELLER` bezeichnet, da die Schreibweise eines Worts einen hohen Stellenwert hat und das Wort `Acme` wahrscheinlich im Wörterverzeichnis `HERSTELLER` definiert ist. Es wäre viel Kontext erforderlich, damit eine andere Bezeichnung zugeordnet würde. Bei Verwendung von Typsystem 1 werden nur 200 Trainingsereignisse `HERSTELLER-FAHRZEUG` identifiziert. Dies ist ein Nachteil im Vergleich zu den 600 Ereignissen des Typs `FAHRZEUG` in Typsystem 2. Da die Cluster der Trainingsereignisse jedoch sehr einheitlich sind, wird eine bessere Leistung erzielt. Die Gruppe der 600 Trainingsereignisse für `FAHRZEUG` im Typsystem 2 besteht aus zwei stark abgegrenzten Clustern: ein Cluster mit Herstellernamen, der auf konkrete Fahrzeuge wie `Acme` und `Ford` verweist, und ein Cluster mit Fahrzeugtypen wie `Limousine`, `SUV` und `Lastwagen`. Auf den ersten Blick handelt es sich um zwei jeweils gleichförmige Cluster. Werden Sie jedoch miteinander vermischt, so führt dies zu einem 'verwässerten' (unspezifischen) Trainingscluster, der ein schwer zu lösendes Problem darstellt. Wenn Sie weitere Annotationen vornehmen und weitere Trainingsereignisse hinzufügen, wird die Leistung des Typsystems 1 immer besser, während die beiden disjunkten Cluster im Typsystem 2 durch weiteres Training nicht verbessert werden können.
