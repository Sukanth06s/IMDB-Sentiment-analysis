# IMDB Movie Review Sentiment Prediction

Hey guys 👋 this is Sukanth, and this is my IMDB movie review sentiment prediction model.  
I used **Logistic Regression** and **Linear SVM** to classify reviews as positive or negative. 


### 1. Preprocessing ( getting the data ready for the Model)
-The dataset has reviews in sentence format, so before using that I need to make sure to remove all the unnecessary stuff like special charcters, numbers, commas and stuff. 
 so that it will be easier


### 2. Feature Extraction (TF-IDF)
- After cleaning, the text is converted into numerical vectors (ML models can only read numbers).
- I used **TF-IDF (Term Frequency – Inverse Document Frequency)** to measure the significance of every word:
  - **Term Frequency** → how often a word appears in a review
  - **Inverse Document Frequency** → reduces the weight of very common words
- By using this each review is transformed into a vector of length 5000, where each number represents the importance of a word/phrase.

### 3. Train/Test Split
- Split the dataset into:
  - 80% for training → used to teach the model
  - 20% for testing → used to evaluate generalization
- Used `stratify=y` to maintain the same proportion of positive/negative reviews in both sets so that there is no inconsistency is spliting the data. learnt it the   hard way 😅.

### 4. Models
I trained **two models** on the TF-IDF features:

#### a) Logistic Regression
- Treats the task as a probability problem
- Each word/phrase is assigned a weight → positive weight pushes toward positive sentiment, negative toward negative

#### b) Linear SVM (Support Vector Machine)
- Finds the best boundary (hyperplane) that separates positive from negative reviews
- Only the most important reviews (**support vectors**) determine this boundary

### 5. Evaluation
- Compared the models using multiple metrics:
  - **Accuracy** → how many reviews were classified correctly overall
  - **Precision** → of predicted positives, how many were actually positive
  - **Recall** → of all actual positives, how many did the model find
  - **F1-score** → balance between precision and recall
- Visualized results:
  - **Confusion Matrix** → true positives, true negatives, false positives, false negatives
  - **Learning Curves** → how training and validation accuracy change as more data is added

---

## Results
- **Logistic Regression** → ~89% accuracy
- **Linear SVM** → ~88% accuracy
