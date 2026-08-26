# PROJECT STATUS — Alberto Deco (site vitrine)

> Source de vérité unique du projet. Chaque session (Cowork, Claude Code local, VS Code) doit LIRE ce fichier au démarrage et le METTRE À JOUR à la fin.

**Dernière mise à jour :** 2026-08-26 — session Cowork (génération des visuels/vidéo hero avec avatar Alberto Deco + équipe, intégration scroll-scrub dans la maquette)
**Statut global :** 🟡 En cours — Maquette HTML (`index.html`) très avancée visuellement (logo final, charte bleu marine, FR/NL/EN, section Primes à jour, hero vidéo scroll-scrub intégré) et en ligne sur alberto-deco.com ; développement du site final (Next.js/Tailwind) pas commencé

---

## 1. Objectif du projet

Site vitrine bilingue (FR/EN) one-page pour Alberto Deco (rénovation/peinture, Brabant wallon, Belgique).
- **V1** : site vitrine + hero vidéo motion + formulaire contact + booking + WhatsApp + chatbot + SEO
- **V2** : devis IA, portail client, CRM, agent IA photo→visuel→devis

> Note : la maquette (`index.html`) est désormais trilingue **FR/NL/EN** (le néerlandais a été ajouté — voir section 4), à reporter dans le site final V1/V2.

## 2. Stack technique décidée

- Next.js + Tailwind CSS (base : ixartz/Next-JS-Landing-Page-Starter-Template, pas encore appliqué)
- Déploiement : Vercel
- Code source : GitHub (repo `creatorsgrowthagency-eng/ALBERTO-DECO`), dossier local `~/Documents/CLAUDE LOCAL/ALBERTO DECO`
- Domaine : `alberto-deco.com`, acheté et actif chez Wix jusqu'au 08/09/2027, DNS géré depuis Wix (pas de transfert de registrar effectué — solution la plus simple et gratuite)
- MCP connectés : Higgsfield (génération image/vidéo), Vercel (déploiement), 21st.dev Magic (composants UI), Intégration GitHub (à vérifier/activer selon la session)
- Skill installé : OSideMedia/higgsfield-ai-prompt-skill (prompts Kling 3.0)

## 3. Budget crédits Higgsfield

Plafond fixé : 97 crédits pour tout le site. Dépense estimée à date : images (~30-40cr) + storyboards (2cr) + 7 clips vidéo prévus (~48.5cr) + logo maquette (1 génération Higgsfield, image finale choisie).

## 4. Fait ✅

- Toutes les images avant/après validées : extérieur, cuisine, salle de bain (voir job IDs section 7)
- Persona "Alberto Deco" (mascotte, généré via Nano Banana, identité verrouillée)
- Storyboards Scene A/B validés
- Plan des 10 plans vidéo finalisé (3 wipe pairs en post-prod + 7 clips caméra Kling 3.0) avec prompts et images de référence
- Repo GitHub + dossier local + Project Cowork créés
- **Statut domaine clarifié et résolu** : `alberto-deco.com` était toujours actif chez Wix (jusqu'au 08/09/2027), abonnement site (pas domaine) non renouvelé — accès au compte Wix toujours disponible, aucun rachat nécessaire
- Maquette HTML de validation (`index.html`, ex `albertodecomockup.html`) déployée sur Vercel (projet `alberto-deco`), connectée au repo GitHub — chaque push GitHub redéploie automatiquement
- Bandeau "Maquette de validation" retiré de la page
- DNS configuré sur Wix : A record `@` → `76.76.21.21`, CNAME `www` → `cname.vercel-dns.com` (anciens A records Wix supprimés)
- Domaine `alberto-deco.com` et `www.alberto-deco.com` rattachés au projet Vercel, certificat SSL généré
- Site testé et accessible en ligne sur le vrai nom de domaine (avec et sans www)
- **Recolorisation complète** : tous les boutons/accents orange remplacés par un bleu marine élégant (`--blue:#1e3a5f`, `--blue-dark:#14283f`), cohérent avec le reste de la charte crème/charbon/laiton
- **Logo final choisi et installé** : logo généré via Higgsfield (job `2a3b77ec-4efe-4f2e-b4f4-eb6766673f4d`), badge circulaire navy "ALBERTO DÉCO — SINCE 1989", installé seul (sans texte à côté) dans le header et le footer ; fichier recadré pour supprimer une marge transparente parasite qui créait un effet de "halo/ombre" autour du logo
- Ancien bandeau texte "ALBERTO DECO" retiré du coin de la photo hero
- Header : logo agrandi (~2.5x, ~118px affiché), animation d'entrée + hover discrets, bandeau beige réduit d'environ 30% en hauteur (le logo dépasse légèrement sur la photo hero, taille identique avant/pendant le scroll), menu (Services/Réalisations/Primes/Avis/Contact) repassé en typo Fraunces italique, un peu plus grande
- **Néerlandais (NL) ajouté comme 3e langue** sur toute la maquette (bascule FR/NL/EN dans le header, footer, formulaire, primes, avis clients), même système `data-fr`/`data-en`/`data-nl` + `setLang()`
- Correction d'un bug CSS de spécificité qui faisait s'afficher les 3 langues en même temps sur certains éléments (labels du formulaire de contact, liens de navigation du footer, attribution des avis clients) — vérifié visuellement dans les 3 langues
- Zone géographique généralisée à **"partout en Belgique" / "across Belgium" / "in heel België"** partout sur le site (hero, services, avant/après, galerie, contact, footer) — **sauf la section Primes**, qui reste organisée par région (la subvention dépend de la région du bien, pas de la localisation de l'entreprise)
- **Section Primes réécrite** avec recherche en ligne des infos à jour (août 2026) :
  - Bloc **Wallonie** mis à jour (pas supprimé) : régime actuel "Primes Habitation" actif jusqu'au 30/09/2026, nouveau régime permanent dès 01/10/2026 (détails non encore publiés), mention du verrou de 8 ans si audit réservé avant l'échéance
  - Bloc **Bruxelles** conservé (Rénolution suspendu depuis 2025, crédit ECORENO, TVA réduite pompe à chaleur, Prêt Bleu, prêt à taux zéro annoncé 2027)
  - Nouveau bloc **Flandre** ajouté (Mijn VerbouwPremie : isolation, châssis, pompes à chaleur, chauffe-eau thermodynamique ; 4 catégories de revenus ; restrictions dès 01/03/2026)
- Aperçu de la maquette maintenu à jour via un Artifact Claude (lien privé, différent du déploiement Vercel réel) : https://claude.ai/code/artifact/d40ecf6a-1311-4f2c-9c7f-a327122a7d6b
- `index.html` et `logo-alberto-deco-final.png` resynchronisés dans le dossier local à chaque itération, changements déjà commités sur `main` (voir `git log`, commit le plus récent `19f7db3 "update"`, synchronisé avec `origin/main`)
- **Analyse concurrentielle SEO/GEO** (peintres/rénovateurs Brabant wallon : Qualideco, BW Decor, Moret & Fils, J-Décoration) : meilleures pratiques identifiées — title/meta description keyword+zone+CTA, JSON-LD `HousePainter` (Moret), aucun concurrent n'a de vrai `llms.txt` custom (seul J-Décoration a un llms.txt Wix générique orienté MCP, pas de contenu GEO travaillé) → quick-win clair pour Alberto Déco
- **Optimisation SEO/GEO on-page de `index.html`** appliquée à partir de cette analyse :
  - `<title>` et `<meta description>` réécrits (mots-clés peinture/rénovation/décoration + Belgique + devis gratuit)
  - `<link rel="canonical">`, meta `robots`, Open Graph + Twitter Card ajoutés
  - Données structurées **schema.org JSON-LD `HousePainter`** ajoutées (areaServed Belgique/Brabant wallon/Bruxelles/Wallonie/Flandre, telephone, sameAs Facebook, services via `makesOffer`) — validé JSON valide
  - H1 réécrit en FR/EN/NL pour intégrer les mots-clés principaux (peinture/rénovation) tout en gardant le ton de marque
  - Alt text des images du hero enrichis (cohérence avec la section avant/après)
  - Fichiers `robots.txt`, `sitemap.xml`, `llms.txt` créés à la racine du repo (référencés pour Vercel)
  - 2 points de détail laissés en suspens (non bloquants) → voir section 6b "Backlog non prioritaire"
- **Vidéo hero intégrée** : Paolo a généré lui-même (dans l'UI Higgsfield, avec les prompts/conseils de cette session) une séquence complète de plans (vue aérienne de la maison, arrivée de la camionnette noire "Alberto Deco" + équipe de 3 ouvriers, travaux en façade/cuisine/salle de bain avec avant/après, avatar "Alberto Deco" qui peint dans le salon, sortie par la porte d'entrée, chargement de la camionnette en fin de chantier), montée dans CapCut en une vidéo unique de 15s (16:9). Intégrée dans `index.html` à la place de l'ancien système d'images avant/après qui changeaient au scroll : le hero utilise maintenant une vraie balise `<video>` (`hero-video.mp4` + poster `hero-video-poster.jpg`) dont la lecture est pilotée image par image par le scroll (`video.currentTime` calculé depuis la position de scroll, sans autoplay ni lecture automatique), conformément au plan de motion documenté dans le notebook NotebookLM "Web Design". Testé et validé visuellement (Playwright) avant intégration.
- Nouveau **Soul Higgsfield "Alberto Deco / Papa"** entraîné par Paolo (personnage identité-fidèle) et utilisé pour générer les visuels de l'avatar dans toutes les nouvelles scènes (profil peinture, sortie de la maison, chargement camionnette) — remplace l'ancienne mascotte statique Nano Banana pour ces plans.
- Nouvelles images de référence créées pour la cohérence des personnages : planche 3 ouvriers (identité + tenue de travail avec logo), planche multi-angles de l'avatar, référence camionnette noire avec logo blanc.
- Nouvelles images avant/après cuisine et salle de bain générées avec Nano Banana 2 (démontage en cours avec un ouvrier visible → pièce rénovée moderne vide), animées en clips séparés (pas de transition morphing entre les deux états — approche qui s'est révélée peu fiable avec Kling 3.0, remplacée par 2 clips distincts assemblés par un cut classique dans CapCut).

## 5. En cours 🟡

- Vercel recommande une migration du CNAME `www` vers une nouvelle valeur (`...vercel-dns-017.com`) — non urgent, l'ancien CNAME continue de fonctionner

## 6. À faire 🔜 (ordre)

1. ~~Générer les clips vidéo + monter la vidéo hero finale~~ — **fait** : vidéo hero de 15s montée par Paolo (Higgsfield + CapCut), intégrée en scroll-scrub dans la maquette (voir section 4)
2. Coder le site Next.js/Tailwind, reporter le hero vidéo scroll-scrub déjà fonctionnel dans la maquette — **remplacera la maquette HTML actuellement en ligne** (reporter aussi la charte bleu marine, le logo, le FR/NL/EN, la section Primes et le SEO/GEO déjà en place dans la maquette)
3. Copy FR/EN/NL définitive (texte du site) — la maquette a maintenant un texte FR/EN/NL complet à titre indicatif, à valider/enrichir par Paolo pour le site final
4. ~~Logo vectoriel propre~~ — **résolu** : logo Higgsfield final choisi et installé (voir section 4)
5. Infos légales/entreprise pour footer — **manquant**
6. ~~Statut domaine alberto-deco.com (transfert ?)~~ — **résolu, voir section 4**
7. Ajouter les fonctionnalités (voir section 8)
8. Redéployer la version finale sur Vercel (le lien domaine/DNS restera identique, aucune reconfiguration nécessaire)
9. ~~Stratégie SEO / visibilité LLM~~ — **fait pour la maquette actuelle** (voir section 4) : title/meta description, H1, alt text, sitemap.xml + robots.txt, schema.org, llms.txt. À reporter tel quel dans le site Next.js final (point 2), et à enrichir de pages dédiées par ville/région si le site final passe en multi-pages
10. Optimisation performance (compression images, lazy loading) une fois le contenu final ajouté
11. Vérifier/activer le connecteur MCP GitHub pour cette session si besoin d'accès direct en lecture/écriture au repo

## 6b. Backlog non prioritaire / non urgent

- Incohérence entre le badge du logo ("ALBERTO DÉCO — SINCE 1989") et le texte du site ("+30 ans d'expérience", ce qui pointe vers ~1996) — à clarifier avec Paolo (quelle est la vraie date de création ?) avant d'ajouter un `foundingDate` en schema.org sur le site final
- URL Facebook utilisée dans le `sameAs` du schema.org (`facebook.com/renovationbatiment1`) déduite automatiquement du handle `@renovationbatiment1` affiché sur le site — à vérifier que c'est bien la bonne page avant mise en prod définitive

## 7. Images validées (job IDs Higgsfield)

| Rôle | Job ID |
|---|---|
| Extérieur avant | `21221cbf-8ebe-4c58-a4b5-35521f700eee` |
| Extérieur après | `6c432d05-b418-4041-8995-1a9b927a6f35` |
| Cuisine avant | `3e818d4a-6efe-4737-9115-f7166d0a7e94` |
| Cuisine après | `9b2f47d0-2e4a-48a0-946d-01e6416a8f6a` |
| Salle de bain avant | `12530aff-1221-4a9a-99c1-f4e884a0febd` |
| Salle de bain après | `e4d6d04d-dee2-4df3-8c94-4113e7411c7e` |
| Salon avant + persona (large) | `03bed3c0-d82a-45f6-942f-1be16940c619` |
| Salon avant + persona (profil) | `648cbf5e-a8d8-41a0-b478-3fd9130f6476` |
| Salon après | `033e1f16-3961-4ddb-be8a-6c2f67c150b6` |
| Persona sort avec matériel | `20f3f6c0-8feb-40a1-9791-e94fde7b8b2a` |
| Persona s'éloigne (échelle) | `2a7c73e7-729b-4dc7-bbbd-725c139c69fb` |
| Vue aérienne après | `e8225084-e3e6-4e5d-b6f9-97f03fa7076e` |
| Logo final Alberto Deco | `2a3b77ec-4efe-4f2e-b4f4-eb6766673f4d` |

## 8. Ressources gratuites à intégrer (fonctionnalités, pas encore fait)

- Formulaire contact → Next.js + Resend
- Booking → Cal.com (embed + sync Google Calendar)
- WhatsApp click-to-chat → lien `wa.me`
- Chatbot IA → github.com/Open-Chat-Widget/openchatwidget
- ~~SEO/GEO (visibilité LLM) → fichier `llms.txt` + schema.org~~ — **fait sur la maquette**, voir section 4

## 9. En attente de décision / brainstorm

- Agent IA "photo + devis" (V2) — pas de plan technique, outil de génération visuelle à redéfinir (pas de resource GitHub retenue à ce jour)
- Connecteurs MCP vérifiés (session Cowork 2026-08-25) : **Vercel MCP** confirmé non connecté (registre : `not_installed`) — déploiement continue de fonctionner automatiquement via push GitHub, donc non bloquant sauf si on veut piloter Vercel depuis le chat ; **GitHub** : aucun connecteur MCP dédié trouvé dans le registre (recherches "github"/"git repository" infructueuses) — l'accès actuel se fait uniquement via le pont "device bridge" vers le dossier local (lecture/écriture des fichiers + `git` en lecture seule), pas de push/PR direct depuis Cowork à ce jour ; **Resend** trouvé dans le registre mais non installé/connecté ; **Cal.com** absent du registre (alternatives type Calendly présentes mais non demandées) ; **chatbot widget** dédié absent du registre. Voir section 11 pour le détail complet transmis à Paolo.
- Un dossier `Avatar/` (photos personnelles de référence, ~20 photos) a été ajouté dans le dossier local. Idée évoquée : entraîner un **Soul Higgsfield** (personnage identité-fidèle) à partir de ces photos pour améliorer les rendus vidéo/image d'un avatar humain, en complément ou à la place de la mascotte "Alberto Deco" (Nano Banana). Une sélection de 16 photos a été proposée par Claude (recadrage EXIF corrigé, exclusion des photos à dominante violette et de celles avec une autre personne trop présente) mais **l'entraînement n'a pas été lancé** — décision et lancement à confirmer par Paolo.

## 10. Autres projets (hors scope Alberto Deco)

- rediumvex/ai-video-generator-claude (skills prompts Seedance) — à installer plus tard pour un autre projet

## 11. Journal des sessions

| Date | Session | Résumé |
|---|---|---|
| 2026-08-25 | Cowork | Recherche prompting vidéo, storyboards, plan vidéo final, setup GitHub/repo/Project, connexion MCP Vercel + 21st.dev, création de ce fichier |
| 2026-08-25 | Cowork | Clarification statut domaine (toujours actif chez Wix, pas de rachat nécessaire). Renommage `albertodecomockup.html` → `index.html`, suppression bandeau maquette, déploiement de la maquette sur Vercel (projet `alberto-deco`), configuration DNS Wix → Vercel (A + CNAME), rattachement du domaine au projet Vercel et génération SSL. Site vérifié en ligne sur alberto-deco.com. Fusion de ce fichier avec une version dupliquée créée par erreur lors d'une session précédente. |
| 2026-08-25 | Cowork | Recolorisation logo, choix logo final + correction halo/ombre (recadrage PNG serré autour du disque marine), suppression bandeau, agrandissement logo header/footer avec animation d'entrée élégante, réduction ~30% de la hauteur du bandeau beige header (logo autorisé à déborder), typo nav plus élégante/grande, ajout langue NL (+ correction de 2 bugs CSS de spécificité multi-langue), passage du texte de zone géographique à "partout en Belgique" partout sauf section Primes, réécriture complète de la section Primes en 3 blocs régionaux (Wallonie/Bruxelles/Flandre). Lien Artifact de preview maintenu à jour. Mise à jour de ce fichier suite à confusion initiale (dossier Avatar découvert mais aucun entraînement Soul lancé, sur demande explicite de Paolo). Vérification des connecteurs MCP manquants (Vercel non connecté, pas de connecteur GitHub dédié, Resend/Cal.com/chatbot non connectés) et rédaction du plan des prochaines tâches. |
| 2026-08-25 | Cowork | Recolorisation orange→bleu marine sur toute la maquette. Choix et installation du logo final (Higgsfield, badge circulaire navy "since 1989") seul dans le header/footer, suppression du bandeau texte "ALBERTO DECO" sur la hero. Ajout du néerlandais (NL) comme 3e langue partout sur le site. Généralisation de la zone géographique en "partout en Belgique" (hors section Primes). Réécriture de la section Primes avec recherche à jour : bloc Wallonie mis à jour (transition 30/09→01/10/2026) au lieu d'être supprimé, bloc Bruxelles conservé, nouveau bloc Flandre ajouté. Correction d'un bug de bascule de langue (3 langues affichées simultanément sur certains éléments). Itérations sur le header : logo agrandi ~2.5x, recadrage du fichier logo pour supprimer un halo/ombre parasite, typo du menu repassée en Fraunces italique, bandeau beige réduit d'environ 30% en hauteur avec logo qui déborde sur la photo hero. Aperçu maintenu via Artifact Claude. Changements commités et poussés sur `main`/`origin/main`. Sélection (non lancée) de 16 photos du dossier `Avatar/` en vue d'un futur entraînement de Soul Higgsfield. |
| 2026-08-25 | Cowork (nouvelle discussion) | Setup/debug des MCP en local sur Claude Code (Mac) : connecteur GitHub (`@modelcontextprotocol/server-github`) et Magic 21st.dev (clé API régénérée) installés et confirmés `✔ Connected` via `claude mcp list`. Aucun changement de code sur le site. Correction d'une confusion : cette session avait d'abord créé une copie obsolète de ce fichier (sans accès au dossier local) — accès direct confirmé et utilisé via le pont device bridge pour relire l'état réel avant toute modification, rien écrasé. |
| 2026-08-26 | Claude Code local | Analyse concurrentielle SEO/GEO sur 4 concurrents directs en Brabant wallon (Qualideco, BW Decor, Moret & Fils, J-Décoration) : comparaison title/meta description, H1, schema.org, robots.txt/sitemap.xml, llms.txt. Constat clé : aucun concurrent n'a de `llms.txt` réellement travaillé pour le GEO (seul un fichier Wix générique chez J-Décoration) → opportunité de différenciation. Optimisation SEO/GEO on-page de `index.html` appliquée directement : title + meta description réécrits, `<link rel="canonical">`, meta `robots`, Open Graph + Twitter Card, JSON-LD schema.org `HousePainter` (areaServed Belgique/Brabant wallon/Bruxelles/Wallonie/Flandre, téléphone, sameAs, services), H1 FR/EN/NL réécrit pour inclure les mots-clés peinture/rénovation, alt text du hero harmonisés. Création de `robots.txt`, `sitemap.xml`, `llms.txt` à la racine du repo. Aucun commit/push effectué (fichiers modifiés/créés en local, à committer par Paolo ou lors d'une prochaine session). 2 points de détail non bloquants ajoutés au backlog non prioritaire (section 6b) : incohérence date "since 1989" vs "+30 ans", et URL Facebook `sameAs` à vérifier. |
| 2026-08-26 | Cowork | Session dédiée à la création de contenu vidéo/image pour la vidéo hero, avec un Soul Higgsfield "Alberto Deco/Papa" entraîné par Paolo en cours de route. Conseil de prompts et de choix de modèles (Nano Banana Pro/2, Kling 3.0, Soul 2.0) pour : régénération de l'avatar seul en tenue de travail, planche multi-angles, scène salon en cours de peinture (grand salon, fenêtres cohérentes avec la façade), équipe de 3 ouvriers + camionnette noire brandée, plans avant/après cuisine et salle de bain (démontage → rénové moderne), plan aérien maison + plan large maison rénovée. Nombreuses itérations sur les prompts vidéo suite à des rendus non satisfaisants (rotation caméra autour du personnage rejetée définitivement après le premier essai ; morphing indésirable entre deux scènes différentes constaté à plusieurs reprises avec l'usage de `start_image`/`end_image` sur Kling 3.0 — solution retenue : clips séparés + cut classique en montage plutôt que transition générée par l'IA). Paolo a monté lui-même la vidéo finale (15s, 16:9) dans CapCut. Intégration technique dans `index.html` : remplacement de l'ancien système d'images avant/après par une vraie balise vidéo pilotée par le scroll (`video.currentTime` lié à la position de scroll, sans autoplay), conformément au plan documenté dans le notebook NotebookLM "Web Design". Conversion du fichier source (.mov) en `hero-video.mp4` (H.264, faststart) + poster JPG via ffmpeg, testé visuellement avec Playwright (serveur local avec support des requêtes Range, car le Chromium de test ne décode pas le H.264 — comportement propre au bac à sable, sans impact sur les navigateurs réels). Fichiers commités sur `main` en local (`git commit` réussi) ; le `git push` doit être fait par Paolo depuis son propre Terminal (pas d'accès aux identifiants Git depuis cet environnement). |
