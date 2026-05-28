# QTI_ILIAS
Générateur Excel avec macro VBA permettant de créer automatiquement un fichier XML QTI compatible ILIAS 8 à partir de questions QCU saisies dans un tableau.

# Générateur QTI ILIAS 8 — QCU uniquement

Ce projet fournit un fichier Excel macro-compatible permettant de générer automatiquement un fichier XML QTI importable dans ILIAS 8.

La version actuelle prend uniquement en charge les questions de type **QCU** : Question à Choix Unique.

## Objectif

L’objectif est de permettre à un utilisateur de saisir des questions dans un fichier Excel, puis de générer automatiquement un fichier XML prêt à être importé dans ILIAS 8.

Le fichier Excel permet de renseigner :

- l’intitulé de la question ;
- plusieurs réponses possibles ;
- la bonne réponse ;
- la pondération de la question ;
- puis de générer un fichier XML via un bouton.

## Fichier fourni

Le fichier principal du projet est :

```text
generateur_qti_ilias8_qcu_uniquement_bouton_gauche.xlsm
```

Il s’agit d’un fichier Excel avec macros VBA.

## Fonctionnalités

- Saisie simple des questions dans Excel.
- Gestion des questions QCU uniquement.
- Jusqu’à 8 réponses possibles par question.
- Définition de la bonne réponse par numéro.
- Définition de la pondération de chaque question.
- Bouton **Générer XML** placé au début de la feuille.
- Génération automatique d’un fichier XML QTI.
- XML destiné à l’import dans ILIAS 8.

## Structure du fichier Excel

Le classeur contient notamment :

- `Mode_emploi` : instructions d’utilisation ;
- `Saisie_Questions` : feuille principale de saisie ;
- `XML_QTI` : feuille de génération XML ;
- `Generation` : feuille technique utilisée par les formules et la macro.

## Utilisation

1. Télécharger le fichier `.xlsm`.
2. Ouvrir le fichier avec Microsoft Excel.
3. Activer les macros si Excel le demande.
4. Aller dans la feuille `Saisie_Questions`.
5. Compléter les colonnes nécessaires :
   - question ;
   - réponses ;
   - bonne réponse ;
   - pondération.
6. Cliquer sur le bouton **Générer XML**.
7. Le fichier XML est généré automatiquement dans le même dossier que le fichier Excel.

Le fichier généré s’appelle :

```text
qti_ilias8.xml
```

## Format attendu pour la bonne réponse

Pour une question QCU, la bonne réponse doit être indiquée par un seul numéro.

Exemple :

```text
1
```

Cela signifie que la réponse 1 est la bonne réponse.

## Exemple de saisie

| Question | Réponse 1 | Réponse 2 | Réponse 3 | Bonne réponse | Pondération |
|---|---|---|---|---|---|
| Quelle est la capitale de la France ? | Paris | Lyon | Marseille | 1 | 1 |

## Import dans ILIAS 8

Une fois le fichier `qti_ilias8.xml` généré :

1. Se connecter à ILIAS 8.
2. Aller dans un pool de questions ou un test.
3. Utiliser la fonction d’import.
4. Sélectionner le fichier XML généré.
5. Vérifier les questions importées.

## Sécurité des macros Excel

Le fichier utilise une macro VBA pour générer le fichier XML.

Selon la configuration de sécurité d’Excel, les macros peuvent être bloquées au premier lancement.

Pour débloquer le fichier :

1. Fermer Excel.
2. Faire clic droit sur le fichier `.xlsm`.
3. Cliquer sur **Propriétés**.
4. Cocher **Débloquer** si l’option est présente.
5. Cliquer sur **Appliquer**, puis **OK**.
6. Rouvrir le fichier Excel.
7. Activer les macros.

## Compatibilité

Testé pour une génération XML destinée à ILIAS 8.

La compatibilité peut dépendre de la configuration exacte d’ILIAS et du mode d’import utilisé. Il est recommandé de tester l’import avec quelques questions avant un import massif.

## Limitations de la version actuelle

- Seules les questions de type QCU sont prises en charge.
- Les questions QCM ne sont pas prises en charge dans cette version.
- Le fichier nécessite Microsoft Excel avec macros activées.
- La génération XML se fait localement via VBA.

## Évolutions possibles

Fonctionnalités envisagées pour de futures versions :

- prise en charge des QCM ;
- génération d’un package ZIP compatible import ILIAS ;
- ajout de feedbacks par réponse ;
- ajout d’explications ou corrections détaillées ;
- gestion des catégories ;
- contrôle renforcé avant génération XML ;
- interface de génération plus avancée.

## Licence

À compléter selon le choix du propriétaire du projet.

Exemples possibles :

- MIT
- GPL-3.0
- Apache-2.0
- Licence privée

## Auteur

Projet de génération de questions QTI pour ILIAS 8 à partir d’un fichier Excel.

