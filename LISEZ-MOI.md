# AoE2 Field Coach v1.11.1 — mise à jour ciblée

## Modifications

- **Décisions :** nouveaux intervalles : 5, 10, 15, 20, 30, 45, 60, 75, 90, 105, 120, 150, 180, 240 secondes. Valeur par défaut inchangée : 105 secondes. Le défilement automatique reste désactivé par défaut hors profils qui l'activent déjà.
- **Nom iPhone :** métadonnée Apple et manifeste PWA uniformisés en **AoE2 Field Coach** (sans abréviation).
- **Compatibilité :** migration de stockage depuis la v1.11 et préservation des profils, y compris les configurations enregistrées et les intervalles choisis.
- Aucun changement de fonctionnement des modes **Circuit** et **Timers** ; aucune fonction d'export/import ou mode démonstration ajoutée.

## Publication GitHub Pages

1. Décompresser l’archive ZIP et transférer tous les fichiers à la **racine** du dépôt.
2. Valider le commit et recharger la page après publication.
3. Pour voir le **nouveau nom sur l’icône iPhone**, supprimer l'ancien raccourci de l'écran d'accueil si nécessaire, puis ouvrir le site dans Safari > Partager > Sur l'écran d'accueil > Ajouter. Le changement de nom ne renomme pas toujours un raccourci déjà créé.

Note : 5 secondes est un choix de test, non une cadence recommandée pour une vraie partie. iOS peut suspendre l'app lorsque la page n'est plus visible ; les alertes sonores ne sont pas garanties en arrière-plan.
