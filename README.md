# 📚 Projet : Classification de Commentaires Toxiques

## 🎯 Objectif du projet
L’objectif de ce projet est de détecter automatiquement les commentaires toxiques postés sur une plateforme en ligne.  
Chaque commentaire doit être classifié dans une ou plusieurs catégories de toxicité :  
- **TOXIC** : propos généraux toxiques  
- **OBSCENE** : propos vulgaires ou obscènes  
- **INSULT** : insultes directes  
- **IDENTITY_HATE** : discours haineux ciblant une identité (race, religion, genre, …)  

**Pourquoi ?**  
- Protéger la plateforme et ses utilisateurs des discours haineux ou inappropriés  
- Automatiser la modération pour minimiser la responsabilité légale  

---


### Consignes de travail

1. **Jeu de données**  
   - Utilisez le dataset fourni pour l’entraînement.  
   - Au démarrage, travaillez sur un sous-ensemble pour accélérer les itérations.

2. **Approche itérative**  
   - **Étape 1** : Modèle de base (TF–IDF + Logistic Regression ou SVM) pour évaluer la difficulté du problème.  
   - **Étape 2** : Passage à un modèle de deep learning (embeddings, RNN/LSTM ou GRU).  
   - **Étape 3** : Affinage du pipeline (prétraitements, réglage d’hyperparamètres).

3. **Pipeline de classification**  
   - **Prétraitement** : nettoyage, tokenisation, suppression des stop-words, lemmatisation.  
   - **Représentation** : TF–IDF / Word2Vec / GloVe / embeddings contextuels (BERT, etc.).  
   - **Modélisation** : classifieur linéaire puis RNN.  
   - **Évaluation** : matrice de confusion, F1-score, ROC AUC.

---

## 🛠️ Approche utilisée

1. **Exploration et prétraitement des données**  
   - Chargement du dataset de commentaires  
   - Analyse de la distribution des classes  
   - Nettoyage :  
     - Passage en minuscules  
     - Suppression des caractères spéciaux  
     - Tokenization et padding des séquences  

2. **Modèle de base : TF–IDF + Naïve Bayes**  
   - Transformation TF–IDF des textes  
   - Entraînement d’un classifieur Multinomial Naïve Bayes  
   - **Bilan :** rapide à entraîner, mais mauvaise détection des classes rares (ex. IDENTITY_HATE)  

3. **Modèle avancé : Word Embeddings + LSTM**  
   - Embeddings de mots (Word2Vec-like)  
   - Réseau de neurones récurrent (LSTM) pour capter les dépendances séquentielles  
   - Activation Sigmoid pour la classification multi-label  

4. **Optimisations apportées**  
   - Sur-échantillonnage de la classe **IDENTITY_HATE**  
   - Ajustement du seuil de décision (passage de 0.5 à 0.4)  
   - Early Stopping pour éviter l’overfitting  
   - Dropout pour régularisation  

---


### Rendu 

1. **Rapport (max. 5 pages) disponible dans le dépot**  
   - **Contexte & sujet** : enjeux de la modération automatique.  
   - **Description des données** et de l’approche.  
   - **Détails de la solution** : choix de modèle, architecture, pipeline.  
   - **Résultats & métriques** : comparatif entre versions itératives.  
   - **Perspectives d’amélioration** : suggestions pour aller plus loin.  


---

### Technologies & bibliothèques

- **Langage :** Python 3.x  
- **Notebook :** Jupyter  
- **Prétraitement :** NLTK / spaCy  
- **ML classique :** scikit-learn  
- **Deep learning :** TensorFlow / PyTorch, Keras  
- **Embeddings :** Gensim, Transformers (Hugging Face)  
- **Visualisation :** Matplotlib, Seaborn  

---


## ✅ Résumé final

Ce projet démontre la mise en place d’un pipeline complet :  
- Prétraitement et analyse exploratoire  
- Modèle de base puis deep learning  
- Optimisations ciblées pour améliorer la détection des classes rares  
- Bilan chiffré et perspectives d’amélioration  
