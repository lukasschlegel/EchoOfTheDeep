# Echo of the Deep

## Projekttitel & Kurzbeschreibung

**Echo of the Deep** ist eine interaktive, audiovisuelle Medieninstallation, die in einem 360°-Igloo eine immersive Unterwasserwelt mit schwimmenden Quallen erlebbar macht.  

Das Publikum kann in diese ruhige, meditative Umgebung eintauchen. Die Besucherinnen und Besucher können über laute Geräusche – insbesondere durch Klatschen – direkt mit der Installation interagieren. Wird ein solcher Impuls erkannt, reagieren die Quallen sichtbar: Sie vergrössern sich und bewegen sich abrupt auseinander, danach beruhigen sie sich langsam wieder. 

## Videodokumentation

Das Video zeigt das Endergebnis, und wie die Installation entstanden ist:

[![Videosokumentation](https://img.youtube.com/vi/tkS_R5urPmU/0.jpg)](https://youtu.be/tkS_R5urPmU)

---

## Komponentenplan

Dieser Komponentenplan zeigt auf, aus welchen Elementen die Installation besteht:

![Komponentenplan](Komponentenplan_neu.png)

Dafür werden die verschiedenen Komponenten gebraucht:

### Software:

- **Premiere Pro**: Sounddesign, Animationen aufbereiten  
- **TouchDesigner**: Programmierung der Installation  
- **Resolume Arena**: Projektion, Mapping, Spout-Verbindung  

### Hardware (im Igloo):

- **Mensch**: Aktion mit Klatschen auslösen  
- **Mikrofon**: Klatschen erkennen 
- **Projektoren**: Visuals auf Leinwand projizieren  
- **Leinwand**: Immersive Umgebung für Projektion  

---

## Reproduzierbarkeit

So kann unser Projekt Echo of the Deep nachgebaut werden:

### 1. Quallenvisuals vorbereiten
- Animierte Quallen online suchen  
- evtl. Video bearbeiten und transparent exportieren (wir hatten Quallen mit Greenscreen und mussten diesen entfernen)
- Dateien komprimieren (z. B. mit Notch) für bessere Performance in TouchDesigner
- Wir haben drei verschiedene Quallen für mehr Varianz im Bild verwendet.

### 2. Sounddesign entwickeln

- Für den Hintergrund: Wellensound und beruhigende Ambient-Musik sammeln, in einem Schnittprogramm (wir haben Premiere Pro verwendet) zusammensetzen und optimalerweise als wav oder sonst als mp3 exportieren. 
- Für den Sound-Effekt: Effekt passend komponieren (z.B. schnelle Wasserbewegung, die das Wegschwimmen der Quallen symbolisiert)

[🎵 Hintergrundmusik abspielen](https://drive.google.com/file/d/19NIAtn2hQZWSFWfP5aOaqnds_dstn-Su/view?usp=drive_link)

[🎵 Soundeffekt abspielen](https://drive.google.com/file/d/19CG1I3g2pxT2V_Kx3L226QoJmCtiMrmz/view?usp=drive_link)

### 3. Projekt in TouchDesigner aufsetzen

Wir stellen ein bereits fertiges Touch Designer Projekt für die Reproduzierbarkeit zur Verfügung. Hier müssen lediglich die fehlenden Dateien neu verknüpft und das richtige Mikrofon verbunden werden. Unter folgendem Link können die Quallenvisuals, das TouchDesigner Projekt und das Sounddesign heruntergeladen werden:

[Zum Download](https://drive.google.com/drive/folders/1o2-5T5PC-PCn-MEhUW-qa93pJ10lwVS9?usp=drive_link)

#### Struktur des TouchDesigner-Projekts

Das TouchDesigner-Netz besteht aus mehreren Bestandteilen, die miteinander verknüpft wurden:

#### 🔊 Trigger

- Mikrofoneingang via `audiodevin`
- Analyse mit `audioAnalysis`, `select`, `trigger`
- Klatsch-Geräusch löst `chopexec1` aus
- Visualisierung über `trail`
- Testbutton zur manuellen Auslösung

#### 🎵 Hintergrundmusik

- Audiodatei über `audiofilein1` eingebunden
- Ausgabe via `audiodevout1`

#### 💥 Soundeffekt

- Zusätzlicher Audioeffekt über `audiofilein2`
- Triggergesteuert
- Modulation mit `pattern`, `noise`, `math`

#### 🌐 Prep Projection for Igloo

- Bewegung mit Noise-CHOPs auf Spheres
- Instanzsteuerung via `sopto`, `merge`
- Optimiert für 360°-Projektion

#### 🪼 Jellyfish Assets for Sphere

- 3 Quallenarten als Videosequenzen
- Eingebunden via `chaix1`, gemappt auf `geo2`
- Instanzierung über `constant1`, `inst`

#### 🌊 Background under the sea

- Meereshintergrund mit `ramp`, `lookup`, `displace`
- Subtile Bewegung für Tiefe und Atmosphäre

#### 🎥 Cam and Render

- Szeneansicht über `cam1`
- Rendering via `render`, `projection1`
- Vorbereitung für Output mit `math3`

#### 📏 Resolution (adjustable)

- Einstellung über `constant2`
- Standard: 8000×2000 px
- **Anpassbar für Tests oder andere Formate**

#### 🌀 Igloo Output

- Zusammensetzung mit `over`
- Ausgabe über `syphonspoutout1` → Resolume Arena

Der Screenshot zeigt das fertige TouchDesigner-Netz:

![Screenshot TouchDesigner](Screenshot_TouchDesigner.png)

### 4. Installation im Igloo

- TouchDesigner-Projekt auf den Rechner laden, der mit dem Beamer-Setup verbunden ist.
- Spout-Verbindung zu Resolume Arena aktivieren.
- In Resolume:
  - Videoeingang vom Spout einbinden
  - Mapping für 5 Beamer einrichten (360°-Verteilung)
- Mikrofon im Igloo korrekt positionieren und in TouchDesigner konfigurieren.

### 5. Feinanpassung vor Ort

- Falls nötig: Sounddesign leicht anpassen oder Lautstärkepegel feinjustieren.
- Reaktion und Bewegung der Quallen im Igloo testen.
- Eventuell Grösse oder Platzierung der Quallen korrigieren.
- Auflösung allenfalls anpassen.

### 6. Fertig – testen & erleben

- Klatschen, beobachten, eintauchen.
- Die Quallen reagieren live auf Geräusche – die Installation ist einsatzbereit.

![GIF Quallenbewegung](Quallenbewegung.gif)
  
---

## Bericht zum Umsetzungsprozess

### Entwicklungsprozess

Die Grundidee einer ruhigen, interaktiven Unterwasserwelt entstand bereits zu Beginn des Projekts und das Team hielt daran bis zum Schluss fest. Alle Gruppenmitglieder waren sofort begeistert davon, eine Welt zu schaffen, in die man eintauchen kann. Das Ziel war es, dass die Betrachtenden durch laute Geräusche mit der Installation interagieren können und z.B.  Fische dadurch auseinander schwärmen.

Nach der Konzeptphase setzte das Team die Idee in TouchDesigner um und installierte die Unterwasserwelt anschliessend im Igloo.

### Verworfene Lösungsansätze
Zunächst wollte das Team animierte Fische in die Unterwasserwelt einfügen. Später fiel die Entscheidung jedoch auf Quallen, da sie durch ihre Tentakeln besonders ästhetisch wirkten.

Für die Reaktion der Quallen wurden zwei Ansätze diskutiert: Entweder sollten sie auf Klatschen reagieren oder durch Tracking mittels Kameras, bei dem sich die Quallen entfernen, sobald sich eine Person nähert. Aufgrund der technischen Komplexität, des Zeitdrucks aber hauptsächlich auch weil der Klang eine zentrale Rolle in unserem Projekt spielt, entschieden wir uns bewusst für die Steuerung über Klatschen. Diese Lösung ergänzt das Sounddesign und verstärkt die immersive Wirkung der Installation.

### Fehlschläge und Umplanung
Ursprünglich hatte das Team vor, die Bewegung der Quallen möglichst realistisch darzustellen – mit dynamischen Bewegungen in verschiedene Richtungen, einem natürlichen Auseinanderschwärmen und einem sehr langsamen Zurückgleiten an die ursprüngliche Position. Nach mehreren Versuchen zeigte sich jedoch, dass diese Art der Animation in TouchDesigner technisch sehr komplex ist. Daher entschied sich das Team schliesslich für eine vereinfachte Variante: Die Quallen vergrössern sich kurzzeitig und beginnen leicht zu schwanken, was ihre Reaktion auf den Geräuschimpuls unterstreicht.
Auch wenn die Bewegung nicht vollständig naturgetreu ist, wirkt der Effekt visuell trotzdem sehr stimmig.

### Herausforderungen

- Die Umsetzung der Quallenbewegung war anspruchsvoller als erwartet.
- Die Komplexität von TouchDesigner wurde unterschätzt.
- Aufgrund der geringen Vorkenntnisse mussten viele technische Lösungen im Projektverlauf durch Learning by Doing erarbeitet werden. Das war sehr zeitintensiv.
- Beim Projektvideo musste die Kamera so eingestellt werden, damit die Aufnahmen im Igloo nicht flimmern.

### Hilfsmittel

- **ChatGPT** (für Umsetzung in TouchDesigner und Dokumentation)
- Unterstützung durch **Dozent Jan Fiess**

### Known Bugs
Im Igloo wurde eine Webcam mit integriertem Mikrofon zur Klatscherkennung verwendet. Aufgrund der eingeschränkten Qualität wurde das Klatschen nicht immer zuverlässig erkannt, wenn nicht in Richtung des Mikrofons geklatscht wurde. Durch die zufällige Verteilung der Quallen kam es zudem vereinzelt zu Überlagerungen beim Klatscheffekt, was die Ästhetik leicht beeinträchtigte. Dieses Problem konnte jedoch grösstenteils durch eine Anpassung der Quallengrösse gelöst werden. Abgesehen davon sind keine weiteren Fehler bekannt – das Projekt funktionierte im Igloo wie geplant.

## Lernfortschritt

Das Projekt war für alle Gruppenmitglieder eine wertvolle Lernerfahrung – insbesondere im Umgang mit dem Programm TouchDesigner, das zuvor kein Teammitglied kannte.  

Gelernt wurde unter anderem:

- Aufbau und Strukturierung eines TouchDesigner-Netzwerks
- Einbindung und Steuerung von Partikelsystemen
- Analyse von Audiosignalen und Erzeugung interaktiver Reaktionen
- Einblick in technisches Setup und Mapping in einem 360°-Igloo
- Zusammenspiel von Audio, Video, Interaktion und Raum

## Projektteam

- **Maria Reichmuth**  
- **Milena Stadelmann**  
- **Lukas Schlegel**

### Aufgabenverteilung & Zusammenarbeit

Während des gesamten Projekts haben die Gruppenmitglieder eng zusammengearbeitet.  Von der Konzeption bis zur finalen Umsetzung wurden Entscheidungen gemeinsam getroffen und die Aufgaben fair verteilt. Alle unterstützten sich zudem gegenseitig bei auftretenden Problemen. 

![Team](Zusammenarbeit.JPG)

Das Konzept sowie ein grosser Teil des TouchDesigner-Projekts wurden gemeinsam erstellt. Um danach effizient voranzukommen, übernahmen die Mitglieder gezielte Aufgaben:

- **Milena Stadelmann** optimierte das Sounddesign. Aus verschiedenen frei verfügbaren Klangquellen – darunter Meeresrauschen und ruhige Ambient-Musik – komponierte sie eine stimmige Hintergrundmusik sowie einen Soundeffekt. Dieser wurde in Adobe Premiere zusammengestellt, exportiert und später in TouchDesigner eingebunden.

- **Maria Reichmuth** optimierte die visuelle Anordnung der Quallen. Sie experimentierte mit Grösse, Bewegung und Dynamik innerhalb des Partikelsystems in TouchDesigner, um ein möglichst harmonisches Gesamtbild und einen stimmigen Effekt beim Klatschen zu erzeugen.

- **Lukas Schlegel** übernahm das Filmen und Schneiden des Projektvideos, welches die Installation dokumentiert und auch den Projekt-Prozess ausserhalb des Igloos sichtbar macht.

Die Dokumentation wurde gemeinsam verfasst, wobei alle Gruppenmitglieder inhaltliche Beiträge leisteten. Während zwei Tagen in **Chur** installierte das Team schliesslich die Installation im Igloo und führte die finalen Tests gemeinsam durch.

![Finalisierung im Igloo](Finalisierung_Igloo.JPG)

---

## Fazit

Echo of the Deep zeigt, wie mit TouchDesigner eine faszinierende und immersive Welt erschaffen werden kann. Die Verbindung von Klang, Bewegung und Interaktion erzeugt ein eindrückliches Erlebnis, das zum Eintauchen und Nachdenken einlädt. Rückblickend wäare es von Vorteil gewesen, sich vor Projektstart noch intensiver mit TouchDesigner vertraut zu machen. Dies hätte den Arbeitsprozess effizienter gestaltet und dadurch wäre die Umsetzung eines noch komplexeren Projekts möglich gewesen. Dennoch ist das Team mit dem Ergebnis sehr zufrieden und stolz darauf, innerhalb kurzer Zeit und ohne Vorkenntnisse ein solches Projekt realisiert zu haben.

---

##  Projektinfos

Dieses Projekt entstand im Rahmen des Minors Creative Technology im Studiengang Multimedia Production an der Fachhochschule Graubünden.

- Dozent: Jan Fiess
- Semester: 4
- Jahr: 2025

