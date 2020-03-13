# Musical Spirits: A new way of categorising music
GA | DSI Capstone Project | 2020 | Aaron Breuer-Weil

---

We are in a new era of music consumption.

Digital natives have instant access to global culture, musical styles have cross-pollinated and listeners now take recommendations from algorithms. People care less for single genre charts and radio DJ's feeding them the hottest 10 pop songs around.

This era of change has seen genre lose its ability to encompass people’s musical taste. Consumers and artists are interested in so much more than one narrow style. 

Rather than continuing to use genre, might there be a mode of categorisation that better represents people’s new broadened music tastes and allows more effective self exploration? Might there be a way of grouping songs together by their underlying musical properties to really help people to seek out the music they like?

---

### Problem Statement:

Is it possible to categorise music in a way that better predicts people’s taste than just using genre?

### Methodology:

1. Collect rating data, musical meta-data and musical feature data.
2. Cluster the albums into groups using musical feature data.
3. Use the clustering output labels in a single feature model to predict user's ratings.
4. Use genre in a seperate single feature model to predict user's ratings.
5. Compare relative performance of the two models.
6. Iteratively tune clustering model to optimise towards cluster-based modelling of user's ratings (i.e. find optimal musical grouping).
7. Interpret clusters to give them real world meaning.

### Data Collection:

1. Scraping:
  * Selenium-based scraper to collect meta-data from Rateyourmusic.com
2. API:
  * Sound features extracted from Spotify's API
3. Other:
  * User ratings from PostgreSQL database shared by @MichaelDarr 

### Modelling:

* Ran 10,000 *simulations* across 66 users and 100,000 ratings.
* 2 sets of KNN classifier models (1 for genre-only, 1 for cluster-only) to predict scores.
* Varied n-neighbours for KNN between 5 and 50 and predicted scores from 2, 3 and 4 levels (i.e. 0-2.5 & 2.5-5; 0-2 & 2-4 & 4-5 etc.)
* KNN for classification and K-Means for clustering selected for computational tractability.

### Results:

With **32** clusters, performance was reliably better than genre at predicting user's album scores.

**Training:**
1. Average 5-fold cross validated training score for **cluster-only** models with KNN classifier: **0.428**
2. Average 5-fold cross validated training score for **genre-only** models with KNN classifier: **0.405**

**Testing:**
3. Average testing score for **cluster-only** models with KNN classifier: **0.407**
4. Average testing score for **genre-only** models with KNN classifier: **0.393**

**Both of the above differences are significant (P<0.001).**

5. Cluster-only performed better in **62.7%** of training instances
6. Cluster-only performed better in **59.7%** of testing instances

### Findings:

Though the improvement over genre is modest, the results suggest the new 32 clusters are a legitimate predictor of people's music taste.

A subjective analysis of the clusters shows some artists and albums grouped in a genre-like manner - instrumental/classical tend to fall into groups together. But the clustering analysis is able to identify more subtle links between songs - darker, more minor songs go together even if one is rap track and another a metal track.

### Future Direction:

* Addition of features to clustering and use recursive feature elimination to tune optimal cluster.
* Run classification per user with additional algorithms to further validate results.
* Rather than a model per user, deploy LightFM for hybrid recommender systems to gauge quality of cluster vs. genre. Use to form a recommender system with clusters.


---

### Clusters Overview:

![alt text](Clusters_Words.png)
