# Questionnaire — Atelier Base de Connaissances (KB) Alberto Deco

> À utiliser pour l'atelier avec Alberto Deco (assumption critique A2, voir `PROJECT_STATUS.md` section 12.3). Objectif : poser ces questions à Alberto, enregistrer/transcrire ses réponses, et transformer le transcript en première version de la base de connaissances (KB) qui alimente le chatbot du site et les réponses email générées par le workflow n8n.

**Format recommandé :** entretien oral enregistré (~1h30-2h), Paolo pose les questions, Alberto répond librement. Le transcript brut sera ensuite structuré en KB (pas besoin qu'Alberto rédige lui-même).

**Comment l'utiliser :** ne pas forcément suivre l'ordre à la lettre — les questions sont groupées par thème pour faciliter la structuration ultérieure du transcript. Relancer/creuser dès qu'une réponse touche un point utile pour le chatbot ou les réponses email (ex. un chiffre, un délai, une exception).

---

## 1. L'entreprise et l'identité

1. Depuis quand Alberto Deco existe-t-il ? (le logo dit "since 1989", le site dit "+30 ans d'expérience" — quelle est la bonne date/histoire à raconter ?)
2. Comment décrirais-tu Alberto Deco en une phrase à quelqu'un qui ne connaît pas l'entreprise ?
3. Qu'est-ce qui différencie Alberto Deco de la concurrence (Qualideco, BW Decor, Moret & Fils, etc.) ? Qu'est-ce que tu fais différemment ou mieux ?
4. Combien de personnes travaillent avec toi actuellement (équipe fixe, sous-traitants) ?
5. Dans quelles zones géographiques travailles-tu principalement ? Jusqu'où acceptes-tu de te déplacer ?

## 2. Les services proposés

6. Quels sont exactement les services que tu proposes ? (peinture intérieure, extérieure, rénovation complète, décoration, autre ?)
7. Y a-t-il des types de travaux que tu ne fais PAS ou que tu refuses généralement ? Pourquoi ?
8. Quels sont les projets/types de chantiers les plus fréquents que tu reçois ?
9. Quels sont les projets dont tu es le plus fier ? (utile pour le chatbot ET pour du contenu réseaux sociaux)
10. As-tu des spécialités ou techniques particulières (enduits décoratifs, finitions spécifiques, etc.) ?

## 3. Le processus client (du premier contact au chantier)

11. Aujourd'hui, sans le nouveau système, comment se passe concrètement un premier contact avec un client ? (appel, visite, etc.)
12. Après le premier contact, quelles sont les étapes jusqu'au début du chantier ? Combien de temps ça prend en général ?
13. Fais-tu toujours une visite sur place avant de faire un devis ? Dans quels cas c'est indispensable, dans quels cas tu peux estimer à distance (avec photos par exemple) ?
14. Quelles infos as-tu absolument besoin d'un client pour pouvoir donner une première estimation ou répondre correctement à sa demande ?
15. Quelles sont les questions que les clients te posent le plus souvent (avant, pendant, après un chantier) ?

## 4. Prix et devis (pour alimenter les futures réponses, même si l'estimation auto est en V2+)

16. Comment fixes-tu généralement tes prix ? (au m², forfait, à la tâche, autre ?)
17. Y a-t-il une fourchette de prix "typique" par type de travaux que tu peux donner, même approximative, pour aider à répondre aux clients en attendant une vraie estimation ?
18. Quels facteurs font varier fortement un prix (état du support, accès difficile, hauteur, délai souhaité, etc.) ?
19. Quel est ton fonctionnement pour l'acompte ? (le système sait déjà : 50% au démarrage — y a-t-il des exceptions, un solde en plusieurs fois, etc. ?)
20. Y a-t-il des délais de paiement, conditions ou clauses que tu mentionnes systématiquement dans tes devis ?

## 5. Matériaux et fournisseurs

21. Qui sont tes fournisseurs principaux (peinture, matériaux de rénovation) ?
22. As-tu des marques ou gammes de produits que tu recommandes/utilises systématiquement ? Pourquoi ?
23. As-tu un catalogue (papier ou en ligne) de ton/tes fournisseur(s) que tu pourrais nous transmettre ou nous montrer ? (utile pour construire la future base de connaissances matériaux, V2+)
24. Y a-t-il des couleurs, finitions ou matériaux à la mode que les clients demandent souvent en ce moment ?

## 6. Disponibilité et communication

25. Quel est ton délai de réponse habituel/souhaité à un client qui te contacte ? (utile pour calibrer les promesses du site, actuellement "24h")
26. Utilises-tu WhatsApp régulièrement ? Et Telegram ? (assumption A1 — confirme le canal de notification à privilégier)
27. Préfères-tu recevoir les notifications de nouveaux messages regroupées (ex. un résumé le matin) ou au fil de l'eau dès qu'un client écrit ?
28. Y a-t-il des moments où tu ne veux vraiment pas être dérangé par des notifications (le soir, le week-end, sur chantier) ?

## 7. Primes et aides régionales (déjà en partie sur le site, à valider/enrichir)

29. Est-ce que tu accompagnes tes clients dans leurs démarches de primes régionales (Wallonie/Bruxelles/Flandre) ? Comment ?
30. Y a-t-il des infos ou pièges fréquents sur les primes que tu expliques souvent aux clients ?

## 8. Cas particuliers et exceptions

31. Y a-t-il des situations où tu refuses catégoriquement un chantier ? Lesquelles ?
32. Comment gères-tu les urgences (dégât des eaux, sinistre) par rapport à une demande de rénovation classique ?
33. As-tu déjà eu des malentendus avec des clients qu'on pourrait éviter en étant plus clair dès le premier contact ? (utile pour calibrer le ton et le contenu des réponses automatiques)

---

## Après l'atelier

1. Transcrire l'enregistrement (Paolo transfère le transcript pour construction de la KB)
2. Structurer le transcript en fiches thématiques (services, prix indicatifs, FAQ, ton de communication, etc.)
3. Injecter la KB structurée dans le chatbot du site et dans le prompt du workflow n8n (génération de réponse email)
4. Revoir la KB avec Alberto pour validation avant mise en prod
5. Prévoir un processus pour enrichir la KB au fil du temps (retours d'usage réel — voir `PROJECT_STATUS.md` section 12.3, assumption A2)
