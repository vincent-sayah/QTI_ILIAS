# Documentation technique — QTI_ILIAS V2.0.1

## 1. Objet

La version 2.0.1 du générateur Excel QTI pour ILIAS augmente la capacité maximale de génération de **100 à 200 questions**.

Cette version corrige également une anomalie détectée lors des tests : malgré l’extension visuelle du classeur, le XML généré ne contenait que 100 questions. La cause était la présence de lignes doublons vides et de plages/formules non correctement alignées sur les lignes 105 à 204.

## 2. Périmètre de la modification

La modification concerne le classeur :

```text
QTI_ILIAS.xlsm
```

Les feuilles concernées sont :

- `Saisie_Questions` ;
- `Generation` ;
- `XML_QTI` ;
- `Interface_Generation`.

Les macros VBA sont conservées à l’identique.

## 3. Modification de la table de saisie

La table Excel structurée `QuestionsTable` est redimensionnée.

Ancienne plage :

```text
A4:Y104
```

Nouvelle plage :

```text
A4:Y204
```

La ligne 4 correspond à l’en-tête du tableau.

Les lignes 5 à 204 correspondent aux 200 lignes de saisie disponibles.

## 4. Extension des formules

Les formules de calcul et de génération ont été étendues pour couvrir toutes les questions jusqu’à la ligne 204.

### Feuille `Saisie_Questions`

Les formules et contrôles nécessaires à la validation des questions ont été propagés jusqu’à la ligne 204.

### Feuille `Generation`

La feuille technique `Generation` a été étendue afin de produire les blocs XML intermédiaires pour les questions 101 à 200.

### Feuille `XML_QTI`

La feuille `XML_QTI` a été étendue afin que les lignes XML finales générées prennent en compte les questions 101 à 200.

## 5. Correction des doublons de lignes

Lors du premier passage à 200 questions, les lignes 105 à 204 existaient en double dans certaines feuilles.

Les premières occurrences étaient vides, ce qui provoquait l’arrêt effectif de la génération XML à 100 questions.

La version 2.0.1 corrige ce point en supprimant les doublons vides et en conservant uniquement les lignes utiles avec les bonnes formules.

## 6. Compteurs et contrôles

Les plages de contrôle ont été adaptées.

Ancienne plage :

```text
O5:O104
```

Nouvelle plage :

```text
O5:O204
```

Cela permet de compter et contrôler correctement les 200 lignes de questions potentielles.

## 7. Interface utilisateur

La feuille `Interface_Generation` a été mise à jour pour afficher :

```text
Maximum questions : 200
```

La notice utilisateur mentionne également la nouvelle capacité maximale de 200 questions.

## 8. Génération QTI

La génération XML repose toujours sur la feuille `XML_QTI`.

La macro exporte les lignes XML non vides afin de produire le fichier QTI importable dans ILIAS.

La version 2.0.1 garantit que les questions valides situées après la ligne 104 sont intégrées dans le fichier XML généré.

## 9. Compatibilité

La version 2.0.1 conserve la compatibilité fonctionnelle avec les usages de la version 2.0.0 :

- questions QCU ;
- auteur par question ;
- feedbacks par réponse ;
- explication / correction détaillée ;
- génération XML QTI pour import dans ILIAS.

## 10. Validation

Les tests réalisés ont permis de valider :

- la saisie de plus de 100 questions ;
- la génération d’un XML contenant plus de 100 questions ;
- l’import dans ILIAS avec plus de 100 questions ;
- la conservation des macros VBA.

## 11. Points d’attention

- Ne pas dépasser 200 questions dans une génération.
- Ne pas supprimer ou déplacer les feuilles techniques `Generation` et `XML_QTI`.
- Ne pas redimensionner manuellement `QuestionsTable` sans adapter les formules associées.
- Tester l’import dans un environnement ILIAS de recette avant un usage en production.

## 12. Synthèse technique

| Élément | Version 2.0.0 | Version 2.0.1 |
|---|---:|---:|
| Nombre maximum de questions | 100 | 200 |
| Plage `QuestionsTable` | `A4:Y104` | `A4:Y204` |
| Plage de contrôle | `O5:O104` | `O5:O204` |
| Génération au-delà de 100 questions | Non validée | Validée |
| Macros VBA | Conservées | Conservées |

## 13. Version

```text
Version : 2.0.1
Date    : 2026-07-02
Statut  : validée
```
