# VSG Getränkelager – Backlog

## 🐛 Bugs

### 1. Einkaufsliste triggert zu früh (gelbe „wird knapp"-Stufe landet schon auf der Liste)
- **Gemeldet:** 2026-09-15
- **Repro:** Verwalten → z. B. Apfelschorle: *Soll* = 6, *Nachkauf ab* = 2. Dann in der Lager-Ansicht ein Sixpack rausnehmen (6 → 5).
- **Erwartet:** Die Sorte wandert **erst** auf die Einkaufsliste (und ins Badge), wenn der Bestand die *Nachkauf-ab*-Schwelle (hier 2) erreicht bzw. unterschreitet.
- **Tatsächlich:** Die Sorte erscheint sofort (schon bei 5) auf der Einkaufsliste und im roten Badge – obwohl noch deutlich über der Schwelle.
- **Ursache:** Die Einkaufsliste enthält aktuell nicht nur die „roten" Artikel (`qty ≤ Nachkauf ab`), sondern auch die „gelbe" Zwischenstufe (`qty < Soll`, aber `> Schwelle`) → `buy = bad + warn`.
- **Fix-Vorschlag:** Einkaufsliste **und** Tab-Badge nur aus `status === 'bad'` (also `qty ≤ Nachkauf ab`) speisen. Die gelbe „wird knapp"-Stufe bleibt als **optische Info** in der Lager-Ansicht (Ampel gelb), löst aber **keinen** Einkauf-Eintrag mehr aus. Betrifft `summary()` und `updateBadges()` in `index.html`; Verdict-Banner-Wording ggf. anpassen.
- **Status:** ✅ behoben (2026-09-20). `summary().buy = bad`; Verdict-„gelb" ohne Einkauf-Button; leerer-Liste-Hinweis auf „wird knapp"-Sorten. Verifiziert mit Beispiel 5/6, Schwelle 2 → nicht auf Liste.

## 💡 Ideen / später
- „Maskable" Android-Icon (Wappen sauber gerahmt fürs runde/Squircle-Icon).
- Echtes team-übergreifendes Teilen via Supabase (statt localStorage).
- Optional: In-App-Hilfe („?"-Button) mit Installations-Anleitung iPhone/Android.
