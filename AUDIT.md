# Audit et validation — AoE2 Field Coach v1.11

## Portée

Base de travail : fichiers de la v1.10, modification directe de `index.html`, mise à jour de `sw.js` et conservation du manifeste et des icônes. La bibliothèque existante, les trois modes, les profils du Circuit par âge et l'ensemble de leurs textes sont conservés.

## Évolutions et protections

| Composant | Évolution | Risque surveillé |
| --- | --- | --- |
| Session | Stop général, pause explicite, pause hors écran, rechargement figé | Temps énorme après fermeture, vieilles échéances |
| Profils | Équilibré, Macro, Scouting, Décisions, personnalisés | Perte des préférences de base |
| Circuit | Bip chaque étape ou début de tour | Signal sonore parasite / superposition |
| Intensité | Apprentissage, Consolidation, Autonomie | Surcharge visuelle |
| Stockage | Nouvelle clé `aoe2-field-coach-v111` et migration de `v110` | Écrasement d'une configuration existante |
| Langues | FR / EN / ES pour les nouvelles sections | Chaînes non traduites |

### Séparation des configurations

Le profil **Équilibré** stocke la configuration de référence ; les presets Macro, Scouting et Décisions sont calculés comme des variantes, sans modifier les couleurs de référence. Les profils personnalisés mémorisent leurs propres réglages. Les compteurs en cours et les événements transitoires ne sont pas inclus dans la configuration d'un profil.

### Politique de session

Une session interrompue est restaurée en pause. Si des données de v1.11 possèdent un `savedAt`, les durées résiduelles sont reconstruites à cette date ; le temps écoulé depuis la fermeture n'est pas compté. Pour une ancienne session v1.10 sans `savedAt`, l'application restaure les préférences mais réinitialise la progression temporelle pour éviter un compteur erroné.

## Tests automatisés réalisés

Navigateur : Chromium présent dans l'environnement, HTML chargé en mémoire avec une simulation de `localStorage`. Cela teste l'interface et le JavaScript, **pas** le service worker en conditions HTTPS ni le fonctionnement natif d'iOS.

- Chargement sans exception JavaScript en 852×393, 668×290 et 393×852.
- Création et application de profils, création d'un profil personnalisé, changement d'intensité et de rythme sonore.
- Changement de langues FR/EN/ES et affichage des libellés.
- Démarrer puis Arrêter : âge I, timers à zéro et profil conservé.
- Migration v1.10 : conservation d'un TC personnalisé à 35 s, de la couleur Production, de l'ordre par âge, des catégories Décisions et du mode sélectionné.
- Ancienne session en cours depuis 24 h : restauration non active sans accumulation de 24 h.
- Changement Scouting → Équilibré : les réglages d'origine restent inchangés.
- Simulations de page cachée : mise en pause générale.
- Simulation d'une fermeture brutale en cours de session v1.11 : restauration en pause avec durées restantes cohérentes.
- Profil Décisions : question visible, défilement activé avec audio désactivé par défaut et « Question suivante » fonctionnel.

## Non validé sur matériel réel

- Comportement exact du service worker lors de la publication GitHub Pages.
- Wake Lock, audio et comportement de l'écran verrouillé sous Brave / Firefox iOS.
- Fluidité et stabilité lors d'une véritable partie longue.
- Mesure objective d'un gain de performance dans AoE2 (l'application n'observe pas le jeu).

## Recommandation après usage

Tester quelques parties avec un **seul profil à la fois**, noter subjectivement si les TCs, l'économie, le scouting et les transitions sont mieux vérifiés, puis comparer avec Équilibré. Ne pas rajouter d'alertes supplémentaires tant que la fréquence des regards et le confort ne sont pas validés.
