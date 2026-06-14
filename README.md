# Aratika — Compagnon de pêche (PWA)

Application web installable, plein écran et hors-ligne, pour les sorties à Aratika.

## Fichiers (à garder ensemble, dans le même dossier)
- `index.html` — l'application (SunCalc intégré, fonctionne hors-ligne)
- `manifest.webmanifest` — déclaration PWA (nom, icônes, couleurs)
- `sw.js` — service worker (cache hors-ligne)
- `icon-192.png`, `icon-512.png`, `icon-180.png`, `icon-maskable-512.png` — icônes

## Important
Une PWA exige d'être servie en **HTTPS** : le service worker ne s'installe pas depuis un
fichier ouvert en `file://`. Il faut donc héberger ces fichiers (gratuit, voir ci-dessous).
Ouvert directement en local, le fichier marche quand même, mais sans installation PWA complète.

## Héberger gratuitement

### Option A — GitHub Pages
1. Créer un dépôt GitHub (public), ex. `aratika`.
2. Y déposer les 7 fichiers (à la racine du dépôt).
3. Settings → Pages → Source : `Deploy from a branch` → branche `main`, dossier `/ (root)` → Save.
4. Après ~1 min, l'app est sur `https://<utilisateur>.github.io/aratika/`.

### Option B — Netlify (glisser-déposer)
1. Aller sur app.netlify.com → « Add new site » → « Deploy manually ».
2. Glisser le dossier contenant les 7 fichiers. URL HTTPS générée aussitôt.

(Cloudflare Pages, Vercel, ou tout serveur HTTPS conviennent aussi.)

## Installer sur le téléphone
- **iPhone (Safari)** : ouvrir l'URL → Partager → « Sur l'écran d'accueil ».
- **Android (Chrome)** : ouvrir l'URL → menu ⋮ → « Installer l'application » / « Ajouter à l'écran d'accueil ».

Au premier chargement en ligne, l'app met en cache la coquille, les polices et le dernier
relevé météo ; ensuite elle s'ouvre et fonctionne sans réseau.

## Mettre à jour l'app
Après toute modification, changer la version du cache dans `sw.js`
(`const CACHE = "aratika-v1";` → `"aratika-v2"`, etc.) pour forcer le rafraîchissement,
puis ré-héberger les fichiers.
