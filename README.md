# 🍔 Smash Patat – Website Documentatie

**Live website:** https://vermope.github.io/smashpatat.github.io/

---

## 📁 Bestandsstructuur

```
smashpatat.github.io/
├── index.html        → De volledige hoofdpagina
├── privacy.html      → Privacybeleid (GDPR-verplicht)
├── menu.json         → Menu database (burgers, dranken, bijgerechten, extras)
├── logo.png          → Zwart/wit logo (witte achtergrond) + favicon
├── sfeer_1.jpg       → Sfeerfoto foodtruck
├── sfeer_2.jpg       → Sfeerfoto burger
├── sfeer_3.jpg       → Sfeerfoto meisje met burger
└── README.md         → Deze documentatie
```

---

## ✏️ Iets aanpassen op de website

1. Ga naar **github.com/vermope/smashpatat.github.io**
2. Klik op `index.html` (of `privacy.html` of `menu.json`)
3. Klik op het **potloodje** (rechtsboven in het bestand)
4. Maak je wijziging
5. Klik op **"Commit changes"**
6. Wacht 1-2 minuten → de website is automatisch bijgewerkt

---

## 🍔 Menu aanpassen

Het menu wordt nu **automatisch geladen** uit `menu.json`. Dit bestand kan ook door de kassa-app worden gebruikt.

### Menu bewerken:

1. Open `menu.json` op GitHub
2. Pas de gewenste items aan
3. Commit de wijzigingen
4. De website laadt automatisch de nieuwe data

### Voorbeeld structuur:

```json
{
  "burgers": [
    {
      "id": "classic",
      "name": "Classic",
      "description": "Dubbel premium beef patty, smash patat saus, sla, tomaat, ui, pickle",
      "price": 9.50,
      "tag": "Bestseller"
    }
  ],
  "sides": [
    {
      "id": "friet",
      "name": "Friet",
      "price": 3.50
    }
  ],
  "drinks": [
    {
      "id": "fris-pils",
      "name": "Fris/Pils",
      "price": 2.80
    }
  ],
  "extras": [
    {
      "id": "cheddar",
      "name": "Cheddar",
      "price": 1.00
    }
  ]
}
```

### Huidig menu:

| Burger | Ingrediënten | Prijs |
|--------|-------------|-------|
| **Kids Smash** | Premium beef patty, saus naar keuze, gefrituurde ajuin | €5,50 |
| **Classic** | Dubbel premium beef patty, smash patat saus, sla, tomaat, ui, pickle | €9,50 |
| **Double Cheese** | Dubbel premium beef patty, cheddar, pickle, ketchup, mosterd, ui | €9,50 |
| **Chili** | Dubbel premium beef patty, smash patat chili saus, romige relish, sla, jalapeño mix | €11,00 |
| **Gorgo ★ Special** | Dubbel premium beef patty, zesty gorgonzola, peer confijt, rucola, tomaat, ui | €11,00 |

**Bijgerechten:** Friet (€3,50)  
**Dranken:** Fris/Pils (€2,80), Speciaal Bier (€3,50)  
**Extra toppings:** Pancetta (€1), Extra Patty (€2), Cheddar (€1), Emmental (€1)

### Tags aanpassen:

- **Bestseller tag:** `"tag": "Bestseller"`
- **Special tag:** `"tag": "Special"` (wordt automatisch wit met ★)
- **Geen tag:** `"tag": null`

---

## 📅 Locaties & Agenda (automatisch via Google Agenda)

De evenementen op de website worden automatisch opgehaald uit Google Agenda.

### Een nieuw evenement toevoegen:

1. Open **Google Agenda** op smashpatat@gmail.com
2. Voeg een nieuw event toe met **naam, datum, tijd en locatie**
3. De website toont het event automatisch — **geen aanpassing nodig!**

*Alleen jij kan de agenda bewerken — bezoekers van de website kunnen enkel lezen.*

---

## 🔧 Technische details Google Apps Script

De koppeling loopt via een Google Apps Script dat als tussendienst fungeert.

- **Script URL:** `https://script.google.com/macros/s/AKfycbzcmNvWJE-kzNoYDrvGPgRWTe3XNtyaWNenhKjtkaCbZVaV17nHjsJjRF5H3WjahbJWWQ/exec`
- **Script beheren:** script.google.com → inloggen met smashpatat@gmail.com → project **"SmashPatatCalendarSyncAPI"**
- Het script leest de **komende 6 maanden** aan events uit
- Als het script ooit stopt met werken: ga naar Apps Script → **Implementeren** → **Nieuwe implementatie** → opnieuw deployen als **Webtoepassing**

---

## 🖼️ Logo of foto's vervangen

1. Upload het nieuwe bestand op GitHub via **"Add file → Upload files"**
2. Gebruik **exact dezelfde bestandsnaam** (bv. `logo.png`, `sfeer_1.jpg`)
3. GitHub overschrijft het oude bestand automatisch

⚠️ **GitHub is hoofdlettergevoelig:** `Logo.png` ≠ `logo.png`

Het logo wordt ook gebruikt als **favicon** (icoontje in het browsertabblad). Bij het vervangen van `logo.png` wordt het favicon dus automatisch ook bijgewerkt.

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

De website bevat een aparte `privacy.html` pagina, **verplicht onder de GDPR/AVG**. De footer van de hoofdpagina linkt automatisch naar deze pagina.

Bij wijzigingen in hoe je gegevens verwerkt (bv. nieuw contactformulier, analytics toevoegen), dien je ook `privacy.html` bij te werken. Vergeet dan ook de datum **"Laatst bijgewerkt"** bovenaan aan te passen.

De toezichthouder in België is de **Gegevensbeschermingsautoriteit (GBA):** gegevensbeschermingsautoriteit.be

---

## 🚀 Hosting

De website wordt **gratis gehost** via **GitHub Pages**. Elke wijziging aan `index.html`, `privacy.html` of `menu.json` is na **1-2 minuten** live.

---

*Gemaakt met ❤️ voor Smash Patat*
