# Détection de tumeurs cérébrales à partir d’images IRM

Cette application web permet de soumettre une image IRM du cerveau et d’obtenir une prédiction produite par un modèle de deep learning entraîné pour distinguer quatre classes. L’application affiche la classe prédite et les informations associées dans l’interface.

> **Avertissement médical** : ce projet est destiné à l’apprentissage et à la démonstration. Il ne s’agit pas d’un dispositif médical validé. Les résultats ne doivent pas être utilisés pour établir un diagnostic, choisir un traitement ou remplacer l’avis d’un professionnel de santé.

## Classes disponibles

| Classe prédite | Signification |
|---|---|
| `glioma` | Gliome |
| `meningioma` | Méningiome |
| `pituitary` | Tumeur hypophysaire |
| `notumor` | Classe « aucune tumeur » selon le modèle |

Ces classes représentent les sorties possibles du modèle, et non un diagnostic médical.

## Fonctionnalités

- Téléverser une image IRM depuis l’interface web.
- Analyser l’image à l’aide du modèle entraîné.
- Afficher l’image envoyée et la classe prédite.
- Consulter les informations affichées par l’application pour le résultat obtenu.

## Dataset utilisé

Ce projet utilise le dataset **[Brain Tumor MRI Dataset — Masoud Nickparvar](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)**, disponible sur Kaggle. Il regroupe des images IRM classées en quatre catégories : `glioma`, `meningioma`, `pituitary` et `notumor`.

### Télécharger le dataset

1. Ouvrez la [page du dataset sur Kaggle](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset) et connectez-vous à Kaggle si nécessaire.
2. Cliquez sur **Download** pour télécharger l’archive.
3. Décompressez l’archive sur votre ordinateur. Le dataset est généralement organisé en dossiers `Training/` et `Testing/`, chacun contenant les sous-dossiers des quatre classes.

Le dataset n’est pas inclus dans ce dépôt GitHub. **Il n’est pas nécessaire de le télécharger pour lancer l’application et effectuer une prédiction** : le dépôt fournit le modèle déjà entraîné. Le dataset est utile si vous souhaitez étudier les images ou reproduire un entraînement. Consultez la page Kaggle pour les conditions d’utilisation et d’attribution applicables.

## Technologies

- Python 3
- Flask
- TensorFlow / Keras
- NumPy
- Pillow

## Prérequis

- Une installation de Python compatible avec la version de TensorFlow utilisée.
- Git pour récupérer le projet depuis GitHub.
- Git LFS pour télécharger le fichier du modèle stocké avec Git Large File Storage.

## Installation et lancement

### 1. Récupérer le projet

Installez [Git LFS](https://git-lfs.com/) si nécessaire, puis exécutez :

```bash
git lfs install
git clone https://github.com/ThorneVyzaard/brain-tumor-detection.git
cd brain-tumor-detection
git lfs pull
```

La commande `git lfs pull` permet de récupérer les fichiers volumineux suivis par Git LFS, notamment le modèle. Le fichier `brain_tumor_model_final.h5` doit être présent à l’emplacement attendu par l’application.

Si vous avez déjà téléchargé le projet, ouvrez simplement un terminal dans le dossier qui contient `app.py`.

### 2. Créer un environnement virtuel (recommandé)

**Windows (cmd) :**

```bat
python -m venv .venv
.venv\Scripts\activate
```

**macOS / Linux :**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Installer les dépendances

```bash
python -m pip install --upgrade pip
python -m pip install flask tensorflow numpy pillow
```

Selon votre version de Python et votre système, il peut être nécessaire d’utiliser des versions de TensorFlow et de Python compatibles entre elles.

### 4. Démarrer l’application

Depuis le dossier qui contient `app.py`, lancez :

```bash
python app.py
```

Ouvrez ensuite cette adresse dans votre navigateur : <http://127.0.0.1:5000>

Pour arrêter l’application, revenez au terminal et appuyez sur `Ctrl + C`.

## Comment utiliser l’application

1. Démarrez l’application et ouvrez <http://127.0.0.1:5000>.
2. Cliquez sur **Choisir une image IRM**.
3. Sélectionnez une image prise en charge par l’application.
4. Cliquez sur **Analyser l’image**.
5. Consultez la classe prédite et les informations affichées.

Utilisez uniquement des images que vous êtes autorisé à utiliser. Évitez de téléverser ou de partager des images médicales contenant des informations permettant d’identifier une personne.

## Structure du projet

```text
brain-tumor-detection/
├── app.py
├── brain_tumor_model_final.h5
├── README.md
├── static/
└── templates/
    └── index.html
```

## Limites

- Les performances dépendent notamment des données d’entraînement, du prétraitement et des données d’évaluation.
- Une prédiction erronée est possible.
- Aucune métrique de performance vérifiée n’est fournie ici. Les résultats doivent être évalués sur un jeu de test indépendant avant toute conclusion sur la qualité du modèle.

## Licence

Aucune licence de réutilisation n’est précisée dans ce dépôt. Vérifiez les droits applicables au code, au modèle et aux données avant de les redistribuer ou de les réutiliser.
