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

1. App öffnen, Namen eingeben. Für jede Besprechung entsteht automatisch ein neuer Raum-Code.
2. **„Einladung per WhatsApp senden“** öffnet WhatsApp mit fertigem Text und Link. Kontakt bzw. Gruppe auswählen und senden.
3. **„Konferenz betreten“** klicken und Kamera/Mikrofon im Browser erlauben.
4. Die Eingeladenen tippen auf den Link, geben ihren Namen ein und sind im selben Raum.

| Knopf | Funktion |
|---|---|
| Mikrofon / Kamera | ein- und ausschalten (rot = aus) |
| Bildschirm | ganzen Bildschirm, ein Fenster oder einen Browser-Tab teilen. Bei allen anderen wird die Freigabe automatisch groß angezeigt. |
| Einladen | Link erneut per WhatsApp senden, kopieren oder teilen |
| Chat | Textnachrichten, z. B. für Werte oder Links |
| Kachel anklicken | Person groß stellen. Mit ⛶ oder Doppelklick auf Vollbild. |

## Hinweise

- **Bildschirm teilen geht nur am PC/Laptop** (Chrome, Edge, Firefox, Safari).
  Handy-Browser können zusehen, aber nicht selbst teilen.
- Wer den Raum zuerst öffnet, eröffnet ihn. Verlässt diese Person die Konferenz, übernimmt automatisch
  ein anderer Teilnehmer. Neue Teilnehmer können also trotzdem noch dazukommen.
- Bei „Gerät wird gerade von einem anderen Programm benutzt“: Teams, Zoom oder WhatsApp-Desktop schließen, die die Kamera belegen.
- Mehr als ca. 5–6 Teilnehmer: Jeder sendet an jeden, dafür reicht die Upload-Bandbreite dann oft nicht mehr.
- In sehr restriktiven Firmennetzen kann die direkte Verbindung blockiert sein.
  Die App weicht dann auf die öffentlichen PeerJS-Relay-Server aus, ohne Garantie auf Verfügbarkeit.

## Lokal testen

```bash
python -m http.server 8765 --directory Bildschirmkonferenz
```

Dann `http://localhost:8765` in zwei Browser-Tabs öffnen und denselben Raum-Code verwenden.
