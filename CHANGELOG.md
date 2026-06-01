# Changelog

Toutes les modifications notables du projet sont documentées dans ce fichier.

Le format s’inspire de [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).

---

## [2.0.0] - 2026-05-31

### Ajouté

- Ajout d’un champ **Auteur** pour chaque question.
- Remplacement de la valeur générique `Générateur Excel QTI` par l’auteur renseigné dans la saisie.
- Ajout de feedbacks optionnels pour chaque réponse.
- Ajout d’un champ **Explication / correction détaillée** pour chaque question.
- Ajout d’une feuille **Interface_Generation**.
- Ajout d’un tableau de bord dans l’interface de génération.
- Ajout de paramètres visibles pour la génération :
  - auteur par défaut ;
  - nom du fichier XML généré ;
  - nombre maximum de questions ;
  - type de question ;
  - version cible ILIAS.
- Ajout de liens rapides vers les feuilles principales du classeur.
- Ajout d’une procédure de génération directement visible dans le classeur.

### Modifié

- Mise à jour de la feuille `Saisie_Questions` pour intégrer les nouvelles colonnes V2.
- Mise à jour de la feuille technique `Generation`.
- Mise à jour de la feuille `XML_QTI` pour produire un XML enrichi.
- Conservation de la macro existante de génération XML.
- Adaptation de la structure XML pour mieux gérer les feedbacks importés dans ILIAS.
- Réorganisation de l’interface pour rendre le fichier plus lisible et plus facile à utiliser.

### Corrigé

- Correction du message de réparation Excel à l’ouverture du fichier.
- Correction de la table Excel `QuestionsTable`, dont la plage ne correspondait pas correctement au nombre de colonnes déclarées.
- Correction de l’import des feedbacks par réponse dans ILIAS.
- Correction de l’association des feedbacks aux réponses via des identifiants compatibles, par exemple :
  - `response_0`
  - `response_1`
  - `response_2`
  - `response_3`
- Correction de la gestion des réponses incorrectes afin que leurs feedbacks soient également importés.
- Correction du placement de l’explication / correction détaillée pour éviter qu’elle soit rattachée uniquement à la première réponse.

### Notes

- Cette version devient la **V2 officielle** du générateur Excel QTI pour ILIAS.
- Les champs de feedback et d’explication restent optionnels.
- Il est recommandé de tester l’import XML dans un environnement ILIAS de test avant une utilisation en production.

---

## [1.0.0] - Version initiale

### Ajouté

- Création du classeur Excel `.xlsm`.
- Saisie structurée des questions dans Excel.
- Génération d’un XML QTI destiné à l’import dans ILIAS.
- Feuille technique de construction XML.
- Feuille finale `XML_QTI`.
- Macro VBA de génération du fichier XML.
- Bouton **Générer XML** dans le classeur.

### Limitations connues

- Auteur fixe et générique dans le XML.
- Pas de feedback par réponse.
- Pas d’explication ou correction détaillée.
- Interface de génération limitée.
