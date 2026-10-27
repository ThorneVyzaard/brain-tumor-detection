# Détection de tumeurs cérébrales à partir d’images IRM

Application web développée avec **Flask** et un modèle de deep learning **TensorFlow/Keras**. Elle permet de téléverser une image IRM du cerveau et d’afficher la classe prédite par le modèle, ainsi qu’une recommandation informative.

> **Avertissement médical :** ce projet est destiné à l’apprentissage et à la démonstration. Il n’est pas un dispositif médical validé et ne doit pas être utilisé pour établir un diagnostic, guider un traitement ou remplacer l’avis d’un professionnel de santé.

## Classes prédites

Le modèle renvoie l’une des quatre classes suivantes :

| Classe | Signification |
|---|---|
| `glioma` | Gliome |
| `meningioma` | Méningiome |
| `pituitary` | Tumeur hypophysaire |
| `notumor` | Classe « aucune tumeur » selon le modèle |

La prédiction est une sortie du modèle et ne constitue pas une conclusion médicale.

## Fonctionnalités

- Téléversement d’une image IRM depuis l’interface web.
- Analyse de l’image par le modèle entraîné `brain_tumor_model_final.h5`.
- Affichage de la classe prédite et de l’image envoyée.
- Affichage d’une recommandation informative associée au résultat.

## Technologies utilisées

- Python 3
- Flask
- TensorFlow / Keras
- NumPy
- Pillow

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

Le dossier `static/` contient les ressources statiques de l’application, et `templates/` contient les pages HTML rendues par Flask.

## Installation et lancement

### 1. Prérequis

- Python installé dans une version compatible avec TensorFlow.
- Git, si vous clonez le projet depuis GitHub.
- Git LFS, si le modèle est hébergé dans le dépôt avec Git Large File Storage.

### 2. Récupérer le projet

Si vous utilisez GitHub :

```bash
git clone https://github.com/ThorneVyzaard/brain-tumor-detection.git
cd brain-tumor-detection
```

Remplacez l’URL par celle de votre dépôt. Si vous avez déjà le dossier du projet sur votre ordinateur, ouvrez un terminal dans ce dossier et passez à l’étape suivante.

### 3. Créer et activer un environnement virtuel (recommandé)

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

### 4. Installer les dépendances

```bash
python -m pip install --upgrade pip
pip install flask tensorflow numpy pillow
```

### 5. Vérifier le fichier du modèle

Vérifiez que `brain_tumor_model_final.h5` se trouve à l’emplacement attendu par `app.py`. Si vous clonez le dépôt et que le modèle est stocké avec Git LFS, installez Git LFS avant de cloner ou exécutez `git lfs pull` dans le dossier du projet.

### 6. Lancer l’application

```bash
python app.py
```

Ouvrez ensuite votre navigateur à l’adresse suivante :

<http://127.0.0.1:5000>

Pour arrêter le serveur, revenez au terminal et appuyez sur `Ctrl + C`.

## Utilisation

1. Lancez l’application et ouvrez `http://127.0.0.1:5000` dans un navigateur.
2. Cliquez sur **Choisir une image IRM** et sélectionnez une image prise en charge par l’application.
3. Cliquez sur **Analyser l’image**.
4. Consultez la classe prédite et les informations affichées par l’interface.

Utilisez uniquement des images que vous êtes autorisé à utiliser. Ne téléversez pas d’images médicales identifiables dans un dépôt public.

## Fichier du modèle et Git LFS

Le fichier `brain_tumor_model_final.h5` fait environ 130 Mo. Pour l’inclure dans le dépôt GitHub, utilisez **Git LFS** plutôt que le suivi Git classique. Avant le premier commit, depuis la racine du projet, exécutez :

```bash
git lfs install
git lfs track "*.h5"
git add .gitattributes
```

Ajoutez ensuite les fichiers du projet et créez le commit. Le fichier `.gitattributes` doit être versionné afin que Git LFS sache quels fichiers suivre.

## Limites et transparence

- Les performances du modèle dépendent notamment des données d’entraînement, du prétraitement des images et des données utilisées pour l’évaluation.
- Ce README ne présente pas de métriques de performance vérifiées. Ajoutez des résultats mesurés sur un jeu de test indépendant si vous en disposez (par exemple, précision, rappel/sensibilité, spécificité, F1-score et matrice de confusion).
- Une prédiction erronée est possible, y compris lorsqu’un résultat semble très convaincant.

## Licence

Aucune licence n’est indiquée pour le moment. Ajoutez un fichier `LICENSE` si vous souhaitez préciser les conditions de réutilisation du code et vérifier séparément les licences du jeu de données et du modèle.
