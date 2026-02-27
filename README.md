# 🍔 Smash Patat – Website Documentatie

Live website: https://vermope.github.io/smashpatat.github.io/

---

## 📁 Bestandsstructuur

```
smashpatat.github.io/
├── index.html        → De volledige website
├── logo.png          → Zwart/wit logo (witte achtergrond)
├── sfeer_1.jpg       → Sfeerfoto foodtruck
├── sfeer_2.jpg       → Sfeerfoto burger
├── sfeer_3.jpg       → Sfeerfoto meisje met burger
└── README.md         → Deze documentatie
```

---

## ✏️ Iets aanpassen op de website

1. Ga naar [github.com/vermope/smashpatat.github.io](https://github.com/vermope/smashpatat.github.io)
2. Klik op `index.html`
3. Klik op het **potloodje** (rechtsboven in het bestand)
4. Maak je wijziging
5. Klik op **"Commit changes"**
6. Wacht 1-2 minuten → de website is automatisch bijgewerkt

---

## 🍔 Menu aanpassen

Zoek in `index.html` naar de sectie `<!-- MENU -->`.  
Elke burger ziet er zo uit:

```html
<div class="menu-card">
  <h3>Naam van de burger</h3>
  <p>Ingrediënten hier</p>
  <div class="price">€ 0,00</div>
</div>
```

**Speciale tag toevoegen** (bv. "Nieuw" of "Bestseller"):
```html
<div class="tag">Bestseller</div>
```

**Witte special tag:**
```html
<div class="tag special">★ Special</div>
```

---

## 📅 Locaties & Agenda (automatisch via Google Agenda)

De evenementen op de website worden **automatisch** opgehaald uit Google Agenda.

**Een nieuw evenement toevoegen:**
1. Open Google Agenda op smashpatat@gmail.com
2. Voeg een nieuw event toe met naam, datum, tijd en locatie
3. De website toont het event automatisch — geen aanpassing nodig!

**Alleen jij kan de agenda bewerken** — bezoekers van de website kunnen enkel lezen.

### 🔧 Technische details Google Apps Script

De koppeling loopt via een Google Apps Script dat als tussendienst fungeert.

- **Script URL:** https://script.google.com/macros/s/AKfycbzcmNvWJE-kzNoYDrvGPgRWTe3XNtyaWNenhKjtkaCbZVaV17nHjsJjRF5H3WjahbJWWQ/exec
- **Script beheren:** [script.google.com](https://script.google.com) → inloggen met smashpatat@gmail.com → project "SmashPatatCalendarSyncAPI"
- Het script leest de komende **6 maanden** aan events uit
- Als het script ooit stopt met werken: ga naar Apps Script → Implementeren → Nieuwe implementatie → opnieuw deployen als Webtoepassing

---

## 🖼️ Logo of foto's vervangen

1. Upload het nieuwe bestand op GitHub via **"Add file → Upload files"**
2. Gebruik **exact dezelfde bestandsnaam** (bv. `logo.png`, `sfeer_1.jpg`)
3. GitHub overschrijft het oude bestand automatisch

> ⚠️ GitHub is hoofdlettergevoelig: `Logo.png` ≠ `logo.png`

---

## 🎨 Kleuren & stijl

| Element | Waarde |
|---|---|
| Achtergrond | `#111111` |
| Wit | `#f5f5f0` |
| Rood accent | `#D72B2B` |
| Font titels | Alfa Slab One (Google Fonts) |
| Font tekst | Inter (Google Fonts) |

---

## 📬 Contact & socials aanpassen

Zoek in `index.html` naar `<!-- CONTACT -->` en pas de links aan:

```html
<a href="mailto:smashpatat@gmail.com">...</a>
<a href="https://instagram.com/smashpatat">...</a>
<a href="https://facebook.com/smashpatat">...</a>
```

---

## 🚀 Hosting

De website wordt gratis gehost via **GitHub Pages**.  
Elke wijziging aan `index.html` is na 1-2 minuten live.

> Gemaakt met ❤️ voor Smash Patat
