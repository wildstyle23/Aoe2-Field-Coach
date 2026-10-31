# AoE2 Field Coach — rappels iPhone (v1.1)

Petit outil de rappels visuels pour **Age of Empires II: Definitive Edition**, conçu pour être affiché sur un iPhone posé près de l'écran de jeu. Il fonctionne **indépendamment du PC de jeu** et ne lit ni ne commande AoE2.

## Affichage horizontal (nouveauté v1.1)

- Tournez l'iPhone **en orientation paysage** : les trois cadrans **Scouting, Production et Économie** apparaissent côte à côte, avec les modes et boutons en dessous ou au-dessus.
- L'affichage s'adapte à la largeur et à la hauteur disponibles. Le mode portrait reste utilisable en dépannage.
- Le manifeste web demande l'orientation `landscape`, mais **Safari sur iPhone peut ignorer cette préférence**. L'application ne peut pas forcer la rotation si l'orientation est verrouillée dans iOS ; désactivez le verrouillage de rotation si nécessaire.
- Les réglages restent accessibles par la roue dentée et sont défilables en paysage.

## Modes

- **Auto** : le compteur se relance automatiquement après une brève alerte de 6 secondes. Vous pouvez aussi le relancer manuellement.
- **Manuel** : le compteur atteint zéro, puis reste sur « À vérifier » jusqu'à ce que vous appuyiez sur le cercle ou la flèche.
- **Hybride** : même fonctionnement manuel, mais l'alerte pulse pour attirer le regard tant que vous ne l'avez pas acquittée.

## Réglages

- Trois compteurs indépendants : **Scouting (60 s)**, **Production (25 s)**, **Économie (45 s)**.
- Intervalles modifiables de **10 à 600 secondes** ; les valeurs initiales sont **expérimentales**, pas une recommandation de gameplay.
- Activation/désactivation de chaque rappel.
- Pause générale, remise à zéro d'un rappel, remise à zéro générale, durée de session.
- Maintien d'écran éveillé, en utilisant **Screen Wake Lock** lorsque Safari l'autorise.
- Bip optionnel (désactivé par défaut), pouvant dépendre des restrictions audio de Safari.
- Réglages conservés localement sur l'appareil tant que les données du site ne sont pas effacées.

## Installer comme application sur iPhone (recommandé)

L'application est un site statique. Elle **n'est pas encore hébergée**. Pour en faire une application Safari, placer les fichiers de ce dossier à la racine d'un hébergement HTTPS, par exemple **GitHub Pages** :

1. Créer un dépôt GitHub dédié (avec GitHub Free, le dépôt Pages doit être public).
2. Déposer les fichiers **index.html**, **manifest.webmanifest**, **sw.js**, les **icônes PNG** à la racine du dépôt.
3. Aller dans **Settings > Pages**, choisir **Deploy from a branch**, puis `main` et `/ (root)` ; enregistrer.
4. Ouvrir l'URL HTTPS de la page publiée dans Safari sur l'iPhone.
5. Dans Safari, utiliser **Partager > Sur l'écran d'accueil > Ouvrir comme app web > Ajouter**.
6. Lancer l'app depuis l'icône de l'écran d'accueil.

Lorsqu'elle est servie en HTTPS et que son service worker a pu mettre les fichiers en cache, l'app peut être utilisée hors ligne après une première ouverture réussie.

Documentations :
- GitHub Pages : https://docs.github.com/fr/pages/getting-started-with-github-pages/creating-a-github-pages-site
- Apple : https://support.apple.com/fr-fr/guide/iphone/iphea86e5236/ios
- Wake Lock : https://developer.mozilla.org/en-US/docs/Web/API/Screen_Wake_Lock_API

## Essayer sans hébergement

`index.html` contient tout le code de l'interface (HTML, CSS et JavaScript). Il peut être ouvert depuis un navigateur de bureau pour un essai. Sur iPhone, l'application **Fichiers** n'ouvre pas systématiquement un fichier HTML local dans Safari comme un site web interactif. Pour un usage fiable et pour bénéficier de l'option « écran allumé », préférez un hébergement HTTPS.

## Limites

- Les minuteurs utilisent le **temps réel**, pas le temps du jeu. Ils ne détectent pas une pause AoE2, un changement de vitesse ou une action réellement effectuée.
- Le bip et l'affichage des rappels ne sont **pas garantis en arrière-plan**, écran verrouillé ou onglet suspendu. La page doit rester visible.
- La fonction « garder l'écran allumé » est soumise aux autorisations et conditions de Safari ; elle n'est pas garantie. Prévoir un test sur l'iPhone.
- Il s'agit d'un outil indépendant : aucune garantie n'est donnée quant à sa conformité aux règles particulières d'un tournoi. La validation de son usage compétitif est distincte de son fonctionnement technique.
- Pas de compte, pas de télémétrie, pas de transmission de données à un serveur applicatif : les réglages sont stockés dans le navigateur.
