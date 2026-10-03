# Reels avant/après — Alberto Déco (niveau 2 : vidéo IA)

Produits le 28/09/2026. Format **1080 × 1920 (9:16)**, **7,0 s**, 30 fps, H.264, **sans audio** (ajouter un audio tendance dans l'app Instagram).

## Fichiers

| Fichier | Sujet | Ligne incrustée |
|---|---|---|
| `REEL-01-salon.mp4` | Salon (papier peint 70's → blanc chaud + parquet chêne) | Wavre · Peinture & préparation des murs |
| `REEL-02-sdb.mp4` | Salle de bain (beige 80's → pierre + douche italienne) | Waterloo · Salle de bain complète |
| `REEL-03-facade.mp4` | Façade brique belge (sale → rejointoyée + châssis anthracite) | Nivelles · Façade & châssis |

**Variante A/B :** `REEL-01b-salon-resultat-dabord.mp4` — même sujet, structure **« résultat d'abord »** recommandée par la recherche : 1,2 s du résultat fini (accroche) → l'avant → balayage → l'après. 6,4 s. À comparer avec `REEL-01-salon.mp4` pour choisir la structure qu'on généralise (voir `../03_RECHERCHE_30JOURS.md`).

`APERCU-frames.jpg` = contrôle visuel (avant à t=1 s / après à t=5 s pour les 3 reels).
`STILL-1/2/3-avant|apres.jpg` = les 6 images verticales utilisées (réutilisables en posts ou en carrousels).

## Montage

| Temps | Contenu |
|---|---|
| 0,0 → 3,2 s | clip **AVANT** (push-in lent, Kling 3.0 Turbo) + ligne ville/prestation en haut |
| 2,8 → 3,2 s | **transition balayage** (`xfade=wipeleft`, 0,4 s) |
| 3,2 → 7,0 s | clip **APRÈS** + CTA « Devis gratuit sous 24h » en bas |

Textes incrustés en **Fraunces** (500 italic — la typo du site), contour + ombre noirs pour rester lisible sur fond clair.
Script reproductible : `/opt/data/scripts/build_reel.sh <clip_avant> <clip_apres> <sortie> "Ville · Prestation"`

## Coûts réels

- 6 images verticales 9:16 (Nano Banana Pro 2k) : **12 crédits**
- 6 clips vidéo (Kling 3.0 Turbo 1080p, 5 s) : **60 crédits**
- Total reels : **72 crédits** (sur le plan pro)

## Prochaine étape

1. Validation visuelle de Paolo.
2. Publication manuelle (upload + audio tendance dans Instagram).
3. Automatisation n8n quand les identifiants de la page sont fournis.
