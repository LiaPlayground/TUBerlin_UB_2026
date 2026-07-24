<!--
author:   Sebastian Zug, André Dietrich

email:    sebastian.zug@informatik.tu-freiberg.de

version:  0.1.0

language: de

narrator: Deutsch Male

mode:     Presentation

date:     24/07/2026

comment:  Demo-Modul (Phase 1) für den Workshop "Interaktive OER mit
          LiaScript" an der TU Berlin, Universitätsbibliothek
          (24.07.2026). Ein durchgängig interaktives Mini-Modul zur
          Erkundung.

repository: https://github.com/LiaPlayground/TUBerlin_UB_2026

attribute: Interaktive OER mit LiaScript
           von Sebastian Zug und André Dietrich
           ist lizenziert unter [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

import:   https://github.com/LiaTemplates/Pyodide

link:     style.css

-->

[![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/TUBerlin_UB_2026/main/01_Erleben.md)

# LiaScript im Bibliotheksalltag

> <h2>Phase 1 — Erleben</h2>
>
> <div style="height: 2.5em;"></div>
>
> <h4>Prof. Dr. Sebastian Zug, TU Bergakademie Freiberg</h4>
> <h4>Dr. André Dietrich, TU Bergakademie Freiberg</h4>
>
> <h4>TU Berlin · Universitätsbibliothek · 24. Juli 2026</h4>

--------------------------------------------


## Motivation

Dieses Modul ist Ihr **erster Kontakt** mit einem fertigen LiaScript-Kurs. Es enthält drei inhaltliche Miniaturen aus dem Bibliotheksalltag — jede führt ein **Kernfeature** von LiaScript ein:

1. **Metadaten**
2. **Datenkompetenz**
3. **Recherchekompetenz**

> **Aufgabe während der nächsten 20 Minuten**
>
> Gehen Sie die Seiten durch, probieren Sie alle interaktiven Elemente aus und notieren Sie sich vier Dinge:
>
> - Was hat Sie überrascht?
> - Welches Element würden Sie in Ihrer eigenen Schulung einsetzen?
> - Was möchten Sie im Tutorial-Teil unbedingt lernen?
> - Was hat vielleicht anders funktioniert als erwartet?

> [!TIP]
> Klicken Sie rechts unten auf den Pfeil nach rechts, um auf die nächste Seite zu blättern. Alternativ können Sie auch die Pfeiltaste auf Ihrer Tastatur verwenden.

## Konzept

Die drei Miniaturen sollen einen Eindruck vermitteln, wie LiaScript die Wissensvermittlung unterstützt. Jeder Abschnitt fokussiert dabei einen anderen Aspekt:

| Abschnitt          | Fokus                                                                                          |
| ------------------ | ---------------------------------------------------------------------------------------------- |
| Metadaten          | *von abstrakten Definitionen zu multimodalen Inhalten* - Wissensvermittlung ohne Medienbrüche  |
| Datenkompetenz     | *von Daten zum Code* - Integrierte Programmierumgebungen                                        |
| Recherchekompetenz | *von Visualisierungen zu Quizzen* - Interaktive Wissensüberprüfung                              |

> [!NOTE]
> **Drei wiederkehrende Bausteine** helfen Ihnen, sich auf den Seiten zu orientieren:
>
> - **Tipp** (💡, gelb hinterlegt) — Definitionen, Begriffsklärungen und Bedienhinweise.
> - **Note** (blau hinterlegt) — Lese-Empfehlungen: *worauf* Sie in diesem Abschnitt achten sollten.
> - **Mini-Aufgabe** — kleine Explorationsaufgaben, mit denen Sie das Gezeigte selbst ausprobieren; oft folgt eine ausklappbare Auflösung.
>
> **Bitte scrollen Sie auf jeder Seite bis ganz nach unten** — wichtige Inhalte (Beispiele, Code, Aufgaben, Lösungen) stehen oft *unterhalb* des sichtbaren Bereichs.

## 1. Metadaten

> [!TIP]
> **Definition** Metadaten sind beschreibende Daten *über* einen bibliografischen Datensatz — Titel, Autor, Verlag, Schlagwort. Aber wie genau werden diese Daten strukturiert, damit sie von Menschen und Maschinen verstanden werden? Und wie sieht das in der Praxis aus?

> [!NOTE]
> **Worauf Sie in diesem Abschnitt achten sollten:** Sie begegnen demselben Sachverhalt in *mehreren Darstellungen* — einem erklärenden Video und konkreten Metadaten-Beispielen als Code. Alle liegen auf *dieser* Seite. Das ist gemeint, wenn LiaScript verspricht, *Wissensvermittlung ohne Medienbrüche* zu ermöglichen: keine Tab-Wechsel, keine Tool-Sprünge, kein Kontextverlust.

### Einstieg per Video

Bevor wir in die Details gehen, ein kurzer Überblick zum Thema:

> [!NOTE]
> Sie müssen das Video nicht komplett anschauen — es dient als Einstieg und zur Illustration.

!?[Metadaten Einführungsvideo](https://www.youtube.com/watch?v=5HJVfp5c0kE)

### Abstraktion und Strukturierung

Offenbar ist es nicht genug, einfach nur Label für Titel, Autor und Verlag zu definieren. Es braucht eine Systematik, damit die Daten von verschiedenen Bibliotheken und Repositorien in derselben Weise interpretiert werden können.

Welche Felder ein OER-Datensatz haben sollte, legen **Metadatenprofile** fest — etwa das **LOM-Profil für Hochschul-OER** der [DINI-AG-KIM](https://dini-ag-kim.github.io/hs-oer-lom-profil/latest/), das mehrere deutsche Hochschul- und Bibliotheks-Repositorien gemeinsam pflegen und aus dem sich auch der OER-Suchindex [OERSI](https://oersi.org) speist. Statt die Spezifikation durchzulesen, prüfen wir das lieber am konkreten Fall.

> **Mini-Aufgabe:** Und jetzt wird es konkret — unten sehen Sie den Metadatensatz **genau dieses Kurses** (den Sie gerade lesen!), beschrieben nach dem **LOM-Profil für Hochschul-OER**. Stellen Sie sich vor, eine Kollegin aus einem anderen Haus möchte dieses Material **nachnutzen und anpassen**. Lesen Sie den Satz durch: Ist die Beschreibung dafür *vollständig* — oder fehlt eine entscheidende Kategorie?

```xml
<lom>
  <general>
    <title><langstring>LiaScript im Bibliotheksalltag</langstring></title>
    <language>de</language>
  </general>

  <lifecycle>
    <version><langstring>0.1.0</langstring></version>
    <contribute>
      <role><value>author</value></role>
      <centity><vcard>Sebastian Zug</vcard></centity>
      <date><datetime>2026-07-24</datetime></date>
    </contribute>
    <contribute>
      <role><value>author</value></role>
      <centity><vcard>André Dietrich</vcard></centity>
    </contribute>
  </lifecycle>
</lom>
```

> [!TIP]
> Gehen Sie die fünf V-Freiheiten im Kopf durch: *verwenden, verarbeiten, vermischen, verbreiten* — was davon dürfte die Kollegin auf Basis dieses Satzes überhaupt rechtssicher tun?

### Lösung

> **Auflösung:** Es fehlt die **Rights-Kategorie** — also die Lizenzangabe. `General` (Titel, Sprache) und `Lifecycle` (Version, Autoren, Datum) sind da, aber es gibt kein `<rights>`-Element. Ohne eine ausdrückliche offene Lizenz (z. B. `https://creativecommons.org/licenses/by-sa/4.0/`) ist *rechtlich unklar*, ob das Material überhaupt bearbeitet oder weitergegeben werden darf. Ohne diese Angabe ist es **streng genommen gar kein OER** — denn die V-Freiheiten *verarbeiten*, *vermischen* und *verbreiten* setzen eine offene Lizenz voraus.
>
> **Warum das wichtig ist:** „Frei zugänglich im Netz" und „offen lizenziert" sind zwei verschiedene Dinge. Ein Material ohne Lizenzangabe gilt urheberrechtlich als *„alle Rechte vorbehalten"* — auffindbar, aber nicht nachnutzbar. Genau hier liegt eine Kernkompetenz der Bibliothek: Materialien nicht nur zugänglich, sondern rechtssicher *nachnutzbar* zu machen. Die Rights-Kategorie ist deshalb das Feld, das eine OER überhaupt erst zur OER macht.

Zum Vergleich derselbe Kurs — diesmal **mit** der eben vermissten `<rights>`-Kategorie. Und tatsächlich: Werfen Sie einen Blick in die Markdown-Quelle dieses Kurses (oder klicken Sie unten auf das i-Icon) — die Lizenz `CC BY-SA 4.0` steht dort im `attribute`-Feld. Achten Sie darauf, wie sie hier als Klartext *und* als maschinenlesbare URL hinterlegt ist:

```xml
<lom>
  <general>
    <title><langstring>LiaScript im Bibliotheksalltag</langstring></title>
    <language>de</language>
  </general>

  <lifecycle>
    <version><langstring>0.1.0</langstring></version>
    <contribute>
      <role><value>author</value></role>
      <centity><vcard>Sebastian Zug</vcard></centity>
      <date><datetime>2026-07-24</datetime></date>
    </contribute>
    <contribute>
      <role><value>author</value></role>
      <centity><vcard>André Dietrich</vcard></centity>
    </contribute>
  </lifecycle>

  <rights>
    <copyrightandotherrestrictions>
      <value>yes</value>
    </copyrightandotherrestrictions>
    <description>
      <langstring xml:lang="x-t-cc-url">https://creativecommons.org/licenses/by-sa/4.0/</langstring>
    </description>
  </rights>
</lom>
```

> [!TIP]
> Klicken Sie rechts oben in der Ecke auf das **i-Icon** (ℹ️), um die Metadaten dieses Kurses in einer übersichtlichen Darstellung zu sehen.

## 2. Datenkompetenz

> [!TIP]
> ... (engl. Data Literacy) ist die Fähigkeit, Daten auf kritische Art und Weise zu sammeln, zu verwalten, zu bewerten, zu analysieren und zu interpretieren. Sie umfasst zudem die Fähigkeit, mit Daten zu kommunizieren und sie zu nutzen, um fundierte Entscheidungen zu treffen.
>
> *(Heidrich, Bauer & Krupka 2018, „Future Skills: Ansätze zur Vermittlung von Data Literacy in der Hochschulbildung", Hochschulforum Digitalisierung, Arbeitspapier 37)*

> [!NOTE]
> **Worauf Sie in diesem Abschnitt achten sollten:** Der Abschnitt zeigt, wie LiaScript die Integration von Code und Daten in Lernmaterialien ermöglicht — und damit die Entwicklung von Datenkompetenz unterstützt.

### Ausleihen als interaktives Diagramm

Verschaffen wir uns zunächst einen Überblick - ein fiktives Beispiel aus einer Bibliothek, das die Anzahl der Ausleihen und Vormerkungen pro Monat zeigt. Nutzen Sie die Stapel am rechten Spaltenrand um die Daten zu sortieren und bestimmen Sie, in welchem Monat es die meisten Ausleihen gab.

<!-- data-type="barchart" -->
| Monat | Ausleihen | Vormerkungen |
| ----- | ---------:| ------------:|
| Jan   |      1240 |           95 |
| Feb   |      1180 |          102 |
| Mär   |      1320 |          110 |
| Apr   |      1450 |          135 |
| Mai   |      1610 |          128 |
| Jun   |      1555 |          140 |

> [!TIP]
> Noch einfacher geht es mit dem integrierten Diagrammgenerator: klicken Sie auf den Button Balkendiagramm über der Tabelle, um die Daten visuell zu erkunden. Finden Sie in der Werkzeugleiste unter dem Diagramm die Möglichkeit, die Daten gleich zu bearbeiten?

### Darf es ein bisschen Code sein?

> [!TIP]
> Manchmal reicht es nicht, Daten zu visualisieren - wir wollen auch Kennzahlen berechnen, um die Daten zu interpretieren. In diesem Beispiel wollen wir die Vormerkungsquote berechnen - also den Anteil der Vormerkungen an den Ausleihen pro Monat.
>
> Wir haben Ihnen den Code schon vorgegeben — führen Sie ihn zunächst über den **Ausführen-Button** (`</>`, unten links am Code-Block) aus. Anschließend aktivieren Sie die Berechnung der Vormerkungsquote: In Zeile 14 beginnt die Anweisung mit einem `#`-Zeichen (Python-Kommentar). Löschen Sie genau dieses eine `#` direkt vor `daten[...]` und führen Sie den Code erneut aus.

```python        python_example.py
import pandas as pd

# hier werden die Daten als DataFrame angelegt - eine tabellarische
# Datenstruktur, die in Python häufig verwendet wird
daten = pd.DataFrame({
    "Monat":        ["Jan", "Feb", "Mär", "Apr", "Mai", "Jun"],
    "Ausleihen":    [ 1240,  1180,  1320,  1450,  1610,  1555],
    "Vormerkungen": [   95,   102,   110,   135,   128,   140]
})

# Berechne die Vormerkungsquote als neue Spalte.
# Entfernen Sie in der Zeile 14 das führende '# ' (Raute + Leerzeichen),
# damit Python die Zeile nicht mehr als Kommentar überspringt:
# daten["Vormerkungsquote"] = daten["Vormerkungen"] / daten["Ausleihen"]
print(daten)
```
@Pyodide.eval


## 3. Recherchekompetenz — Boole'sche Operatoren

> [!TIP]
> Recherchekompetenz ist eines der klassischen Schulungsthemen in Bibliotheken — und eines der am schwersten greifbaren. Wir machen es hier konkret: Sie bekommen einen überschaubaren Datenbestand, und der Klick auf ein Venn-Diagramm zeigt, welche Treffer eine Boole'sche Anfrage tatsächlich liefert.

> [!NOTE]
> **Worauf Sie in diesem Abschnitt achten sollten:** Im abschließenden Themenfeld dokumentieren wir die Quizformate, die LiaScript abbildet, um Lernstandserfassungen zu ermöglichen.

### Ein Mini-Datenbestand

Stellen Sie sich vor, eine Fachdatenbank hätte nur die folgenden zehn Treffer zu Ihrer Schulungsrecherche. Jeder Titel ist mit keinem, einem oder beiden der Schlagworte **Informationskompetenz (IK)** bzw. **Berufsbildung (BB)** verknüpft.

| #   | Titel                                                                                             |  IK  |  BB  |
| ---:| ------------------------------------------------------------------------------------------------- |:----:|:----:|
|  1  | *Informationskompetenz in Universitätsbibliotheken*                                               |  ✓   |      |
|  2  | *Suchkompetenz und Recherche-Training*                                                            |  ✓   |      |
|  3  | *Open Access und wissenschaftliche Informationskompetenz*                                         |  ✓   |      |
|  4  | *Digitale Informationskompetenz an Schulen*                                                       |  ✓   |      |
|  5  | *Informationskompetenz für Auszubildende in technischen Berufen*                                  |  ✓   |  ✓   |
|  6  | *Recherchetraining im dualen Berufsausbildungssystem*                                             |  ✓   |  ✓   |
|  7  | *Digitale Kompetenzen in der beruflichen Weiterbildung — Schwerpunkt Informationskompetenz*       |  ✓   |  ✓   |
|  8  | *Curriculumentwicklung in der Berufsausbildung*                                                   |      |  ✓   |
|  9  | *Duale Berufsausbildung im Wandel*                                                                |      |  ✓   |
| 10  | *Qualitätsstandards in der beruflichen Bildung*                                                   |      |  ✓   |

> Recherchekompetenz bedeutet hier, die Schlagworte so zu kombinieren, dass spezifische Treffermengen bereitgestellt werden. Die drei wichtigsten Operatoren sind `AND`, `OR` und `NOT` — sie entsprechen den Schnitt-, Vereinigungs- und Differenzmengen in der Mengenlehre.

| Operator | Bedeutung                           | Wirkung auf Treffermenge | Im Datensatz oben       |
|:--------:| ----------------------------------- |:------------------------:|:------------------------|
|  `AND`   | **Beide** Begriffe müssen vorkommen | verkleinert              | 3 Treffer (5, 6, 7)     |
|  `OR`    | **Mindestens einer** muss vorkommen | vergrößert               | 10 Treffer (alle)       |
|  `NOT`   | Begriff **darf nicht** vorkommen    | verkleinert              | 4 bzw. 3 Treffer        |

> Kleiner Merksatz: **AND ist streng, OR ist großzügig, NOT ist wählerisch.**

### Venn-Diagramm zum Datensatz

Das Diagramm visualisiert, wie sich die zehn Titel auf die drei Schnittbereiche verteilen:

<svg class="boole-venn" viewBox="0 0 440 270" xmlns="http://www.w3.org/2000/svg" style="max-width: 620px; display: block; margin: 0 auto;">
  <defs>
    <mask id="notB">
      <rect width="100%" height="100%" fill="white"/>
      <circle cx="260" cy="140" r="85" fill="black"/>
    </mask>
    <mask id="notA">
      <rect width="100%" height="100%" fill="white"/>
      <circle cx="180" cy="140" r="85" fill="black"/>
    </mask>
    <clipPath id="inA">
      <circle cx="180" cy="140" r="85"/>
    </clipPath>
  </defs>

  <text x="110" y="35" text-anchor="middle" font-size="13" fill="#2c3e50" font-weight="bold">Informationskompetenz</text>
  <text x="330" y="35" text-anchor="middle" font-size="13" fill="#2c3e50" font-weight="bold">Berufsbildung</text>

  <circle cx="180" cy="140" r="85" fill="#3498db" fill-opacity="0.5" mask="url(#notB)"/>
  <circle cx="260" cy="140" r="85" fill="#9b59b6" fill-opacity="0.7" clip-path="url(#inA)"/>
  <circle cx="260" cy="140" r="85" fill="#e74c3c" fill-opacity="0.5" mask="url(#notA)"/>

  <circle cx="180" cy="140" r="85" fill="none" stroke="#2c3e50" stroke-width="2" pointer-events="none"/>
  <circle cx="260" cy="140" r="85" fill="none" stroke="#2c3e50" stroke-width="2" pointer-events="none"/>

  <text x="115" y="145" text-anchor="middle" font-size="13" font-weight="bold" fill="#1a5490" pointer-events="none">IK NOT BB</text>
  <text x="220" y="145" text-anchor="middle" font-size="13" font-weight="bold" fill="#5b2c6f" pointer-events="none">IK AND BB</text>
  <text x="325" y="145" text-anchor="middle" font-size="13" font-weight="bold" fill="#922b21" pointer-events="none">BB NOT IK</text>

  <text x="220" y="255" text-anchor="middle" font-size="12" fill="#7f8c8d" pointer-events="none">IK OR BB = alle drei Bereiche zusammen</text>
</svg>

> [!TIP]
> Die folgenden Aufgaben prüfen Ihr Verständnis am gleichen Datensatz — und zeigen gleichzeitig drei verschiedene LiaScript-Quizformate: **Einfachauswahl**, **Zahleneingabe** und **Mehrfachauswahl**. Jede Aufgabe hat einen ausklappbaren Hinweis (💡) und eine einklappbare Lösung.

**Aufgabe 1 — Welcher Bereich entspricht welcher Anfrage?** *(Einfachauswahl)*

Welcher Bereich des Venn-Diagramms zeigt Titel, die mit *beiden* Schlagworten verknüpft sind?

- [( )] Der blaue Bereich (links)
- [(X)] Der violette Schnittbereich (Mitte)
- [( )] Der rote Bereich (rechts)
- [( )] Alle drei Bereiche zusammen
- [[?]] Hinweis: "Mit beiden Schlagworten" entspricht der Anfrage `IK AND BB`. AND meint immer den *Schnitt* zweier Mengen.

<details>
<summary><strong>Lösung anzeigen</strong></summary>

Der violette Schnittbereich. Drei Titel haben in der Tabelle beide Häkchen gesetzt:

- 5 · *Informationskompetenz für Auszubildende in technischen Berufen*
- 6 · *Recherchetraining im dualen Berufsausbildungssystem*
- 7 · *Digitale Kompetenzen in der beruflichen Weiterbildung — Schwerpunkt Informationskompetenz*

</details>

**Aufgabe 2 — Treffer zählen.** *(Zahleneingabe)*

Wie viele Titel aus dem Datensatz liefert die Anfrage `IK OR BB`?

[[10]]

- [[?]] Hinweis: OR ist großzügig — es reicht, wenn *eines* der beiden Schlagworte gesetzt ist. Schauen Sie in die Tabelle: gibt es überhaupt einen Titel, der *gar kein* Häkchen hat?

<details>
<summary><strong>Lösung anzeigen</strong></summary>

**Alle zehn.** In diesem konstruierten Datensatz hat jeder Titel mindestens eines der beiden Schlagworte gesetzt — es gibt keinen "leeren" Eintrag. Das `OR` umfasst hier also den gesamten Bestand.

</details>

**Aufgabe 3 — Eine Kollegin braucht Beratung.** *(Mehrfachauswahl)*

Eine Kollegin sucht Bücher zur *Berufsbildung*, die *keinen* Informationskompetenz-Bezug haben. Welche Aussagen treffen zu?

- [[X]] Die passende Anfrage lautet `BB NOT IK`.
- [[X]] Sie liefert 3 Treffer.
- [[ ]] Sie liefert mehr Treffer als `IK NOT BB`.
- [[ ]] `BB NOT IK` und `BB AND NOT IK` liefern unterschiedliche Treffermengen.
- [[X]] Sie entspricht im Diagramm dem roten Bereich, der nicht mit dem blauen überlappt.
- [[?]] Hinweis: Lesen Sie das Diagramm als "BB ohne den Schnitt mit IK" — der rote Teil ohne den violetten.

<details>
<summary><strong>Lösung anzeigen</strong></summary>

Richtig sind die erste, zweite und fünfte Aussage. Die drei Treffer:

- 8 · *Curriculumentwicklung in der Berufsausbildung*
- 9 · *Duale Berufsausbildung im Wandel*
- 10 · *Qualitätsstandards in der beruflichen Bildung*

Zu den Distraktoren:

- `IK NOT BB` liefert **4** Treffer — also *mehr*, nicht weniger als `BB NOT IK`.
- `BB NOT IK` und `BB AND NOT IK` sind logisch äquivalent — das explizite `AND NOT` ändert nichts am Ergebnis.

</details>

## Wie geht es weiter?

Wie so etwas entsteht — und wie Sie selbst solche Kurse bauen und in die Community einbringen — schauen wir uns in den folgenden Phasen des Workshops an.

> Ihre vier Notizen aus der Einstiegs-Aufgabe kommen jetzt zum Einsatz:
>
> - Was hat Sie überrascht?
> - Welches Element würden Sie in Ihrer eigenen Schulung einsetzen?
> - Was möchten Sie im Tutorial-Teil unbedingt lernen?
> - Was hat vielleicht anders funktioniert als erwartet?
