
# HTML Bild-Annotator

Ein einfacher, aber leistungsstarker, client-seitiger Bild-Annotator, der direkt im Browser läuft. Dieses Tool wurde entwickelt, um das Erstellen von Annotationen für Objekterkennungs-Workflows zu beschleunigen. Es erfordert keine Installation oder serverseitige Komponenten – einfach die HTML-Datei öffnen und loslegen.

<img width="1259" height="937" alt="{9B8DDF38-57B5-4AA1-B7E9-A52620DC9DA5}" src="https://github.com/user-attachments/assets/2c6b12c9-4a6f-46cc-83c1-d916c5dd10ef" />


## ✨ Features

* **Keine Installation:** Läuft als einzelne HTML-Datei in jedem modernen Webbrowser.
* **Client-Seitig:** Alle Bilder und Annotationen werden lokal in deinem Browser verarbeitet. Es werden keine Daten auf einen Server hochgeladen, was Datenschutz und Geschwindigkeit gewährleistet.
* **Mehrere Bilder:** Lade und annotiere mehrere Bilder in einer Sitzung.
* **Navigationssteuerung:** Wechsle einfach zwischen den geladenen Bildern.
* **Zoom-Funktionen:** Zoome stufenlos in Bilder hinein und heraus oder passe das Bild optimal an die Ansicht an.
* **Annotationstools:**
    * **Bounding Boxes:** Zeichne rechteckige Boxen um Objekte.
    * **Polygone:** Definiere komplexe Formen Punkt für Punkt. *(Hinweis: Aktuell als "Work in Progress" markiert)*
    * **Auswählen & Bearbeiten:** Verschiebe und verändere die Größe von bestehenden Annotationen präzise.
* **Effiziente Labelvergabe:**
    * **Dynamischer Modus:** Jede neue Annotation öffnet ein Modal zur Eingabe eines Labels und optionaler Attribute.
    * **Globaler Modus:** Wähle eine globale Klasse aus, um schnell viele Objekte desselben Typs ohne wiederholte Eingaben zu annotieren.
* **Standard-Exportformate:** Exportiere alle Annotationen mit einem Klick in gängige Formate für Machine Learning:
    * **Pascal VOC** (.zip mit .xml-Dateien)
    * **COCO** (.json)

---

## 🚀 Anleitung: So wird's gemacht

### 1. Starten des Tools
Lade die `Annotator2.html`-Datei herunter und öffne sie einfach mit einem Webbrowser wie Google Chrome, Firefox oder Edge.

### 2. Bilder hochladen
Klicke auf den Button **"Durchsuchen"** (oder ähnlich, je nach Browser) unter "Bilder hochladen:", um ein oder mehrere Bilder von deinem Computer auszuwählen.

### 3. Der Annotations-Workflow

#### Schritt 1: Werkzeug auswählen
* **Bounding Box:** Wähle dieses Werkzeug, um rechteckige Rahmen zu zeichnen.
* **Polygon (WIP):** Wähle dieses Werkzeug, um Formen mit mehreren Ecken zu erstellen. Klicke, um Punkte zu setzen, und klicke in die Nähe des Startpunktes, um die Form zu schließen.
* **Auswählen/Bearbeiten:** Wähle dieses Werkzeug, um bestehende Annotationen zu verschieben oder deren Größe anzupassen.

#### Schritt 2: Annotation zeichnen
* **Bounding Box:** Klicke auf das Bild, halte die Maustaste gedrückt und ziehe einen Rahmen um das gewünschte Objekt auf. Lasse die Maustaste los.
* **Polygon:** Klicke nacheinander auf die Eckpunkte deines Objekts. Eine Linie zum Mauszeiger zeigt die nächste Kante an. Um das Polygon zu schließen, klicke in die Nähe des ersten Punktes.

#### Schritt 3: Label vergeben
Nach dem Erstellen einer neuen Annotation hast du zwei Möglichkeiten, je nach aktivem Modus:

* **Modus "Dynamische Labelvergabe" (Standard):**
    1.  Ein Pop-up-Fenster erscheint.
    2.  Gib im Feld **"Label"** einen Namen für das Objekt ein (z.B. "Hund", "Auto").
    3.  Nutze die **Schnellauswahl**, um bereits verwendete Labels erneut zuzuweisen.
    4.  Setze bei Bedarf Haken für Attribute wie **"Abgeschnitten"** (Truncated) oder **"Schwierig"** (Difficult).
    5.  Klicke auf **"Speichern"**.

* **Modus "Globale Klasse verwenden":**
    1.  Klicke auf den Button **"Dynamische Labelvergabe (Aktiv)"**, um ihn zu deaktivieren.
    2.  Wähle aus der Liste **"Globale Klassenauswahl"** ein bereits vorhandenes Label aus.
    3.  Jede neue Annotation, die du jetzt zeichnest, erhält automatisch dieses Label, ohne dass ein Pop-up erscheint. Dies ist ideal für die schnelle Annotation vieler gleicher Objekte.

#### Schritt 4: Annotationen bearbeiten und löschen
1.  Wechsle zum Werkzeug **"Auswählen/Bearbeiten"**.
2.  Klicke auf eine Annotation im Bild oder in der Liste **"Annotationen für aktuelles Bild"**, um sie auszuwählen.
3.  **Verschieben:** Klicke in die ausgewählte Box und ziehe sie an die neue Position.
4.  **Größe ändern:** Ziehe an den weißen Ankerpunkten an den Ecken und Kanten der Box.
5.  **Löschen:** Wähle eine Annotation aus und klicke auf den Button **"Ausgewählte löschen"**.

### 4. Navigation und Zoom
* Nutze die Buttons **"< Vorheriges"** und **"Nächstes >"**, um durch deine Bilder zu blättern.
* Verwende die **Zoom-Buttons (+ / -)**, um Details genauer zu betrachten.
* Klicke auf **"Anpassen"**, um das Bild automatisch so zu skalieren, dass es vollständig in den Anzeigebereich passt.

### 5. Annotationen exportieren
Wenn du mit der Annotation aller Bilder fertig bist, wähle im Bereich **"Exportieren (Alle Bilder)"** dein gewünschtes Format:
* **Als Pascal VOC (.zip):** Erstellt eine ZIP-Datei, die für jedes annotierte Bild eine `.xml`-Datei im Pascal-VOC-Format enthält.
* **Als COCO (.json):** Erstellt eine einzelne `.json`-Datei, die alle Bilder und Annotationen im COCO-Format enthält.

---

## 🛠️ Technische Hinweise

* **Abhängigkeiten:** Das Tool verwendet die folgenden externen Bibliotheken, die über ein CDN (Content Delivery Network) geladen werden:
    * **Tailwind CSS:** Für das UI-Styling.
    * **JSZip:** Zum Erstellen der ZIP-Datei für den Pascal-VOC-Export.
    * Eine Internetverbindung ist beim ersten Laden erforderlich, um diese Bibliotheken abzurufen.
* **Datenhaltung:** Alle Bilddaten und Annotationen werden ausschließlich im Arbeitsspeicher des Browsers (in einer JavaScript-Variable) gehalten. Beim Schließen oder Neuladen des Browser-Tabs geht der aktuelle Fortschritt verloren.
* **Kompatibilität:** Entwickelt für moderne Desktop-Browser. Die Funktionalität auf mobilen Geräten ist nicht optimiert.

## 🚧 Einschränkungen & Mögliche Erweiterungen

* **Kein Speichern des Projektstatus:** Es gibt keine Funktion, um eine Annotationssitzung zu speichern und später fortzusetzen. Der Export ist der einzige Weg, die Daten zu sichern.
* **Performance:** Das Laden von sehr vielen (>100) oder extrem großen Bildern (4K+) kann die Leistung des Browsers beeinträchtigen.
* **Polygon-Tool:** Die Bearbeitung (Verschieben von Punkten) von Polygonen ist noch nicht implementiert.

Mögliche zukünftige Features könnten sein:
* Projektdatei speichern/laden (z.B. als JSON).
* Unterstützung für weitere Annotationstypen (z.B. Keypoints, Masken).
* Verbesserte Bearbeitungswerkzeuge für Polygone.

## 📜 License

This project is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**. This means it is free to use, share, and adapt for personal and non-commercial purposes, provided that appropriate credit is given.

See the `NOTICE.md` file for full license details, including the licenses of third-party libraries used in this project.

## 💼 Commercial Use

The CC BY-NC 4.0 license does not permit commercial use.

If you wish to integrate this software into a commercial project, please contact me to request a commercial license. Affordable licenses are available, with the price depending on the scope and scale of your project.
