# 🍔 Smash Patat – Website Documentatie

**Live website:** https://vermope.github.io/smashpatat.github.io/

---

## 📁 Bestandsstructuur

```
smashpatat.github.io/
├── index.html                        → De volledige hoofdpagina
├── privacy.html                      → Privacybeleid (GDPR-verplicht)
├── menu.json                         → Menu database (burgers, dranken, bijgerechten, extras)
├── photos.json                       → Automatisch gegenereerde fotolijst (niet handmatig aanpassen!)
├── logo.png                          → Zwart/wit logo (witte achtergrond) + favicon
├── logo_no_txt.png                   → Logo zonder tekst
├── logo_special.png                  → Foto voor de specials burgers
├── fotos/                            → Map met alle sfeerfoto's voor het prikbord
│   ├── sfeer_burger_1.jpg
│   ├── sfeer_burger_2.jpg
│   └── ...
├── .github/
│   └── workflows/
│       └── update-photos.yml         → GitHub Action: genereert photos.json automatisch
└── README.md                         → Deze documentatie
```

---

## ✏️ Iets aanpassen op de website

1. Ga naar **github.com/vermope/smashpatat.github.io**
2. Klik op het bestand dat je wil aanpassen (`index.html`, `privacy.html` of `menu.json`)
3. Klik op het **potloodje** (rechtsboven in het bestand)
4. Maak je wijziging
5. Klik op **"Commit changes"**
6. Wacht 1-2 minuten → de website is automatisch bijgewerkt

---

## 🖼️ Sfeerfoto's beheren (prikbord)

Het prikbord op de website laadt automatisch alle foto's uit de `fotos/` map. Je hoeft nooit code aan te passen.

### Foto's toevoegen:

1. Ga naar je repo op GitHub
2. Klik op de map **`fotos/`**
3. Klik **"Add file"** → **"Upload files"**
4. Sleep je foto's erin (JPG, PNG of WEBP)
5. Klik **"Commit changes"**

✅ GitHub start automatisch een actie die `photos.json` hergenereert.
Na ongeveer 1 minuut verschijnen de nieuwe foto's op de website.

### Foto's verwijderen:

1. Ga naar de `fotos/` map op GitHub
2. Klik op de foto die je wil verwijderen
3. Klik het **prullenbak-icoontje** rechtsboven
4. Commit — `photos.json` wordt automatisch bijgewerkt

### Foto volgorde aanpassen:

Foto's verschijnen in **alfabetische volgorde** op bestandsnaam.
Wil je een specifieke volgorde? Geef foto's een naam als:
- `01_burger.jpg`
- `02_team.jpg`
- `03_truck.jpg`

### Prikbord layout:

- **Desktop:** mozaïek van 9 foto's per pagina in wisselende groottes, met punaises en lichte rotatie
- **Mobiel:** 1 foto tegelijk met automatische rotatie elke 3,5 seconden, ook te bedienen met pijltjes
- Meer dan 9 foto's? Er wordt automatisch een nieuwe pagina aangemaakt (pijltjes + bolletjes onderaan)

### Problemen?

- **Foto's verschijnen niet?** Wacht 1-2 minuten en ververs de pagina (Ctrl+F5)
- **GitHub Action mislukt?** Ga naar het tabblad "Actions" in je repo voor details
- **Oude foto's nog zichtbaar?** Browser cache — open in incognito venster

---

## 🍔 Menu aanpassen

Het menu wordt automatisch geladen uit `menu.json`.

### Menu bewerken:

1. Open `menu.json` op GitHub
2. Pas de gewenste items aan
3. Commit de wijzigingen
4. De website laadt automatisch de nieuwe data

### Structuur van een menu-item:

```json
{
  "id": "classic",
  "name": "Smash Patat Classic",
  "description": "Dubbel premium beef patty, SP burger saus, sla, tomaat, ui, pickle",
  "price": 9.50,
  "tag": "Bestseller",
  "image": "https://vermope.github.io/smashpatat.github.io/classic-smash.jpg"
}
```

### Tags:

- **Bestseller tag:** `"tag": "Bestseller"`
- **Special tag:** `"tag": "Special"` (wit kader met ★, aparte sectie bovenaan menu)
- **Geen tag:** `"tag": null`

### Huidig menu:

| Burger | Prijs |
|--------|-------|
| Kids Smash Patat 🎈 | €6,50 |
| Smash Patat Classic ★ Bestseller | €9,50 |
| Smash Patat Double Cheese | €9,50 |
| Gorgo Smash ★ Special | €11,00 |
| Chili Smash 🌶️🌶️ ★ Special | €11,00 |
| Truffel Smash ★ Special | €11,50 |

**Dranken:** Fris/Pils (€2,80), Speciaal Bier (€3,50)

**Extra toppings:** Pancetta (€1), Extra Patty (€2,50), Cheddar (€1), Jalapeño Infused Hot Honey (€1), Oklahoma Stijl (€1,50), Jalapeño Mix (€1), Pickled Onion (€0,50), Ajuin Peer Confijt (€1), Bourbon Bacon Jam (€1), Zesty Gorgo Saus (€1), SP Chili Saus (€0,50), SP Burger Saus (€0,50), SP Truffelsaus (€0,75), Rucola (€0,50), Parmigiano (€0,50), Balsamico Glaze (€0,50)

---

## 📅 Locaties & Agenda (automatisch via Google Agenda)

Evenementen op de website worden automatisch opgehaald uit Google Agenda.

### Een nieuw evenement toevoegen:

1. Open **Google Agenda** op smashpatat@gmail.com
2. Voeg een nieuw event toe met **naam, datum, tijd en locatie**
3. De website toont het event automatisch — geen aanpassing nodig!

*Alleen jij kan de agenda bewerken — bezoekers kunnen enkel lezen.*

### Technische details:

- **Script URL:** `https://script.google.com/macros/s/AKfycbzcmNvWJE-kzNoYDrvGPgRWTe3XNtyaWNenhKjtkaCbZVaV17nHjsJjRF5H3WjahbJWWQ/exec`
- **Script beheren:** script.google.com → inloggen met smashpatat@gmail.com → project **"SmashPatatCalendarSyncAPI"**
- Het script leest de komende **6 maanden** aan events uit
- Als het script stopt met werken: ga naar Apps Script → **Implementeren** → **Nieuwe implementatie** → opnieuw deployen als **Webtoepassing**

---

## 🖼️ Logo of vaste afbeeldingen vervangen

1. Upload het nieuwe bestand op GitHub via **"Add file → Upload files"**
2. Gebruik **exact dezelfde bestandsnaam** (bv. `logo.png`)
3. GitHub overschrijft het oude bestand automatisch

⚠️ **GitHub is hoofdlettergevoelig:** `Logo.png` ≠ `logo.png`

Het logo wordt ook gebruikt als **favicon** (icoontje in het browsertabblad). Bij het vervangen van `logo.png` wordt het favicon automatisch ook bijgewerkt.

---

## 🎨 Kleuren & stijl

| Element | Waarde |
|---------|--------|
| Achtergrond | `#111111` |
| Hero achtergrond | `#ffffff` |
| Wit | `#f5f5f0` |
| Rood accent | `#D72B2B` |
| Font titels | **Alfa Slab One** (Google Fonts) |
| Font tekst | **Inter** (Google Fonts) |

---

## 📬 Contact & socials aanpassen

Zoek in `index.html` naar de sectie met `id="contact"` en pas de links aan:

```html
✉ smashpatat@gmail.com
📷 Instagram
👍 Facebook
```

---

## 🔒 Privacybeleid

De website bevat een aparte `privacy.html` pagina, verplicht onder de GDPR/AVG. De footer linkt automatisch naar deze pagina.

Bij wijzigingen in hoe je gegevens verwerkt, pas dan ook `privacy.html` bij en update de datum **"Laatst bijgewerkt"** bovenaan.

De toezichthouder in België is de **Gegevensbeschermingsautoriteit (GBA):** gegevensbeschermingsautoriteit.be

---

## 🚀 Hosting

De website wordt **gratis gehost** via **GitHub Pages**. Elke wijziging is na **1-2 minuten** live.

---

*Gemaakt met ❤️ voor Smash Patat*
