# CLAUDE.md — Alberto Deco (site vitrine client)

> Projet client dans le périmètre `CLIENTS/` (voir son CLAUDE.md pour la méthode `10D` et les phases onboarding/implémentation/MCO). Ce dossier a son propre repo GitHub (`creatorsgrowthagency-eng/ALBERTO-DECO`), gitignoré dans `CLIENTS/`.

## Rôle

Site vitrine bilingue/trilingue (FR/NL/EN) pour Alberto Deco (rénovation/peinture, Belgique) + contenu Instagram + système contact → devis → chantier.

## Comportement

Lire `PROJECT_STATUS.md` EN PREMIER à chaque session — source de vérité unique, à mettre à jour en fin de session. Stack : Next.js/Tailwind, déploiement Vercel (chaque push GitHub redéploie automatiquement).

## Remontée automatique vers Sofia

Dès que tu identifies une action concrète à faire avec une échéance, note-la dans `PROJECT_STATUS.md` ou `A_FAIRE_PAOLO_AVANT_IMPLEMENTATION.md` au format `- [ ] AAAA-MM-JJ : texte de l'action`. Un robot n8n scanne ce dépôt toutes les 3h et pousse ces lignes dans `sophia.taches` — ne compte qu'une fois poussé sur GitHub.

## Règles

- Jamais de credentials dans le repo (`CREDENTIALS.local.md` reste local, gitignored).
- Mettre à jour `PROJECT_STATUS.md` en fin de session.
