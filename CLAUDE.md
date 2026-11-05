# APLE-Trainer · BTF Traisen

Lern-Website für die Mitglieder der **Betriebsfeuerwehr Traisen** (BTF Traisen, verbunden mit voestalpine und +GF+ Georg Fischer).
Man übt damit, wo im **TLF 3000/200** welches Gerät liegt.
Website der Feuerwehr: https://www.betriebsfeuerwehr-traisen.at/

## Für Claude
- Mit dem Nutzer **auf Deutsch** sprechen, einfach erklären. Er ist kein Programmierer und lernt gerade.
- Die Seite wird hauptsächlich **am Handy** benutzt, also jede Änderung auch bei schmaler Breite prüfen (`@media (max-width: 560px)`).
- Alles bleibt in **einer Datei** (`index.html`), nur die Logos liegen extra in `logos/`. Kein Build-Tool, keine Frameworks.
- Den localStorage-Schlüssel `aple_tlf_stats_v1` nicht ändern, sonst verlieren alle ihren Lernstand.
- Änderungen gehen online, indem der Nutzer `index.html` auf GitHub hochlädt (GitHub Pages). Git ist nicht installiert, hochgeladen wird über den Browser.

## Dateien
| Datei | Inhalt |
|---|---|
| `index.html` | Die ganze App: CSS oben, HTML in der Mitte, JavaScript unten |
| `logos/btf-traisen.png` | Feuerwehr-Logo (rund), von der BTF-Website |
| `logos/voestalpine.svg` | voestalpine-Logo, von Wikimedia Commons |
| `logos/gf.svg` | +GF+-Logo, von Wikimedia Commons (viewBox wurde von Hand korrigiert) |

## Aufbau von index.html
- **CSS**: nummerierte Abschnitte 1–9. Die Farben stehen als Variablen in `:root` (`--bg`, `--card`, `--card-2`, `--soft`, `--red` …). Der Hintergrund wurde absichtlich dunkler gemacht, weil Weiß den Nutzer gestört hat.
- **Kopfbereich**: drei Spalten. Links voestalpine, in der Mitte das Feuerwehr-Logo mit „BTF TRAISEN“ groß, rechts +GF+.
- **JavaScript**: nummerierte Abschnitte 1–16 (Einstellungen, Beladeliste, Geräteräume, Statistik, Fahrzeug, Navigation und je ein Abschnitt pro Ansicht).
- **Ansichten**: Start, Zuordnen (Drag & Drop aufs Fahrzeug), Quiz, Lernen, Beladeliste.
- **Beladeliste**: `DEFAULT_LIST`, eine Zeile pro Gerät im Format `Gerät;Geräteraum;Fach;Hinweis`. Räume: G1–G6, MR, DACH, HECK. Fahrerseite G1/G3/G5, Beifahrerseite G2/G4/G6.
- Geräte, die man falsch beantwortet, kommen öfter dran (`weightOf`).

## Offene Punkte
- [ ] Die Beladeliste ist noch eine **Beispielliste**, nicht die echte vom TLF. Sobald der Nutzer die echte Liste hat, `DEFAULT_LIST` und `CONFIG.listStand` ersetzen.
- [ ] Klären, ob die Firmenlogos und die echte Liste öffentlich online sein dürfen (Kommando fragen).
- [ ] Der Nutzer will die Logos im Kopfbereich noch etwas verschieben.
