# À FAIRE / À AVOIR — Paolo, avant de lancer l'implémentation V1 (Alberto Deco)

> Ce fichier est autonome : tu peux l'ouvrir dans une nouvelle conversation Claude (Cowork, Claude Code, etc.) sans avoir besoin du reste de l'historique. Objectif : réunir tout ce qu'il faut pour lancer l'implémentation automatisée du système de contact/devis/chatbot d'Alberto Deco (V1), en local sur VS Code avec plusieurs agents.
>
> Fichiers de référence dans le dossier `ALBERTO DECO` (à donner à la nouvelle conversation si besoin) : `PROJECT_STATUS.md` (état global du projet), `V1_SPECIFICATIONS.md` (spec technique détaillée + task list T1-T15), `ROADMAP.md` (V2-V5, pour plus tard), `KB_WORKSHOP_QUESTIONNAIRE.md` (atelier base de connaissances).

**Dernière mise à jour :** 2026-08-30

---

## 1. Comptes et accès à créer/réunir

Coche au fur et à mesure. Pour chaque ligne : ce qu'il faut faire, et ce qu'il faut transmettre à la conversation qui implémentera.

- [ ] **VPS (easyPanel)** — déjà existant, rien à créer. Réunir : adresse SSH (IP ou domaine), port SSH, nom d'utilisateur, mot de passe **ou** clé privée SSH. *(Alternative si tu préfères ne pas partager l'accès SSH directement : tu peux faire toi-même l'installation de PocketBase en suivant `POCKETBASE_SETUP_GUIDE.md`, étape par étape, et dire ensuite "c'est fait".)*

- [ ] **n8n** — déjà en place, rien à créer. Réunir : URL de ton instance n8n + une clé API (dans n8n : Settings → API → "Create an API Key").

- [ ] **Telegram** — à créer, 2 minutes. Dans l'app Telegram, chercher `@BotFather`, envoyer `/newbot`, choisir un nom et un username pour le bot. Réunir : le token donné par BotFather (ressemble à `123456789:ABCdefGhIJKlmNoPQRsTUVwxyZ`).

- [ ] **SendGrid** — à créer, compte gratuit sur sendgrid.com (100 emails/jour gratuits à vie). Configurer l'authentification du domaine `alberto-deco.com` (SendGrid donne des enregistrements DNS à ajouter dans le panneau DNS Wix — même principe que ce qui a déjà été fait pour Vercel). Réunir : la clé API SendGrid (Settings → API Keys → Create API Key) + confirmation que le domaine est vérifié. *(Cette étape peut prendre quelques heures à se propager — à lancer en premier si possible.)*

- [ ] **Supabase** — à créer, projet gratuit sur supabase.com. Réunir : l'URL du projet + les clés API (`anon` et `service_role`, visibles dans Project Settings → API).

- [ ] **Open Router** — déjà en place. Juste confirmer que la clé API existante fonctionne toujours.

- [ ] **PocketBase** — rien à faire avant l'installation. Décider d'un email/mot de passe admin (ou laisser la conversation d'implémentation en générer un et te le communiquer une seule fois).

- [ ] **Cal.com** — à créer, compte gratuit sur cal.com au nom d'Alberto Deco. Configurer un "event type" simple (ex. "Visite chantier / Devis", 1h). Réunir : le lien public de l'event type (ex. `cal.com/alberto-deco/visite`).

- [ ] **GitHub** — normalement déjà en place (repo `creatorsgrowthagency-eng/ALBERTO-DECO`, accès local via `~/Documents/CLAUDE LOCAL/ALBERTO DECO`). Juste confirmer que push/pull fonctionne toujours.

- [ ] **DNS Wix** — à prévoir un sous-domaine pour PocketBase, ex. `pocketbase.alberto-deco.com` (détaillé dans `POCKETBASE_SETUP_GUIDE.md` étape 4). Peut se faire au moment de l'implémentation, pas besoin de le préparer à l'avance.

- [ ] **Contact Telegram d'Alberto** — rien à préparer à l'avance : le chat ID d'Alberto s'obtient automatiquement dès qu'il envoie un premier message au bot créé ci-dessus. Prévoir juste qu'Alberto installe Telegram sur son téléphone et envoie ce premier message le moment venu.

---

## 2. Comment transmettre les identifiants sensibles

Ne colle pas les mots de passe/clés API en clair dans une conversation si tu préfères éviter. Options :
- Les ajouter toi-même dans un fichier `.env` local (dans le dossier du projet) que tu ne partages qu'en local, jamais collé dans le chat
- Les transmettre un par un, seulement au moment où l'étape correspondante en a besoin, plutôt que tout regrouper à l'avance

---

## 3. Ce que tu n'as PAS besoin de faire pour le V1

Pour éviter de perdre du temps sur des choses hors scope :
- ❌ Pas besoin de compte Meta Business / WhatsApp Business API (le V1 utilise uniquement Telegram comme canal interne avec toi — le client, lui, reçoit un email, jamais de WhatsApp/Telegram)
- ❌ Pas besoin d'accès à l'inventaire/stock du fournisseur (l'estimation de prix et les recommandations matériaux sont repoussées en V2+, voir `ROADMAP.md`)
- ❌ Pas besoin de créer une landing page dédiée réseaux sociaux (repoussé en V2+)

---

## 4. Minimum pour démarrer tout de suite

Si tu veux que l'implémentation démarre avant d'avoir tout réuni, le strict minimum est : **VPS (accès SSH ou toi-même en train de suivre le guide)** + **Telegram (token BotFather)** + **Open Router (confirmation)**. Le reste (SendGrid, Supabase, Cal.com) peut être préparé en parallèle pendant que le reste de l'implémentation avance.

---

## 5. Une fois tout réuni

Donne ce fichier (ou dis simplement "j'ai tout réuni, voici mes accès") dans la nouvelle conversation, avec accès au dossier `ALBERTO DECO`. La conversation pourra alors construire le plan d'exécution détaillé (quel agent VS Code fait quelle tâche parmi T1-T15 de `V1_SPECIFICATIONS.md`, dans quel ordre, quelles dépendances) et lancer l'implémentation.
