# IMDB Movie Review Sentiment Prediction

Hey guys 👋 this is Sukanth, and this is my IMDB movie review sentiment prediction model.  
I used **Logistic Regression** and **Linear SVM** to classify reviews as positive or negative. 


### 1. Preprocessing ( getting the data ready for the Model)
The dataset has reviews in sentence format, so before using that I need to make sure to convert all the words to lowercase and remove all the unnecessary stuff like special charcters, numbers, commas and stuff. 
so that it will be easier for the vectorizer to efficiently handle the review data.


### 2. Feature Extraction (TF-IDF)
Once the cleaning is done, the text is converted into numerical vectors as Ml models can only deal with numbers. Here I used the TF_IDF vectoriser to convert as this provides the right balance btwn efficiency and giving importance to the words. TF refers to Term Frequency this measures the significanve of every word and IDF refers to Inverse Document Frequency which reduces the important of common words like "the" , "a" and stuff. Aft this each review is transformed into a vector of length 5000, where each number represents the importance of a word or pair of words.

### 3. Train/Test Split
Next up I split the data into train and test data, where the train data is used to train the model and the test data is the unseen data that is used to test the accuracy of the model. I've used a ratio of 0.8 for train data and 0.2 for test data.

### 4. Models
I've used Logistic Regression and SVM for this problem 

#### a) Logistic Regression
here each word in the tf-idf vector is given a weight depeding on the nature of the word, if its positive word then the model will give it a positive weight else negative weight, and once the tranining is done, to finally calculate if a feature is positive or negative the model sums up the product of all the weights of feature along with its feature value and then we finally get a floating point value, which is then converted into probablity using the sigmoid function.

#### b) Linear SVM (Support Vector Machine)
Here each word in the tf-idf vector is given a weight depending on the nature of the word, if it is a positive-indicating word then the model will assign it a positive weight, else a negative weight. Once training is done, to classify a review the model takes the sum of the product of all the word weights with their tf-idf values, which gives a single floating point score. Instead of converting this into probability (like logistic regression), the SVM checks on which side of a separating hyperplane this score lies: if it’s greater than 0, the review is classified as positive; if less than 0, it is classified as negative.

### 5. Evaluation
Compared the models using multiple metrics:
Accuracy - How many reviews were classified correctly.
Presision - Out of all the predicted positives, How many of the were actually positive.
Recall - similar to presision but its the vice versa here.
F1 Score - offers a balance btwn precision and recall.
Confusion Matrix - hels indentify where the model performed well and where it underperformed by giving us true positives, true negatives, false positives, false negatives
leanring curve - tells us how the training accuracy and validation accuracy changes as more and more data is added.

---

## Results
- **Logistic Regression** → ~89% accuracy
- **Linear SVM** → ~88% accuracy
