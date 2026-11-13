# Charika Web — landing page de l'agence

One-page pour démarcher des clients (artisans, indépendants, PME). Objectif unique : faire cliquer sur « Demander ma maquette ».

- Repo : `mohamedscaler/LandingPage`, branche `main`
- En ligne (GitHub Pages) : https://mohamedscaler.github.io/LandingPage/
- En local : `~/Sites/charika-web`

## Fichiers

| Chemin | Rôle |
|---|---|
| `index.html` | Toute la page : HTML, CSS (`<style>`), JS (4 `<script>`) |
| `frames/` | 120 JPG 861×1076 (recadrage central de la source, mobile/vertical). Ne pas ouvrir |
| `frames-hd/` | 120 WebP 1924×1076 q90 (ordi/écran large). Ne pas ouvrir. Source : `~/Downloads/Video landing page charika /Single-continuous-shot-…mp4` |
| `images/` | `service-{landing,vitrine,boutique,refonte}.jpg`, `logo.jpg`, `favicon.png`, `apple-touch-icon.png` |

## Structure de la page

1. Nav : pilule en verre fixe avec logo, bouton « Demander ma maquette » (WhatsApp) toujours visible
   + CTA flottant en bas (`#floatCta`) : apparaît après le tunnel, masqué sur Contact
2. Hero : tunnel 3D piloté par le scroll (canvas `#seq`, section figée 130 %), titre « Des sites qui vendent. »
3. Services (`#services`) : 4 cartes, inclinaison 3D au survol (`.t-tilt`, transitions.dev)
4. Les étapes (`#methode`) : 4 tuiles
5. À propos (`#apropos`) : « by Miro », logo + texte + 3 faits (Paris, WhatsApp, maquette avant engagement). Pas de photo ni de chiffres inventés
6. Grand texte défilant, puis Contact (`#contact`)

## Technique

- CDN : GSAP 3.12.5 + ScrollTrigger, Lenis 1.1.13, Three.js 0.160
- Scripts dans l'ordre : tunnel (suite d'images) → interface (GSAP, Lenis, curseur) → tilt des cartes → scène Three.js (objet chrome, `#webgl`)
- Sans GSAP ou en mouvement réduit, la page s'affiche sans animations
- Sur ordi le tunnel charge `frames-hd/`, sur mobile `frames/`

## Ton des textes

- Cible : épavistes, nail artists, artisans, gens qui ne connaissent rien à l'informatique
- Mots simples, tutoiement. Bannis : landing page, site vitrine, Shopify/Webflow/Framer, refonte, coder, développer
- Lisibilité d'abord : textes ≥ 18 px, gris clair (#c4c4ca et plus), étiquettes qui portent une info en police normale (pas de mono majuscule)
- Confirmé par Miro : maquette gratuite sur demande, prête en 48 h
- Ne rien affirmer d'autre sans son accord (prix, délais du site complet, zone d'intervention)

## Style

- Fond `#0b0b0c`, accent violet `#9d84ff`, police Geist / Geist Mono
- Verre façon Apple : flou uniquement sur éléments fixes et boutons, jamais sur les grandes cartes
- Classes Client-First (`padding-global`, `container-large`, `section_x`, `x_item`)
- Le CSS a des blocs de surcharge en fin de `<style>` : ajouter les nouvelles règles à la fin

## Reste à faire

- [x] Lien WhatsApp `https://wa.me/message/AXORZOBAWECGN1` sur tous les « Demander ma maquette » et au contact (mail retiré)
- [x] Section Réalisations retirée (décision : pas de projets montrés)
- [x] Logo dans la nav (« C » en verre, `images/logo.jpg`, fond noir fondu en `mix-blend-mode:screen`) + favicon et apple-touch-icon
- [ ] Avis clients si disponibles
- [ ] Image de partage dédiée (`og:image` pointe pour l'instant sur `images/service-landing.jpg`)
- [x] Passe impeccable : meta SEO/Open Graph + JSON-LD, focus clavier, lien d'évitement, labels ≥ 12 px, ombre neutre sur le bouton principal

## Règles de travail

- Ne pas relire tout `index.html` : `grep` la partie concernée, lire seulement ces lignes
- Modifications ciblées, jamais de réécriture complète du fichier
- Réponses courtes, en français, tutoiement, pas d'explication après le code
- Un commit par changement, push sur `main`
- Mettre à jour ce fichier quand une tâche est terminée ou qu'une décision change
