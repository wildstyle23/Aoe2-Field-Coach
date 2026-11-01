# AoE2 Field Coach — v1.7

Application web autonome pour iPhone, compatible avec un hébergement statique GitHub Pages. Ne lit ni ne modifie AoE2.

## Nouveautés

- **Deux espaces distincts, toujours disponibles : `Timers` et `Circuit`.** Les 32 rappels, les 4 cadrans, le classement personnalisé par âge, les transitions via « › », les couleurs, le mode Auto et la gestion anti-flood des messages de la v1.5 sont conservés.
- **Circuit des yeux** avec 6 étapes dans l'ordre : 1. Villageois, 2. Économie, 3. Maisons, 4. Production militaire, 5. Carte, 6. Scout / armée.
- **Pictogrammes distincts pour villageois et maisons** : silhouette(s) humaine(s) contre deux toits de maisons.
- **Deux variantes de rythme :**
  - **Guidé** : le cadre actif change automatiquement à intervalles configurables (3, 4, 5, 6, 7 ou 8 secondes par étape) ; les trois derniers quarts d'étape restent stables, puis une anticipation visuelle apparaît pendant le dernier quart. À 6 secondes/étape, un tour complet dure 36 secondes.
  - **Libre** : aucun passage automatique d'étape ; les six pictogrammes restent visibles et un pulse collectif revient toutes les 15, 20, 25, 30, 40, 45 ou 60 secondes (25 s par défaut).
- **Deux dispositions de circuit :** `Six carrés + texte unique` (étape active et description en dessous) ou `Six rectangles nommés` (six noms intégrés). Les deux conservent le sélecteur d'âge I–IV et le bouton « › ».
- **Six couleurs configurables** indépendantes des couleurs des timers existants.
- **Langues sélectionnables dans les réglages : Français, English, Español.** L'interface et les noms/messages des 32 rappels sont traduits. Le choix est sauvegardé dans le navigateur.
- **Notifications contextuelles plus lisibles et positionnées en haut de l'écran.** Les noms des cadrans Timers sont agrandis.
- **Conservation des réglages de la v1.5** lors de l'ouverture de la v1.7 sur le même site et dans le même stockage navigateur (avec migration automatique).

## Choisir la cadence

Les six étapes guident un tour complet :

| Durée par étape | Durée d'un tour |
| ---: | ---: |
| 3 s | 18 s |
| 4 s | 24 s |
| 5 s | 30 s |
| 6 s (par défaut) | 36 s |
| 7 s | 42 s |
| 8 s | 48 s |

On ne peut pas faire six étapes complètes de 6 ou 7 secondes en moins de 30 secondes : pour cela, choisir 3 ou 4 secondes par étape, ou utiliser le **circuit libre** avec une fréquence de 20 à 25 secondes.

## Utilisation

1. En paysage, toucher `Circuit` pour afficher les six étapes, ou `Timers` pour retrouver les cadrans historiques.
2. Toucher le fond noir pour afficher les commandes, puis ouvrir `⚙ Paramètres`.
3. Dans **Circuit de vérification**, choisir Guidé / Libre, l'une des deux présentations, les durées et les six couleurs.
4. Dans **Langue**, sélectionner Français, English ou Español.
5. En jeu, les boutons I–IV et `›` restent toujours visibles pour les profils par âge et les transitions.

La session démarre / s'arrête via les commandes de l'application. Les cycles suivent l'horloge réelle et sont figés quand tu mets en pause **l'application**. Une pause du jeu seul ne peut pas être détectée par l'iPhone.

## Mise à jour GitHub Pages

1. Extraire le ZIP.
2. Remplacer les fichiers à la racine du dépôt existant, notamment `index.html`, `sw.js`, `manifest.webmanifest`, les trois icônes et ce fichier.
3. Valider le commit. Garder le même dépôt et la même URL GitHub Pages.
4. Une fois le déploiement terminé, actualiser la page ou fermer / rouvrir l'app web sur iPhone. Le cache du service worker porte désormais le nom `aoe2-fieldcoach-v1.7`.

**Remarque :** stockage local à l'origine web. Un changement de navigateur ou de domaine peut séparer les réglages. Faire une sauvegarde externe avant de changer de navigateur si les préférences sont importantes.

## Validations

Tests dans Chromium automatisé sur des écrans 852×393, 668×290 et 393×852 : circuit libre et guidé, parcours des six étapes, pause/reprise, 6 rectangles, couleurs, bascule de langue FR/EN/ES, conservation des modes Timers, migration des réglages v1.5, absence d'erreurs JavaScript. **Non testé physiquement sur iPhone / Firefox iOS / Brave iOS.**
