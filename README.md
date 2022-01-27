# Algo_Python_Class_Project
 
The problem we are trying to approch here has been subject to some study by Ilyes Talbi, the author of the article [XGBoost vs Random Forest : prédire la gravité d’un accident de la route](https://larevueia.fr/xgboost-vs-random-forest-predire-la-gravite-dun-accident-de-la-route/) published in September 6, 2021 in the IA review. The author proposed as main problem to test and find the better algorithm between `Random Forest` and `XGBoost` in order to predict the gravity of the people who had a road accident in France. The data used in this study can be downloaded on the [Open Data Gouv](http://data.gouv.fr/) website.

The author found out that the `XGBoost` algorithm predicted better the labels than the Random Forest and their respective accuracy were given by `Random Forest : 60.35%` and `XGBoost : 65.9%`. The author also provided some opportunities for improvement like the tuning of the hyperparameters and the handling of the imbalanced proportions of the data. So this is the situation we want to address in this Notebook.

To provide a larger solution, we try to present some differents approaches to solve the problem. To do so, we proceeded like this : 
- We try to reformulate the problem three ways :
    * Firstly, we have the same problem as the author (4 classes).
    * Secondly, we merge the people who need medical attention (classes 3 and 4) and now we are dealing with a 3 classes problem.
    * Finaly, we let all the people who are killed in one class (class 2) and merge all the others classes and considered them as survivors (class 1).
- We introduce the `k-Nearest Neighbors` and the `Linear Discriminant Analysis (LDA)` algorithms to provide other grounds of comparison.
- We tuned the hyperparameters except for the `XGBoost` algorithm due to the numbers of parameters to specify and we leave the base `LDA` algorithm. The author also had the same problem for `XGBoost`.
- We used the `under sampling` method to handle the improper balanced data. However, a problem with this method is that we could lose some valuable informations in the prediction process that would potentially be helpful to the algorithm to predict the labels. And it was convenient for us also because of the computational problem that we would have in order to deal with at least 50000 observations by classes.
- Given that we also had to implement different methods, we ensured that the overwhelming part of our proposed solution is function based. So we defined the `cleansing()`, `merge_classes()`, `model_accuracy()`, `underSamp()`, `splitting()`,`tuning()` and `score_summary()` functions to automate some of our results.

At the end of our experience, we arrive as the same conclusion as the author of the article :
> The `XBGoost algorithm` performs better in the majority of the formulations. 

The only times were it's not the case is when we found out that the Random Forest algorithm has a better accuracy on the train set but the overfitting in the data undermined the confidence in the predictions. We found out also that the `LDA` algorithm can perform a quite good fit to the problem.

Now as improvement opportunities, it would be very interesting to tune the hyperparameters of the `XBGoost algorithm` in order to see exactly the limits of it. Our best results with it was in the binary problem were we had `79.3%` of accuracy.