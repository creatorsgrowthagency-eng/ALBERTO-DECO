# Spécification des 3 reels avant/après — Alberto Déco

> Répond à : « comment les reels seront faits, quelle durée, quels effets ? »
> Version 28/09/2026. À valider par Paolo avant production.

## 1. Format technique

| Élément | Valeur | Pourquoi |
|---|---|---|
| Format | **1080 × 1920 (9:16)** | Format natif Reels — plein écran, meilleure portée. Les visuels actuels sont en 4:5 (posts) → à régénérer en 9:16 pour les reels |
| Durée | **7 s** (6 à 9 s accepté) | Assez court pour être regardé en boucle, assez long pour que l'avant/après soit lisible |
| Poids | < 50 Mo, H.264 | Limite d'upload Instagram |
| Son | **aucun son intégré** | On ajoute un **audio tendance** dans l'app Instagram à la publication (ce qui booste la portée) — jamais de musique intégrée au fichier |
| Boucle | début = fin visuellement proches | Le reel rejoue sans coupure visible |

## 2. Structure du reel (7 s)

| Temps | Image | Mouvement / effet |
|---|---|---|
| 0,0 → 2,6 s | **AVANT** | Lent **push-in** (zoom avant 100 % → 108 %), très subtil |
| 2,6 → 3,0 s | transition | **Balayage** (wipe) : un élément passe devant l'objectif et masque le cadre — c'est le code visuel qu'on a déjà utilisé sur le hero du site |
| 3,0 → 6,6 s | **APRÈS** | **Push-in** inverse ou léger **dolly** latéral (100 % → 110 %), dans l'autre sens que l'avant pour marquer le changement |
| 6,6 → 7,0 s | fin | Retour progressif à l'image d'ouverture → boucle naturelle |

**Textes incrustés** (ajoutés en post-prod, jamais par le modèle) :
- En haut, 3 s : `Wavre · Peinture & préparation des murs` (ville + prestation)
- En bas, à partir de 3 s : `Devis gratuit sous 24h` (petit, fixe)
- Style : typo **Fraunces italique** (celle du site), blanc, ombre portée légère. Jamais plus de 6 mots à l'écran.

## 3. Deux niveaux de production

**Niveau 1 — « stills animées » (recommandé pour démarrer) — coût : 0 crédit**
Les deux images (avant + après) sont animées par un **Ken Burns** (zoom/pan lent) avec ffmpeg, puis assemblées avec la transition de balayage. Résultat : un vrai reel qui bouge, indétectable d'un reel filmé à l'iPhone, et **gratuit**. C'est ce que font énormément de comptes de rénovation.

**Niveau 2 — « image → vidéo IA » (si on veut plus de vie) — coût : ~7,5 crédit par clip de 5 s**
Kling 3.0 Turbo (`kling3_0_turbo`, 5 s, 720p) anime l'image : peinture qui coule, poussière dans la lumière, rideau qui bouge, ouvrier qui passe au fond. Un clip par image.
- 3 reels = 6 clips = **~45 crédits** (sur les 561 restants).
- Option intermédiaire : n'animer que les 3 **« après »** (3 × 7,5 = **22,5 cr**) et garder les « avant » en Ken Burns → meilleur rapport effet/prix.

## 4. Ce dont j'ai besoin pour produire

1. Ton **choix de niveau** (1, 2 ou intermédiaire).
2. Validation des 3 paires actuelles → je les **régénère en 9:16** pour les reels (**12 crédits** pour les 6 images).
3. Le **CapCut** n'est même pas nécessaire : je sors le MP4 final monté (ffmpeg) ; toi tu n'ajoutes que l'audio tendance dans Instagram.

## 5. Ce qu'on ne fait pas

- Pas de voix off (aucun son parlé) — les reels rénovation performent mieux en musique + texte.
- Pas de texte généré par l'IA (souvent illisible et faute d'orthographe) : tout le texte est incrusté proprement après.
- Pas de musique intégrée (détection de droits + perte du boost « audio tendance »).
