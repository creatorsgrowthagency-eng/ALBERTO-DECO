# Les 9 posts d'ouverture — Alberto Déco

> Prêt à exécuter. Chaque fiche : format, pilier, **prompt Higgsfield** (en anglais, c'est ce que le modèle comprend le mieux), commande CLI, légende FR, hashtags, notes de production.
> Soul à utiliser partout où Alberto apparaît : `cd217d56-7ee9-4b09-ac62-0f78ea1fbddc` (`Alberto Deco/ Papa`).
> Les **textes incrustés** (ville, prestation) ne sont PAS demandés au modèle : on les ajoute en post-prod (CapCut/Canva) — les modèles génèrent mal le texte, et il faut du FR/NL propre.

## Semaine 1 — lancer la page (le trio « preuve / utilité / visage »)

### Post 1 — REEL avant/après · Salon belge
- **Pilier** : A · **Format** : reel 6–9 s, 4:5 ou 9:16 · **Coût image** : 0,12 cr ×2
- **Prompt (avant)** :
  `Realistic photo of a tired Belgian living room before renovation, dated floral wallpaper, brownish 1970s interior, worn parquet floor, old white PVC window frames, empty room, natural window light, documentary photography, no people, no text`
- **Prompt (après)** :
  `Realistic photo of the same Belgian living room after a complete renovation, freshly painted warm white walls, new light oak parquet, restored white window frames with brick wall visible, elegant minimal styling, plant and linen sofa, natural light, editorial interior photography, no people, no text`
- **CLI** :
  ```bash
  higgsfield generate create nano_banana_flash --prompt "<prompt ci-dessus>" --aspect_ratio 4:5 --wait
  ```
- **Légende** :
  `Salon remis à neuf : murs, plafonds et boiseries — fini les années 80. 🎨`
  `Devis gratuit sous 24h, partout en Belgique.`
  `#avantapres #renovationbelgique #peinturebelgique #brabantwallon #wavre`
- **Notes** : transition de la transition (élément qui balaie le cadre). En post-prod : incruster « Wavre · Peinture + préparation des murs ».

### Post 2 — CARROUSEL · Primes rénovation 2026 (Wallonie / Bruxelles / Flandre)
- **Pilier** : C · **Format** : 5–6 slides · **Visuel** : 1 image générique belle (salle d'un chantier lumineux) + texte incrusté par slide
- **Prompt** :
  `Realistic photo of a bright Belgian house interior with fresh white paint and a ladder, painter's tools neatly arranged on a drop cloth, brick wall, natural light, clean and professional, no people, no text`
- **Slides** : 1) « Primes rénovation : ce qui est encore possible en 2026 » 2) Wallonie 3) Bruxelles 4) Flandre 5) « On vous aide à monter le dossier » 6) « Devis gratuit sous 24h »
- **Légende** : `Les primes changent en 2026 — voici l'essentiel par région. On peut vous aider à monter le dossier.`
- **Hashtags** : `#primesrenovation #renovationbelgique #renovationbruxelles #renovationwallonie #mijnverbouwpremie`
- **Notes** : contenu à valider sur le fond avant publication (les régimes évoluent, cf. section Primes du site).

### Post 3 — STATIQUE · L'équipe / le visage d'Alberto
- **Pilier** : B · **Format** : statique 4:5 · **Coût** : 0,12 cr
- **Prompt (avec Soul)** :
  `Portrait of the man in the reference, a Belgian master painter in his 60s, clean navy workwear, arms crossed, standing in front of a white plastered wall in a bright Belgian house under renovation, warm natural daylight, professional documentary portrait, looking at camera, no text`
- **CLI** :
  ```bash
  higgsfield generate create text2image_soul_v2 --prompt "<prompt>" \
    --custom_reference_id cd217d56-7ee9-4b09-ac62-0f78ea1fbddc --aspect_ratio 4:5 --quality 2k --wait
  ```
- **Légende (bio-post)** : `Depuis 1989, deux générations à peindre et rénover les maisons belges. Alberto, le papa, est toujours sur les chantiers. 👷`
  `#artisanbelge #peinturebelgique #entreprisefamiliale #brabantwallon #depuis1989`

## Semaine 2 — installer les piliers

### Post 4 — REEL avant/après · Salle de bain
- **Prompt (avant)** : `Realistic photo of an outdated Belgian bathroom before renovation, old small square wall tiles in beige, dated washbasin and mirror, worn joints, narrow room, artificial light, documentary photography, no people, no text`
- **Prompt (après)** : `Realistic photo of the same Belgian bathroom fully renovated, large-format grey stone-effect tiles, walk-in shower with black frame glass, matte black taps, round mirror, warm LED lighting, magazine interior photography, no people, no text`
- **Incrustation** : `Waterloo · Salle de bain complète`
- **Légende** : `Une salle de bain des années 90 devenue sobre et moderne. Tous corps de métier coordonnés par Alberto Déco.`
  `#salledebain #renovationbelgique #avantapres #waterloo #renovationsalledebain`

### Post 5 — CARROUSEL · 5 erreurs à éviter avant de repeindre
- **Pilier** : C · **Slides** : 1) la promesse 2) pas de sous-couche sur mur neuf 3) peindre par temps humide 4) mauvais choix de finition (mate/satin) 5) ne pas protéger les sols 6) CTA
- **Prompt** : `Realistic close-up photo of a painter's roller applying soft white paint on a smooth wall in a Belgian house, sharp texture, professional tools, natural light, no people visible, no text`
- **Légende** : `80 % de la qualité d'une peinture se joue avant le premier coup de rouleau. Voici les 5 erreurs qu'on voit le plus souvent.`
  `#conseilpeinture #peinturebelgique #renovationinterieure #bricolagebelgique`

### Post 6 — STATIQUE · Matières & couleurs 2026
- **Pilier** : D · **Prompt** : `Realistic moodboard-style photo of 2026 interior finishing materials: warm white paint swatches, natural linen fabric, light oak wood sample, brushed brass detail, on a light plaster background, soft daylight, flat lay, no text`
- **Légende** : `Notre palette 2026 : blanc chaud, chêne clair, lin et laiton brossé. Simple, lumineux, intemporel.`
  `#decorationinterieure #tendances2026 #interiorbelgium #couleurs #peinture`

## Semaine 3 — élargir au gros œuvre et à la confiance

### Post 7 — REEL avant/après · Façade maison belge
- **Pilier** : A · **Prompt (avant)** : `Realistic photo of a Belgian brick house facade needing renovation, faded and dirty brickwork, dated aluminium windows, cracked jointing, overcast Belgian sky, street view, documentary photography, no people, no text`
- **Prompt (après)** : `Realistic photo of the same Belgian brick house facade after full renovation, clean repointed brickwork, new anthracite aluminium windows, freshly painted white window surrounds, neat front garden, soft daylight, real estate photography, no people, no text`
- **Incrustation** : `Nivelles · Façade + châssis`
- **Légende** : `Façade rafraîchie + châssis remplacés : la maison a 40 ans de moins.`
  `#facade #renovationbelgique #chassis #avantapres #nivelles`

### Post 8 — CARROUSEL · Un chantier propre, étape par étape
- **Pilier** : B · **Slides** : 1) « Ce qui se passe chez vous, jour par jour » 2) protection des sols et meubles 3) préparation des murs 4) peinture 5) remise en ordre + évacuation des déchets 6) CTA
- **Prompt** : `Realistic photo of a well-organised Belgian renovation worksite: floors fully covered with protective cardboard and plastic sheeting, furniture wrapped, paint buckets aligned in a corner, natural light, tidy and professional, no people, no text`
- **Légende** : `On part comme on est arrivés : propre. Protection, préparation, remise en ordre — c'est notre méthode.`
  `#chantierpropre #artisanbelge #renovationbelgique #serieux #confiance`

### Post 9 — STATIQUE · Résultat + invitation
- **Pilier** : A + conversion · **Prompt (avec Soul, optionnel)** : `Realistic photo of the man in the reference, a Belgian painter in his 60s in navy workwear, standing in a freshly finished bright living room painted in warm white, giving a slight nod of satisfaction, natural light, editorial photography, no text`
- **Légende** : `Un chantier terminé, un client qui sourit. C'est le seul résultat qui compte. 🙌`
  `Devis gratuit sous 24h → lien en bio.`
  `#renovationbelgique #peinturebelgique #devisgratuit #brabantwallon #bruxelles`

---

## Ordre de production recommandé

1. **Post 3** (portrait Soul) — le plus identitaire, sert de photo de profil/post épinglé.
2. **Posts 1, 4, 7** (les 3 reels avant/après) — le cœur de la page.
3. **Posts 2, 5, 8, 6, 9** (carrousels + statiques).

**Coût estimé des 9 visuels** : ~10–15 crédits (images), + crédits vidéo si les reels sont animés. Plan pro = 600 crédits/mois : largement dans le budget pour plusieurs mois de contenu.

## Ce qui reste à faire pour publier

- [ ] **@handle** de la page Instagram
- [ ] Validation des visuels générés (Paolo / son père)
- [ ] Montage des 3 reels (CapCut, comme le hero du site)
- [ ] Bio + photo de profil + lien du site
- [ ] Publication (manuelle au début, n8n ensuite)
