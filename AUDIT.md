# AoE2 Field Coach v1.10 — Audit et validation

**Source examinée :** archive `AoE2-Field-Coach-iPhone-v1.9.zip` présente dans la conversation. Mise à jour incrémentale de `index.html`, `sw.js` et du document d'accompagnement. Les icônes PWA, le manifeste et les autres fichiers sont conservés.

## 1. Architecture examinée

| Composant | État v1.9 et traitement v1.10 |
|---|---|
| `index.html` | Styles, navigation, Timers, Circuit, traductions, stockage et notifications regroupés dans un fichier. Nouveau composant Décisions ajouté sans réécriture générale. |
| Navigation | Choix de vue `coachView`, conservé pour Circuit et Timers ; ajout de `decisions`. Le sélecteur reste caché dans l'écran paysage minimaliste. |
| Âges | Une seule variable `state.age` (`I`–`IV`) ; Décisions lit cette variable. Aucun âge parallèle. |
| Timers | Banque des 32 rappels existants, ordre des cadrans et profils par âge conservés. |
| Circuit | Six catégories, ordre/activation/durées par âge, signaux et bouton de relance conservés. Production militaire désactivée par défaut en âge I, sans écraser les profils existants. |
| Audio | Routage des sources `timer`, `circuit`, `decisions`. Son de Décisions indépendant, désactivé initialement ; les sons des modes invisibles ne passent pas. |
| Stockage | Ancienne clé `aoe2-field-coach-v19` relue ; nouvelle clé `aoe2-field-coach-v110` écrite. L'ancien mode choisi et les personnalisations sont conservés. |
| PWA | Service worker et cache renommés pour v1.10. Pas de changement du modèle d'hébergement GitHub Pages. |

## 2. Nouveau mode Décisions

- **32 questions localisées FR/EN/ES**, filtrées par âge et par l'une des sept catégories : Observer, Anticiper, Mission, Composition, Financement, Sécurité, Consolidation.
- Une grande question centrale, une catégorie et l'âge courant ; aucune saisie requise.
- Bouton « Question suivante », même si le défilement automatique est en pause.
- Défilement automatique **désactivé par défaut**, avec intervalle réglable : 90, 105, 120, 150, 180 ou 240 secondes réelles.
- Son **désactivé par défaut** ; la seule question périodique affichée change sans notification additionnelle de type bannière.
- Sélection locale déterministe, ordre remélangé à la fin d'un cycle, sans répétition à l'intérieur d'un cycle ni doublon immédiat au début du suivant lorsqu'il existe plusieurs questions.
- Changement d'âge : question adaptée sans alerte automatique immédiate.
- Pause indépendante : n'arrête pas la session commune, ni les Timers, ni le Circuit.
- Quand le navigateur passe en arrière-plan, aucune rafale de questions en retard n'est générée au retour.

## 3. Icône Production militaire

L'icône `swords` de **Lucide**, dont le SVG original était disponible dans la conversation, remplace le dessin personnalisé dans la fonction de rendu des pictogrammes. Les huit chemins originaux et leur viewBox 24×24 sont utilisés par le Circuit et les Timers ; les couleurs personnalisées restent appliquées via `currentColor`.

## 4. Contrôles réalisés

| Test | Résultat |
|---|---|
| Compilation syntaxique du JavaScript embarqué | Réussie |
| Démarrage propre : Circuit sélectionné, Décisions sans rappel automatique ni son | Réussi |
| Passage de Circuit vers Décisions en paysage, question unique et quatre âges visibles | Réussi |
| Affichage paysage 852×393 et 668×290 : question et commandes sans débordement | Réussi |
| Affichage portrait 393×852 et choix des trois modes | Réussi |
| FR/EN/ES, changement de langue pendant la session et maintien du texte | Réussi |
| Bouton Question suivante, pause Décisions indépendante de la session | Réussi |
| Question adaptée à chaque âge I/II/III/IV | Réussi |
| Cycle complet par âge et anti-répétition | Réussi |
| Toutes les catégories décochées : message explicite, aucune question fantôme | Réussi |
| Simuler l'échéance automatique d'une question | Réussi |
| Simuler l'échéance simultanée d'un Timer et d'une question avec son : **un bip** | Réussi |
| Pictogramme Lucide en vue Timers : huit chemins SVG attendus | Réussi |
| Migration synthétique v1.9 → v1.10 (mode Timers et couleur militaire personnalisée) | Réussie |
| Préférences Décisions persistantes via stockage simulé et rechargement | Réussie |

Les tests de navigateur ont été effectués avec **Chromium en automatisation** (dimensions représentatives de l'iPhone), via rendu en mémoire et stockage local simulé. Il ne s'agit **pas** de tests réels sur iOS, Brave, Firefox ou en cours de partie. Le comportement réel des sons, du maintien de l'écran allumé et de la suspension iOS doit être validé sur l'appareil.

## 5. Limites et prochaines améliorations

1. **Valider les décisions en partie réelle** : une question toutes les 105 secondes est un point de départ, pas une fréquence démontrée optimale.
2. **Tester l'audio sur iPhone** : le navigateur peut exiger une interaction avant d'autoriser les sons. Éviter de promettre un bip précis en arrière-plan.
3. **Évaluer la charge visuelle** : si les rappels contextuels existants perturbent la lecture de Décisions, prévoir une politique explicite de priorité entre bannière et question, sans modifier la fréquence de chacun silencieusement.
4. **Événements manuels facultatifs** (« attaque subie », « combat gagné », etc.) : envisager seulement après retour utilisateur ; ne pas ajouter de gestes à faire pendant un combat.
5. **Exporter/importer la configuration** : amélioration potentiellement utile pour conserver les profils en cas de réinstallation du navigateur, mais non indispensable au MVP.

**Principe de conception :** l'application ne lit pas le HUD, ne détecte aucun événement de jeu et ne donne pas d'ordre automatisé. Les couleurs entraînent le tour des yeux ; les questions entraînent le raisonnement. L'objectif est de rendre ces réflexes de plus en plus autonomes.
