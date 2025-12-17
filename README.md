# Teams Embed Tab

Een simpele Microsoft Teams app om externe content (zoals ClickUp lijsten) te embedden in een Teams tab.

## 🚀 Snelle Setup

### Stap 1: GitHub Repository

1. Maak een **private** repository op GitHub (bijv. `teams-embed-tab`)
2. Upload alle bestanden uit deze map naar de repository
3. Ga naar **Settings** → **Pages**
4. Onder "Source" selecteer **Deploy from a branch**
5. Kies de `main` branch en `/ (root)` folder
6. Klik **Save**

Na een minuut of twee is je site live op:
```
https://JOUW_USERNAME.github.io/teams-embed-tab/
```

### Stap 2: Manifest aanpassen

Open `manifest.json` en vervang:

1. **`{{GENERATE_NEW_GUID}}`** → Genereer een nieuwe GUID op https://www.guidgenerator.com/
2. **`JOUW_GITHUB_USERNAME`** → Je GitHub username (komt 2x voor!)
3. **Developer info** → Je eigen organisatie naam

Voorbeeld:
```json
"id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
"configurationUrl": "https://jandevries.github.io/teams-embed-tab/config.html",
"validDomains": [
    "jandevries.github.io",
    ...
]
```

### Stap 3: App Package maken

Maak een ZIP bestand met **alleen** deze 3 bestanden:
- `manifest.json`
- `color.png`
- `outline.png`

**Belangrijk:** De bestanden moeten in de root van de ZIP zitten, niet in een subfolder!

Op Mac/Linux:
```bash
zip teams-embed-app.zip manifest.json color.png outline.png
```

Op Windows: Selecteer de 3 bestanden → Rechtermuisknop → "Comprimeren naar ZIP"

### Stap 4: Uploaden naar Teams

**Optie A: Sideloading (voor testen)**

1. Open Microsoft Teams
2. Klik op **Apps** (linker sidebar)
3. Klik op **Manage your apps** (onderin)
4. Klik op **Upload an app** → **Upload a custom app**
5. Selecteer je ZIP bestand

**Optie B: Organisatie App Catalog (voor hele team)**

Vraag je IT-admin om de app te uploaden naar de organisatie app catalog.

### Stap 5: Tab toevoegen

1. Ga naar een Teams channel
2. Klik op **+** (tab toevoegen)
3. Zoek "Embed Tab"
4. Plak je ClickUp (of andere) URL
5. Geef de tab een naam
6. Klik **Save**

---

## 📋 ClickUp Setup

Om een ClickUp lijst te delen:

1. Open de lijst/view in ClickUp
2. Klik op **Share** (rechtsboven)
3. Zet **Public link** aan
4. Kopieer de link (begint met `https://sharing.clickup.com/...`)
5. Plak deze in de Teams tab configuratie

---

## ⚠️ Troubleshooting

### "App kan niet worden geladen"
- Check of GitHub Pages actief is (kan paar minuten duren)
- Controleer of de URLs in manifest.json correct zijn

### "Content weigert te laden" / Lege iframe
- Sommige websites blokkeren embedding (X-Frame-Options header)
- ClickUp public links zouden moeten werken
- Test de URL eerst in een normale browser iframe

### "Invalid manifest"
- Controleer of de GUID geldig is (geen quotes, correct format)
- Check of alle URLs beginnen met https://
- Zorg dat de ZIP geen subfolders bevat

---

## 🔒 Privacy & Security

- Deze app draait volledig op GitHub Pages (jouw repo)
- Er worden geen gegevens opgeslagen of verstuurd naar derden
- De iframe laadt direct van de bron (bijv. ClickUp servers)
- Met een private repo kan niemand anders je hosting zien

---

## 📁 Bestanden

| Bestand | Doel |
|---------|------|
| `manifest.json` | Teams app configuratie |
| `config.html` | Configuratiepagina voor URL invoer |
| `tab.html` | De tab zelf met de iframe |
| `color.png` | App icon (192x192, kleur) |
| `outline.png` | App icon (32x32, outline) |

---

## 🔄 Updates

Wil je de app updaten? Pas de bestanden aan in GitHub, en verhoog het `version` nummer in manifest.json (bijv. van "1.0.0" naar "1.0.1"). Upload dan de nieuwe ZIP naar Teams.
