# AoE2 Field Coach v1.8

## Changements v1.8
- Mode Circuit, présentation **6 rectangles** : suppression du texte bas pour gagner de l’espace.
- Grille 3 colonnes × 2 lignes conservée, avec carrés agrandis.
- Noms dans les rectangles agrandis.
- Icône **Production** redessinée pour être plus lisible.

## Audit synthétique orienté objectif de l’app
Objectif central : entraîner des automatismes et un "tour des yeux" sans détourner l’attention du jeu.

### Ce qui fonctionne très bien
1. **Placement sous la minimap** : excellent, car l’app devient un point d’ancrage vers la carte.
2. **Séparation Timers / Circuit** : pertinente, car les deux modes servent des objectifs différents.
3. **Couleurs personnalisables** : très utiles pour construire des réflexes visuels stables.
4. **Profils par âge + rappels contextuels** : bonne aide mémoire sans dépendance au jeu.
5. **Vue paysage minimaliste** : cohérente avec l’usage en partie.

### Priorités d’amélioration recommandées
1. **Présets de circuit** : proposer des ordres prédéfinis (Macro, Scout-heavy, Army-heavy).
2. **A/B testing du rythme** : conserver quelques profils 4s / 5s / 6s par étape.
3. **Mode "entraînement" puis "entretien"** : mêmes couleurs, mais glow plus discret une fois les automatismes acquis.
4. **Optimisation batterie / fluidité** : le rendu actuel est déjà léger, mais un rafraîchissement adaptatif pourrait encore réduire la charge.
5. **Mode test intégré** : bouton pour lancer une boucle de démonstration de 30 secondes sans démarrer une vraie session.

### Risques UX à surveiller
- Trop de rappels contextuels = perte d’attention.
- Cadence trop rapide du circuit = regard attiré vers l’iPhone au lieu du jeu.
- Trop de couleurs proches = perte d’association mentale.

### Recommandations concrètes d’usage
- Démarrer avec **Circuit guidé 5–6 s** par étape.
- Garder des couleurs très distinctes pour Villageois / Économie / Maisons / Production / Carte / Scout.
- Utiliser les Timers surtout comme deuxième couche, pas comme mode principal si le but est l’automatisme visuel.

### Prochaines optimisations possibles
- Présets exportables/importables.
- Intensité du glow réglable.
- Historique léger de session (ex. nombre de tours réalisés), uniquement local.
- Option de duplication d’un ordre de cadrans entre les âges.
