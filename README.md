# D-tection_Cancer_C-r-bral_CNN

Description
-----------
Projet de classification d'images médicales pour détecter et classer les tumeurs cérébrales (glioma, meningioma, pituitary) et les coupes sans tumeur (notumor) à l'aide d'un modèle CNN.

Le notebook principal `data.ipynb` contient le pipeline de préparation des données :
- lecture et nettoyage des images
- redimensionnement à 224x224
- visualisation et analyse des classes
- rééquilibrage (augmentation) et sauvegarde du dataset équilibré (`Data_Balanced`)
- encodage des labels et normalisation
- séparation train/test
- définition, entraînement et évaluation d'un modèle CNN

Structure des fichiers
---------------------
```
D-tection_Cancer_C-r-bral_CNN/
├─ data.ipynb                # Notebook principal (prétraitement, entraînement, évaluation)
├─ requirements.txt          # Dépendances Python
├─ Data/                     # Dossier original contenant les images non équilibrées (par classe)
│  ├─ glioma/
│  ├─ meningioma/
│  ├─ notumor/
│  └─ pituitary/
├─ Data_Balanced/            # Dossier généré contenant images rééquilibrées (2000 par classe)
├─ splits/                   # (optionnel) Contient fichiers .npz des splits train/test
└─ README.md                 # Ce fichier
```

Prérequis
---------
- Python 3.8+ (ou 3.10/3.11 recommandés)
- Virtualenv / venv recommandé

Installer les dépendances :

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Exécution
---------
1) Ouvrir le notebook `data.ipynb` dans Jupyter / VS Code et exécuter les cellules du début à la fin.

2) Étapes clés du notebook :
   - Charger et vérifier les images dans `Data/`.
   - Générer `Data_Balanced/` via l'augmentation (2000 images/classe).
   - Charger `Data_Balanced/`, normaliser les images (0-1) et encoder les labels.
   - Séparer en `train/test` (stratifié).
   - Définir et entraîner le modèle CNN.
   - Sauvegarder le modèle entraîné (`my_model.h5` ou `best_model.keras`).

Astuce pour relancer rapidement :
- Si vous avez déjà généré `Data_Balanced/`, sautez la cellule de génération pour gagner du temps.
- Les splits sont sauvegardés dans `splits/balanced_splits.npz` si la cellule correspondante est activée.

Support
-------
Pour toute question sur l'exécution ou pour demander une amélioration (ex : fine-tuning, transfert learning, évaluation avancée), ouvrez une issue ou répondez dans le notebook.

Licence
-------
MIT
