# furniture.mdumont.ca · Moving Sale Site

## Stack
- **Frontend**: Single HTML file (zero dependencies)
- **Data**: Google Sheets (public, read-only)
- **Hosting**: GitHub Pages → furniture.mdumont.ca

---

## ÉTAPE 1 — Google Sheet

1. Crée un nouveau Google Sheet : **Tokyo Moving Sale**
2. Renomme l'onglet : `Items`
3. Headers en ligne 1 (exact, respecte la casse) :

| Col | Header |
|-----|--------|
| A | Name |
| B | Category |
| C | Description |
| D | Specs |
| E | New Price |
| F | Asking Price |
| G | Status |
| H | Photo URL |

4. **Catégories valides** : Electronics, Appliance, Furniture, Bike, Clothing, Kitchen, Sport, Other
5. **Statuts valides** : Available, Reserved, Sold

### Exemple de ligne :
```
Bizlife BWC-024P | Appliance | Wine cooler 24 bottles, dual zone, excellent condition | AC100V 115W | 49800 | 22000 | Available | https://drive.google.com/...
```

---

## ÉTAPE 2 — Photos (Google Drive)

1. Upload tes photos dans un dossier Google Drive
2. Clic droit sur la photo → **Partager** → "Toute personne avec le lien" → Lecteur
3. Copie le lien de partage : `https://drive.google.com/file/d/FILE_ID/view`
4. Transforme-le en lien direct :
   - De : `https://drive.google.com/file/d/FILE_ID/view`
   - Vers : `https://drive.google.com/thumbnail?id=FILE_ID&sz=w800`
5. Colle cette URL dans la colonne **Photo URL** du Sheet

---

## ÉTAPE 3 — Publier le Google Sheet

1. **Fichier** → **Partager** → **Publier sur le Web**
2. Choisir : **Feuille entière** → **Page Web**
3. Clique **Publier** → confirme
4. Copie l'**ID du Sheet** depuis l'URL :
   `https://docs.google.com/spreadsheets/d/`**`SHEET_ID`**`/edit`

---

## ÉTAPE 4 — Configurer index.html

Ouvre `index.html` et remplace ligne ~160 :
```javascript
const SHEET_ID  = 'YOUR_GOOGLE_SHEET_ID';
```
Par ton vrai ID.

---

## ÉTAPE 5 — GitHub Pages

1. Crée un repo GitHub **privé** : `furniture-sale`
2. Push le fichier `index.html`
3. Settings → **Pages** → Source : `main` branch → `/root`
4. GitHub génère une URL : `matducreate.github.io/furniture-sale`

---

## ÉTAPE 6 — furniture.mdumont.ca (WHC)

1. GitHub Pages → Settings → **Custom domain** → tape `furniture.mdumont.ca` → Save
2. WHC → DNS → Ajoute :
   - Type : **CNAME**
   - Nom : `furniture`
   - Valeur : `matducreate.github.io`
3. Attends 5-15 minutes → furniture.mdumont.ca est live ✅

---

## Workflow quotidien

1. Tu ajoutes une ligne dans le Google Sheet
2. Tu uploads la photo dans Drive, tu copies l'URL thumbnail
3. La page web se met à jour **automatiquement** (pas de redéploiement)
4. Pour marquer vendu → change "Available" → "Sold" dans le Sheet

---

## Mettre à jour l'email de contact

Dans `index.html`, cherche `contact@mdumont.ca` et remplace par ton email.
