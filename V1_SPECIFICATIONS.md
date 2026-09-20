# SPÉCIFICATIONS V1 — Système Contact/Devis + Notification + Chatbot (Alberto Deco)

> Produit du workflow DEVLP CODE, Phase 2-3 (Spec Kit) — s'appuie sur le scope gelé dans `PROJECT_STATUS.md` section 12.2 et la roadmap `ROADMAP.md`. Une fois ce document validé ("tasks are ready"), on transitionne vers Phase 4 (Implémentation).

**Statut :** 🟡 Draft — en attente de validation Paolo
**Dernière mise à jour :** 2026-08-30

---

## 1. Objectif V1 (rappel)

Permettre à un visiteur du site de contacter Alberto Deco ou demander un devis (avec ou sans photos) via un formulaire unique, avec une réponse générée par IA mais **toujours validée par Alberto avant envoi**, plus un chatbot basique sur le site connecté à une base de connaissances (KB) initiale. Rien d'automatique n'est envoyé au client sans passage par Alberto.

**Hors scope V1** (voir `ROADMAP.md`) : estimation de prix automatique, recommandations matériaux basées sur stock fournisseur, landing page dédiée réseaux sociaux, tout le système de gestion de chantier post-devis (V2-V5).

---

## 2. Requirements fonctionnels

### R1 — Formulaire unique
- Un seul formulaire, accessible via bouton "Contacter / Demander un devis" sur le site
- Champs : nom, email, téléphone (optionnel), service souhaité, message, upload photo(s) (optionnel, 0 à N photos)
- Pas de branche UI différente selon présence/absence de photo — la différence est traitée côté backend/notification (voir R3)
- Soumission → enregistrement dans PocketBase (collection `formulaires`, déjà spécifiée dans `POCKETBASE_SETUP_GUIDE.md`) + champ photos à ajouter au schéma (voir T2)

### R2 — Génération de réponse IA (brouillon, jamais envoyé directement)
- À chaque nouvelle soumission, n8n déclenche Open Router pour générer une proposition de réponse email, personnalisée avec le contenu du message
- Cette réponse est un **brouillon**, jamais envoyée sans validation Alberto

### R3 — Notification à Alberto (courte, pas de pavé de texte)
- **Décision (30/08/2026) : Telegram uniquement pour le V1** — canal interne à Alberto (le client, lui, ne reçoit jamais de WhatsApp/Telegram, uniquement l'email final, voir R5). WhatsApp Cloud API reste une option pour V2+ si besoin, mais retiré du scope V1 (élimine la vérification Meta Business, non nécessaire pour un canal purement interne)
- Notification Telegram envoyée à Alberto dès réception d'une soumission : format court, ex. "📬 Nouveau message de [nom] — réponds ici pour voir les détails"
- Si le message contient des photos, le préciser dans la notification (signal qu'une estimation/recommandation est demandée, même si le traitement de l'estimation elle-même est V2+)

### R4 — Flux de consultation/validation par Alberto (question par question)
- Alberto répond à la notification (ex. "ok") pour déclencher la suite
- Le système présente ensuite l'information **de façon séquentielle** (pas un pavé unique) : nom/contact du client, puis le message, puis la proposition de réponse IA
- Alberto peut répondre **par écrit ou en vocal** à chaque étape pour adapter la réponse proposée
- Un **lien vers l'agenda Cal.com d'Alberto** est systématiquement inclus si la réponse implique une date/rendez-vous, pour qu'il puisse vérifier sa disponibilité en répondant
- Une fois la réponse finalisée par Alberto → il valide explicitement l'envoi (ex. répond "envoie" ou équivalent)

### R5 — Envoi de la réponse
- Une fois validée, la réponse (email) est envoyée au client via SendGrid
- Une copie de l'échange est archivée dans Supabase (y compris photos, pour préparation V2+)

### R6 — Chatbot sur le site
- Chatbot basique intégré au site, connecté à la base de connaissances (KB) initiale construite avec Alberto (voir `KB_WORKSHOP_QUESTIONNAIRE.md`)
- Répond aux questions fréquentes des visiteurs (services, zone géographique, délais, etc.) sans intervention humaine — car ce ne sont pas des réponses personnalisées à un client identifié, contrairement au flux email (R2-R5)

### R7 — Base de connaissances (KB) initiale
- Construite à partir du transcript de l'atelier avec Alberto (`KB_WORKSHOP_QUESTIONNAIRE.md`)
- Utilisée à la fois par le chatbot (R6) et par le prompt de génération de réponse email (R2), pour que les deux soient cohérents avec les infos réelles de l'entreprise

---

## 3. Architecture technique (stack confirmée)

| Composant | Outil | Statut |
|---|---|---|
| Backend formulaire | PocketBase (auto-hébergé, VPS easyPanel) | Guide prêt (`POCKETBASE_SETUP_GUIDE.md`), à installer |
| Automatisation / orchestration | n8n (déjà sur le VPS) | Workflow de base prêt (`n8n-workflow-pocketbase.json`), à adapter pour R3/R4 |
| Génération réponse IA | Open Router (déjà en place) | Prompt à ajuster avec la KB (R7) |
| Notification + validation Alberto | Telegram Bot API | **Décidé pour V1** — canal interne uniquement, gratuit, gère nativement les vocaux (voir 5.2). WhatsApp Cloud API reste possible en V2+ si besoin d'un canal supplémentaire, mais pas nécessaire pour V1 |
| Transcription vocale | faster-whisper (self-hébergé sur le VPS) | **Décidé** — conteneur Docker séparé, API compatible OpenAI (voir 5.3) |
| Envoi email | SendGrid | OK, déjà dans le workflow de base |
| Agenda | Cal.com | **Non encore intégré** — compte à créer, lien direct suffit pour V1 (voir 5.4) |
| Archivage | Supabase | OK, déjà dans le workflow de base |
| Chatbot site | Mini-RAG maison (widget HTML/JS → webhook n8n → recherche KB → Open Router) | **Décidé** — pas de dépendance à un widget tiers peu maintenu (voir 5.5) |

---

## 4. Modèle de données (PocketBase — collection `formulaires`)

Schéma actuel (`POCKETBASE_SETUP_GUIDE.md`) + ajouts nécessaires pour V1 :

| Champ | Type | Requis | Notes |
|---|---|---|---|
| nom | Text | ✓ | existant |
| email | Email | ✓ | existant |
| phone | Text | – | existant |
| service | Text | – | existant |
| message | Text (textarea) | ✓ | existant |
| statut | Select (nouveau / en cours / répondu / résolu) | ✓ | existant, valeurs à confirmer avec le flux de validation R4 |
| date | DateTime | ✓ | existant |
| **photos** | File (multiple) | – | **à ajouter** — nécessaire pour R1/R3 |
| **reponse_ia_brouillon** | Text | – | **à ajouter** — stocke la proposition générée par Open Router (R2) |
| **reponse_finale** | Text | – | **à ajouter** — stocke la version validée par Alberto avant envoi (R4/R5) |
| **valide_par_alberto** | Bool | – | **à ajouter** — passe à `true` une fois qu'Alberto a validé l'envoi |

---

## 5. Questions techniques — RÉSOLUES (recherche effectuée le 30/08/2026)

### 5.1 WhatsApp — reporté à V2+ (non nécessaire pour V1)
Recherche faite (API officielle Meta Cloud API : conversations "service" gratuites et illimitées depuis nov. 2024, node natif n8n) mais **le design V1 ne prévoit aucune communication WhatsApp/Telegram avec le client** — le client reçoit uniquement un email (R5). WhatsApp n'a donc d'utilité que si on veut un second canal interne pour Alberto en plus de Telegram, ce qui n'est pas nécessaire pour V1. À reconsidérer en V2+ si Alberto préfère finalement WhatsApp à Telegram à l'usage.

### 5.2 Notification/validation Alberto — DÉCISION : Telegram (seul canal V1)
Le node Telegram natif de n8n gère nativement les messages vocaux (récupère le fichier `.ogg` via `file_id` → "Get File"). Simple à mettre en place : pas de vérification Business Manager, gratuit, configuration en quelques minutes (token BotFather, voir checklist section 8). Un template n8n officiel existe déjà pour "transcrire les vocaux Telegram avec Whisper".
(T7 — à confirmer avec Alberto qu'il est ok d'installer Telegram sur son téléphone, même si c'est juste pour cet usage interne.)

### 5.3 Transcription vocale — DÉCISION : faster-whisper self-hébergé sur le VPS
Open Router propose une API de transcription Whisper mais elle est payante à l'usage (contraire à la contrainte "100% gratuit"). Solution retenue : héberger **faster-whisper** dans un conteneur Docker séparé sur le même VPS easyPanel que n8n, exposé en API compatible OpenAI (`/v1/audio/transcriptions`). Intégration n8n : un simple node HTTP Request. Gratuit et illimité.
**À faire (T5) :** installer faster-whisper sur le VPS (conteneur dédié), tester avec un message vocal réel.

### 5.4 Cal.com
Confirmer le compte Cal.com d'Alberto (à créer s'il n'existe pas), et la méthode d'intégration (lien direct suffit pour V1 — pas besoin d'embed complexe). **À faire (T8).**

### 5.5 Chatbot + KB — DÉCISION : mini-RAG maison (n8n) + widget front `@n8n/chat`
Backend : un webhook n8n → recherche dans la KB stockée en PocketBase/Supabase → Open Router → réponse. Réutilise entièrement l'infra déjà en place. `Open-Chat-Widget/openchatwidget` écarté (maintenance incertaine, pas de RAG clé en main de toute façon).

Front-end (interface visuelle du chat) — comparaison faite le 30/08/2026 selon 3 critères (rapidité, faible coût en tokens LLM pour le construire, qualité visuelle) :
- **`@n8n/chat`** (package npm officiel de l'équipe n8n) : conçu spécifiquement pour se connecter à un webhook n8n (nœud "Chat Trigger"). Intégration en ~10-15 lignes JS, **compatible nativement avec le site HTML/CSS/JS vanilla actuel** (pas besoin de React/build tool). Design par défaut correct mais générique — se personnalise entièrement via variables CSS (couleurs, rayons, typographie) sans toucher au JS, donc peu de tokens nécessaires pour l'habiller à la charte Alberto Deco (bleu marine #1e3a5f, Fraunces/Work Sans, glass morphism). Un outil complémentaire, n8nchatui.com, permet même de générer le thème visuellement sans coder.
- **21st.dev** (marketplace de composants "AI Chat", ex. "Floating Chat Widget") : rendu visuel plus premium out-of-the-box, mais 100% React/Tailwind — nécessiterait un bundler React isolé sur le site vanilla actuel (complexité + temps + tokens en hausse, contraire aux contraintes).
- Magic UI : pas de composant chat/widget disponible dans sa bibliothèque — écarté.

**Décision retenue pour V1 : `@n8n/chat`**, personnalisé en CSS pour matcher la charte Alberto Deco. **Prévu pour re-évaluation au moment de la migration Next.js/Tailwind** (voir `PROJECT_STATUS.md` section 6, tâche 2) : à ce moment, un composant 21st.dev pourra remplacer uniquement l'UI (le backend n8n reste inchangé) pour un rendu encore plus premium, le coût d'intégration React devenant nul puisque le site sera déjà en React.
**À faire (T12) :** construire ce mini-RAG (backend) une fois la KB structurée (T10), puis intégrer et personnaliser `@n8n/chat` (front).

---

## 6. Task list V1 (Phase 4 — implémentation)

| # | Tâche | Owner | Input | Output | Success condition |
|---|---|---|---|---|---|
| T1 | Installer PocketBase sur le VPS easyPanel | Paolo (avec guide Claude) | `POCKETBASE_SETUP_GUIDE.md` | Instance PocketBase accessible en ligne, admin configuré | Interface admin accessible, collection créée |
| T2 | Étendre le schéma `formulaires` (photos, reponse_ia_brouillon, reponse_finale, valide_par_alberto) | Paolo / Claude | Schéma actuel + section 4 de ce doc | Collection PocketBase mise à jour | Champs visibles et fonctionnels dans l'admin PocketBase |
| T3 | Intégrer `contact-form.html` au site (remplacer POCKETBASE_URL, ajouter upload photo) | Claude | `contact-form.html`, URL PocketBase réelle | Formulaire fonctionnel sur le site, avec upload photo | Soumission test crée un enregistrement avec photo dans PocketBase |
| T4 | Configurer le bot Telegram (BotFather) et le node n8n correspondant | Paolo (créer le bot), Claude (config n8n) | Token BotFather (checklist section 8) | Bot Telegram fonctionnel dans n8n | Envoi + réception d'un message test fonctionne |
| T5 | Rechercher et valider la solution de transcription vocale | Claude (recherche), Paolo (validation) | Question technique #2 (section 5) | Solution retenue documentée | Message vocal test transcrit correctement |
| T6 | Adapter `n8n-workflow-pocketbase.json` pour le flux complet (notification courte → attente réponse Alberto → présentation séquentielle → validation → envoi) | Claude | Workflow actuel + R2-R5 de ce doc | Nouveau workflow n8n fonctionnel | Test end-to-end : soumission → notification → validation Alberto → email reçu par client test |
| T7 | Confirmer avec Alberto qu'il installe Telegram sur son téléphone | Paolo | — | Confirmation d'Alberto | Alberto a Telegram installé et a envoyé un premier message au bot (pour récupérer son chat ID) |
| T8 | Créer/configurer le compte Cal.com d'Alberto et intégrer le lien dans le workflow n8n | Paolo (compte), Claude (intégration workflow) | Compte Cal.com | Lien agenda inclus dans chaque notification pertinente | Lien fonctionnel testé dans une notification réelle |
| T9 | Faire l'atelier KB avec Alberto Deco | Paolo | `KB_WORKSHOP_QUESTIONNAIRE.md` | Transcript de l'atelier | Transcript complet obtenu, couvrant les 8 thèmes du questionnaire |
| T10 | Structurer le transcript en KB utilisable | Claude | Transcript de T9 | KB structurée (fichier ou base) | KB validée par Paolo/Alberto comme fidèle à la réalité de l'entreprise |
| T11 | Connecter la KB au prompt Open Router (génération réponse email) | Claude | KB (T10) | Prompt n8n mis à jour | Réponses générées cohérentes avec les infos réelles de l'entreprise (test sur 3-5 cas) |
| T12 | Construire le mini-RAG (webhook n8n + KB) et intégrer/personnaliser `@n8n/chat` sur le site (charte Alberto Deco) | Claude | Décision section 5.5, KB (T10) | Chatbot fonctionnel et stylé sur le site | Chatbot répond correctement à 5 questions test tirées de la KB, rendu visuel conforme à la charte |
| T13 | Test de charge : soumissions simultanées | Claude / Paolo | Workflow complet (T6) | Rapport de test | 10 soumissions simultanées traitées sans erreur ni perte de donnée (assumption A3) |
| T14 | Test réel avec Alberto sur 5-10 messages | Paolo + Alberto | Workflow complet en prod | Retours d'Alberto | Alberto confirme pouvoir valider/répondre sans que ce soit une charge excessive (assumption A1) |
| T15 | Mise à jour finale de `PROJECT_STATUS.md` (V1 terminé, design docs) | Claude | Résultat de T1-T14 | Section 12 mise à jour, statut V1 passé à "terminé" | Documentation complète et à jour, prête pour Phase 5 (audit) |

---

## 7. Critère de sortie de cette phase

Selon le workflow DEVLP CODE (Scénario B, Phase 2-3) : *"Remaining task list is clear, owners assigned, no scope creep."* — cette liste ci-dessus répond à ce critère : 15 tâches, chacune avec owner/input/output/condition de succès, aucune tâche ne dépasse le scope V1 gelé (section 12.2 de `PROJECT_STATUS.md`).

**Signal pour avancer :** Paolo confirme "tasks are ready" / "je peux commencer à implémenter" → transition vers **Phase 4 : IMPLÉMENTER**.

---

## 8. Checklist de configuration requise (à préparer AVANT de lancer l'implémentation automatisée)

Paolo a choisi de tout préparer d'avance pour lancer l'implémentation en une fois avec plusieurs agents (VS Code / Claude Code). Voici exactement ce qu'il faut réunir, service par service. Rien ici ne nécessite de compétence technique poussée — chaque étape est indiquée avec son niveau de difficulté.

| # | Service | Ce qu'il faut faire | Ce qu'il faut me transmettre | Difficulté |
|---|---|---|---|---|
| C1 | **VPS (easyPanel)** | Rien à créer, juste récupérer l'accès existant | Adresse SSH (IP ou domaine), port SSH, nom d'utilisateur, mot de passe **ou** clé privée SSH. Alternative plus sûre : tu peux directement effectuer T1 (installation PocketBase) toi-même en suivant `POCKETBASE_SETUP_GUIDE.md` si tu préfères ne pas partager l'accès SSH | Facile (accès déjà existant) |
| C2 | **n8n** | Rien à créer (déjà en place) | URL de ton instance n8n + une clé API n8n (Settings → API dans n8n, "Create an API Key") pour que les agents puissent déployer/modifier les workflows automatiquement | Facile (2 min dans l'interface n8n) |
| C3 | **Telegram** | Créer un bot via l'app Telegram : chercher `@BotFather`, envoyer `/newbot`, suivre les instructions (nom + username du bot) | Le token que BotFather te donne (ressemble à `123456789:ABCdefGhIJKlmNoPQRsTUVwxyZ`) | Facile (2 min) |
| C4 | **SendGrid** | Créer un compte gratuit sur sendgrid.com (100 emails/jour gratuits à vie), configurer l'authentification du domaine `alberto-deco.com` (SendGrid te donne des enregistrements DNS à ajouter — tu les ajoutes dans le panneau DNS Wix, comme pour Vercel) | Clé API SendGrid (Settings → API Keys → Create API Key), + confirmation que le domaine est vérifié | Moyen (creation compte facile, la vérification DNS prend le même principe que ce qu'on a déjà fait pour Vercel) |
| C5 | **Supabase** | Créer un projet gratuit sur supabase.com | URL du projet + clé API (`anon` et `service_role`, visibles dans Project Settings → API) | Facile (2 min) |
| C6 | **Open Router** | Rien à créer (déjà en place) | Confirmer que la clé API existante fonctionne toujours (juste à me dire "oui c'est bon" ou me la retransmettre si tu as un doute) | Trivial |
| C7 | **PocketBase** | Rien à faire avant — les identifiants admin seront créés pendant l'installation (T1) | Décider d'un email/mot de passe admin PocketBase (ou je peux en générer un et te le communiquer une seule fois de façon sécurisée) | Trivial |
| C8 | **Cal.com** | Créer un compte gratuit sur cal.com au nom d'Alberto Deco (ou toi en attendant), configurer un "event type" simple (ex. "Visite chantier / Devis", 1h) | Le lien public de l'event type (ex. `cal.com/alberto-deco/visite`) | Facile (5-10 min) |
| C9 | **GitHub** | Rien à créer si le repo `creatorsgrowthagency-eng/ALBERTO-DECO` existe déjà et que tu y as accès en local | Confirmer que l'accès Git en local (`~/Documents/CLAUDE LOCAL/ALBERTO DECO`) fonctionne toujours pour push/pull | Trivial (déjà en place selon `PROJECT_STATUS.md`) |
| C10 | **DNS (Wix)** | Prévoir un sous-domaine pour PocketBase, ex. `pocketbase.alberto-deco.com` (comme indiqué dans `POCKETBASE_SETUP_GUIDE.md` étape 4) | Rien à transmettre — je peux te guider pour l'ajouter dans le panneau DNS Wix quand on y sera (même principe que le A record déjà fait pour Vercel) | Facile (déjà fait une fois pour Vercel) |
| C11 | **Numéro de contact Alberto** | Le chat ID Telegram d'Alberto s'obtient automatiquement dès qu'il envoie un premier message au bot créé en C3 (voir T7) | Rien à préparer à l'avance, ça se fait pendant T7 | Trivial |

**Pas indispensable pour lancer l'implémentation, mais à garder en tête :** C4 (SendGrid, vérification domaine) et C10 (DNS) prennent un peu de temps à se propager (jusqu'à quelques heures) — les lancer en premier si possible, pendant que le reste de l'implémentation avance en parallèle.

**Comment transmettre les identifiants sensibles (SSH, clés API) :** ne les colle pas directement dans ce chat si tu préfères éviter — dis-le-moi et on trouve un canal plus sûr (ex. tu les ajoutes toi-même dans un fichier `.env` local que je ne lis jamais en clair, ou tu me les donnes un par un au moment de l'étape qui en a besoin).

Une fois C1 à C11 réunis (ou au moins C1-C3-C6, le strict minimum pour démarrer T1-T6), je peux construire un plan d'exécution détaillé pour VS Code / Claude Code multi-agents (quel agent fait quelle tâche T1-T15, dans quel ordre, quelles dépendances entre tâches).
