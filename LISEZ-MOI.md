# AoE2 Field Coach — v1.2 (iPhone)

Application web de rappels visuels, entièrement indépendante du jeu. Tous les compteurs s'exécutent sur l'iPhone et ne communiquent pas avec AoE2.

## Nouveautés

- **Paysage :** fond noir et seulement trois cadrans côte à côte (icônes, anneaux de progression, décomptes), sans barre ni commandes.
- **Faire apparaître les commandes :** toucher le fond noir ou une tuile en dehors de son cercle. Toucher une seconde fois le fond noir pour les masquer ; bouton **Masquer** dans la barre supérieure.
- **Portrait :** interface complète, comme avant.
- **Auto par défaut**, y compris lors du premier lancement après migration depuis v1.1. Les choix effectués ensuite dans v1.2 sont conservés.
- **Alertes :** quand le cadran clignote, la bordure rectangulaire pulse également (si animations activées).
- Icônes vectorielles plus détaillées : **boussole** pour le scouting et **grange / blé / pièce** pour l'économie. L'icône de production est conservée.

## Utilisation

1. Mettre à jour sur GitHub : envoyer tous les fichiers de cette archive à la **racine** du dépôt GitHub Pages, en remplaçant `index.html`, `sw.js` et `manifest.webmanifest`.
2. Ouvrir la page sur l'iPhone. Si la version précédente reste visible, rafraîchir ou fermer/réouvrir l'application ; le service worker peut nécessiter un nouveau chargement pour s'actualiser.
3. Tourner en paysage : trois cadrans seulement. Touchez le fond noir pour faire apparaître les commandes, puis **Démarrer la session**. Appuyer sur **Masquer** pour revenir aux cadrans seuls.
4. Toucher un **cercle** pour réinitialiser le rappel correspondant. Un appui à côté du cercle sur une tuile compacte ouvre les commandes.
5. Tourner en portrait pour afficher directement l'interface et accéder aux réglages.

## Modes et réglages

- **Auto :** relance automatiquement le décompte ; alerte visuelle pendant quelques secondes.
- **Manuel :** attend l'acquittement par une touche sur le cercle.
- **Hybride :** rappel persistant avec pulsation jusqu'à acquittement.
- Durées initiales : scouting 60 s, production 25 s, économie 45 s. Valeurs expérimentales, personnalisables de 10 à 600 s.
- Pause, remise à zéro, réglages des alertes visuelles, bip optionnel, fonction de maintien de l'écran allumé si prise en charge par le navigateur.

## Points importants

- On ne peut pas forcer l'orientation du téléphone si le verrouillage de rotation est activé dans iOS.
- Le maintien de l'écran allumé dépend de la prise en charge par Brave/Firefox iOS et du fonctionnement au premier plan.
- Les minuteries utilisent le **temps réel**, pas celui du jeu. La pause du jeu ne met pas automatiquement le coach en pause.
- Les données de configuration restent dans le stockage local du navigateur ; une suppression des données du site peut effacer les préférences.
- L'application n'interagit pas avec le processus du jeu. Cela ne constitue pas une garantie de conformité aux règles d'une compétition.
