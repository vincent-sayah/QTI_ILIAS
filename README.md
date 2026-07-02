# Générateur Excel QTI pour ILIAS — Version 2.0.1

Ce dépôt contient un classeur Excel macro-enabled (`.xlsm`) permettant de générer un fichier XML QTI importable dans ILIAS à partir d’une saisie structurée de questions dans Excel.

La **version 2.0.1** conserve les fonctionnalités de la V2 et ajoute la possibilité de générer jusqu’à **200 questions** dans un même fichier XML QTI.

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
- Prise en charge de **200 questions maximum**.
- Bouton de génération XML intégré.
- Recalcul automatique des formules avant export.
- Export des lignes XML non vides depuis la feuille technique `XML_QTI`.
- Gestion d’un auteur par question.
- Gestion des feedbacks par réponse.
- Gestion d’une explication ou correction détaillée par question.

---

## Nouveautés de la version 2.0.1

### Passage à 200 questions

La version 2.0.1 augmente la capacité maximale du classeur de **100 à 200 questions**.

Les éléments suivants ont été étendus :

- table Excel `QuestionsTable` ;
- feuille `Saisie_Questions` ;
- feuille technique `Generation` ;
- feuille finale `XML_QTI` ;
- compteurs et contrôles de génération ;
- interface de génération.

### Correction de la génération au-delà de 100 questions

Une anomalie empêchait la génération effective des questions au-delà de la question 100.

La correction supprime les lignes doublons vides 105 à 204 et garantit que les questions 101 à 200 sont bien reprises dans le XML QTI généré.

---

## Fonctionnalités de la version 2

### Auteur de la question

La V2 ajoute une colonne **Auteur** dans la saisie des questions.

Cette information remplace la valeur générique utilisée précédemment :

```text
Générateur Excel QTI
```

Chaque question peut donc maintenant être associée à son auteur réel.

### Feedbacks par réponse

La V2 permet de renseigner un feedback optionnel pour chaque proposition de réponse.

Exemple :

| Réponse | Feedback |
|---|---|
| Paris | Bonne réponse : Paris est la capitale de la France. |
| Lyon | Lyon est une grande ville française, mais ce n’est pas la capitale. |
| Marseille | Marseille n’est pas la capitale de la France. |
| Toulouse | Toulouse n’est pas la capitale de la France. |

Les feedbacks restent facultatifs. Si un champ de feedback est vide, il n’est pas nécessaire de le compléter.

### Explication ou correction détaillée

Une colonne **Explication / correction détaillée** permet d’ajouter un commentaire global à la question.

Cette explication peut être utilisée pour donner une correction complète après réponse, indépendamment des feedbacks associés à chaque proposition.

### Interface de génération améliorée

La V2 ajoute une feuille dédiée :

```text
Interface_Generation
```

Cette feuille fournit :

- les paramètres principaux de génération ;
- le nom du fichier XML généré ;
- le type de question ;
- la version cible ILIAS ;
- le nombre maximum de questions ;
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

La table `QuestionsTable` est dimensionnée sur la plage :

```text
A4:Y204
```

Cela correspond à une ligne d’en-tête et à 200 lignes de saisie.

### `Generation`

Feuille technique utilisée pour construire les blocs XML intermédiaires.

Cette feuille ne doit généralement pas être modifiée manuellement.

### `XML_QTI`

Feuille contenant les lignes XML finales qui seront exportées par la macro.

La macro lit les lignes non vides de cette feuille pour créer le fichier XML.

### `Interface_Generation`

Interface de pilotage introduite en V2.

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

- Ne pas dépasser 200 questions par génération.
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

La version 2.0.1 a été validée avec un fichier généré contenant plus de 100 questions importées dans ILIAS.

---

## Documentation technique

La documentation technique spécifique à la version 2.0.1 est disponible dans :

```text
Doc/Doc_tech_V2.0.1.md
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
Version : 2.0.1
Statut  : validée avec génération et import ILIAS de plus de 100 questions
Capacité : 200 questions maximum
```

---

## Auteur

Vincent Sayah
