# Charika Web — landing page de l'agence

One-page pour démarcher des clients (artisans, indépendants, PME). Objectif unique : faire cliquer sur « Demander ma maquette ».

- Repo : `mohamedscaler/LandingPage`, branche `main`
- En ligne (GitHub Pages) : https://mohamedscaler.github.io/LandingPage/
- En local : `~/Sites/charika-web`

## Fichiers

| Chemin | Rôle |
|---|---|
| `index.html` | Toute la page : HTML, CSS (`<style>`), JS (4 `<script>`) |
| `frames/` | 120 JPG 1280 px du tunnel (mobile). Ne pas ouvrir |
| `frames-hd/` | 120 WebP 1920 px du tunnel (ordi). Ne pas ouvrir |
| `images/` | `service-{landing,vitrine,boutique,refonte}.jpg` |

## Structure de la page

1. Nav : pilule en verre fixe, bouton « Demander ma maquette » toujours visible
2. Hero : tunnel 3D piloté par le scroll (canvas `#seq`, section figée 130 %), titre « Des sites qui vendent. »
3. Services (`#services`) : 4 cartes, inclinaison 3D au survol (`.t-tilt`, transitions.dev)
4. Méthode (`#methode`) : 4 tuiles
5. Grand texte défilant, puis Contact (`#contact`)

## Technique

- CDN : GSAP 3.12.5 + ScrollTrigger, Lenis 1.1.13, Three.js 0.160
- Scripts dans l'ordre : tunnel (suite d'images) → interface (GSAP, Lenis, curseur) → tilt des cartes → scène Three.js (objet chrome, `#webgl`)
- Sans GSAP ou en mouvement réduit, la page s'affiche sans animations
- Sur ordi le tunnel charge `frames-hd/`, sur mobile `frames/`

## Style

- Fond `#0b0b0c`, accent violet `#9d84ff`, police Geist / Geist Mono
- Verre façon Apple : flou uniquement sur éléments fixes et boutons, jamais sur les grandes cartes
- Classes Client-First (`padding-global`, `container-large`, `section_x`, `x_item`)
- Le CSS a des blocs de surcharge en fin de `<style>` : ajouter les nouvelles règles à la fin

## Reste à faire

- [x] Lien WhatsApp `https://wa.me/message/AXORZOBAWECGN1` sur tous les « Demander ma maquette » et au contact (mail retiré)
- [x] Section Réalisations retirée (décision : pas de projets montrés)
- [ ] Logo dans la nav (4 pistes générées sur Higgsfield, choix en attente)
- [ ] Avis clients si disponibles
- [ ] Image de partage dédiée (`og:image` pointe pour l'instant sur `images/service-landing.jpg`) et favicon à remplacer par le logo
- [x] Passe impeccable : meta SEO/Open Graph + JSON-LD, focus clavier, lien d'évitement, labels ≥ 12 px, ombre neutre sur le bouton principal

## Règles de travail

- Ne pas relire tout `index.html` : `grep` la partie concernée, lire seulement ces lignes
- Modifications ciblées, jamais de réécriture complète du fichier
- Réponses courtes, en français, tutoiement, pas d'explication après le code
- Un commit par changement, push sur `main`
- Mettre à jour ce fichier quand une tâche est terminée ou qu'une décision change
