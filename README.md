# 🍔 Smash Patat – Website Documentatie

**Live website:** https://smashpatat.be

> ⚠️ **Deze repository is publiek.** Alles wat je hier commit, is voor iedereen leesbaar — ook bestanden die nergens op de site gelinkt staan, en ook nadat je ze verwijdert (via de git-historie). Commit dus nooit kassabestanden, Excel-bestanden, scriptkopieën, wachtwoorden of foto's die niet publiek mogen. Zie ook "Wat nooit in deze repo hoort" onderaan.

---

## 📁 Bestandsstructuur

```
smashpatat.github.io/
├── index.html                        → De volledige hoofdpagina
├── reservering.html                  → Boekingsformulier + beschikbaarheidskalender
├── allergenen.html                   → Allergeneninformatie
├── privacy.html                      → Privacybeleid (GDPR-verplicht)
├── smash-catch.html                  → Het arcadespel "Smash & Catch"
├── menu.json                         → Menu database (burgers, dranken, extra's)
├── reviews.json                      → Google-reviews, handmatig ingevoerd
├── photos.json                       → Automatisch gegenereerde fotolijst (niet handmatig aanpassen!)
├── logo.png                          → Logo + favicon
├── logo_no_txt.png                   → Logo zonder tekst
├── logo-veld.png                     → Logo-masker voor de achtergrond van het spel
├── logo_special.png                  → Foto voor de specials
├── classic-smash.png / cheese-smash.png / kids-smash.png / veggie_smash.jpg / oklahoma.jpg
│                                     → Foto's van de menukaart
├── checker.png / insta.png           → Tegelpatroon en icoon (worden nooit herschaald)
├── over_ons.jpg / over_ons_night.jpg → Foto's bij "Over ons"
├── smash-gameover.mp4                → Video op het game-over-scherm
├── fotos/                            → Map met alle sfeerfoto's voor de fotoband
├── sitemap.xml / robots.txt / BingSiteAuth.xml / CNAME
├── .github/workflows/update-photos.yml → GitHub Action: optimaliseert beelden + genereert photos.json
└── README.md                         → Deze documentatie
```

**Niet in deze repo:** `menu-print.html` (de printbare A4-menukaart) staat op Google Drive en wordt daar bijgehouden.

---

## ✏️ Iets aanpassen op de website

1. Ga naar **github.com/vermope/smashpatat.github.io**
2. Klik op het bestand dat je wil aanpassen
3. Klik op het **potloodje** (rechtsboven in het bestand)
4. Maak je wijziging
5. Klik op **"Commit changes"**
6. Wacht 1-2 minuten → de website is automatisch bijgewerkt

---

## 📅 Locaties & Agenda

Evenementen op de website komen automatisch uit Google Agenda.

### 🔴 Op WELKE agenda?

Er zijn drie agenda's, en het maakt uit welke je gebruikt:

| Agenda | Waarvoor | Komt op de site? |
|--------|----------|------------------|
| **Smash Patat - Publieke Events** | Waar we publiek staan | **Ja** — titel, datum, uur, locatie |
| **Smash Patat - Beschikbaarheid** | Bezette dagen | Alleen als "bezet" op de reserveringspagina |
| **Smash Patat - Persoonlijk** (primaire agenda) | Al de rest | Nee |

**Zet publieke events altijd op "Smash Patat - Publieke Events".** Wat daar op staat, komt op de site — verder niets. Vergeet je van agenda te wisselen, dan verschijnt het event niet online; dat is bewust zo gebouwd, zodat een vergetelheid nooit privégegevens publiceert.

### Een nieuw evenement toevoegen:

1. Open **Google Agenda**
2. Nieuw event met **naam, datum, uur en locatie**
3. Kies bij de agenda-dropdown **Smash Patat - Publieke Events**
4. Opslaan — de site toont het automatisch

Staan er geen events, dan toont de site: *"Geen aankomende publieke evenementen gepland."*

### Technische details

Twee aparte Apps Script-projecten, beide te beheren op script.google.com met het smashpatat-account:

| Project | Leest | Gebruikt door |
|---------|-------|---------------|
| `SmahPatatCalendarSyncAPI` | Publieke Events | `index.html` |
| `SmashPatatBeschikbaarheid` | Beschikbaarheid | `reservering.html` |

De eventfeed geeft alleen titel, begin, einde en locatie terug, en kijkt 6 maanden vooruit. De beschikbaarheidsfeed geeft alleen datum + status ("bezet" of "aanvraag"), 365 dagen vooruit.

**Bij aanpassingen aan een script:** vervang de code, en ga dan naar **Deploy → Implementaties beheren** → potloodje → Version op **New version** → Deploy. Zo blijft de URL gelijk en hoeft de HTML niet aangepast te worden.

> ⚠️ **Kies niet "Nieuwe implementatie"** tenzij je de URL in de HTML ook wil aanpassen — je krijgt dan een tweede, andere URL.
>
> ⚠️ **Archiveer oude implementaties.** Een implementatie blijft leven op zijn eigen URL, ook nadat je de code aanpast of de URL uit de HTML haalt. Zolang hij actief staat, serveert hij de oude code aan wie die URL kent. Controleer bij elke wijziging of er onder "Active" niets overblijft dat niemand meer gebruikt.
>
> ⚠️ **Zet de agenda's nooit op "Openbaar beschikbaar".** De scripts lezen met de rechten van het account, dus dat is niet nodig. Staat het aan, dan is de hele agenda leesbaar via een embed- en ICS-URL, buiten de scripts om — inclusief alles wat de feed juist wegfiltert.

---

## 🍔 Menu aanpassen

Het menu wordt geladen uit `menu.json`. Dat bestand is de **enige** bron: de homepage, de allergenenpagina en de printmenukaart lezen er allemaal uit.

1. Open `menu.json` op GitHub
2. Pas de items aan
3. Commit — de site laadt de nieuwe data automatisch

### Structuur van een menu-item

```json
{
  "id": "smash-patat-classic",
  "name": "Smash Patat Classic",
  "description": "Dubbel premium beef patty, SP burger saus, sla, tomaat, ui, pickle",
  "price": 9.50,
  "tags": ["Bestseller"],
  "image": "classic-smash.png"
}
```

`tags` is een **array**, zodat een item meerdere labels kan hebben (bv. `["New", "Veggie"]`). Oudere items gebruiken nog het enkelvoudige veld `"tag"`; beide werken, maar gebruik voor nieuwe items de array.

### Niet vergeten bij een nieuwe burger

Een menu-item toevoegen raakt vier plekken:

1. `menu.json` — het item zelf
2. `index.html` — alleen als er een nieuw soort tag of kaartweergave nodig is; **nooit** de content zelf
3. `allergenen.html` — volledige tabelrij met alle 14 EU-allergenen, en de datum in de voettekst bijwerken
4. `menu-print.html` op Drive → opnieuw exporteren naar PDF

De actuele prijzen en beschrijvingen staan in `menu.json`. Ze staan bewust **niet** in deze README, want een tweede lijst loopt gegarandeerd uit de pas met de eerste.

---

## ⭐ Reviews aanpassen

De reviewsectie leest `reviews.json`. Reviews worden handmatig ingevoerd — dat is een bewuste keuze, geen automatisering via de Google API.

Neem reviewteksten **letterlijk** over: geen spelling corrigeren, niet inkorten, geen taalfouten wegwerken. Moet er toch iets weg (bv. een emoji die de layout breekt), vermeld dat dan.

De veldnamen in `reviews.json` volgen de vorm van de Google Places API. Wijk daar niet van af, ook niet als een eigen naam mooier lijkt — de structuur bestaat zodat een eventuele overstap naar de echte API niets aan de front-end verandert.

---

## 🖼️ Sfeerfoto's beheren (fotoband "Smash Patat in Beeld")

De fotoband laadt automatisch alle foto's uit de `fotos/` map. Je hoeft nooit code aan te passen.

### Foto's toevoegen

1. Ga naar de map **`fotos/`** op GitHub
2. **"Add file"** → **"Upload files"**
3. Sleep je foto's erin (JPG, PNG of WEBP)
4. **"Commit changes"**

✅ De GitHub Action optimaliseert de foto's en hergenereert `photos.json`. Na 1-2 minuten staan ze op de site.

### Foto's verwijderen

Klik de foto aan in de `fotos/` map → prullenbak-icoontje → commit. `photos.json` wordt automatisch bijgewerkt.

> ⚠️ **Let op bij foto's van thuis of van privé-events.** Telefoonfoto's bevatten GPS-coördinaten in hun EXIF-data. De Action strípt die, maar pas *nadat* de originele foto al gecommit is — en die originele versie blijft in de git-historie van een publieke repo staan. Wil je zeker zijn: verwijder de locatiegegevens vóór het uploaden (in Windows: rechtsklik → Eigenschappen → Details → "Eigenschappen en persoonlijke gegevens verwijderen").

### Volgorde en layout

De volgorde wordt **bij elk paginabezoek willekeurig geschud**. Bestandsnamen bepalen dus niets.

- **Desktop:** twee rijen die tegen elkaar in schuiven; pauzeert bij hover
- **Mobiel:** één veegbare strip, één foto per veeg
- **Klikken** opent de foto groot in een lightbox (sluiten met × of Escape)
- Bezoekers met "verminderde beweging" aan krijgen een stilstaande, scrollbare band

### Problemen?

- **Foto's verschijnen niet?** Wacht 1-2 minuten en ververs met Ctrl+F5
- **Action mislukt?** Tabblad "Actions" in de repo voor details
- **Oude foto's nog zichtbaar?** Browsercache — probeer een privévenster
- **Foto ligt op zijn kant?** Zie hieronder

---

## ⚙️ De GitHub Action: `update-photos.yml`

Draait bij elke push naar `fotos/**` of naar een afbeelding in de root, en handmatig via **Actions → Run workflow**.

1. **Sfeerfoto's** (`fotos/`): rechtzetten volgens EXIF (`-auto-orient`), max 1600px, EXIF strippen, JPEG progressive kwaliteit 82
2. **Beelden in de root**: max 960px, PNG's door pngquant (80–96%). `checker.png` en `insta.png` worden overgeslagen, net als alles onder 150KB
3. **`photos.json`** genereren met relatieve paden
4. Alles terugcommitten

⚠️ De Action **herschrijft je originelen in de repo**. Bewaar de camerabestanden buiten de repo.

⚠️ Vereist **Settings → Actions → General → Workflow permissions → Read and write permissions**.

⚠️ De Action commit met de ingebouwde `GITHUB_TOKEN`. Vervang die **nooit** door een personal access token: commits met een PAT starten de workflow opnieuw, en omdat de Action naar precies die paden commit, krijg je een oneindige lus.

**Foto op zijn kant?** Sinds `-auto-orient` in de Action zit, gebeurt dat niet meer bij nieuwe uploads. Een foto die al fout in de repo staat, moet je gedraaid opnieuw uploaden.

---

## ⚠️ Altijd relatieve paden

Verwijs **nooit** naar `https://vermope.github.io/smashpatat.github.io/...`. Schrijf het pad zonder domein:

```html
<img src="logo.png">
<img src="fotos/sfeer_burger.jpg">
```

`index.html` vangt oude absolute URL's uit `menu.json` en `photos.json` nog op via de helper `localAsset()`, maar nieuwe verwijzingen doe je relatief.

---

## 🐛 Afbeeldingen die niet laden

1. **Absolute URL's** — zie hierboven
2. **Firefox en `loading="lazy"`.** Firefox laadt lazy-afbeeldingen die via JavaScript worden toegevoegd vaak niet. De fotoband en menukaarten gebruiken daarom een eigen loader (`data-src` + IntersectionObserver, met een vangnet na 3 seconden). Voeg bij nieuwe, door JavaScript gegenereerde afbeeldingen dus **geen** `loading="lazy"` toe, maar gebruik `data-src` en roep `hydrateLazyImages(container)` aan

---

## 🖼️ Logo of vaste afbeeldingen vervangen

1. Upload het nieuwe bestand via **"Add file → Upload files"**
2. Gebruik **exact dezelfde bestandsnaam**
3. GitHub overschrijft het oude bestand

⚠️ **GitHub is hoofdlettergevoelig:** `Logo.png` ≠ `logo.png`

`logo.png` doet ook dienst als favicon; die wordt dus automatisch meegewijzigd.

---

## 🎨 Kleuren & stijl

| Element | Waarde |
|---------|--------|
| Achtergrond / nav / footer | `#111111` |
| Off-white (tekst op donker) | `#f5f5f0` |
| Rood accent | `#D72B2B` |
| Rood hover | `#b82424` |
| Sectie-achtergrond | `#181818` |
| Groen — **alleen** voor vegetarisch | `#4CAF50` |
| Font titels | **Alfa Slab One** (Google Fonts) |
| Font tekst | **Inter** (Google Fonts) |

Geen andere kleuren, geen gradients, geen `border-radius`, geen zachte schaduwen. Groen is *semantisch*: het betekent vegetarisch en niets anders — niet "succes", niet "beschikbaar".

---

## 📬 Contact & socials aanpassen

Zoek in `index.html` naar de sectie met `id="contact"`. De site linkt naar het mailadres en naar Instagram; Facebook wordt bewust niet gelinkt.

---

## 🔒 Beveiliging & privacy

### Het reservatieformulier

Loopt via **Formspree**. Er zit een spamval in: een verborgen veld met de naam `_gotcha`, plus een controle die verzendingen binnen 3 seconden negeert. **Haal dat verborgen veld niet weg en maak het niet zichtbaar** — bots vullen het in, echte bezoekers zien het niet.

Inzendingen blijven ook bij Formspree staan. Ruim die daar minstens één keer per jaar op; dat staat zo in het privacybeleid.

### Privacybeleid

`privacy.html` is verplicht onder de GDPR/AVG. Verwerk je iets nieuws — een ander formulier, een nieuwe dienst, statistieken — pas dan `privacy.html` bij **en** de datum bovenaan.

Vermelde verwerkers: Formspree, Google (Gmail, Fonts, Agenda), Cloudflare en GitHub. Komt er een dienst bij, zet die er dan ook in.

Toezichthouder in België: **Gegevensbeschermingsautoriteit (GBA)** — gegevensbeschermingsautoriteit.be

### Security headers

Staan in **Cloudflare → Rules → Modify Response Header**, niet in de HTML. De `Content-Security-Policy` somt op met welke externe domeinen de site mag praten: Google Fonts, `script.google.com` en `formspree.io`.

**Voeg je een nieuwe externe bron toe** (een ander script, een andere API, een externe afbeelding), dan moet die in de CSP bij, anders blokkeert de browser hem stil. Symptoom: iets werkt niet en de console (F12) toont "Refused to..." of "Content Security Policy".

### Wat nooit in deze repo hoort

- Kassabestanden (`App.jsx` en verwanten), Excel-bestanden, boekhouding
- Kopieën van Apps Script-code of deployment-URL's die nergens gebruikt worden
- API-keys, tokens, wachtwoorden — in geen enkel bestand, ook niet in een comment
- Foto's met GPS-data van privé-adressen
- Backups zoals `index-oud.html` of `test.html`

Verwijderen helpt niet: het blijft in de git-historie staan. Is er per ongeluk iets in beland, meld het dan meteen in plaats van het stil te verwijderen.

---

## 🚀 Hosting

**GitHub Pages** vanaf de `main` branch, op het eigen domein `smashpatat.be`. **Cloudflare** zit ervoor voor HTTPS, security headers en caching. Elke wijziging is na 1-2 minuten live.

Twee dingen om te weten:

- **"Enforce HTTPS" in Settings → Pages blijft grijs.** Dat komt doordat de DNS-records via Cloudflare geproxied worden, waardoor GitHub geen eigen certificaat kan uitgeven. Geen probleem: bezoekers krijgen HTTPS van Cloudflare, met HSTS aan.
- **De origin blijft direct bereikbaar** op `vermope.github.io`. Wie dat adres kent, omzeilt Cloudflare en dus ook de security headers. Voor een statische site is dat aanvaardbaar, maar reken er niet op dat Cloudflare een vangnet is.

⚠️ **Zet deze repo niet op privé.** GitHub Pages werkt op een gratis account niet vanaf een privérepo — de site gaat dan offline en Pages moet daarna opnieuw ingesteld worden, inclusief het custom domain.

---

*Gemaakt met ❤️ voor Smash Patat*
