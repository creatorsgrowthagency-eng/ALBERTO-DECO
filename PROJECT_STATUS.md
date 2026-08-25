# PROJECT STATUS — Alberto Deco (site vitrine)

> Source de vérité unique du projet. Chaque session (Cowork, Claude Code local, VS Code) doit LIRE ce fichier au démarrage et le METTRE À JOUR à la fin.

**Dernière mise à jour :** 2026-08-25 — session Cowork (mise en ligne domaine + maquette)
**Statut global :** 🟡 En cours — Domaine récupéré et maquette HTML mise en ligne sur alberto-deco.com ; développement du site final (Next.js/Tailwind) pas commencé

---

## 1. Objectif du projet

Site vitrine bilingue (FR/EN) one-page pour Alberto Deco (rénovation/peinture, Brabant wallon, Belgique).
- **V1** : site vitrine + hero vidéo motion + formulaire contact + booking + WhatsApp + chatbot + SEO
- **V2** : devis IA, portail client, CRM, agent IA photo→visuel→devis

## 2. Stack technique décidée

- Next.js + Tailwind CSS (base : ixartz/Next-JS-Landing-Page-Starter-Template, pas encore appliqué)
- Déploiement : Vercel
- Code source : GitHub (repo `creatorsgrowthagency-eng/ALBERTO-DECO`), dossier local `~/Documents/CLAUDE LOCAL/ALBERTO DECO`
- Domaine : `alberto-deco.com`, acheté et actif chez Wix jusqu'au 08/09/2027, DNS géré depuis Wix (pas de transfert de registrar effectué — solution la plus simple et gratuite)
- MCP connectés : Higgsfield (génération image/vidéo), Vercel (déploiement), 21st.dev Magic (composants UI), Intégration GitHub (à vérifier/activer selon la session)
- Skill installé : OSideMedia/higgsfield-ai-prompt-skill (prompts Kling 3.0)

## 3. Budget crédits Higgsfield

Plafond fixé : 97 crédits pour tout le site. Dépense estimée à date : images (~30-40cr) + storyboards (2cr) + 7 clips vidéo prévus (~48.5cr).

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

## 5. En cours 🟡

- Génération des 7 clips vidéo Kling 3.0 (à faire par Paolo dans l'UI Higgsfield)
- Montage final (wipes + logo/slogan overlay)
- Vercel recommande une migration du CNAME `www` vers une nouvelle valeur (`...vercel-dns-017.com`) — non urgent, l'ancien CNAME continue de fonctionner

## 6. À faire 🔜 (ordre)

1. Générer les 7 clips vidéo + monter la vidéo hero finale
2. Coder le site Next.js/Tailwind, intégrer le hero vidéo (scroll-driven) — **remplacera la maquette HTML actuellement en ligne**
3. Copy FR/EN définitive (texte du site) — **manquant, à fournir par Paolo**
4. Logo vectoriel propre — fichiers logo présents dans le dossier local (`logo-alberto-deco-*.png/svg`), à valider
5. Infos légales/entreprise pour footer — **manquant**
6. ~~Statut domaine alberto-deco.com (transfert ?)~~ — **résolu, voir section 4**
7. Ajouter les fonctionnalités (voir section 8)
8. Redéployer la version finale sur Vercel (le lien domaine/DNS restera identique, aucune reconfiguration nécessaire)
9. Stratégie SEO / visibilité LLM à mettre en place : title/meta description par page, structure H1/H2, alt text images, sitemap.xml + robots.txt, données structurées (schema.org), fichier `llms.txt`
10. Optimisation performance (compression images, lazy loading) une fois le contenu final ajouté
11. Vérifier/activer le connecteur MCP GitHub pour cette session si besoin d'accès direct en lecture/écriture au repo

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

## 8. Ressources gratuites à intégrer (fonctionnalités, pas encore fait)

- Formulaire contact → Next.js + Resend
- Booking → Cal.com (embed + sync Google Calendar)
- WhatsApp click-to-chat → lien `wa.me`
- Chatbot IA → github.com/Open-Chat-Widget/openchatwidget
- SEO/GEO (visibilité LLM) → fichier `llms.txt` + schema.org

## 9. En attente de décision / brainstorm

- Agent IA "photo + devis" (V2) — pas de plan technique, outil de génération visuelle à redéfinir (pas de resource GitHub retenue à ce jour)

## 10. Autres projets (hors scope Alberto Deco)

- rediumvex/ai-video-generator-claude (skills prompts Seedance) — à installer plus tard pour un autre projet

## 11. Journal des sessions

| Date | Session | Résumé |
|---|---|---|
| 2026-08-25 | Cowork | Recherche prompting vidéo, storyboards, plan vidéo final, setup GitHub/repo/Project, connexion MCP Vercel + 21st.dev, création de ce fichier |
| 2026-08-25 | Cowork | Clarification statut domaine (toujours actif chez Wix, pas de rachat nécessaire). Renommage `albertodecomockup.html` → `index.html`, suppression bandeau maquette, déploiement de la maquette sur Vercel (projet `alberto-deco`), configuration DNS Wix → Vercel (A + CNAME), rattachement du domaine au projet Vercel et génération SSL. Site vérifié en ligne sur alberto-deco.com. Fusion de ce fichier avec une version dupliquée créée par erreur lors d'une session précédente. |
