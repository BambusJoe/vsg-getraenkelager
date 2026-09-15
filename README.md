# VSG Getränkelager

Kleine PWA für den **Getränke-Bestand der VSG Kleinsteinbach** am Spieltag.
Wer den nächsten Heimspieltag eröffnet, sieht per **Ampel** sofort: einkaufen – ja oder nein?

## Funktionen
- **Lager** – Bestand je Sorte mit Ampel (grün reicht / gelb wird knapp / rot nachkaufen), gezählt in Gebinden (Kiste/Sixpack) über +/− Stepper.
- **Einkauf** – automatische Einkaufsliste mit Mengen bis zum Soll, teilbar (WhatsApp), „Eingekauft" füllt auf Soll auf.
- **Verwalten** – Sortiment, Soll-Bestand und Nachkauf-Schwelle frei einstellbar.
- Installierbar als App (Zum Home-Bildschirm), funktioniert offline.

## Stand
Erste Version. Daten liegen aktuell **lokal auf dem Gerät** (`localStorage`) – noch kein geräteübergreifendes Teilen.
Die Datenschicht ist für einen späteren **Supabase**-Anschluss (echtes Team-übergreifendes Teilen ohne Login) vorbereitet.

## Technik
Statische PWA (eine `index.html`, Service Worker, Manifest). Kein Build-Schritt, gehostet über GitHub Pages.

## Lokal ansehen
```bash
python3 -m http.server 8842
# dann http://localhost:8842 öffnen
```
