# Reconnaissance de l'Écriture Manuscrite avec BiLSTM

## Description
Ce projet explore l'utilisation des réseaux de neurones BiLSTM pour la reconnaissance de l'écriture manuscrite à partir d'images. L'objectif principal est de créer un système efficace qui capture les dépendances temporelles et contextuelles dans des séquences manuscrites pour convertir des images en texte.

---

## Objectifs
- Reconnaître et convertir des textes manuscrits en texte numérique.
- Exploiter les BiLSTM pour capturer le contexte à la fois dans les directions avant et arrière.
- Développer un modèle robuste pour des applications pratiques, telles que :
  - Lecture automatique de documents manuscrits (archives, formulaires, notes médicales).
  - Digitalisation et indexation de contenus manuscrits.

---

## Défis et Avantages
### Défis :
- Variabilité interindividuelle (style, taille, inclinaison).
- Présence de bruit dans les images (résolution, ombres).
### Avantages des BiLSTM :
- Gestion efficace des séquences temporelles.
- Capture du contexte bidirectionnel.

---

## Dataset
- **Source** : [IAM Handwriting Database](https://www.iam.unibe.ch/fki/databases/iam-handwriting-database).
- **Préparation** :
  - Téléchargement et extraction des données.
  - Organisation à partir du fichier `words.txt`.
  - Nettoyage des données pour exclure les images manquantes ou erronées.
- **Prétraitement** :
  - Redimensionnement des images à (32x128), conversion en niveaux de gris et normalisation.
  - Encodage des étiquettes en indices numériques.
  - Stockage des données dans des fichiers Numpy prêts pour l'entraînement.

---

## Architecture du Modèle
1. **Extraction des Caractéristiques** :
   - Trois couches convolutionnelles avec filtres de taille 3x3.
   - Max pooling (2x2) pour réduire la dimension spatiale.
2. **Transformation en Séquences** :
   - Conversion des caractéristiques en séquences temporelles via une couche de reshape.
3. **BiLSTM** :
   - Deux couches LSTM bidirectionnelles pour capturer les dépendances contextuelles.
4. **Prédictions** :
   - Une couche TimeDistributed Dense avec activation softmax pour prédire les caractères.

---

## Entraînement
- **Précision** :
  - Précision d’entraînement proche de 100%.
  - Précision de validation stabilisée à environ 70%.
- **Perte** :
  - Perte d’entraînement en diminution régulière.
  - Perte de validation fluctuante, suggérant un surapprentissage potentiel.

---

## Résultats et Discussion
### Performances :
- Bonne reconnaissance des mots simples et courts.
- Résistance aux variations mineures dans les images.
### Limites :
- Difficulté avec des mots longs, bruités ou mal alignés.
- Performances affectées par des caractères ou styles inhabituels.
### Pistes d'Amélioration :
- Augmentation des données avec des transformations d’images.
- Intégration de données multilingues et variées.
- Optimisation des hyperparamètres.
- Exploration de modèles avancés comme les Transformers.

---

## Conclusion
Ce projet met en lumière les capacités des BiLSTM pour la reconnaissance manuscrite, tout en soulignant l'importance de la qualité et de la diversité des données. Des améliorations futures incluront l'enrichissement des datasets et l'exploration de nouvelles architectures.

---

## Prérequis
- Python 3.8+
- Bibliothèques :
  - TensorFlow/Keras
  - NumPy, Pandas
  - Matplotlib, scikit-learn

---

## Installation
1. Clonez ce dépôt :
   ```bash
   git clone https://github.com/BarbaraRacha/Mini-Projet-Handwriting-Recognition-with-BiLSTM.git
