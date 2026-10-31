# AoE2 Field Coach — v1.4

Application web autonome pour iPhone en paysage, pensée pour entraîner les vérifications et décisions dans **Age of Empires II: Definitive Edition**. Elle ne communique pas avec le jeu, ne lit pas sa mémoire et n'automatise aucune action.

## Ce qui change depuis la v1.3

- **Quatre grands cadrans maximum**, même si davantage de rappels sont configurés : l'excédent est automatiquement traité comme des messages. Le nom figure **à l'intérieur du cadre et au-dessus de l'icône**, comme demandé.
- **32 rappels/vérifications personnalisables** en cinq catégories : automatismes (4), bâtiments/infrastructure (9), économie (6), carte/défense (6), stratégie/transitions (7).
- Chacun des rappels **périodiques** peut être affiché en **cadran** ou sous forme de **message temporaire**, avec son intervalle, sa base de temps, ses âges d'activation et sa priorité.
- **Bouton `›` toujours visible en paysage** : dès que tu cliques le passage d'âge *dans le jeu*, touche `›` sur l'iPhone. Le coach programme la transition, propose des checks de préparation et passe **automatiquement** au profil d'âge suivant à la fin *estimée*. Les boutons I–IV restent disponibles pour corriger l'âge manuellement. Cliquer sur `›` démarre également la session si elle était arrêtée.
- **Légère anticipation du changement de profil**, de 5 secondes réelles par défaut, modifiable de 0 à 15 secondes. Le temps de recherche de référence est 130 / 160 / 190 secondes **de jeu** pour les passages II / III / IV, converti selon la vitesse configurée (1,7× par défaut). Les civilisations ayant un bonus de recherche et les pauses du jeu nécessitent une correction manuelle.
- Les **événements d'arrivée** en Féodal/Castle/Impérial comprennent notamment : deuxième bâtiment militaire, forge, TC2, monastère, atelier de siège, université, siège de fin de partie. Ils sont désactivables séparément et leurs délais sont personnalisables.
- **Un seul message contextuel à la fois**, affiché 5 s par défaut, avec au minimum 45 s entre les débuts des messages. Regroupement des messages du même thème prévus à moins de 30 s, et abandon des alertes trop anciennes. Durées et regroupement configurables.
- **Mode Combat supprimé** : l'option « Économie après combat ? » existe désormais comme rappel périodique facultatif, sans aucun geste en pleine bataille.
- Les icônes minimalistes et leurs couleurs/glows configurables sont conservés. Le mode **Auto** demeure le défaut des nouvelles installations ; un mode déjà enregistré est respecté.
- Les réglages de v1.3 sont migrés quand un équivalent existe : TCs, scouting, économie, armée, mission, sécurité, reliques, les options d'événements correspondantes, couleurs, modes, etc. L'ancien rappel séparé « Population et maisons » est désormais couvert par le message du cadran « TCs et villageois » (logements), et non recréé comme cadran indépendant. Les sessions en cours ne sont pas reprises pendant une migration de version.

## Installation sur GitHub Pages

1. Décompresse `AoE2-Field-Coach-iPhone-v1.4.zip`.
2. À la racine du dépôt GitHub Pages existant (`aoe2-field-coach`), remplace **tous** les fichiers : `index.html`, `sw.js`, `manifest.webmanifest`, les trois PNG et, facultativement, `LISEZ-MOI.md`.
3. Valide le **commit** : GitHub Pages conserve la même adresse HTTPS, aucun nouveau dépôt nécessaire.
4. Sur l'iPhone, actualise le site et, si l'ancienne version reste affichée, ferme puis rouvre l'application. Le service worker utilise un nouveau cache `aoe2-fieldcoach-v1.4` et supprimera les caches de versions précédentes lors de son activation.

Tu peux aussi ouvrir `AoE2-Field-Coach-iPhone-v1.4.html` sur un ordinateur pour faire un essai, sans installation. Pour le maintien de l'écran allumé sur iPhone, privilégie la version hébergée en HTTPS.

## Utilisation type pendant une partie

1. Démarre l'application (bouton **Démarrer**, dans la vue développée), ou touche directement **`›`** lorsque tu cliques le Féodal dans AoE2 : cela démarre la session et la transition.
2. Les cadrans colorés te rappellent TCs, scouting, économie et production militaire. **Un appui sur un cercle relance ce seul timer.** En mode Auto, il redémarre seul.
3. Quand tu cliques le passage à l'âge suivant dans le jeu, touche **`›`**. Une ou deux questions de transition peuvent apparaître, puis le profil change automatiquement. Aucun suivi du jeu n'est effectué.
4. En cas de pause d'AoE2, affiche les commandes (touche le fond noir, pas le cercle) et mets les timers en pause également. Si la recherche d'âge prend un temps différent, corrige le profil via I–IV.
5. Ouvre **⚙ Paramètres → catégorie** pour modifier les profils, les rappels et les priorités. L'option « Reliques et carte » est conçue pour être activée en **message temporaire** à l'âge III, sans cadran.

### Rappels activés par défaut

| Famille | Au début | Après les transitions |
|---|---|---|
| Quatre cadrans | TC 25 s, Scout 50 s, Économie 70 s, Armée 40 s (à partir de II) | Les profils activent automatiquement les cadrans pertinents selon l'âge |
| Arrivée Féodal | — | 2e bâtiment (+20 s) et forge (+40 s), regroupables |
| Arrivée Castle | — | TC2 (+35 s), monastère (+65 s), atelier de siège (+90 s), université (+110 s), regroupables |
| Arrivée Impérial | — | Vérification du plan de siège |
| Stratégie | — | Plan Castle (âge II, toutes les 180 s), Mission/Composition/Financement (III, 180 s), Condition de victoire (IV, 180 s) |

La majorité des 32 rappels restent **désactivés par défaut**. Leur durée est une hypothèse d'entraînement configurable, pas une optimisation garantie.

## Limites et confidentialité

- Un timer n'indique pas qu'une action s'est réellement déroulée. Un message « Forge ? » demande une vérification, sans prescrire la construction.
- **Le profil d'âge automatique est une estimation** calculée à partir du moment où tu appuies sur `›`, pas une lecture du jeu. Les temps réels changent avec les vitesses et certains bonus de civilisation. Les pauses du jeu ne sont pas détectées.
- Si le navigateur suspend l'application en arrière-plan, l'interface ne peut pas y afficher ses rappels. Au retour, les échéances sont recalculées et les anciens messages ne sont pas rejoués en rafale.
- Les données (configurations, état des minuteurs) résident dans le `localStorage` du navigateur/app web sur l'iPhone. Brave, Firefox et l'application ajoutée à l'écran d'accueil peuvent utiliser des espaces de stockage distincts.
- La prise en charge de **Screen Wake Lock** dépend du navigateur iOS, de HTTPS et des autorisations en cours. Non garantie.
- La conformité avec les règles de parties classées et tournois n'est **pas garantie** par le projet. Utilisé sur l'iPhone, aucun logiciel de rappel ne s'exécute sur le PC AoE2.

## Contrôles et validation

Tests avec Chromium automatisé, en dimensions simulées **852×393**, **668×290** et **393×852** : affichage, quatre cadrans maximum, bibliothèque de 32 entrées, modifications des paramètres, sauvegarde, migration v1.3, transitions automatiques, événements d'arrivée, regroupement de deux messages, pause/reprise. **Non testé directement sur Firefox ou Brave iOS**.
