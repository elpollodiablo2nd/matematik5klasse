# Math Aid · Kawaii-udgaven 🐻🍓

En ny, ekstra cute version af **Math Aid** — denne gang med **nemmere matematik-stykker på dansk 4./5. klasse-niveau** og et helt nyt kawaii/squishy UI med bamser, enhjørninger, jordbær og japanske bamse-agtige figurer. Core-koden (problem-generator, svar-tjek, statistik, tastatur-genveje) er den samme som i den oprindelige Math Aid — kun opgaverne er lettere og designet er helt nyt.

## Versioner

Der følger **to versioner** med:

| Version | Sti | Sådan bruger du den |
|---|---|---|
| 🌐 **Webversion** | `index.html` (i roden af repoet) | Åbn filen direkte i en browser — eller læg repoet på GitHub Pages, så ligger webversionen på roden. |
| 📱 **Appversion** | `app/index.html` | En installérbar PWA (Progressive Web App). Servér mappen `app/` (fx GitHub Pages eller en lokal server), åbn den på telefonen, og vælg **"Tilføj til hjemmeskærm"** — så får du en rigtig app, der også virker **offline**. |

App-versionen består af:

- `app/index.html` — samme kode som webversionen + manifest og service worker
- `app/manifest.webmanifest` — navn, ikoner og tema til installationen
- `app/sw.js` — service worker, der cacher appen, så den virker uden internet
- `app/icon.svg`, `app/icon-192.png`, `app/icon-512.png` — kawaii bamse-ikoner

### Lokal test

```bash
# webversion: åbn bare filen
xdg-open index.html        # eller højreklik → åbn med browser

# appversion (kræver en lokal server pga. service worker):
python3 -m http.server 8000
# åbn derefter http://localhost:8000/app/ i browseren
```

## Indhold (4./5. klasse-niveau)

Fire moduler, du skifter mellem øverst:

- 🔢 **Tal** — plus og minus med 2-3-cifrede tal (med tier-overgang/mente), den lille gangetabel (2–10), division inden for gangetabellen
- 📐 **Geometri** — areal og omkreds af rektangel og kvadrat, omkreds af trekant (med nuttede figurer, der får kawaii-ansigter)
- 📏 **Enheder** — omregning mellem km/m/cm/mm, kg/g/t og L/dL/mL med pæne tal
- 🍰 **Brøker** — plus/minus med samme nævner, brøk ganget med heltal, forkortning

Hver opgave har en **trin-for-trin-løsning** (💡 Vis løsning), svar-tjek (✅, også brøker som `3/4` og decimaltal med komma), statistik over løste opgaver — og en squishy bamse i headeren, der bliver glad med hjerter, når svaret er rigtigt 🎉

Tastatur: `ENTER` tjekker svaret, `R` giver en ny opgave.

## Teknik

- Én selvstændig `index.html` pr. version — ingen build step, ingen dependencies
- Core-logikken (vægtet valg af opgavetype, `generateProblem`, `checkAnswer`, `parseAnswer`, `renderStats`, ...) er den samme struktur som i den oprindelige Math Aid
- UI: pastel kawaii-tema, runde "squishy" knapper, flydende emoji-dyr i baggrunden, Fredoka/Baloo 2-skrifttyper (hentes fra Google Fonts i webversionen; app-versionen cacher dem offline)
- App-versionen er en PWA: manifest + service worker + ikoner
