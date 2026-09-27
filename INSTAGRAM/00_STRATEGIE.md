# Stratégie Instagram — Alberto Déco

> Document opérationnel. Statut : **v1 à valider par Paolo**. Créé le 27/09/2026 (Hermes, VPS).
> Objectif de la v1 : passer d'une page vide à une **page vitrine crédible** (= 9 contenus), puis installer un rythme de **3 posts/semaine**.

---

## 1. Décisions prises (à corriger si désaccord)

| Sujet | Décision |
|---|---|
| Nature de la page | **Page vitrine + crédibilité** d'abord, génération de devis ensuite |
| Visages | **Alberto Déco (le patron, Soul Higgsfield existant)** + **les 3 ouvriers** = l'équipe. La mascotte reste pour les illustrations/ambiances uniquement |
| Langue | **FR** par défaut (NL en légende secondaire sur les posts « primes », marché flamand étant le plus gros) |
| Type de visuels | **100 % IA** (le client n'a pas encore de photos de chantiers récents) |
| Réalisme | **Obligatoirement belge** : briques cuites, châssis blancs, pierre bleue, sols en carrelage/briques, toits à deux pans, intérieurs belges — jamais de typologie US/espagnole |
| Ici on ne fait pas | Pas de vague de 9 posts le même jour avec des visuels qui se ressemblent : **9 visuels = 9 scènes différentes** |
| Cadence après ouverture | **3/semaine** : mardi = reel avant/après · jeudi = carrousel utilité (primes/conseil) · samedi = statique (matières, équipe, témoignage) |
| Lien en bio | Site `https://alberto-deco.com` + CTA « Devis gratuit sous 24h » |
| Handle | ⏳ **à fournir** (la sœur détient la page, Paolo a les identifiants) |

## 2. Positionnement (fil rouge de toutes les légendes)

> **Entreprise familiale belge depuis 1989 — peinture, rénovation et décoration, partout en Belgique. Devis gratuit sous 24h.**

Trois angles qui reviennent :

1. **Le savoir-faire qui dure** — « depuis 1989 », ~35 ans de métier (crédibilité artisan).
2. **La propreté du chantier** — protection, ordre, respect de la maison : c'est LE critère de choix pour un particulier.
3. **Le gain financier** — primes régionales expliquées simplement (Wallonie / Bruxelles / Flandre).

## 3. Piliers éditoriaux (répartition cible)

| Pilier | Part | Format dominant | Rôle |
|---|---|---|---|
| A. Avant / Après | 40 % | Reel | Preuve. C'est ce qui fait sauvegarder et partager |
| B. Coullisses & équipe | 20 % | Reel | Confiance — on voit qui vient chez soi |
| C. Conseils & primes | 25 % | Carrousel | Portée + utilité (aides régionales = forte demande) |
| D. Matières, couleurs & tendances | 15 % | Statique | Esthétique, abonnés « inspiration » |

## 4. Gabarit des posts

- **Reel (avant/après)** : 6–9 s. Plan 1 : état « avant » (3 s) → transition (1 s, élément qui balaie le cadre) → plan 2 : état « après » (3 s). Son : tendance du moment. Texte incrusté : la ville + la prestation (« Peinture + préparation des murs · Wavre »).
- **Carrousel** : 5–7 slides. Slide 1 = la promesse/questions (« Quelles primes en 2026 ? »), slides 2–6 = une info par slide, dernier slide = CTA devis. Visuel : photo IA + texte incrusté.
- **Statique** : une image forte + 1 à 2 phrases. Peu de texte, beaucoup d'image.
- **Légendes** : 2 lignes utiles + 1 CTA + 5–8 hashtags. Ville mentionnée systématiquement (SEO Instagram local).

## 5. Hashtags (rotation, jamais les mêmes 5 d'affilée)

Établis : `#renovationbelgique #peinturebelgique #renovationgenerale #artisanbelge #renovationinterieure`
Locaux (2 par post) : `#brabantwallon #wavre #louvainlaneuve #waterloo #bruxelles #namur #ottignies #renovationbruxelles`
Thématiques : `#avantapres #peinturerevetement #primesrenovation #menuisierbelge #decorationinterieure`

## 6. Garde-fous (importants)

1. **Traçabilité des visuels** : les visuels IA sont des **démonstrations**. Les posts « avant/après » doivent être présentés comme des **réalisations d'illustration** (mention discrète en légende, ex. « visuel de démonstration ») tant que ce ne sont pas de vraies photos de chantier. Raison : ne pas s'exposer aux critiques « c'est faux » — ça tuerait la crédibilité artisan qu'on cherche justement à construire.
2. **Photos réelles disponibles** : le dossier `WEBSITE/IMG Ref/Avant renovation/` contient de **vraies photos « avant »** de chantier (façades, cuisine, SDB, salon). Les utiliser comme base : « avant » réel + « après » généré = nettement plus crédible qu'un avant/après 100 % IA. À faire dès que Paolo valide.
3. **Pas de faux témoignages nominatifs** : utiliser des avis génériques anonymisés ou de vraies recommandations apportées par Alberto.
4. **Cohérence géographique** : chaque visuel doit être plausible en Belgique. À repasser avant publication.

## 7. Outil & coûts

- Génération via **Higgsfield CLI** (Hermes, VPS) — authentifié, plan pro (600 crédits).
- Repères : **Soul 2.0 (avatar identité-fidèle) = 0,12 crédit/image** · Nano Banana 2 = 1,5 cr/image · vidéo (Kling/Seedance 2.5) = à chiffrer au plan.
- Soul à utiliser : **`Alberto Deco/ Papa` = `cd217d56-7ee9-4b09-ac62-0f78ea1fbddc`**.
- Commande type :
  ```bash
  higgsfield generate create text2image_soul_v2 \
    --prompt "<scène>" --custom_reference_id cd217d56-7ee9-4b09-ac62-0f78ea1fbddc \
    --aspect_ratio 4:5 --quality 2k --wait
  ```

## 8. Automatisation (phase 2, après validation)

Publication automatique n8n (contenu + visuel + légende planifiés) dès que les identifiants Instagram sont fournis → même logique que le projet `veille-contenu`. Non lancé pour l'instant.

## 9. KPI à 90 jours

- 9 posts d'ouverture en ligne
- 30 posts publiés, rythme de 3/semaine tenu
- +X abonnés (à fixer avec Paolo), 5 messages qualifiés/mois, 2 devis issus d'Instagram
