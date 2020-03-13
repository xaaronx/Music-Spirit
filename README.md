# Musical Spirits: a new way of categorising music
GA DSI Capstone Project 2020

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

* Scraping:
  * Selenium-based scraper to collect meta-data from Rateyourmusic.com
* API:
  * Sound features extracted from Spotify's API
* Other:
  * User ratings from PostgreSQL database shared by @MichaelDarr 

### Modelling:



### Results:

With 32 clusters, performance was reliably better than genre at predicting user's album scores.

Training:
1. Average 5-fold cross validated training score for **cluster-only** models with KNN classifier: **0.428**
2. Average 5-fold cross validated training score for **genre-only** models with KNN classifier: **0.405**

Testing:
3. Average testing score for **cluster-only** models with KNN classifier: **0.407**
4. Average testing score for **genre-only** models with KNN classifier: **0.393**

**Both of the above differences are significant (P<0.001).**

5. Cluster-only performed better in **62.7%** of training instances
6. Cluster-only performed better in **59.7%** of testing instances

### Findings:

Though the improvement over genre is modest, the results suggest the new 32 clusters are a legitimate predictor of people's music taste. 

### Conclusion:

