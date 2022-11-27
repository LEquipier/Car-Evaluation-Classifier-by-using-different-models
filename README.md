Car Evaluation Classification

1. Description
    In this project, I explored the data set of vehicle evaluation and analyzed the data set. At the same time, 
I used 7 models to learn from the training set and make predictions against the test set.

2. DataSet
     Car Evaluation Database was derived from a simple hierarchical
   decision model originally developed for the demonstration of DEX
   (M. Bohanec, V. Rajkovic: Expert system for decision
   making. Sistemica 1(1), pp. 145-157, 1990.). The model evaluates
   cars according to the following concept structure:

   CAR Evaluation           car acceptability
   . PRICE                  overall price
   . . buying               buying price
   . . maint                price of the maintenance
   . TECH                   technical characteristics
   . . COMFORT              comfort
   . . . doors              number of doors
   . . . persons            capacity in terms of persons to carry
   . . . lug_boot           the size of luggage boot
   . . safety               estimated safety of the car

   Input attributes are printed in lowercase. Besides the target
   concept (CAR), the model includes three intermediate concepts:
   PRICE, TECH, COMFORT. 

   The Car Evaluation Database contains examples with the structural
   information removed, i.e., directly relates CAR to the six input
   attributes: buying, maint, doors, persons, lug_boot, safety.


3. models
    (a)KNN
        In the part of data preprocessing, I read the data, transcode the DataFrame data with a Mapping function, 
    and then convert it into the form of a dictionary. After that, the training set and the test set were divided at 7:3.
	    In the KNN model section, I first added feature labels to the data and then sorted it in ascending order. Then, 
    the best K value after testing is used to divide the training set. After that, I weighed the different results of 
    'evaluation'. Finally, generate the result.
	    Finally, the accuracy was 94.13%. I calculated the running time and added the prediction of the test set to the 
    end of the test set.


    (b)Naive Bayes
        In terms of data processing, unlike KNN, I used sklearn's LabelEncoder () function to convert all str data to int. 
    The first 800 data is divided into the training set and the rest is the test set.
	    Then the Bayesian classification was realized by calling NaiveBayesClassifier () algorithm. The accuracy was 74.34%.


    (c)Perceptron
        In the perceptron model, I integrated the data preprocessing function into a function for later invocation.
        The processing method is the same as described above). In terms of the model, I first set the learning rate and 
    converted the three parameters of 'evaluation' into a 3D matrix to get the data behind the map. The values of W and b 
    are initialized to the best of the randomly generated values. In the course of training, I first initialized the partial 
    derivative with [0] * 6 since the data set has 6 classes. After that, partial derivatives of each training data are 
    accumulated. And I update the W and b by multiple derivatives and learning rates in ever generation.
	    After training 100 times, the result shows the accuracy is 68.05%, I think the result is not good because the values 
    of W and b are inappropriate.

    (d)Logistic Regression
        As before, we first read and transcode the data, and use sklearn's train_test_split() feature to divide the 
    training and test sets.
	    In the model part, I used sklearn's built-in model package for training, and the accuracy rate was 73.68%. Since 
    the accuracy rate was not ideal, I checked the learning curve and found that the accuracy decreased with the increase in data.
        So, I tried to modify the regularization parameter. I used GridSearch to get the best possible parameters. As it is an 
    unbalanced classification problem, accuracy can't be a good criterion for evaluation. But accuracy itself is very low.


    (e)Random Forest
        As before, we first read and transcode the data, and use sklearn's train_test_split() feature to divide the training 
    and test sets.
	    In this model, I still used the built-in random forest algorithm of sklearn, and the result reached 95%, so I tried to continue 
    to increase the accuracy. Firstly, I check the effect of n_estimators on the model. So, with the increasing n_estimators, 
    test accuracy is increasing. The model is evaluated best at n_estimators = 30. After n_estimators = 30, the model starts overfitting. 
    Now, we've reached approx. 96.3% accuracy. I checked how the model fits for various values of 'max_features'. From the graph, it 
    is clear that the model is giving the best result for max_features=5. And after that, I used GridSearch to get the best parameters 
    and get the best accuracy which is 97.42%, and it is the best model in this project.


    (f)Linear SVC
        As before, we first read and transcode the data, and use sklearn's train_test_split() feature to divide the training and test sets.
	    In this model, I still used the built-in random Linear-SVC algorithm of sklearn, and finally, I got an accuracy of 74.69%.

    
    (g)Decision Tree
        As before, we first read and transcode the data, and use sklearn's train_test_split() feature to divide the training and test sets.
	    In this model, I still used the built-in random Linear-SVC algorithm of sklearn, and finally, I got an accuracy of 97.24%.
