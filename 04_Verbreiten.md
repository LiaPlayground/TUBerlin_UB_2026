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

import:    https://raw.githubusercontent.com/LiaTemplates/LiveEdit-Embeddings/refs/tags/0.0.1/README.md

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

Danach ordnen wir kurz die weiteren Wege ein (Data-URI, ZIP, SCORM), damit Sie für jedes Szenario den passenden kennen. Vorweg werfen wir aber noch einen Blick darauf, wie **KI** Ihnen beim *Erstellen* der Kurse hilft.

## Zum Aufwärmen: Die Systematik hinter den Medien-Befehlen

Bevor es ums Teilen geht, ein kurzer Blick auf eine Eigenschaft, die genau dann wichtig wird: Zunächst sieht die LiaScript-Syntax für Medien vielleicht unübersichtlich aus — aber dahinter steckt ein **intuitives System**. Alle Medien wachsen aus *derselben* vertrauten Markdown-Link-Schreibweise; es kommen nur ein oder zwei Zeichen davor.

Probieren Sie es in der eingebetteten Vorschau aus — **dieselbe Text-URL, vier verschiedene Ergebnisse**, je nachdem, welches Zeichen davorsteht (scrollen Sie im Rahmen bis nach unten):

````markdown @embed.style(height: 600px; min-width: 100%; border: 1px black solid)
# Systematik hinter den Befehlen

__Ein Link__
+ https://tu-freiberg.de/
+ [TUBAF](https://tu-freiberg.de/)

__Ein externes Bild__ (!)
[image](https://tu-freiberg.de/sites/default/files/2024-04/732_Silber_Calcit_01_HM.jpg)

__Ein Tondokument__ (?)
[sound](https://open.spotify.com/album/69cO89tra0gETaDHwsKZo5)

__Ein Video__ (!?)
[video](https://www.youtube.com/watch?v=TJHEDKSahoM)

__Ein Irgendwas__ (??)
[webapp](https://sketchfab.com/3d-models/familienschacht-freiberg-germany-7c7d30506c554385a4a4321366e2e601)
````

> [!TIP]
> **Die Faustregel:** `!` steht für das Auge (**Bild**), `?` steht für das Ohr (**Audio**) — und `!?` bzw. `??` kombinieren beides zu **Video** und **eingebetteter Ressource**. Ein und dieselbe URL, nur ein anderes Vorzeichen.

> [!IMPORTANT]
> **Und hier schlägt die Brücke zum Verbreiten:** Ein `![…]`-Bild oder eine lokale Audiodatei *reist nicht von allein mit*, wenn Sie nur die Markdown-Datei weitergeben. Genau deshalb gibt es weiter unten Wege wie **ZIP** (packt alle Bilder mit ein) und das **GitHub-Repository** (hält Quelle *und* Medien zusammen). Eingebettete Ressourcen per `??` liegen dagegen ohnehin extern — sie reisen als URL mit.

## Vorab: KI als Co-Autorin für LiaScript-Kurse

Viele der Handgriffe, die Sie in [Phase 3](03_Anwenden.md) selbst gemacht haben, übernehmen inzwischen KI-Assistenten. Vor zwei Jahren hieß die Antwort auf „Wie schreibe ich einen LiaScript-Kurs?" noch: *„Cheat Sheet öffnen, Syntax nachschlagen, ausprobieren."* Heute heißt sie zunehmend: *„Beschreiben Sie der KI, was Sie vermitteln wollen — und prüfen Sie die Vorlage."*

> [!NOTE]
> **Was sich nicht geändert hat:** Sie entscheiden, *was* vermittelt wird, *welches Beispiel* aus dem Bibliotheksalltag passt, *welche Differenzierung* sinnvoll ist. Die KI nimmt nur die **Syntax-Last** ab — sie weiß, wie ein Quiz, eine Formel oder eine Animation in LiaScript geschrieben werden.

### Stufe 1 — Web-KI mit angehängter Skill-Datei

Die niedrigschwellige Variante: Eine einzige Markdown-Datei, [**LiaSkill**](https://github.com/LiaScript/LiaSkill), wird einer Web-KI als Kontext mitgegeben — Claude, ChatGPT, Gemini oder Mistral, egal welche. Die KI „lernt" daraus die vollständige LiaScript-Syntax und kann anschließend komplette Kurse aus Klartext-Beschreibungen erzeugen.

| Schritt | Was tun?                                                                                            |
| ------- | --------------------------------------------------------------------------------------------------- |
| 1       | [SKILL.md](https://github.com/LiaScript/LiaSkill/blob/main/liascript-skill/SKILL.md) als Datei in den Chat ziehen |
| 2       | Beschreiben: *„Erstelle eine Schulung zu …, Zielgruppe …, mit … Quizzen und … Differenzierung."*    |
| 3       | Ergebnis im [LiveEditor](https://liascript.github.io/LiveEditor/) prüfen, anpassen                  |

> **Geeignet für:** Kolleginnen und Kollegen, die heute schon ChatGPT oder Copilot nutzen — kein neues Werkzeug, nur ein angehängtes Dokument.

### Stufe 2 — Geführter Prozess in VS Code: der Teaching-Agent

Die professionelle Variante: [**Teaching-Agent**](https://github.com/LiaScript/teaching-agent) führt Sie in **VS Code mit GitHub Copilot** durch einen vollständigen, strukturierten Kursentwurf — vom Lernziel über die Didaktik bis zum fertigen Material. Statt eines einzelnen Prompts entsteht ein iterativer Dialog mit definierten Phasen:

![Einzelprompt vs. Agenten-Brigade — ein einzelner Prompt gegenüber einem geführten Team spezialisierter Agenten](https://github.com/andre-dietrich/Ein-Prompt-ist-kein-Team/blob/main/assets/images/einzelprompt-vs-agenten-brigade.png?raw=true)

> Mehr dazu: [Ein Prompt ist kein Team](https://github.com/andre-dietrich/Ein-Prompt-ist-kein-Team)

> [!TIP]
> **Der professionelle Editier-Weg im Hintergrund:** Sowohl LiaSkill (Stufe 1) als auch der Teaching-Agent (Stufe 2) laufen am runden Ende auf **VS Code mit GitHub Copilot** oder **GitHub Codespaces** (im Browser, ohne lokale Installation) hinaus — mit Syntax-Highlighting, Versionskontrolle und KI-Unterstützung. Und damit sind wir beim Thema Verbreiten: Wo diese Werkzeuge arbeiten, ist GitHub schon zur Hand.

## Die weiteren Wege im Überblick

GitHub ist der Königsweg — aber nicht immer der schnellste. Drei weitere Wege ergänzen ihn:

| Weg             | Was wird geteilt?              | Wofür geeignet?                                        |
| --------------- | ------------------------------ | ------------------------------------------------------ |
| **Data-URI**    | Ein Link, der den Kurs enthält | Schnelle Vorschau, kurze Materialien, Versand per Mail |
| **GitHub**      | Repository mit Kursinhalten    | Umfangreiche Materialien, Zusammenarbeit, stabile Links |
| **ZIP-Export**  | Alle Dateien als Archiv        | Vollständige Kurse mit Bildern, lokale Nutzung         |
| **SCORM-Paket** | LMS-fähiges Lernpaket          | Integration in Moodle, ISIS, ILIAS — inkl. Lernstand   |

### Data-URI — ein Link, der den Kurs enthält

Über die Import/Export-Übersicht lässt sich eine URL erzeugen, die den **kompletten Kursinhalt in der Adresse** transportiert — kein Hosting nötig, weitergebbar per Mail, Chat oder QR-Code.

> [!NOTE]
> Data-URIs werden mit zunehmender Kurslänge sehr lang. Für kurze Materialien elegant — für umfangreiche Kurse mit Bildern stoßen Sie an URL-Längengrenzen mancher Programme.

### GitHub — das Repository als Kurscontainer

> [!IMPORTANT]
> Der LiveEditor kann **direkt zu GitHub** veröffentlichen und aktualisieren — Import, Publish, Push und Pull, alles aus dem Editor heraus. Ein lokal installiertes `git` brauchen Sie dafür **nicht** mehr.

LiveDemo mit dem heutigen Kursmaterial: [github.com/LiaPlayground/TUBerlin_UB_2026](https://github.com/LiaPlayground/TUBerlin_UB_2026)

Dafür brauchen Sie einen Github-Account und ein **Personal Access Token** (PAT) mit den Rechten `repo` (für *Publish*) oder `contents: read/write` (für *Push*). Das Token wird einmalig im LiveEditor hinterlegt, danach können Sie direkt aus dem Menü ⋮ → Tab „GitHub" arbeiten.

https://github.com/settings/tokens/new

### ZIP-Export — die vollständige Quelle als Archiv

Der LiveEditor exportiert den gesamten Kurs samt Bildern als **ZIP**.

> [!IMPORTANT]
> Die ZIP-Datei wird **nicht entpackt**, sondern per **Drag & Drop in den LiveEditor** gezogen ([liascript.github.io/LiveEditor](https://liascript.github.io/LiveEditor/)). Der Editor liest das Archiv, stellt die Quelle her und schaltet in den Player-Modus. Geben Sie diesen Hinweis beim Versand immer mit.

### SCORM-Paket — Anschluss ans LMS

Mit dem [LiaScript-Exporter](https://liascript.github.io/exporter/) erzeugen Sie ein **SCORM-Paket** für Moodle, ISIS, ILIAS & Co.

> [!NOTE]
> SCORM ist der Standard, mit dem ein LMS Inhalte einliest *und* Lernstand erfasst (Quiz bearbeitet? abgeschlossen?). Ihr Kurs bekommt diese Anbindung — ohne seine offene Markdown-Quelle zu verlieren.

## Zusammengefasst

> 0. **KI als Co-Autorin:** LiaSkill (Datei an die Web-KI anhängen) oder Teaching-Agent (geführt in VS Code) nehmen die Syntax-Last ab — Sie entscheiden über Inhalt und Didaktik.
> 1. **GitHub (Schwerpunkt):** Publish/Push/Pull/Import direkt aus dem LiveEditor — für umfangreiche Materialien, Zusammenarbeit und stabile Links.
> 2. **Data-URI:** Ein Link — ideal für kurze Materialien und schnelle Vorschau.
> 3. **ZIP-Export:** Die vollständige Quelle als Archiv — per Drag & Drop zurück in den LiveEditor.
> 4. **SCORM-Paket:** Die LMS-Integration mit Lernstandserfassung.
>
> **Die OER-Pointe bleibt in allen Wegen erhalten:** Der Markdown-Quelltext reist mit. Wer Ihren Kurs erhält, kann ihn anpassen, weiterentwickeln und in eigenen Kontexten wiederverwenden — genau das macht ihn zur echten Open Educational Resource.

> [!TIP]
> Den Quelltext dieses Workshops finden Sie unter [github.com/LiaPlayground/TUBerlin_UB_2026](https://github.com/LiaPlayground/TUBerlin_UB_2026) — ein Beispiel dafür, wie ein Repository einen kompletten Mehr-Phasen-Kurs strukturiert. Und ja: veröffentlicht wurde es genau über den Weg, den wir gerade gezeigt haben.

## Lizenz

Dieses Material steht unter [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.de).
