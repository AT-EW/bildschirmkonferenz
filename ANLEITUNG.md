# Bildschirmkonferenz – Anleitung

Browser-App für Video, Ton und Bildschirmfreigabe mit bis zu ca. 5 Personen.
Die Einladung wird per WhatsApp verschickt, die Gesprächspartner brauchen nur den Link.

## 1. Adresse der App

**https://at-ew.github.io/bildschirmkonferenz/**  (am besten als Lesezeichen speichern, auch auf dem Handy)

Die App liegt per GitHub Pages im Repository https://github.com/AT-EW/bildschirmkonferenz.
Änderungen an `index.html` gehen so online (im Ordner `Bildschirmkonferenz`):

```bash
git add -A
git commit -m "Änderung"
git push
```

Nach ca. 1 Minute ist die neue Version online.

Ein eigener Server ist nicht nötig: Die Teilnehmer finden sich über den öffentlichen, kostenlosen
PeerJS-Vermittlungsdienst. Bild und Ton laufen danach direkt und verschlüsselt (DTLS-SRTP)
zwischen den Teilnehmern.

## 2. Konferenz durchführen

1. App öffnen und **„Kamera und Mikrofon einschalten“** klicken. Fragt der Browser nach, auf **„Zulassen“** klicken.
   In der Vorschau sehen Sie Ihr Bild, und der Balken „Mikro“ schlägt aus, wenn Sie sprechen.
   Stimmt das Gerät nicht, unter **„Kamera / Mikrofon auswählen“** ein anderes wählen. Die Wahl wird gespeichert.
2. Namen eingeben und auf **„Konferenz starten“** klicken.
3. Im Raum erscheint neben Ihrem Bild **„Mit WhatsApp einladen“**. Der Knopf öffnet die WhatsApp-App mit fertigem Text,
   Sie wählen Kontakt oder Gruppe und senden. Der Text liegt zusätzlich in der Zwischenablage (notfalls mit Strg+V einfügen).
4. Die Eingeladenen tippen auf den Link, prüfen kurz Bild und Ton und tippen auf **„Jetzt beitreten“**.

Beim ersten Mal fragt Edge oder Chrome eventuell: *„Diese Website versucht, WhatsApp zu öffnen“*. Haken bei „immer erlauben“ setzen und auf **Öffnen** klicken.

| Knopf | Funktion |
|---|---|
| Mikrofon / Kamera | ein- und ausschalten (rot = aus) |
| ⚙ (oben rechts) | Kamera oder Mikrofon wechseln |
| Bildschirm | ganzen Bildschirm, ein Fenster oder einen Browser-Tab teilen. Bei allen anderen wird die Freigabe automatisch groß angezeigt. |
| Einladen | Link erneut per WhatsApp senden, kopieren oder teilen |
| Chat | Textnachrichten, z. B. für Werte oder Links |
| Kachel anklicken | Person groß stellen. Mit ⛶ oder Doppelklick auf Vollbild. |

## Hinweise

- **Bildschirm teilen geht nur am PC/Laptop** (Chrome, Edge, Firefox, Safari).
  Handy-Browser können zusehen, aber nicht selbst teilen.
- Wer den Raum zuerst öffnet, eröffnet ihn. Verlässt diese Person die Konferenz, übernimmt automatisch
  ein anderer Teilnehmer. Neue Teilnehmer können also trotzdem noch dazukommen.
- Kamera oder Mikrofon gehen nicht? Die App zeigt einen roten Kasten mit der genauen Abhilfe. Die häufigsten Ursachen:
  - **Gesperrt:** In der Adresszeile links auf das Symbol (Schloss/Regler) klicken → Kamera/Mikrofon „Zulassen“ → „Erneut versuchen“.
  - **Belegt:** Ein anderes Programm nutzt die Kamera (WhatsApp-Anruf, Teams, Zoom, Kamera-App). Programm schließen oder ein anderes Gerät wählen.
  - **Link im WhatsApp-internen Browser geöffnet** (Handy): ⋮ → „Im Browser öffnen“.
- Mehr als ca. 5–6 Teilnehmer: Jeder sendet an jeden, dafür reicht die Upload-Bandbreite dann oft nicht mehr.
- In sehr restriktiven Firmennetzen kann die direkte Verbindung blockiert sein.
  Die App weicht dann auf die öffentlichen PeerJS-Relay-Server aus, ohne Garantie auf Verfügbarkeit.

## Lokal testen

```bash
python -m http.server 8765 --directory Bildschirmkonferenz
```

Dann `http://localhost:8765` öffnen, die Konferenz starten und den Einladungslink in einem zweiten Tab öffnen.
