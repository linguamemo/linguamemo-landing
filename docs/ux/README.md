# Améliorations UX / accessibilité / performance — captures et mesures

Mesures faites **en local uniquement** (01/11/2026) :

- site servi par `python3 -m http.server` (avant = `main`, après = branche `ux-linguamemo`) ;
- les hôtes tiers de la version « avant » (`fonts.googleapis.com`, `fonts.gstatic.com`, `stats.crea-dapp.com`) sont redirigés vers un **faux serveur local** (`--host-resolver-rules`, tout autre hôte → `NOTFOUND`, aucun proxy) : aucune requête n'est partie vers Google, Umami ni le site en ligne. Le faux Umami renvoie un script vide.
- captures Playwright (Chromium) en 390×844 (mobile, DPR 2) et 1366×860 (ordinateur) ;
- Lighthouse 12 (préréglage mobile par défaut, puis `--preset=desktop`), 2 à 3 passes chacun, résultats stables.

## Scores Lighthouse

| | Performance | Accessibilité | Bonnes pratiques | SEO | CLS | FCP | LCP | Rendu bloqué |
|---|---|---|---|---|---|---|---|---|
| Mobile — avant | 70 | 91 | 96 | 100 | 0,559 | 2,7 s | 2,7 s | ≈1,9 s (Google Fonts) |
| Mobile — après | 99–100 | 100 | 100 | 100 | 0 | 0,8 s | 1,5–1,7 s | 0 |
| Ordinateur — avant | 95–96 | 91 | 96 | 100 | 0,117 | 0,7 s | 0,7 s | ≈0,5 s |
| Ordinateur — après | 100 | 100 | 100 | 100 | 0 | 0,2 s | 0,4 s | 0 |

Contrastes insuffisants : 8 → 0. Erreurs console : 1 (`/favicon.ico` 404) → 0.

CLS mesuré avec un HTML servi lentement (morceaux de 1,5 Ko toutes les 120 ms) :
mobile 0,546 → 0,001 ; ordinateur 0,294 → 0,000.

## Captures

| Point | Avant | Après |
|---|---|---|
| 1. Bouton principal (mobile, haut) | [avant](1-cta-mobile-hero-avant.png) | [après](1-cta-mobile-hero-apres.png) |
| 1. Bouton principal (ordinateur, haut) | [avant](1-cta-ordinateur-hero-avant.png) | [après](1-cta-ordinateur-hero-apres.png) |
| 1. Bouton bas de page (mobile) | [avant](1-cta-mobile-bas-de-page-avant.png) | [après](1-cta-mobile-bas-de-page-apres.png) |
| 1. Bouton bas de page (ordinateur) | [avant](1-cta-ordinateur-bas-de-page-avant.png) | [après](1-cta-ordinateur-bas-de-page-apres.png) |
| 2. CLS — chargement lent, image à 0,9 s puis finale (mobile) | [avant](2-cls-mobile-chargement-lent-avant.png) | [après](2-cls-mobile-chargement-lent-apres.png) |
| 2. CLS — police de repli puis police web (mobile) | [avant](2-cls-mobile-repli-vs-police-avant.png) | [après](2-cls-mobile-repli-vs-police-apres.png) |
| 3. Contrastes — cartes fonctionnalités (mobile) | [avant](3-contraste-mobile-avant.png) | [après](3-contraste-mobile-apres.png) |
| 3. Contrastes — cartes fonctionnalités (ordinateur) | [avant](3-contraste-ordinateur-avant.png) | [après](3-contraste-ordinateur-apres.png) |
