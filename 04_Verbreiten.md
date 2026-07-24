<!--
author:   Sebastian Zug, André Dietrich

email:    sebastian.zug@informatik.tu-freiberg.de

version:  0.1.0

language: de

narrator: Deutsch Male

mode:     Presentation

date:     24/07/2026

comment:  Phase 4 des Workshops "Interaktive OER mit LiaScript" an der
          TU Berlin, Universitätsbibliothek (24.07.2026).
          Verbreiten eigener Kurse — Schwerpunkt: die direkte
          GitHub-Anbindung des LiveEditors. 15 Minuten.

repository: https://github.com/LiaPlayground/TUBerlin_UB_2026

attribute: Interaktive OER mit LiaScript
           von Sebastian Zug und André Dietrich
           ist lizenziert unter [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

link:     style.css

-->

[![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/TUBerlin_UB_2026/main/04_Verbreiten.md)

# Verbreiten von LiaScript-Kursen

> <h2>Phase 4 — Verbreiten</h2>
>
> <div style="height: 2.5em;"></div>
>
> <h4>Prof. Dr. Sebastian Zug, TU Bergakademie Freiberg</h4>
> <h4>Dr. André Dietrich, TU Bergakademie Freiberg</h4>
>
> <h4>TU Berlin · Universitätsbibliothek · 24. Juli 2026</h4>

--------------------------------------------

## Worum geht es in diesen 15 Minuten?

Sie haben in [Phase 3](03_Anwenden.md) Ihren eigenen Kurs gebaut — jetzt geht es darum, ihn aus dem LiveEditor herauszubekommen und mit anderen zu teilen. Der **Schwerpunkt** liegt heute auf einer Neuerung, die das Teilen enorm vereinfacht hat:

> [!IMPORTANT]
> Der LiveEditor kann Ihren Kurs inzwischen **direkt zu GitHub** veröffentlichen und aktualisieren — Import, Publish, Push und Pull, alles aus dem Editor heraus. Ein lokal installiertes `git` brauchen Sie dafür **nicht** mehr.

Danach ordnen wir kurz die weiteren Wege ein (Data-URI, ZIP, SCORM), damit Sie für jedes Szenario den passenden kennen.

## Der Schwerpunkt: GitHub direkt aus dem LiveEditor

Bisher war der Weg „Kurs → GitHub" ein Bruch: Datei herunterladen, lokales Repository anlegen, committen, pushen — mehrere Werkzeuge, mehrere Fehlerquellen. Der aktuelle LiveEditor bündelt das in **einem Menü**.

### Wo Sie die Funktionen finden

Öffnen Sie im LiveEditor oben das **Menü** (das Drei-Punkte-Symbol ⋮ in der Navigationsleiste). Es öffnet die **Import/Export-Übersicht** mit mehreren Tabs — darunter der Tab **„GitHub"**. Dort finden Sie vier Aktionen:

| Aktion                          | Symbol | Was sie tut                                                        |
| ------------------------------- | :----: | ----------------------------------------------------------------- |
| **Import from GitHub**          |   ⬇    | Dateien aus einem bestehenden Repository in den Editor laden       |
| **Publish to new repository**   |   ☁    | Ein **neues** GitHub-Repository anlegen und alle Dateien hochladen |
| **Push to GitHub**              |   ⬆    | Änderungen committen und in das verknüpfte Repository schieben      |
| **Pull from GitHub**            |   ⬇    | Änderungen aus dem verknüpften Repository zurückholen               |

> [!NOTE]
> **Push** und **Pull** sind zunächst ausgegraut. Sie werden erst aktiv, sobald Ihr Projekt mit einem Repository **verknüpft** ist — das geschieht automatisch nach einem *Import* oder einem *Publish*.

<div class="live-demo">

**🖥️ Live-Demo:** Wir öffnen jetzt gemeinsam das Menü ⋮ → Tab „GitHub" und schauen uns die vier Aktionen im echten Editor an.

</div>

### Der Token — die einzige echte Hürde

Die GitHub-Anbindung nutzt **keinen** OAuth-„Anmelden mit GitHub"-Knopf, sondern einen **Personal Access Token (PAT)**, den Sie einmalig bei GitHub erzeugen und im Editor einfügen. Der Editor speichert ihn lokal in Ihrem Browser.

> [!TIP]
> - **Öffentliche** Repositorien **importieren** Sie ganz **ohne** Token.
> - Ein Token wird nötig für **Push**, **Publish**, **Pull** und den Zugriff auf **private** Repositorien.
> - Der Editor fragt den Token **genau dann** ab, wenn er ihn braucht — mit der eingeblendeten Anleitung „*How do I create a token?*". Sie müssen also nichts vorbereiten.

<details>
<summary><strong>📋 Schritt-für-Schritt: Fine-grained Token erstellen (zum Nachschlagen)</strong></summary>

Für **Import (privat)**, **Push** und **Pull** genügt ein *fine-grained* Token mit minimalen Rechten:

1. Öffnen Sie <https://github.com/settings/personal-access-tokens/new> (GitHub → *Settings* → *Developer settings* → *Fine-grained tokens*).
2. **Token name** vergeben (z. B. `LiaScript LiveEditor`) und ein **Expiration**-Datum wählen — z. B. 30 oder 90 Tage. *Kein* „No expiration".
3. Unter **Repository access** nur die Repositorien auswählen, die Sie wirklich brauchen (nicht „All repositories").
4. Unter **Repository permissions** den Eintrag **„Contents"** setzen:
   - **Read-only** genügt zum *Importieren* privater Repos.
   - **Read and write** ist nötig zum *Pushen* und *Pullen*.
5. **Generate token**, den angezeigten Wert kopieren (`github_pat_…`) und im LiveEditor in das Feld einfügen → **Save**. Die zuvor gestartete Aktion wird automatisch fortgesetzt.

> [!CAUTION]
> **Sonderfall „Publish to new repository":** Ein *neues* Repository anlegen können fine-grained Tokens (noch) nicht. Für **Publish** brauchen Sie einen **klassischen** Token mit dem Scope **`repo`**:
> <https://github.com/settings/tokens/new?scopes=repo> — ebenfalls mit Ablaufdatum.

> [!NOTE]
> **Sicherheit:** Behandeln Sie einen Token wie ein Passwort. Vergeben Sie *immer* ein Ablaufdatum, *immer* nur die nötigen Rechte, und beschränken Sie den Zugriff auf einzelne Repositorien. Einen nicht mehr benötigten Token löschen Sie in den GitHub-Einstellungen.

</details>

### Ablauf 1 — Kurs zum ersten Mal veröffentlichen (Publish)

So bringen Sie Ihren in Phase 3 gebauten Kurs erstmals auf GitHub:

1. Menü ⋮ → Tab **„GitHub"** → **Publish to new repository**.
2. **Owner** wählen (Ihr Account oder eine Organisation), **Repository name** (aus dem Kurstitel vorbelegt) und optional eine **Description** eintragen; bei Bedarf **Private repository** ankreuzen.
3. **Create & publish** — der Editor legt das Repository an und lädt alle Dateien hoch. Danach ist Ihr Projekt mit dem Repo **verknüpft**; Push und Pull sind ab jetzt aktiv.

<div class="live-demo">

**🖥️ Live-Demo:** Ich veröffentliche einen kleinen Beispielkurs mit meinem eigenen Token — Sie sehen Repository-Anlage und Upload in einem Schritt.

</div>

### Ablauf 2 — Änderungen nachschieben (Push)

Sie haben im Editor weitergearbeitet und wollen die Änderungen sichern:

1. Menü ⋮ → Tab **„GitHub"** → **Push to GitHub**.
2. Der Editor zeigt Ihre lokalen Änderungen gegen den Stand auf GitHub (*added / modified / deleted*); pro Datei können Sie über **Diff** die Unterschiede vergleichen.
3. Eine **Commit message** eingeben und **Commit & push** klicken — Commit und Push sind **ein** Schritt.

> [!NOTE]
> Warnt der Editor vor „remote drift", hat sich das Repository seit Ihrem letzten Abgleich geändert — dann vorher einmal **Pull from GitHub** ausführen.

### Ablauf 3 — Bestehenden Kurs importieren

Um an einem vorhandenen Repository weiterzuarbeiten:

- Menü ⋮ → Tab **„GitHub"** → **Import from GitHub**, dann `owner/repo` (oder die volle URL) eingeben, **Load**, gewünschte Dateien auswählen, **Import**.
- **Noch schneller — der Direkt-Link:** `https://liascript.github.io/LiveEditor/?/github/<owner>/<repo>` öffnet die Dateiauswahl sofort. Genau so haben Sie in [Phase 3](03_Anwenden.md) das Übungs-Template geladen — praktisch für Handouts und zum Teilen mit Kolleginnen.

> [!TIP]
> **Der OER-Königsweg:** Repository = Quelle + Historie + Lizenz + Zusammenarbeitsplattform in einem. Kolleginnen aus anderen Häusern können per *Pull Request* Verbesserungen vorschlagen, der Link bleibt dauerhaft stabil, und alle fünf V-Freiheiten aus [Phase 2](02_Verstehen.md) greifen — *kollaborativ*, nicht nur als einseitige Weitergabe.

> [!NOTE]
> **Und wie wird ein Repo-Kurs zum Player-Link?** Der LiaScript-Player rendert jede Markdown-Datei direkt aus ihrer **Raw-URL**:
>
> `https://liascript.github.io/course/?` + Raw-URL
>
> Genau dieses Muster steckt hinter dem Badge oben auf jeder Workshop-Phase.

## Die weiteren Wege im Überblick

GitHub ist der Königsweg — aber nicht immer der schnellste. Drei weitere Wege ergänzen ihn:

| Weg              | Was wird geteilt?              | Wofür geeignet?                                        |
| ---------------- | ------------------------------ | ------------------------------------------------------ |
| **Data-URI**     | Ein Link, der den Kurs enthält | Schnelle Vorschau, kurze Materialien, Versand per Mail |
| **ZIP-Export**   | Alle Dateien als Archiv        | Vollständige Kurse mit Bildern, lokale Nutzung         |
| **SCORM-Paket**  | LMS-fähiges Lernpaket          | Integration in Moodle, ISIS, ILIAS — inkl. Lernstand   |

### Data-URI — ein Link, der den Kurs enthält

Über die Import/Export-Übersicht lässt sich eine URL erzeugen, die den **kompletten Kursinhalt in der Adresse** transportiert — kein Hosting nötig, weitergebbar per Mail, Chat oder QR-Code.

> [!NOTE]
> Data-URIs werden mit zunehmender Kurslänge sehr lang. Für kurze Materialien elegant — für umfangreiche Kurse mit Bildern stoßen Sie an URL-Längengrenzen mancher Programme.

### ZIP-Export — die vollständige Quelle als Archiv

Der LiveEditor exportiert den gesamten Kurs samt Bildern als **ZIP**.

> [!IMPORTANT]
> Die ZIP-Datei wird **nicht entpackt**, sondern per **Drag & Drop in den LiveEditor** gezogen ([liascript.github.io/LiveEditor](https://liascript.github.io/LiveEditor/)). Der Editor liest das Archiv, stellt die Quelle her und schaltet in den Player-Modus. Geben Sie diesen Hinweis beim Versand immer mit.

### SCORM-Paket — Anschluss ans LMS

Mit dem [LiaScript-Exporter](https://liascript.github.io/exporter/) erzeugen Sie ein **SCORM-Paket** für Moodle, ISIS, ILIAS & Co.

> [!NOTE]
> SCORM ist der Standard, mit dem ein LMS Inhalte einliest *und* Lernstand erfasst (Quiz bearbeitet? abgeschlossen?). Ihr Kurs bekommt diese Anbindung — ohne seine offene Markdown-Quelle zu verlieren.

## Zusammengefasst

> [!TIP]
> 1. **GitHub (Schwerpunkt):** Publish/Push/Pull/Import direkt aus dem Menü ⋮ → Tab „GitHub". Ein *Personal Access Token* ist die einzige Vorbereitung — fine-grained mit „Contents: Read/Write", für *Publish* ein klassischer Token mit `repo`-Scope.
> 2. **Data-URI:** Ein Link — ideal für kurze Materialien und schnelle Vorschau.
> 3. **ZIP-Export:** Die vollständige Quelle als Archiv — per Drag & Drop zurück in den LiveEditor.
> 4. **SCORM-Paket:** Die LMS-Integration mit Lernstandserfassung.
>
> **Die OER-Pointe bleibt in allen Wegen erhalten:** Der Markdown-Quelltext reist mit. Wer Ihren Kurs erhält, kann ihn anpassen, weiterentwickeln und in eigenen Kontexten wiederverwenden — genau das macht ihn zur echten Open Educational Resource.

> [!TIP]
> Den Quelltext dieses Workshops finden Sie unter [github.com/LiaPlayground/TUBerlin_UB_2026](https://github.com/LiaPlayground/TUBerlin_UB_2026) — ein Beispiel dafür, wie ein Repository einen kompletten Mehr-Phasen-Kurs strukturiert. Und ja: veröffentlicht wurde es genau über den Weg, den wir gerade gezeigt haben.

## Lizenz

Dieses Material steht unter [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.de).
