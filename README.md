# Comparaison de ResNet50 et EfficientNetB0

Ce projet compare deux architectures de réseaux de neurones convolutifs, **ResNet50** et **EfficientNetB0**, pour la classification d’images alimentaires. L’objectif est de mesurer leurs performances sur le même jeu de données et d’observer l’effet du fine-tuning sur EfficientNetB0.

## Protocole expérimental

- Le jeu de données contient trois classes, `corba`, `donat` et `makarna`. Il comprend 960 images d’entraînement, 240 images de validation et 240 images de test.
- Les deux modèles utilisent des poids préentraînés sur ImageNet. Leur base convolutive est d’abord gelée et seule la tête de classification est entraînée pendant 10 époques.
- Pour EfficientNetB0, un second entraînement de 5 époques ajuste une partie des dernières couches de la base préentraînée.
- L’évaluation s’appuie sur l’exactitude sur le jeu de test, les matrices de confusion et les rapports de classification par classe.

## Résultats

| Configuration | Exactitude sur le test |
| --- | ---: |
| ResNet50 avec base gelée | 95,42 % |
| EfficientNetB0 avec base gelée | **96,25 %** |
| EfficientNetB0 après fine-tuning | 95,83 % |

Sur ce jeu de test, EfficientNetB0 avec base gelée obtient le meilleur score, avec 0,83 point de pourcentage d’avance sur ResNet50. Le fine-tuning d’EfficientNetB0 fait baisser son exactitude de 0,42 point dans cette expérience.

## Notebook

Les archives sont fournies dans le dossier [`data/`](data/).

| Archive | Utilisation |
| --- | --- |
| [`food_dataset.zip`](data/food_dataset.zip) | Classification d’images alimentaires |
| [`PH2Dataset.zip`](data/PH2Dataset.zip) | Exercice de segmentation PH2 |

Ouvrir [ResNet and EfficientNet.ipynb](ResNet%20and%20EfficientNet.ipynb) dans Google Colab, puis téléverser les deux archives dans `/content` en conservant leurs noms. Exécuter ensuite les cellules dans l’ordre. Le notebook extrait les archives automatiquement.
