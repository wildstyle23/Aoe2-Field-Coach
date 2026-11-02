# AoE2 Field Coach v1.10 — Décisions

## Nouveautés
- Icône de production : **Lucide `swords`**, même pictogramme dans Circuit et Timers, couleur configurable inchangée.
- Troisième mode **Décisions**, disponible dans Paramètres > Mode affiché et sur le sélecteur en portrait.
- Une question ouverte, lisible en paysage, filtrée par âge et catégories, traduite en français, anglais et espagnol.
- Défilement manuel par défaut ; défilement automatique facultatif 90–240 s, pause indépendante, son indépendant désactivé par défaut.
- Banque de 32 questions entièrement locale, ordre pseudo-aléatoire déterministe et anti-répétition, conservation de l'état et des préférences.
- Circuit avant Timers dans le sélecteur, Circuit mode initial pour les nouvelles installations ; anciens choix préservés.
- Timers, Circuit, transitions I–IV et 32 rappels existants préservés.

## Utilisation sur GitHub Pages
Décompresser l'archive ZIP et placer **tous ses fichiers à la racine** du dépôt GitHub Pages : `index.html`, `sw.js`, `manifest.webmanifest`, les icônes et ce document. Commit. Rechargez l'application ; le cache versionné est renouvelé.

## Comportements et limites
- Aucune lecture de l'écran ou des états d'AoE2. L'âge doit être changé manuellement ou via la transition estimée.
- Les questions n'exigent aucune saisie. Le bouton de pause de Décisions n'arrête pas les deux autres modes.
- Défilement automatique et son de Décisions **désactivés** pour les installations nouvelles et migrées.
- Le défilement automatique ne rattrape pas les questions manquées après mise en arrière-plan ; les limitations iOS restent applicables.
- La génération du bip requiert l'autorisation d'AudioContext du navigateur, généralement débloquée après un geste utilisateur.

## Vérifications / projet
- Tests dans Chromium automatisé, fenêtre portrait et paysage. Validation directe iPhone, Brave et Firefox à effectuer.
- Test de migration de la clé `aoe2-field-coach-v19` vers `aoe2-field-coach-v110`.
