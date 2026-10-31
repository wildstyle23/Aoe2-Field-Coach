# AoE2 Field Coach — v1.5

Mise à jour visuelle et ergonomique de la v1.4, spécialement pour l'iPhone à l'horizontale.

## Nouveautés

- **Anneaux de progression et pictogrammes agrandis en paysage**. La taille suit la hauteur disponible et reste contrainte par la largeur de chaque cadran pour ne pas masquer les noms ou les compteurs.
- **Positionnement indépendant pour chaque âge** : Paramètres → **Ordre et position des cadrans** → âge I, II, III ou IV. Chaque emplacement (1 à 4, de gauche à droite) propose une liste de cadrans ; les boutons **← / →** échangent deux positions, sans glisser-déposer.
- **Choix du contenu parmi tous les timers activés pour l'âge sélectionné**. Si plus de quatre timers sont demandés, les quatre choisis sont affichés, les autres continuent de fonctionner sous forme de messages temporaires.
- **Conservation des dispositions entre les sessions** sur le même navigateur/app installée. La sauvegarde est locale (`localStorage`).
- **Migration des réglages de v1.4** : modes, couleurs, glow, préférences des 32 rappels, profils d'âge, fréquences et messages. Les sessions en cours ne sont pas poursuivies lors d'une migration, afin de ne pas déclencher d'alertes obsolètes.
- **Retour aux cadrans en paysage** après fermeture des paramètres, sans laisser involontairement la barre de commandes ouverte.

Les quatre cadrans maximum, les transitions automatiques, le mode Auto, les rappels d'infrastructure et l'anti-flood de la v1.4 restent inchangés.

## Changer l'ordre

1. Ouvrir les **paramètres** depuis les commandes de l'application.
2. Descendre jusqu'à **Ordre et position des cadrans**.
3. Choisir l'âge à personnaliser (I, II, III, IV).
4. Sélectionner un timer dans l'une des **positions 1–4** ou utiliser les flèches **← / →** pour le déplacer.
5. Recommencer pour les autres âges, puis appuyer sur **Terminé**.

Les positions suivent l'ordre **gauche → droite**. Les emplacements sans cadran ne sont pas conservés comme espaces vides : s'il y a trois cadrans actifs, ceux-ci occupent équitablement l'écran. Pour afficher un cadran supplémentaire, l'activer en mode **Cadran permanent** pour l'âge concerné dans la bibliothèque.

## Mise à jour GitHub Pages

1. Décompresser `AoE2-Field-Coach-iPhone-v1.5.zip`.
2. Remplacer les fichiers à la racine du dépôt existant : `index.html`, `sw.js`, `manifest.webmanifest`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png` et, si souhaité, `LISEZ-MOI.md`.
3. Valider le commit GitHub ; l'URL GitHub Pages ne change pas.
4. Une fois le déploiement effectué, rouvrir ou actualiser l'application sur l'iPhone. Le cache de service worker porte désormais le nom `aoe2-fieldcoach-v1.5`.

Le fichier HTML autonome `AoE2-Field-Coach-iPhone-v1.5.html` est fourni séparément pour les essais sur ordinateur.

## Validation

Tests de navigateur automatisés : écran paysage 852×393 et 668×290, portrait 393×852, sélection et échange de cadrans, stockage et restauration de l'ordre, changement d'âge, conservation des réglages v1.4, absence d'erreurs JavaScript. **Pas encore testé directement sur Firefox ou Brave iOS.**

L'application est autonome sur iPhone : elle ne communique pas avec Age of Empires II et ne peut pas détecter si une action du jeu a réellement été effectuée. Le passage automatique à l'âge suivant demeure une estimation.
