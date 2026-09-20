# Base de connaissances Alberto Deco — DRAFT

> Construite à partir des transcripts d'atelier (`Papa1_ KB.txt`, `Papa2_KB.txt` — qualité audio dégradée, peu exploitables seuls) **complétés par les réponses directes de Paolo le 13/09/2026** (le plus fiable des deux sources). Statut : quasi complet, reste 2 points à valider avec Alberto (voir bas de fichier). Rien n'est inventé au-delà de ce qui a été dit.

---

## 1. Entreprise et identité

- **Date de création : 1989** (confirmé transcript, cohérent avec le logo "SINCE 1989" et "+30 ans d'expérience" du site — **incohérence du backlog `PROJECT_STATUS.md` section 6b résolue**, rien à changer sur le site).
- **Différenciation vs concurrence** : pas de différenciation "technique" particulière — Alberto est spécialisé en **peinture intérieure/extérieure**. Sa vraie force : **l'ancienneté** (37 ans d'activité), une clientèle historique satisfaite, et un service **très aux petits soins** — la satisfaction client est la priorité affichée.
- **Équipe** : pas d'équipe fixe nombreuse. Un **noyau fixe de ~3 personnes**, complété par de la **sous-traitance selon le chantier** (l'équipe varie à chaque projet).
- **Zone géographique** : principalement Bruxelles et alentours, déplacement possible partout en Belgique (déjà dans le site).

## 2. Services proposés

Liste confirmée (transcript) : peinture intérieure/extérieure, rénovation intérieure/extérieure (façades), décoration/finitions, plafonnage, enduisage, cloisons placoplâtre, isolation intérieure, carrelage, pose de parquets, rénovation de planchers, installation de cuisines, rénovation de parking.

- **Spécialités techniques** : **enduits décoratifs** et **finitions** — au-delà de ça, Alberto se positionne comme polyvalent ("il fait tout").

### Travaux refusés / non pris en charge
- **Jardinage** : refusé (confirme et clarifie l'ambiguïté "bardage/jardinage" du transcript — c'est bien le jardinage qui n'est pas fait, en plus du bardage).
- **Bardage** : refusé.
- **Devis liés à un dégât couvert par une assurance** : en général refusé **en tant que chantier classique**. Si une demande de devis arrive dans ce contexte (sinistre à faire valoir en assurance), Alberto facture directement **100€ pour l'établissement du devis** (déductible si contrat signé ensuite — cohérent avec la section urgences, voir §8).

### Projets phares (pour chatbot + contenu réseaux sociaux)
1. **Le Hard Rock Café** (à Bruxelles) — café mythique américain, Alberto a refait **toute la peinture intérieure**.
2. Un client dont le père était **le fils de Picasso** — a réalisé la peinture pour lui (mentionné dans le transcript comme "descendant direct du peintre Picasso").

### Projets fréquents
Rénovation et peinture (le type de chantier le plus courant).

## 3. Processus client

- 1er contact : majoritairement par **appel téléphonique**, puis mail, puis SMS. Alberto répond toujours à l'appel direct.
- Après 1er contact : **rendez-vous** puis **visite sur place** avant devis (sauf cas rares : chantier éloigné et simple, estimation par téléphone).
- **Devis réalisé en ~1h** sur place, **validité 15 jours**.

## 4. Prix et devis

- **Aucune fourchette de prix indicative possible** — chaque projet est différent selon les matériaux utilisés et le contexte. Confirmé explicitement : "impossible à donner" une fourchette, même approximative. **→ à ne pas essayer de faire dire une fourchette au chatbot/prompt email : orienter systématiquement vers un devis sur place.**
- **Mode de calcul (confirmé définitivement par Paolo le 13/09/2026)** : Alberto estime le chantier en **heures/jours de travail**, facturés à **400€/jour**. **Il ne base pas son prix sur un pourcentage du matériel acheté** — le "+25% matériel" mentionné dans une version précédente de ce document était une mauvaise lecture du transcript audio dégradé, **à ignorer définitivement**. Le mode de calcul par matériel/marge est identifié comme un axe d'optimisation future, pas la méthode actuelle.
- **Acompte** : **50%** à la signature du contrat, avant le début des travaux.
- **Paiement intermédiaire** : **40%**, exigible **à la moitié du chantier** (calculé sur la durée totale estimée dans le devis — ex. chantier de 14 jours → paiement des 40% au jour 7). **Point d'action : cette règle "moitié du chantier" doit être formalisée comme clause explicite dans le template de devis (V2, génération de devis)** — actuellement c'est une règle informelle appliquée par Alberto.
- **Solde final : 10%** à la fin du chantier (précision confirmée : c'est bien 10%, pas 5%).
- **Devis pour sinistre/assurance** : 100€, déductible si le contrat est signé.
- **Demande urgente** (hors sinistre assurance) : **majoration de 35%** sur le prix habituel.

## 5. Matériaux et fournisseurs

- **Décision de Paolo (13/09/2026) : hors scope pour l'instant, volontairement.** Aucune info fournisseur/matériaux ne sera intégrée à la KB dans cette première version. Le chatbot et le prompt email doivent rester silencieux sur ce sujet et renvoyer vers un contact direct. Piste pour plus tard : enrichir ce point une fois le système en usage réel, via les retours/itérations d'Alberto (apprentissage progressif plutôt qu'un atelier dédié dès maintenant) — cohérent avec le principe déjà noté dans `ROADMAP.md` (V3, stock digital qui se construit avec le temps).

## 6. Disponibilité et communication

- Délai de réponse promis : **24h**, souvent **le jour même**.
- Horaires : **8h–16h30**.
- Canaux clients : appel, WhatsApp, SMS.
- Préférence notifications : **regroupées**, plutôt le matin.

## 7. Primes régionales

- **Aujourd'hui, Alberto n'accompagne pas ses clients dans les démarches de primes.**
- **Décision de Paolo (13/09/2026)** : ce sera un **nouveau service à valeur ajoutée** à construire — pas encore prêt, **nécessite une recherche en ligne dédiée** pour réunir les informations nécessaires (conditions, montants, démarches par région) afin que le système puisse accompagner les clients **dès la signature du contrat**. **Ce n'est pas encore un contenu à mettre sur le site** (le site a déjà une section Primes générale à jour, voir `PROJECT_STATUS.md` section 4) — c'est un service d'accompagnement personnalisé post-signature, à concevoir séparément.
- **Action à prévoir** (hors scope KB immédiat) : session dédiée de recherche + conception de ce service primes, avant de l'intégrer au prompt IA / workflow n8n.

## 8. Cas particuliers

- **Sinistre/assurance** : voir §4, devis payant 100€, généralement pas pris en charge comme chantier classique.
- **Urgence hors sinistre** : majoration de 35% du prix habituel, pas de délai d'intervention chiffré donné.
- **N'a jamais refusé de chantier classique.**
- **Est assuré.**
- **Malentendus** : Alberto n'a rien partagé de concret ("il ne m'a rien partagé par rapport au malentendu, mais c'est normal qu'il peut y en avoir"). Principe général donné par Paolo pour le système : **en cas de problème constaté sur le chantier ("il y a toujours quelqu'un sur le chantier"), le coût est réajusté avec le client** — approche humaine au cas par cas, pas de politique formelle écrite à ce jour.

---

## Statut : KB V1 considérée complète

Plus de point ouvert bloquant. Le sujet fournisseurs/matériaux est un choix de scope assumé (voir §5), pas un trou à combler dans l'immédiat.

## Actions dérivées (hors périmètre strict de la KB)

1. **Service "accompagnement primes régionales"** : recherche faite le 13/09/2026, voir `PRIMES-ACCOMPAGNEMENT/RECHERCHE-PRIMES-2026.md` — conception du service encore à faire (déclenché à la signature du contrat).
2. **Clause "40% à mi-chantier"** à intégrer dans le futur template de devis (V2).
