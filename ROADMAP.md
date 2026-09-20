# ROADMAP — Système de gestion Alberto Deco (V2 à V5)

> Compagnon de `PROJECT_STATUS.md` (section 12). Ce fichier documente le scope complet exprimé par Paolo le 30/08/2026, volontairement **repoussé hors V1** pour ne pas transformer le lancement en un chantier de plusieurs mois. Chaque phase sera reprise avec le même processus que V1 : Phase 0b (minimiser le scope de la phase) → Phase 2-3 (spécifier + rechercher des solutions open source/no-code) → Phase 4 (implémenter) → Phase 5 (audit).

**Statut :** 📋 Documenté, non commencé. À activer phase par phase une fois V1 stable et en usage réel (voir `PROJECT_STATUS.md` section 12.5).

**Principe directeur (rappelé par Paolo) :** pour chaque phase, chercher d'abord des solutions open source / gratuites / no-code (GitHub, Composio, etc.) avant d'envisager du développement sur-mesure — la recherche se fait une fois la phase suivante spécifiée, pas avant.

---

## Vue d'ensemble du cycle de vie d'un chantier

```
CONTACT (V1) → DEVIS → ACCEPTATION + ACOMPTE (V2)
   → ACHAT MATÉRIEL (V3) → PLANNING OUVRIERS (V4)
   → SUIVI CHANTIER (photos, avancement) (V5) → CLÔTURE
```

À chaque étape, la donnée reste liée à un **client** et un **projet/chantier** — l'objectif à terme est une mémoire consistante par client/projet qui accompagne Alberto sur toute la durée du chantier (pas seulement au moment du devis).

---

## V2 — Devis, acceptation et suivi financier

**Objectif :** transformer un contact validé en devis, puis suivre son cycle de vie jusqu'au paiement de l'acompte.

- Génération de devis à partir de templates (à créer avec Alberto — plusieurs modèles selon type de chantier)
- Flux de révision : premier devis → visite/retour terrain d'Alberto → compte-rendu (texte ou vocal) → devis final ajusté par le système → validation par Alberto avant envoi au client
- Statut du devis trackable (envoyé / accepté / refusé)
- Une fois le devis **accepté** : Alberto doit pouvoir marquer/déclencher "acompte reçu" dans l'interface
- Suivi financier basique : Alberto demande généralement **50% d'acompte** pour démarrer un chantier — le système doit suivre réception du premier versement (50%) et du solde
- L'événement "acompte reçu" est le déclencheur qui ouvre la Phase V3 (achat matériel)

**À rechercher (solutions open source/no-code) :** génération de devis PDF avec templates (ex. via n8n + un générateur de documents), suivi de statut simple (Airtable/PocketBase), pas de vraie comptabilité — juste un suivi de statut, pas un outil de facturation légale (à clarifier avec Paolo si un outil de facturation belge est nécessaire séparément).

---

## V3 — Achat matériel et stock

**Objectif :** dès qu'un acompte est reçu (déclencheur venant de V2), générer automatiquement une proposition de liste de matériel nécessaire pour le chantier, à valider par Alberto.

- Message/liste générée automatiquement avec le matériel estimé nécessaire pour le chantier accepté
- Alberto valide/ajuste la liste avant achat
- **Pas de vue en temps réel sur le stock du fournisseur d'Alberto Deco au démarrage** (contrainte confirmée par Paolo — pas d'API/accès direct connu)
- Constitution progressive d'un **stock digital** : au fur et à mesure des achats, on enregistre ce qui est acheté → on obtient avec le temps une vue réelle (approximative) du stock d'Alberto Deco
- Lien avec la base de connaissances matériaux (catalogue fournisseur, si scrapé — voir note V1 sur l'estimation de prix/recommandations, actuellement hors scope V1)

**À rechercher :** pas de solution "stock" toute faite tant qu'il n'y a pas d'accès fournisseur — probablement une simple base de données (PocketBase/Airtable) alimentée manuellement au début, semi-automatisée ensuite.

---

## V4 — Planning et gestion des ouvriers

**Objectif :** une fois le matériel validé, organiser l'équipe pour le chantier.

- Base de données des ouvriers : qui fait quoi, qui est plus performant sur quelle tâche (donnée qui se construit avec le temps, notamment via les données de durée de tâche captées en V5)
- Estimation automatique (ou semi-automatique, via un agent) du nombre de personnes et du temps nécessaire pour le chantier
- Envoi d'un brief de disponibilité aux ouvriers concernés ("es-tu dispo à telle date ?")
- Une fois les ouvriers confirmés dispo : envoi du brief complet de travail (tâches à faire, où aller chercher le matériel, etc.)

**À rechercher :** outil de planning/dispo simple avec notifications (WhatsApp/Telegram déjà en place pour Alberto — possiblement réutilisable pour les ouvriers), pas de solution RH complexe.

---

## V5 — Suivi de chantier (photos, avancement, post-mortem)

**Objectif :** donner à Alberto une visibilité à distance sur l'avancement du chantier, et constituer une mémoire d'entreprise utile pour l'avenir.

- Les ouvriers envoient des photos d'avancement pendant le chantier (canal à définir — probablement WhatsApp/Telegram, cohérent avec le reste du système)
- Alberto peut suivre l'évolution du chantier à distance via ces photos
- Usages multiples des photos :
  - Contenu réseaux sociaux (avant/après, storytelling chantier)
  - Contrôle d'avancement des travaux
  - **Données de performance** : combien de temps chaque ouvrier prend sur chaque type de tâche → alimente en retour la base de connaissances utilisée en V4 (meilleure estimation du temps/nombre de personnes nécessaires pour les futurs chantiers) et potentiellement l'estimation de prix (V1/V2 — actuellement hors scope, basée sur les prix du marché en attendant)

**À rechercher :** stockage photo (déjà Supabase en place pour l'archivage), pas de solution "vision" avancée nécessaire pour V5 — la valeur est surtout dans la capture structurée (quelle tâche, quel ouvrier, quelle date) plus que dans l'analyse d'image elle-même.

---

## Notes transverses (toutes phases V2-V5)

- **Estimation de prix automatique** (mentionnée en V1 comme hors scope) : nécessite une recherche sur les prix du marché belge (peinture/rénovation) + une variable de coût de déplacement/essence selon la région du chantier (Wallonie/Bruxelles/Flandre) + variable régionale. Actuellement, on prévoit de démarrer avec des tests basés sur les prix constatés du marché, pas une vraie modélisation.
- **Recommandations matériaux/couleurs** : doivent être strictement limitées à ce qui est disponible chez le(s) fournisseur(s) d'Alberto Deco. Nécessite un scraping du catalogue fournisseur (papier → captures d'écran → extraction, ou catalogue en ligne → scraping direct) pour constituer une base de connaissances "matériaux disponibles".
- **Mémoire par client/projet** : à terme, chaque client et chaque projet doit avoir un historique consultable qui suit tout le cycle (premier contact → devis → révisions → acceptation → chantier → clôture), pas des silos déconnectés par phase.

---

## Comment activer une phase

1. Relire cette section avec Paolo, confirmer que V1 (ou la phase précédente) est stable et en usage réel
2. Lancer une session **Phase 0b (Elon Musk, mode audit)** sur le scope de la phase concernée, en s'appuyant sur les retours réels d'usage de la phase précédente
3. Geler le scope minimal de la phase (comme fait pour V1 dans `PROJECT_STATUS.md` section 12.2)
4. Rechercher les solutions open source/no-code disponibles pour ce scope gelé
5. Spécifier (Phase 2-3, Spec Kit) puis implémenter (Phase 4)
6. Mettre à jour ce fichier et `PROJECT_STATUS.md` avec le résultat
