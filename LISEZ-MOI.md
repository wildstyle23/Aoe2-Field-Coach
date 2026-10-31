# AoE2 Field Coach — v1.3

Application web autonome (iPhone en paysage ou portrait), sans connexion au processus d'Age of Empires II.

## Nouveautés de cette version

- **Changement d'âge en un appui** : les boutons **I, II, III, IV** restent visibles en bas, même dans la vue minimaliste paysage.
- **Profils d'âge modifiables** : pour chacun des huit rappels, sélectionner individuellement les âges où il doit apparaître. Le nombre de cadrans affichés ajuste automatiquement la grille (une ligne de 1 à 4, deux lignes de 5 à 8).
- **Couleurs personnalisées** : choix indépendant de la couleur du symbole et de celle du glow/bordure, enregistré localement.
- **Icônes minimalistes** : maison (TCs), compas (scouting), épi de blé (économie), épées (armée), ainsi que quatre autres symboles pour les rappels facultatifs.
- **Huit rappels périodiques** : TCs/villageois, reconnaissance, économie/fermes, production militaire, mission/prochain âge, sécurité/murs, reliques/carte et population/maisons.
- **Mode Auto par défaut** pour une nouvelle installation ; les choix déjà sauvegardés sont respectés.
- **Mode Combat** : suspend les rappels secondaires (et leur décompte) tout en conservant les rappels TCs et production militaire. La sortie du mode Combat peut déclencher un rappel économique 30 s plus tard.
- **Rappels ponctuels configurables** : murs au Féodal (+45 s), deuxième TC au Castle (+75 s), reliques au Castle (+90 s, désactivé par défaut), siège à l'Impérial (immédiat), retour à l'économie après un combat (+30 s).
- **Timer de recherche d'âge facultatif** : « Lancer passage à II/III/IV » depuis les commandes. Durées indicatives paramétrées à 130/160/190 secondes *de jeu*, converties avec la vitesse définie (1,7× par défaut). Alerte facultative 20 secondes réelles avant la fin. Le changement d'âge affiché demeure **manuel**.
- **Temps réel ou temps de jeu** : pour chaque rappel périodique, choisir la base de la durée. Le coefficient de vitesse est ajustable de 0,25 à 4.
- Les réglages précédents connus sont repris lorsque c'est possible : mode, confort, et intervalles personnalisés pour scouting, économie et ancienne production.

Les durées sont des propositions d'entraînement et peuvent être inadaptées à certaines civilisations ou conditions de jeu. Le coach n'observe aucun événement dans AoE2.

## Installer la mise à jour sur GitHub Pages

1. Décompresser l'archive ZIP sur le PC.
2. Dans le dépôt GitHub Pages déjà configuré, remplacer **à la racine** : `index.html`, `sw.js`, `manifest.webmanifest`, les trois images d'icônes et éventuellement ce fichier `LISEZ-MOI.md`.
3. Effectuer un commit ; GitHub Pages republiera le site à la même adresse.
4. Sur l'iPhone, recharger la page. Si l'ancienne interface est encore visible, fermer puis rouvrir le site ; le service worker peut prendre un rechargement supplémentaire pour adopter la nouvelle version.

**Aucun nouveau dépôt GitHub ou réglage Pages n'est nécessaire.** Les préférences sont stockées dans le navigateur utilisé : une installation Safari et un onglet Brave peuvent avoir des préférences différentes.

## En partie, sans multiplier les manipulations

1. Tourner l'iPhone en paysage. Toucher le fond noir (pas le cadran) pour faire apparaître les commandes, puis choisir **Démarrer**. Toucher « Masquer » pour revenir à la vue compacte.
2. Quand l'âge change **dans le jeu**, appuyer simplement sur **I, II, III ou IV** en bas. Les cadrans changent automatiquement selon votre profil défini dans les réglages.
3. Si nécessaire, toucher **⚔ Combat** pour suspendre temporairement les rappels secondaires, puis le retoucher en fin de combat. Le rappel TC et la production militaire continuent.
4. Un appui sur un **cercle** relance uniquement son rappel. Le comportement Auto/Manuel/Hybride reste disponible.
5. Pour ouvrir les réglages en paysage, toucher une zone noire libre puis **⚙** ; en portrait l'interface est visible directement.

### Paramétrage des profils d'âge

Dans **⚙ → Timers et affichage par âge** :

- Activez ou désactivez globalement chaque rappel.
- Cochez séparément les âges **I / II / III / IV** correspondant à ses périodes utiles.
- Choisissez l'intervalle, la base de temps (s réelles ou s jeu), la couleur de l'icône et la couleur du glow/bordure.
- Les changements sont enregistrés automatiquement. Les changements de couleur ne relancent pas le chronomètre.

### Configurations de départ

| Rappel | Intervalle réel proposé | Âges actifs par défaut |
| --- | --- | --- |
| TCs et villageois | 25 s | I, II, III, IV |
| Scouting | 50 s | I, II, III |
| Économie et fermes | 70 s | I, II, III, IV |
| Production militaire | 40 s | II, III, IV |
| Mission et prochain âge | 110 s | Précoché II, III, IV, mais désactivé globalement |
| Sécurité et murs | 55 s | Précoché II, III, mais désactivé globalement |
| Reliques et carte | 105 s | Précoché III, IV, mais désactivé globalement |
| Population et maisons | 45 s | Précoché I, II, III, IV, mais désactivé globalement |

Les autres rappels peuvent être activés à volonté. Si huit rappels sont visibles, la grille passe à deux rangées ; il est préférable d'en activer seulement quelques-uns pour conserver une bonne lisibilité.

## Contraintes et confidentialité

- **Aucune interaction avec AoE2 :** pas d'injection, pas de lecture mémoire, pas d'automatisation du jeu, pas de capture écran.
- L'app n'identifie pas l'âge, la civilisation, les files de production ou la mise en pause du jeu. **Chaque changement d'âge doit être effectué manuellement.**
- Les timers ne peuvent s'afficher en temps réel lorsque l'iPhone est verrouillé ou que la page n'est plus visible. Au retour à l'app, les échéances sont recalculées ; les événements manqués ne déclenchent pas une série d'alertes.
- Le maintien de l'écran allumé est une demande faite au navigateur, sans garantie de prise en charge ni de disponibilité sur Firefox ou Brave iOS.
- Un onglet Brave/Firefox peut présenter des barres de navigation ; pour un affichage proche d'une application plein écran, installer le site sur l'écran d'accueil avec Safari.
- Les informations restent stockées localement dans le navigateur via `localStorage`, sauf les fichiers publics de l'application hébergés sur GitHub Pages. Aucun service d'analyse ou serveur applicatif n'est inclus.
- La compatibilité avec les règles des parties classées et des tournois n'est pas garantie par ce projet ; l'outil ne tourne pas sur le PC de jeu lorsqu'il est utilisé sur l'iPhone.
- L'application est une aide visuelle d'entraînement, **pas un outil mesurant automatiquement les actions réalisées**.

## Vérifications techniques

La version a été testée dans Chromium automatisé aux tailles 852×393, 668×290 et 393×852 : profils par âge, grille de 3/4/8 cadrans, paramètres de couleur, sauvegarde, mode Auto/Manuel, pause/reprise, alertes de changement d'âge, timer de recherche et absence d'alertes d'un âge quitté. Elle **n'a pas encore été testée directement sur Firefox/Brave iOS**.
