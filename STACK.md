# STACK.md — Contraintes techniques

> Règles de code non négociables. Claude ne propose jamais de solution incompatible avec ces contraintes.

---

## Stack

| Élément | Choix | Raison |
|---------|-------|--------|
| Langage | HTML/CSS/JS pur | Zéro dépendance, Claude natif, preview double-clic |
| Structure | Fichier unique par page | Déploiement immédiat, pas de build |
| CSS | Inline dans `<style>` | Tout dans un seul fichier |
| JS | Inline dans `<script>` | Idem |
| Polices | Google Fonts CDN | Seule dépendance externe autorisée |
| Images | Dossier `assets/` ou URL externe | Pas de base64 inline sauf icônes SVG simples |
| Framework | Aucun | Pas de React, Vue, Tailwind, Bootstrap |
| Build tool | Aucun | Pas de npm, webpack, vite |

---

## Déploiement — Cloudflare Pages

- Repo GitHub connecté à Cloudflare Pages
- Push sur `main` = déploiement automatique en ~30 secondes
- Pas de commande de build (build command : vide, output directory : `/`)
- Domaine : `nachboris.fr` pointé via DNS Cloudflare

**Workflow de Boris :**
1. Claude génère le fichier HTML
2. Boris ouvre dans le navigateur (double-clic) → preview immédiat
3. Boris valide ou demande ajustements dans le même chat
4. Boris push sur GitHub → Cloudflare déploie automatiquement

---

## Règles de code

### HTML
- DOCTYPE HTML5
- `lang="en"` sur la balise html (site en anglais)
- Meta charset UTF-8
- Meta viewport mobile-first
- Meta description remplie (SEO de base)
- Titre de page : `Boris Nachbaur — Trusted Operator for Founders`
- Sémantique : `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`

### CSS
- Variables CSS dans `:root` pour toutes les couleurs et typos
- Mobile-first : styles de base = mobile, `@media (min-width: 768px)` pour desktop
- Pas de `!important`
- Pas de `position: fixed` sur les éléments de contenu (nav sticky OK)
- Préférer `flexbox` et `grid` à `float`

### Placeholders
Tout lien ou info manquante → commentaire HTML explicite :
```html
<!-- TODO: remplacer par lien Calendly -->
<!-- TODO: remplacer par lien LinkedIn -->
<!-- TODO: remplacer par lien Twitter/X -->
<!-- TODO: remplacer par email de contact -->
<!-- TODO: remplacer par photo de profil -->
```

### Performance
- Pas de polices inutiles (max 2 familles, max 3 weights chacune)
- Pas d'images non optimisées
- Pas de JS inutile — animations en CSS pur quand possible
- Pas de librairies externes (jQuery, GSAP, etc.)

---

## Variables CSS de référence (à utiliser dans chaque fichier)

```css
:root {
  /* Couleurs */
  --bg: #F7F5F2;
  --bg-secondary: #EFEDE9;
  --text-primary: #1A1A18;
  --text-secondary: #6B6B67;
  --text-tertiary: #9B9B97;
  --accent: #D4845A;
  --accent-hover: #C0734A;
  --border: #E2DED8;

  /* Typographie */
  --font-serif: 'Playfair Display', Georgia, serif;
  --font-sans: 'DM Sans', -apple-system, sans-serif;

  /* Espacements */
  --space-xs: 8px;
  --space-sm: 16px;
  --space-md: 24px;
  --space-lg: 48px;
  --space-xl: 80px;
  --space-2xl: 120px;

  /* Layout */
  --max-width: 720px;
  --max-width-wide: 1100px;
  --radius: 8px;
  --radius-lg: 16px;
}
```

---

## Polices Google Fonts

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600&family=DM+Sans:wght@400;500&display=swap" rel="stylesheet">
```

---

## Structure de fichier type

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Meta -->
  <!-- Google Fonts -->
  <style>
    /* Variables CSS */
    /* Reset minimal */
    /* Composants globaux (nav, footer) */
    /* Sections de la page */
    /* Responsive */
  </style>
</head>
<body>
  <nav>...</nav>
  <main>
    <section id="hero">...</section>
    <section id="proof">...</section>
    <section id="offer">...</section>
    <section id="trust">...</section>
    <section id="process">...</section>
    <section id="contact">...</section>
  </main>
  <footer>...</footer>
  <script>
    /* JS minimal si nécessaire */
  </script>
</body>
</html>
```
