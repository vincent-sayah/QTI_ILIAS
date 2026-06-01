# Générateur Excel QTI pour ILIAS — Version 2

Ce dépôt contient un classeur Excel macro-enabled (`.xlsm`) permettant de générer un fichier XML QTI importable dans ILIAS à partir d’une saisie structurée de questions dans Excel.

La **version 2** enrichit la version initiale avec la gestion de l’auteur, des feedbacks par réponse, des corrections détaillées et une interface de génération plus avancée.

---

## Fichier principal

```text
QTI_ILIAS.xlsm
```

Le classeur contient les feuilles nécessaires à la saisie des questions, au calcul du XML QTI et à la génération du fichier XML final via macro VBA.

---

## Fonctionnalités principales

- Saisie de questions QCU dans Excel.
- Génération automatique d’un fichier XML QTI compatible avec l’import dans ILIAS.
- Bouton de génération XML intégré.
- Recalcul automatique des formules avant export.
- Export des lignes XML non vides depuis la feuille technique `XML_QTI`.

---

## Nouveautés de la version 2

### 1. Auteur de la question

La V2 ajoute une colonne **Auteur** dans la saisie des questions.

Cette information remplace la valeur générique utilisée précédemment :

```text
Générateur Excel QTI
```

Chaque question peut donc maintenant être associée à son auteur réel.

---

### 2. Feedbacks par réponse

La V2 permet de renseigner un feedback optionnel pour chaque proposition de réponse.

Exemple :

| Réponse | Feedback |
|---|---|
| Paris | Bonne réponse : Paris est la capitale de la France. |
| Lyon | Lyon est une grande ville française, mais ce n’est pas la capitale. |
| Marseille | Marseille n’est pas la capitale de la France. |
| Toulouse | Toulouse n’est pas la capitale de la France. |

Les feedbacks restent facultatifs. Si un champ de feedback est vide, il n’est pas nécessaire de le compléter.

---

### 3. Explication ou correction détaillée

Une colonne **Explication / correction détaillée** permet d’ajouter un commentaire global à la question.

Cette explication peut être utilisée pour donner une correction complète après réponse, indépendamment des feedbacks associés à chaque proposition.

---

### 4. Interface de génération améliorée

La V2 ajoute une feuille dédiée :

```text
Interface_Generation
```

Cette feuille fournit :

- les paramètres principaux de génération ;
- le nom du fichier XML généré ;
- le type de question ;
- la version cible ILIAS ;
- un tableau de bord de contrôle ;
- des liens rapides vers les feuilles importantes ;
- une procédure de génération rappelée directement dans le classeur.

---

## Feuilles du classeur

### `Saisie_Questions`

Feuille principale de saisie.

Elle contient les informations nécessaires à la génération des questions :

- identifiant ou numéro de question ;
- titre ;
- énoncé ;
- propositions de réponses ;
- score ou indicateur de bonne réponse ;
- auteur ;
- feedbacks par réponse ;
- explication / correction détaillée ;
- colonne de contrôle.

### `Generation`

Feuille technique utilisée pour construire les blocs XML intermédiaires.

Cette feuille ne doit généralement pas être modifiée manuellement.

### `XML_QTI`

Feuille contenant les lignes XML finales qui seront exportées par la macro.

La macro lit les lignes non vides de cette feuille pour créer le fichier XML.

### `Interface_Generation`

Nouvelle interface de pilotage introduite en V2.

Elle sert de point d’entrée pour vérifier les paramètres, contrôler les données et accéder rapidement aux feuilles utiles.

---

## Utilisation

1. Ouvrir le fichier `QTI_ILIAS.xlsm` dans Microsoft Excel.
2. Activer les macros si Excel le demande.
3. Aller dans la feuille `Saisie_Questions`.
4. Compléter les questions et les réponses.
5. Renseigner, si nécessaire :
   - l’auteur ;
   - les feedbacks par réponse ;
   - l’explication ou correction détaillée.
6. Vérifier que la colonne de contrôle indique que les lignes sont valides.
7. Cliquer sur le bouton **Générer XML**.
8. Importer le fichier XML généré dans ILIAS.

---

## Conseils de saisie

- Éviter les caractères spéciaux non nécessaires dans les identifiants.
- Compléter au minimum le titre, l’énoncé, les réponses et la bonne réponse.
- Laisser les champs optionnels vides lorsqu’ils ne sont pas utiles.
- Vérifier les feedbacks dans ILIAS après import.
- Conserver une copie du fichier `.xlsm` avant toute modification importante.

---

## Import dans ILIAS

Après génération du fichier XML :

1. Se connecter à ILIAS.
2. Aller dans le test ou le pool de questions cible.
3. Utiliser la fonction d’import QTI.
4. Sélectionner le fichier XML généré.
5. Contrôler quelques questions importées, notamment :
   - l’énoncé ;
   - les réponses ;
   - les bonnes réponses ;
   - les feedbacks par réponse ;
   - les feedbacks/corrections générales.

---

## Corrections intégrées après validation V2

La version V2 finale corrige deux problèmes identifiés lors des tests :

### Correction ouverture Excel

La table Excel `QuestionsTable` a été corrigée afin d’éviter le message de réparation à l’ouverture du fichier.

### Correction import feedbacks ILIAS

Les feedbacks par réponse ont été ajustés pour être correctement reportés dans l’édition de la question après import dans ILIAS.

Les identifiants de réponse utilisés dans le XML suivent maintenant une forme compatible avec ILIAS, par exemple :

```text
response_0
response_1
response_2
response_3
```

---

## Prérequis

- Microsoft Excel avec prise en charge des macros VBA.
- Macros activées à l’ouverture du fichier.
- ILIAS avec fonction d’import QTI disponible.

---

## Sécurité

Le fichier contient une macro VBA destinée uniquement à exporter le XML généré depuis la feuille `XML_QTI`.

Avant utilisation en production :

- vérifier le code VBA si nécessaire ;
- conserver une copie originale du classeur ;
- tester l’import XML sur un environnement ILIAS de test.

---

## Version

```text
Version : 2.0
Statut  : validée après correction des bugs d’ouverture Excel et de feedbacks ILIAS
```

---

## Auteur

Vincent Sayah
