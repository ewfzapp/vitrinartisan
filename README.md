# VitrinArtisan.com

Site juridique et administratif gratuit pour artisans et auto-entrepreneurs du BTP.

## Structure

```
vitrinartisan/
├── index.html              ← Page d'accueil
├── ads.txt                 ← AdSense (mettre ton publisher ID)
├── sitemap.xml             ← SEO
├── css/
│   └── style.css           ← CSS commun à toutes les pages
└── pages/
    ├── ia.html             ← Chat IA Juridique (Groq)
    ├── documents.html      ← Modèles de documents + PDF
    ├── demat.html          ← Guide dématérialisation factures
    ├── fiches.html         ← Fiches pratiques SEO
    └── mentions.html       ← Mentions légales
```

## Déploiement GitHub Pages

1. Créer le repo GitHub : `vitrinartisan`
2. Pousser le code :
   ```bash
   cd vitrinartisan
   git init
   git add .
   git commit -m "Initial commit — VitrinArtisan.com"
   git branch -M main
   git remote add origin https://github.com/TON_USER/vitrinartisan.git
   git push -u origin main
   ```
3. Dans GitHub → Settings → Pages → Source : `main` / `/ (root)`
4. Dans Cloudflare DNS (vitrinartisan.com) :
   - CNAME `www` → `TON_USER.github.io`
   - CNAME `@` → `TON_USER.github.io`
   - Ajouter le fichier `CNAME` dans le repo avec : `vitrinartisan.com`

## Configuration IA Juridique

Dans `pages/ia.html`, remplacer :
```javascript
const GROQ_API_KEY = 'VOTRE_CLE_GROQ_ICI';
```

**Option A** (simple, démo) : Mettre la clé Groq directement (risque d'exposition).

**Option B** (recommandée) : Passer par le proxy ia-proxy déjà en place sur Oracle 1.
Modifier l'URL de fetch pour pointer vers ton proxy :
```javascript
const response = await fetch('https://ia.service-express.org/api/chat', {
```
Adapter le proxy pour accepter le system prompt artisan.

## AdSense

Dans `ads.txt`, remplacer `pub-XXXXXXXXXXXXXXXXX` par ton Publisher ID AdSense.
Placer les blocs AdSense dans les pages SEO (fiches.html, demat.html).

## Pages SEO à créer ensuite

- `pages/client-ne-paie-pas.html` — article longue traîne
- `pages/assurance-decennale-obligatoire.html`
- `pages/tva-travaux-renovation.html`
- `pages/facture-electronique-artisan-2026.html`
- `pages/auto-entrepreneur-btp-plafond-2025.html`
