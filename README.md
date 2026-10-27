# Détection des tumeurs cérébrales par IRM

Application web qui analyse une image IRM du cerveau et prédit une des classes suivantes :

- **glioma** — gliome
- **meningioma** — méningiome
- **pituitary** — tumeur hypophysaire
- **notumor** — aucune tumeur détectée

Le modèle de deep learning (`brain_tumor_model_final.h5`) est chargé au démarrage. L’interface permet d’envoyer une image, d’afficher la prédiction et une recommandation informative.

> **Important :** cet outil est un projet pédagogique. Il ne remplace pas un diagnostic médical. Toute décision clinique doit être prise par un professionnel de santé.

## Technologies

- Python
- Flask
- TensorFlow / Keras
- NumPy

## Prérequis

- Python 3 installé
- Les bibliothèques nécessaires, par exemple :

```bash
pip install flask tensorflow numpy pillow
```

Le fichier du modèle `brain_tumor_model_final.h5` doit se trouver dans le dossier `projet`.

## Utilisation

1. Ouvrir l’invite de commandes (**cmd**).

2. Aller dans le dossier du projet (dossier parent, puis `projet`) :

```bash
cd "C:\Users\Mohamed\Documents\Nouveau dossier (3)\projet"
```

Adaptez le chemin si le projet est ailleurs.

3. Lancer l’application :

```bash
python app.py
```

4. Ouvrir un navigateur et aller à l’adresse :

```
http://127.0.0.1:5000
```

5. Cliquer sur **Choisir une image IRM** et sélectionner une image de tumeur cérébrale. Vous pouvez utiliser une image du dossier d’entraînement (**Training**), si vous l’avez dans le projet.

6. Cliquer sur **Analyser l'image**.

7. Consulter le résultat : la classe prédite, l’image envoyée, et la recommandation associée.

Pour arrêter le serveur, revenez dans le cmd et appuyez sur `Ctrl + C`.
