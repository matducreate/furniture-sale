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
| H | Photo 1 |
| I | Photo 2 |
| J | Photo 3 |

4. **Catégories valides** : Electronics, Appliance, Furniture, Bike, Clothing, Kitchen, Sport, Other
5. **Statuts valides** : Available, Reserved, Sold
6. Photo 1 = photo principale (étiquette ou meilleure vue), Photo 2 et 3 = optionnelles

### Exemple de ligne :
```
Bizlife BWC-024P | Appliance | Wine cooler 24 bottles, dual zone | AC100V 115W | 49800 | 22000 | Available | https://drive.google.com/thumbnail?id=XXX&sz=w800 | https://... | 
```

---

## ÉTAPE 2 — Photos (Google Drive)

1. Upload tes photos dans un dossier Google Drive
2. Clic droit sur la photo → **Partager** → "Toute personne avec le lien" → Lecteur
3. Copie le lien de partage :
   `https://drive.google.com/file/d/FILE_ID/view`
4. Transforme en URL directe :
   `https://drive.google.com/thumbnail?id=FILE_ID&sz=w800`
5. Colle dans **Photo 1**, **Photo 2**, ou **Photo 3** selon l'ordre voulu

> Le `sz=w800` contrôle la taille. Tu peux mettre `sz=w400` pour plus petit.

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
const SHEET_ID = 'YOUR_GOOGLE_SHEET_ID';
```
Par ton vrai ID.

Change aussi l'email de contact (cherche `contact@mdumont.ca`).

---

## ÉTAPE 5 — GitHub Pages

1. Crée un repo GitHub **public** : `furniture-sale`
2. Push le fichier `index.html`
3. Settings → **Pages** → Source : `main` → `/root`
4. GitHub génère : `matducreate.github.io/furniture-sale`

---

## ÉTAPE 6 — furniture.mdumont.ca (WHC)

1. GitHub Pages → Settings → **Custom domain** → `furniture.mdumont.ca` → Save
2. WHC → DNS → Ajoute :
   - Type : **CNAME**
   - Nom : `furniture`
   - Valeur : `matducreate.github.io`
3. Propagation : 5-15 minutes ✅

---

## Workflow quotidien

1. Ajoute une ligne dans le Sheet (Name, Category, Description, Prix, Status)
2. Upload photos dans Drive → copie les URLs thumbnail
3. La page se met à jour automatiquement au prochain chargement
4. Marquer vendu → change "Available" → "Sold" dans le Sheet

## Features du site

- Galerie 3 photos par article avec navigation ← →
- Miniatures cliquables dans le modal
- Touches clavier : ← → pour naviguer, Escape pour fermer
- Badge 📷 N sur les cards qui ont plusieurs photos
- Filtre par catégorie auto-généré
- Toggle "Show sold"
- % d'économie calculé automatiquement
- Bouton "Contact to Purchase" avec email pré-rempli
