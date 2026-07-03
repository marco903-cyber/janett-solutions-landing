# janett-solutions-landing

Site vitrine JANETT Solutions — landing page statique (HTML/CSS pur, aucun
build step nécessaire). Déployé séparément du repo GO Flow principal.

## Structure

```
index.html                    → page d'accueil (hero, modules, exhibits, FAQ)
suite-go.html                 → page Suite GO
methode.html                  → page Méthode
mentions-legales.html         → ⚠️ contient des [à compléter] — voir ci-dessous
politique-confidentialite.html → ⚠️ contient des [à compléter] — voir ci-dessous
assets/                       → captures d'écran GO BIZ utilisées comme exhibits
```

## ⚠️ Avant la mise en ligne publique

Les deux pages légales contiennent des champs `[à compléter]` en surbrillance
(RCCM, NIU, forme juridique, adresse, email de contact, référence exacte de
la loi camerounaise sur la protection des données). **Ne pas publier avant
d'avoir rempli ces champs avec les vraies informations d'immatriculation.**

## Déploiement — première fois

```bash
cd landing-page
git init
git add .
git commit -m "Initial landing page — hero, suite, méthode, legal pages"
git branch -M main
git remote add origin https://github.com/marco903-cyber/janett-solutions-landing.git
git push -u origin main
```

(Créer le repo vide sur GitHub d'abord si `janett-solutions-landing`
n'existe pas encore — via github.com/new, sans README/gitignore pour
éviter un conflit avec le push initial.)

## Connecter à Vercel

1. vercel.com → Add New → Project → Import le repo `janett-solutions-landing`
2. Framework Preset : **Other** (site statique, pas de build step)
3. Build Command : laisser vide
4. Output Directory : laisser vide (racine du repo)
5. Deploy

## Domaine

Une fois déployé, dans Vercel → Settings → Domains :
- Ajouter `janett-solutions.com` (root) → pointe vers ce projet
- Le sous-domaine `biz.janett-solutions.com` (l'application GO BIZ elle-même)
  est un **projet Vercel séparé** — ne pas mélanger avec ce repo

## Ajouter la vidéo d'intro (quand elle sera prête)

1. Placer le fichier `.mp4` exporté depuis Happy Horse dans `assets/`
   (ex. `assets/janett_intro.mp4`)
2. Dans `index.html`, chercher le bloc `<!-- <video id="introVideo" ...`
   (commenté, en haut du `<body>`)
3. Décommenter le bloc et changer `src="janett_intro.mp4"` en
   `src="assets/janett_intro.mp4"`
4. Commit + push — Vercel redéploie automatiquement

## Modifier une page

Chaque page est un fichier HTML autonome avec CSS inline dans `<style>`.
Pas de composants partagés — un changement de nav/footer doit être répété
dans les 5 fichiers `.html`. (Migration vers Next.js prévue plus tard pour
éliminer cette duplication, une fois le site stabilisé.)
