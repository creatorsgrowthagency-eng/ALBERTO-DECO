# Recherche — Service d'accompagnement primes régionales (nouveau service, post-signature)

> Contexte : décision de Paolo (13/09/2026) — Alberto n'accompagne pas aujourd'hui ses clients dans les démarches de primes ; c'est identifié comme un **nouveau service à valeur ajoutée**, déclenché **après la signature du contrat**, distinct de la section "Primes" déjà présente sur le site vitrine (qui reste une info générale pour convaincre, pas un accompagnement personnalisé). Recherche en ligne effectuée le 13/09/2026 pour poser une première base — **à peaufiner plus tard**, notamment avec une vérification directe sur les sites officiels avant tout usage client réel (les infos primes changent vite et ce résumé vient de sources tierces, pas des sites .be officiels).

**⚠️ Statut : brouillon de recherche, pas encore validé.** Ne pas injecter tel quel dans le chatbot/prompt email sans revérification sur les sources officielles (SPW Wallonie, Bruxelles Environnement / Fonds du Logement, Vlaanderen.be) — les montants et conditions bougent souvent.

---

## 1. Wallonie

- **Échéance critique : 30 septembre 2026.** Toute demande de "Primes Habitation" (régime actuel, en vigueur depuis le 14/02/2025) doit être introduite **avant cette date** pour être traitée aux conditions actuelles.
- **À partir du 1er octobre 2026** : bascule vers un **nouveau régime permanent basé sur des prêts, plus des primes directes** :
  - **Rénopack** : prêt à taux zéro avec réduction du montant à rembourser (effet quasi-subvention) pour les catégories de revenus **C1 à C3**.
  - **Rénoprêt** : prêt à taux préférentiel pour la catégorie **C4**, les propriétaires-bailleurs et les copropriétés.
- **Travaux couverts (régime actuel)** : isolation (toiture/murs/sols), châssis/menuiseries, chauffage renouvelable (PAC, biomasse, pellets), chauffe-eau solaire, boiler thermodynamique, ventilation (VMC), conformité électrique/gaz, salubrité (humidité, radon, mérule).
- **Démarche/documents (Rénopack)** :
  - Devis détaillé de l'entrepreneur : description précise des travaux, quantités, prix unitaires, montant TVAC.
  - Entrepreneur inscrit à la **BCE** (numéro d'entreprise) + engagement à remplir l'**annexe technique** de l'administration wallonne.
  - Dépôt du dossier : plateforme **Mes Aides Financières** (mes-aides-financieres.be), plateforme **AppiCredit** (SWCS), ou courrier à la SWCS (Rue de l'Écluse 10, 6000 Charleroi).
  - Facture finale à introduire également avant le 30/09/2026 pour rester sous l'ancien régime.
- **Implication directe pour Alberto Deco** : ses devis doivent déjà respecter le format attendu (description précise, quantités, prix unitaires, n° BCE visible) — **à vérifier que ses devis actuels le font déjà**, sinon c'est un prérequis simple à corriger dans le futur template de devis (V2).

## 2. Bruxelles

- **Primes RENOLUTION supprimées** depuis février 2026 pour les nouveaux travaux (confirmation gouvernementale, contexte budgétaire bruxellois déficitaire).
- **Alternative principale : crédit ECORENO** (Fonds du Logement / Bruxelles Environnement), rouvert le 02/01/2026 après suspension :
  - Taux 2,5% ou 3,5% selon revenus.
  - Montant : 1 500€ à 25 000€ sans hypothèque (max 10 ans), ou jusqu'à 120% de la valeur après travaux en hypothécaire (max 30 ans).
  - Ouvert aux propriétaires, futurs propriétaires et locataires, bien situé dans une des 19 communes bruxelloises, sous plafond de revenus selon composition du ménage.
  - Travaux éligibles : isolation, ventilation, nouveaux systèmes de chauffage, pompes à chaleur, chauffe-eaux solaires, photovoltaïque.
- **Autres pistes résiduelles** : TVA à 6% (rénovation logement >10 ans), primes communales (variables selon la commune).
- **Implication pour Alberto Deco** : la disparition de Rénolution change beaucoup le discours vs ce qui est probablement encore dans la tête de certains clients — important que le service d'accompagnement clarifie tout de suite qu'il n'y a **plus de prime directe à Bruxelles**, seulement du crédit à taux réduit.

## 3. Flandre

- **Mijn VerbouwPremie**, réformée en profondeur au **1er mars 2026** :
  - 4 catégories de revenus (plus le revenu est bas, plus la prime est élevée), seuil augmenté de 4 420€ par personne à charge supplémentaire.
  - **Depuis le 01/03/2026** : isolation, façade, châssis/portes → **réservé aux catégories 3 et 4** uniquement. Les catégories 1 et 2 n'ont plus droit qu'à la prime pompe à chaleur.
- **Démarche** : demande **en ligne via Mijn VerbouwLoket**, uniquement **après travaux complètement terminés et facturés**. Factures acceptées jusqu'à **2 ans** après leur date.
- **Implication pour Alberto Deco** : logique inversée par rapport à la Wallonie — en Flandre, on demande **après** la fin du chantier, pas avant. Le service d'accompagnement devra donc avoir 2 timings différents selon la région.

---

## Synthèse pour la conception du service

| Région | Statut | Timing de la demande | Canal |
|---|---|---|---|
| Wallonie | Transition en cours (bascule prime→prêt le 01/10/2026) | Avant travaux, échéance 30/09/2026 pour l'ancien régime | Mes Aides Financières / AppiCredit / SWCS |
| Bruxelles | Primes directes supprimées, reste le crédit ECORENO | Selon le crédit, généralement avant/pendant | Fonds du Logement |
| Flandre | Réforme au 01/03/2026, primes resserrées sur bas revenus | **Après** travaux terminés et facturés (< 2 ans) | Mijn VerbouwLoket (en ligne) |

**Conséquence pratique pour le service d'accompagnement (déclenché à la signature, comme prévu par Paolo)** :
- Le bon moment pour informer le client n'est pas le même partout — en Wallonie/Bruxelles il faut agir **avant/au début** du chantier, en Flandre il faut préparer le client à déposer son dossier **après**. Le workflow n8n (V1/V2) devra donc adapter le message envoyé selon la région du chantier, pas un message générique unique.
- Les 3 régimes bougent vite (Wallonie change de fond en comble au 01/10/2026) — **ce document a une date de péremption courte**, à revérifier avant tout usage en prod, surtout après le 01/10/2026.

## À faire avant d'utiliser ces infos avec de vrais clients

1. Vérifier chaque point directement sur les sites officiels (SPW Économie/Logement, Bruxelles Environnement, Vlaanderen.be) — les sources utilisées ici sont des sites tiers (courtiers, blogs spécialisés), fiables pour une première synthèse mais pas des sources primaires.
2. Vérifier que les devis actuels d'Alberto Deco respectent déjà le format attendu par la Wallonie (n° BCE, quantités, prix unitaires).
3. Concevoir le message/flux différencié par région dans le workflow n8n une fois le reste de V1 stabilisé.
4. Revoir cette page après le 01/10/2026 (bascule Rénopack/Rénoprêt) — le contenu Wallonie sera obsolète à cette date.

## Sources consultées (13/09/2026)

- [Primes rénovation Wallonie : date clé 30 septembre 2026 | Blog Crelan](https://www.crelan.be/fr/particuliers/blog/habitation/primes-renovation-wallonie-2026-evolution)
- [Primes Habitation Wallonie 2026 : fin et futur régime](https://www.peb-connect.be/actualites/fin-des-primes-renovation-en-wallonie-ce-que-change-le-renopack-en-2026)
- [Rénopack Wallonie · le nouveau régime qui finance vos travaux](https://www.reno-pack.be/)
- [Primes Rénolution supprimées à Bruxelles : que faire ?](https://www.energyprotect.be/fr/blog/primes-renolution-bruxelles-supprimees)
- [Aides rénovation Bruxelles 2026 — Crédit ECORENO](https://primes-energie-belgique.be/bruxelles)
- [Mijn VerbouwPremie 2026: bedragen, voorwaarden en aanvragen](https://callmepower.be/nl/energie/gids/procedure/renovatiepremie)
- [Nieuwe regels Mijn Verbouwpremie 2026 - Stebo vzw](https://stebo.be/nieuwe-regels-mijn-verbouwpremie-2026/)
