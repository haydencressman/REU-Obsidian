This is the data when taking all 300 data points, and the outlier data was removed from the total data.

-------- K nearest ---------

              precision    recall  f1-score   support

  

         0.0       0.86      0.92      0.89        13

         1.0       0.83      0.71      0.77         7

  

    accuracy                           0.85        20

   macro avg       0.85      0.82      0.83        20

weighted avg       0.85      0.85      0.85        20

  

[[12  1]

 [ 2  5]]

  

------- Logistic Regression -------

              precision    recall  f1-score   support

  

         0.0       1.00      0.92      0.96        13

         1.0       0.88      1.00      0.93         7

  

    accuracy                           0.95        20

   macro avg       0.94      0.96      0.95        20

weighted avg       0.96      0.95      0.95        20

  

[[12  1]

 [ 0  7]]

  

------- Decision Tree -----------

              precision    recall  f1-score   support

  

         0.0       0.92      0.85      0.88        13

         1.0       0.75      0.86      0.80         7

  

    accuracy                           0.85        20

   macro avg       0.83      0.85      0.84        20

weighted avg       0.86      0.85      0.85        20

  

[[11  2]

 [ 1  6]]

  

----------- Complement Naive Bayes ----------

              precision    recall  f1-score   support

  

         0.0       0.92      0.92      0.92        13

         1.0       0.86      0.86      0.86         7

  

    accuracy                           0.90        20

   macro avg       0.89      0.89      0.89        20

weighted avg       0.90      0.90      0.90        20

  

[[12  1]

 [ 1  6]]

  

——————

Next group, this one was doing the 20 seconds or ~2000 data points, still with the outliers removed

——————

-------- K nearest ---------

              precision    recall  f1-score   support

  

         0.0       0.93      1.00      0.96        13

         1.0       1.00      0.86      0.92         7

  

    accuracy                           0.95        20

   macro avg       0.96      0.93      0.94        20

weighted avg       0.95      0.95      0.95        20

  

[[13  0]

 [ 1  6]]

  

------- Logistic Regression -------

              precision    recall  f1-score   support

  

         0.0       1.00      0.92      0.96        13

         1.0       0.88      1.00      0.93         7

  

    accuracy                           0.95        20

   macro avg       0.94      0.96      0.95        20

weighted avg       0.96      0.95      0.95        20

  

[[12  1]

 [ 0  7]]

  

------- Decision Tree -----------

              precision    recall  f1-score   support

  

         0.0       1.00      1.00      1.00        13

         1.0       1.00      1.00      1.00         7

  

    accuracy                           1.00        20

   macro avg       1.00      1.00      1.00        20

weighted avg       1.00      1.00      1.00        20

  

[[13  0]

 [ 0  7]]

  

----------- Complement Naive Bayes ----------

              precision    recall  f1-score   support

  

         0.0       1.00      0.92      0.96        13

         1.0       0.88      1.00      0.93         7

  

    accuracy                           0.95        20

   macro avg       0.94      0.96      0.95        20

weighted avg       0.96      0.95      0.95        20

  

[[12  1]

 [ 0  7]]