# Guide d'installation — PocketBase sur EasyPanel (Alberto Deco)

> Recrée le guide mentionné dans `A_FAIRE_PAOLO_AVANT_IMPLEMENTATION.md` et `V1_SPECIFICATIONS.md` (T1-T2), perdu car jamais commité (créé en session Cowork le 30/08/2026). Correspond à la tâche T1 de `V1_SPECIFICATIONS.md`.
>
> **Fait par :** Paolo, directement via l'interface EasyPanel (pas besoin d'accès SSH — voir alternative C1 dans `V1_SPECIFICATIONS.md`).

---

## Pourquoi PocketBase

Backend du formulaire de contact du site Alberto Deco : reçoit les soumissions (nom, email, message, photos), les stocke, et déclenche le workflow n8n (notification Telegram → validation Alberto → email client). Choisi pour la contrainte "100% gratuit / open source" (voir `PROJECT_STATUS.md` §12) — auto-hébergé sur le VPS EasyPanel qui fait déjà tourner n8n.

---

## Étape 1 — Se connecter à EasyPanel

Ouvre l'interface EasyPanel de ton VPS (celle où tourne déjà n8n). Note l'IP ou le domaine du VPS, tu en auras besoin à l'étape 4.

## Étape 2 — Créer le service PocketBase

Dans EasyPanel : **Create Service → App** (ou "Docker Image" selon la version de l'UI).
- **Nom du service** : `pocketbase` (ou `alberto-deco-pocketbase` si tu veux le distinguer d'autres projets sur le même VPS)
- **Image Docker** : `ghcr.io/muchobien/pocketbase:latest` (image communautaire la plus maintenue) — alternative : builder toi-même l'image officielle depuis `github.com/pocketbase/pocketbase`, mais l'image communautaire suffit pour du V1
- **Port interne** : `8090` (port par défaut de PocketBase)

## Étape 3 — Volume persistant

**Obligatoire** — sans ça, toutes les données (soumissions, admin, schéma) disparaissent au redéploiement du conteneur.
- Ajoute un volume monté sur `/pb_data`
- Nom du volume : `pocketbase_data` (ou équivalent selon la nomenclature EasyPanel)

## Étape 4 — DNS (sous-domaine)

Sur le panneau DNS de Wix (même principe que le A record déjà fait pour Vercel — voir `V1_SPECIFICATIONS.md` C10) :
- Ajoute un enregistrement **A** : `pocketbase` → IP du VPS EasyPanel
- Résultat visé : `pocketbase.alberto-deco.com`
- Propagation DNS : quelques minutes à quelques heures, teste avec `dig pocketbase.alberto-deco.com` ou simplement en ouvrant l'URL dans le navigateur

## Étape 5 — Domaine + SSL dans EasyPanel

Dans la config du service `pocketbase` : onglet **Domains** → ajouter `pocketbase.alberto-deco.com`. EasyPanel génère automatiquement le certificat SSL (Let's Encrypt) une fois le DNS propagé.

## Étape 6 — Déployer

Lance le déploiement du service. Vérifie que le conteneur démarre sans erreur (logs EasyPanel).

## Étape 7 — Premier accès et création du compte admin

Va sur `https://pocketbase.alberto-deco.com/_/` — PocketBase affiche un écran de création du **premier compte admin** (email + mot de passe).

⚠️ Voir la recommandation ci-dessous sur **quel email utiliser** — c'est la question posée, réponse détaillée hors de ce guide, dans la conversation.

## Étape 8 — Créer la collection `formulaires`

Dans l'admin UI PocketBase : **Collections → New collection** → nom `formulaires`, type `Base`.

Champs à créer (modèle complet, `V1_SPECIFICATIONS.md` §4) :

| Champ | Type PocketBase | Requis | Notes |
|---|---|---|---|
| `nom` | Text | ✓ | |
| `email` | Email | ✓ | |
| `phone` | Text | – | |
| `service` | Text | – | |
| `message` | Text (long) | ✓ | |
| `statut` | Select | ✓ | options : `nouveau`, `en cours`, `répondu`, `résolu` |
| `date` | Date | ✓ | auto via `created` si tu préfères utiliser le champ système plutôt qu'un champ custom |
| `photos` | File (multiple) | – | autoriser plusieurs fichiers, limiter le poids max (ex. 5 Mo/fichier) |
| `reponse_ia_brouillon` | Text (long) | – | |
| `reponse_finale` | Text (long) | – | |
| `valide_par_alberto` | Bool | – | défaut `false` |

## Étape 9 — Règles d'API (sécurité — ne pas sauter)

Par défaut une collection `Base` n'autorise **rien** publiquement. Dans l'onglet **API Rules** de la collection `formulaires` :
- **Create (soumission publique du formulaire)** : règle vide (`""`, tout le monde peut créer) — c'est le comportement voulu, le site public doit pouvoir soumettre sans être connecté
- **List / View / Update / Delete** : laisser **verrouillé** (règle par défaut refusant tout sauf admin) — seul Alberto/Paolo via l'admin UI ou n8n (avec la clé admin) doit pouvoir lire/modifier les soumissions. Ne jamais mettre ces règles à vide, sinon n'importe qui peut lire les données de tous les clients.

## Étape 10 — Récupérer l'URL API

L'URL de base pour les intégrations futures est `https://pocketbase.alberto-deco.com`. Elle sera utilisée :
- Dans `contact-form.html` (T3, à créer/intégrer) pour poster les soumissions
- Dans le workflow n8n (`n8n-workflow-pocketbase.json`, à recréer) pour lire les nouvelles entrées et déclencher les notifications Telegram

---

## Checklist de validation (fin de T1)

- [ ] `https://pocketbase.alberto-deco.com/_/` accessible avec certificat SSL valide
- [ ] Compte admin créé et fonctionnel
- [ ] Collection `formulaires` créée avec tous les champs de l'étape 8
- [ ] Règle "Create" ouverte, règles "List/View/Update/Delete" verrouillées (étape 9)
- [ ] Volume persistant confirmé (redémarrer le conteneur et vérifier que les données restent)

Une fois coché : T1 est terminé, tu peux passer à T2 (déjà couvert par ce guide, étape 8) puis T3 (intégration au site).
