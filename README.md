# Airbnb-Pricing-Prediction-

## Résumé

Ce projet vise à traiter des données collectées sur le site Aribnb pour la date du 14 décembre 2020 qui comporte toutes les données relatives aux listings a cette date.

Ce projet comporte trois parties principales : 
- le premier est une analyse de données qui vise à effectuer une analyse exploratoire des données et à réaliser des visualisations, ce qui inclut le traitement des données nécessaires.
- La seconde consiste à effectuer un prétraitement des données (nettoyage, encodage des données, Features engineering).
- Le dernier est la modélisation et la prédiction qui comprend également certaines étapes de traitement telles que le traitement des valeurs aberrantes et la sélection des features, ainsi que des visualisations.


![Cycle du projet](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Cycle_du_projet.png)


## La partie Pré-traitement de données 

Nettoyage et encodage et feature  engineering 

Pré-traitement

1.  Nettoyage du dataset listings
2.  Traiter les valeurs manquantes
3.  One-hot encode les variables catégorielles
4.  Feature Engineering: 
    * **last\_review**: cette colonnne servira à filtrer les listes qui ne sont plus active
    * **host\_location**: nous pouvons l'utiliser pour déterminer si l'hôte est local ou non
    * **host\_since**:  peut  être  utilisé  pour  calculer  l'expérience  des  hôtes  en  fonction  du nombres d’années depuis leur première inscription
    * **amenities:**  créer  des  features  à  partir  de  cette  colonne  en  Prétraiter  la  colonne amenities pour extraire tous les valeur amenities possibles et affecter un identifiant à chacun  d'entre  eux,  après  avoir  défini une  fonction  d'encodage  qui  mettra  1  dans l'index correspondant dans une matrice. Et enfin, on va avoir la matrice document - terme en appliquant cette fonction d'encodage à tous les documents du corpus.
5.  Del meme facon ( bag-of-words binaire) créer des features à partir de **host\_verifications** 
6. Créer des Feature à partir de colonnes de texte **description**
```
def nlp\_pipeline(book\_texts):     clean\_books = []
`for book in book\_texts:
`        `book = **remove\_hypens**(book)
`        `book\_i = **tokenize\_text**(book)
`        `book\_i = **remove\_characters\_after\_tokenization**(book\_i)         
          book\_i = **convert\_to\_lowercase**(book\_i)
`        `book\_i = **remove\_stopwords**(book\_i, custom\_stopwords)         
          book\_i = **get\_lemma**(book\_i)
`        `book\_i = **remove\_short\_tokens**(book\_i) 
`        `book\_i = **keep\_only\_words\_in\_wordnet**(book\_i)         
          book\_i = **apply\_lemmatize**(book\_i) 
`        `clean\_books.append(book\_i) 
`    `return clean\_books 
```

Apré avoir passer les documents par le pipline NLP il faut vectoriser le corpus maintenant que nous avons le corpus nettoyé, nous pouvons utiliser **TfidfVectorizer** pour convertir le texte en format vectoriel.|![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Screenshot%20from%202021-04-14%2013-04-19.png)

## La partie Analyse de données 

Analyser les données afin de répondre  aux questions et d'obtenir des  informations sur le prix des listings. 


![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.011.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.012.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.013.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.014.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.015.jpeg)


![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.016.jpeg)

**last\_review**: ce champ servira à filtrer les listes qui ne sont plus actives

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.017.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.018.jpeg)

**host\_location**: nous pouvons l'utiliser pour déterminer si l'hôte est local ou non

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.019.png)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.020.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.021.jpeg)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.021.jpeg)

**host\_since**: peut être utilisé pour calculer l'expérience des hôtes en fonction de la durée depuis leur première inscription

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.022.jpeg)|![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.023.png)

**amenities**: Créer des features à partir de amenities (équipements)

![](https://github.com/Amine-OMRI/Airbnb-Pricing-Prediction-/blob/main/Airbnb-Pricing-md/Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.024.png)


**description** : extraction de features à partir de la description (colonne textuelle) ![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.025.png)à l'aide d'un pipline NLP


**calculated\_host\_listings\_count:** valeur continue qui correspond aux nombres effectifs de listings pour les hôtes - mesure permettant de déterminer l'expérience des hôtes ou de distinguer les entreprises et les individus![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.026.jpeg)

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.027.jpeg)

Visualisation du prix moyen du jour pour deux personnes

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.028.jpeg)**Calculer les revenus** estimés pour chaque listing, les revenus estimés pour chaque listing seront calculés sur la base du prix d'une nuit et du nombre minimum de nuits à partir de la base de données

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.029.jpeg)

**Cette fois-ci en se basant sur la colonne prix au lieu de revenu**

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.030.jpeg)

**je récupère les 100 listings les plus chers**

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.031.jpeg)


**Type de bien a acherter**

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.032.jpeg)

**Cette fois-ci en se basant sur la colonne prix au lieu de revenu**

**je récupère les 100 listings les plus chers**

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.033.jpeg)


La partie  ![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.004.png)![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.034.jpeg)prédiction du prix  des listings 

Ici, j'ai fait une sélection de features et  une analyse de corrélation afin de  trouver le meilleur modèle qui pourrait  s'adapter à nos données 


**Le premier essai** : j'ai utilisé un ensemble de données de toutes les colonnes prétraitées sauf celles créées dans la ![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.001.jpeg)partie ingénierie de données (menities, host\_verifications, description)

**Suppression des colonnes comportant beaucoup de valeurs aberrantes**

![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.035.jpeg)

**établir une graphique   ![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.036.jpeg)collinearity heatmap   pour détecter les  features corrélées qui  pourraient empêcher  notre modèle de  converge**r 

**Normalisation et  ![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.037.jpeg)standardisation:** 

A l'exception de  **accommodates** et de  **host\_experience**, les autres  features numériques sont  toutes asymétriques et  pourraient bénéficier d'une  transformation logarithmique 

J'ai utilisé différentes  méthodes pour standardiser  mes données : 

- StandardScaler 
- MinMaxScaler 
- RobustScaler 

Et j'ai gardé MinMaxScaler  puisqu'il conserve la structure  globale des données 

**R SQUARED et RMSE**



||RL|RIDGE|LASSO|XGB trees|
| :- | - | - | - | - |
|TRAIN|<p>Training RMSE: 0.1914</p><p>Training r2: 0.5128</p>|<p>Training RMSE: 0.1915</p><p>Training r2: 0.5125</p>|<p>Training RMSE: 0.1914</p><p>Training r2: 0.5128</p>|<p>Training MSE: 0.1827</p><p>Training r2: 0.5351</p>|
|TEST|<p>Validation RMSE: 0.191</p><p>Validation r2: **0.5193**</p>|<p>Validation RMSE: 0.191</p><p>Validation r2: **0.5193**</p>|<p>Validation RMSE: 0.191</p><p>Validation r2: **0.5193**</p>|<p>Validation MSE: 0.1843</p><p>Validation r2: **0.5361**</p>|
![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.038.jpeg)**Le deuxième essai : J'ai utilisé un ensemble de données de toutes les colonnes prétraitées et aussi celles créées dans la ![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.001.jpeg)partie ingénierie des données (menities, host\_verifications, description)**

**Mon jeu de données était de taille (65917, 2673)**

**R SQUARED et RMSE**



||RL|RIDGE|LASSO|XGB trees|
| :- | - | - | - | - |
|TRAIN|<p>Training RMSE: 0.1504</p><p>Training r2: **0.6172**</p>|<p>Training RMSE: 0.1424</p><p>Training r2: **0.6376**</p>|<p>Training RMSE: 0.1421</p><p>Training r2: **0.6384**</p>|<p>Training MSE: 0.1714</p><p>Training r2: 0.5637</p>|
|TEST|<p>Validation RMSE: 2.8569801186007695 e+18</p><p>Validation r2: **-7.190735871508386 e+18**</p>|<p>Validation RMSE: 0.1567</p><p>Validation r2: **0.6056**</p>|<p>Validation RMSE: 0.1572</p><p>Validation r2:  **0.6043**</p>|<p>Validation MSE: 0.1783</p><p>Validation r2: **0.5512**</p>|
**RANDOM FOREST**



|AVEC n\_estimators = 20|AVEC n\_estimators = 100|
| - | - |
|<p>Training RMSE: 0.0271 Validation RMSE: 0.1774</p><p>Training r2: **0.931** Validation r2: **0.5535**</p>|<p>Training RMSE: 0.0234 Validation RMSE: 0.1688</p><p>Training r2: **0.9403** Validation r2: **0.5753**</p>|
![](Aspose.Words.5d66db9f-6f87-4ae4-9eb7-4d8ce57715a5.039.jpeg)

**Questions ?**
