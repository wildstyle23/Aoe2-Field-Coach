# AoE2 Field Coach v1.9

Application web autonome destinée à l'iPhone, en mode paysage. Les **Timers** et le **Circuit** restent indépendants, et l'application ne communique pas avec Age of Empires II.

## Nouveautés

- Icône **Production** redessinée avec deux épées croisées.
- **Circuit sélectionné par défaut** ; le sélecteur visible en portrait place Circuit avant Timers. En paysage, il reste volontairement masqué. Le mode affiché se choisit également dans les paramètres.
- **Circuit configurable par âge I, II, III, IV** : cocher/décocher les étapes et modifier leur ordre avec les flèches. Les configurations de chaque âge sont sauvegardées séparément. En âge I, la production militaire n'est pas sélectionnée par défaut (mais reste activable).
- Choix entre **une durée commune** pour toutes les étapes et **des durées individuelles par étape et par âge** (2–30 s).
- **Bips synchronisés** : en mode Circuit, seul le changement d'étape (ou le signal du mode libre) peut produire un bip. Les échéances des Timers et des messages contextuels n'émettent plus de bip supplémentaire dans cette vue. Garde-fou anti-double signal de 420 ms.
- Le bouton **Relancer les Timers + Circuit** réinitialise les compteurs des deux modes, même si l'un n'est pas affiché.
- Séparation explicite des réglages **Circuit** et **Timers — ordre et position des cadrans**.
- Traductions de ces réglages en français, anglais et espagnol.

## Installer ou mettre à jour GitHub Pages

1. Décompresser l'archive ZIP.
2. Copier ses fichiers **à la racine** du dépôt GitHub Pages, dont `index.html`, `manifest.webmanifest` et `sw.js`. Ne pas ajouter un sous-dossier supplémentaire.
3. Valider les changements sur la branche utilisée par GitHub Pages.
4. Sur l'iPhone, recharger l'application après publication. Le cache du service worker passe en version `v1.9`.

Les préférences enregistrées par la version v1.8 sont récupérées lorsque l'application est ouverte depuis **le même site et le même espace de stockage du navigateur**. La première ouverture de la v1.9 passe au Circuit par défaut ; tu peux choisir à nouveau Timers dans les paramètres ou en portrait.

## Logique de la routine

**Villageois → Économie → Maisons → Production → Carte → Scout / Armée**. Ce circuit est un parcours d'attention proposé, pas une routine rigide. Une menace ou un combat important doit primer sur la séquence.

Le Circuit est conçu pour développer des automatismes de vérification ; les Timers gardent leur rôle de rappels périodiques indépendants. Le passage d'âge reste un événement initié manuellement, avec échéance estimée et correction possible via I–IV. Les bips sont désactivés par défaut.

## Limites techniques

- Le rythme du jeu, les pauses et les événements de combat ne sont pas détectés automatiquement.
- Les tests automatisés ont été réalisés dans Chromium, pas directement sur Brave/Firefox iOS.
- L'API de maintien de l'écran allumé dépend des autorisations et du navigateur.
