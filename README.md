# Reconnaissance Automatique de la Parole (ASR) : Chiffres Arabes

## Présentation du Projet
Ce projet présente un pipeline complet de Reconnaissance Automatique de la Parole (RAP) conçu pour identifier et classifier des chiffres arabes prononcés (de 0 à 9). 

L'objectif de ce dépôt est de démontrer la maîtrise du traitement de séries temporelles et du signal vocal, en comparant trois approches mathématiques et algorithmiques distinctes : un modèle discriminatif (SVM), un modèle probabiliste (HMM-GMM) et un réseau de neurones récurrents (LSTM).

## Stack Technique
* **Langage :** Python
* **Deep Learning & Machine Learning :** TensorFlow/Keras, Scikit-learn, hmmlearn
* **Traitement Audio :** Librosa
* **Manipulation de Données :** NumPy

## Dataset et Prétraitement (Audio Engineering)
Le modèle a été entraîné sur un dataset personnalisé contenant **1 594 fichiers audio (`.wav`)** enregistrés par différents locuteurs pour assurer une diversité d'accents et de voix. 

Le pipeline de prétraitement du signal audio comprend :
1. **Acquisition et Standardisation :** Rééchantillonnage de tous les fichiers audio à 16 kHz en mono.
2. **Nettoyage :** Suppression automatisée des silences (trimming) aux extrémités des enregistrements.
3. **Extraction de Caractéristiques :** Extraction des séquences temporelles via **13 coefficients MFCC** (Mel-Frequency Cepstral Coefficients) pour obtenir une représentation exploitable par les algorithmes.

## Modèles et Performances
Le projet compare trois architectures pour évaluer le compromis entre complexité de modélisation temporelle et précision.
Chaque modèle a été soumis à une phase d'expérimentation avec différents hyperparamètres, et seules les configurations les plus performantes ont été conservées pour l'évaluation finale :

| Architecture | Type de Modèle | Stratégie Temporelle | Hyperparamètres Clés | Précision (Accuracy) |
| :--- | :--- | :--- | :--- | :--- |
| **LSTM** | Deep Learning (RNN) | Séquentiel | 256 unités, Dropout (0.1) | **92.48%** |
| **SVM** | Discriminatif | Moyenne (Statique) | Noyau RBF, C=300 | **87.15%** |
| **HMM-GMM** | Probabiliste | Séquentiel (Markov) | 5 états, 7 mélanges gaussiens | **85.36%** |

**Conclusion de l'ingénierie :** L'approche par Deep Learning (LSTM) s'est avérée la plus robuste (92.48 %) grâce à sa capacité à modéliser finement la dynamique temporelle et les dépendances à long terme du signal vocal complexe, surpassant les hypothèses statistiques rigides du modèle HMM-GMM et l'écrasement temporel du SVM.

## Structure du Dépôt
```text
asr-arabic-digits/
├── notebooks/
│   ├── LSTM.ipynb                 # Entraînement et évaluation du réseau de neurones récurrents
│   ├── MFCC-HNN-GMM-VIBERTI.ipynb # Modélisation probabiliste des séquences temporelles
│   └── MFCC-MEAN-SVM.ipynb        # Extraction des moyennes MFCC et classification Support Vector Machine
├── samples/                       # (Optionnel) Quelques échantillons .wav pour démonstration
├── .gitignore                     # Exclusion du dataset lourd et des poids du modèle (.pkl, .h5)
└── README.md
```

##  Author
**Mohammed Essalhi**
* [LinkedIn](https://linkedin.com/in/mohammed-essalhi-23794b24b)

