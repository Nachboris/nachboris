# PROJECT.md — Fichier de pilotage Claude

> Lire en premier à chaque session. Contient les règles de réponse et le cadre du projet.

---

## A — Règles de réponse Claude

- **Langue** : anglais pour tout le code et le copy du site. Français pour les échanges avec Boris.
- **Agis directement** : si la demande est claire et le contexte suffisant dans les fichiers, produis le livrable sans demander confirmation. Pose une question uniquement si une ambiguïté bloque vraiment l'output.
- **Livrables complets** : jamais de troncature, jamais de "suite à la demande". Le fichier HTML entier en une seule réponse.
- **Pas de préambule** : pas de "bien sûr !", pas de résumé de ce que tu vas faire. Livrable directement.
- **Placeholders** : tout lien ou info manquante (Calendly, LinkedIn, Twitter, email) → commentaire HTML `<!-- TODO: remplacer par [description] -->`.
- **Cohérence** : avant de générer une nouvelle page ou section, lire `COPY.md` et `DESIGN.md` pour rester aligné avec ce qui est validé.
- **Modifications** : quand Boris demande un ajustement, modifier uniquement ce qui est demandé. Ne pas refactorer le reste.

## B — Objectif du projet

Créer et maintenir le site personnel **nachboris.fr** — site de personal branding pour Boris Nachbaur, opérateur digital freelance.

**Rôle du site :**
1. Présenter Boris de façon humaine et crédible en 10 secondes
2. Communiquer l'offre clairement (pas de jargon)
3. Servir de base pour des pages dédiées ultra-personnalisées par cible (`/marc-lou`, etc.)
4. Inciter à une action simple : email ou call 20 min

## C — Stack technique (non négociable)

- **HTML/CSS/JS pur** — fichier unique par page, tout inline
- **Zéro dépendance** — pas de framework, pas de npm, pas de build step
- **Polices** — Google Fonts via CDN uniquement
- **Déploiement** — Cloudflare Pages (fichiers statiques, fonctionne tel quel)
- **Images** — optimisées, hébergées dans le même dossier ou via URL externe
- **Responsive** — mobile-first obligatoire sur chaque page

## D — Structure du projet

```
nachboris.fr/
├── index.html          ← Homepage généraliste
├── marc-lou.html       ← Page dédiée (exemple)
├── [prenom].html       ← Autres pages dédiées
└── assets/
    └── (images, si nécessaire)
```

## E — Priorités de développement

1. `index.html` — Homepage (P1, à faire en premier)
2. Première page dédiée `/marc-lou` (P2)
3. Pages dédiées suivantes (P3)
4. Ajustements copy et design au fur et à mesure des retours
