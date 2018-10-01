# Machine Learning and Data-Mining
I. Machine Learning Fundamentals

II. Supervised Learning


## I. Machine Learning Fundamentals
- Machine learning is an important part of AI that involves making predictions and decisions; this model gets better with more experience and data
- Types of learning:
  - **Supervised learning**- every example has a "best" target answer; you train the AI to get close to that answer
  - **Unsupervised learning**- no specific target; goal is to understand the data (aka data-mining)
    - Preprocessing problem
    - Looking for patterns and clusters
    - Data scientists will analyze the data to make sense of it
    - Ex. Computational biology, genetic analysis, social networking
  - **Semi-supervised learning**- supervised learning but you don't always have a target answer
    - Ex. Image tagging
  - **Reinforced learning**- indirect feedback; "better" or "worse" decisions
    - Alter plan/behavior to improve feedback
    - Feedback may be delayed
- Which model is better? Must look at accuracy, complexity, and mistakes (are all mistakes equally bad?)
- Python offers many libraries to work with machine learning: numpy, matplotlib -> good for data exploration
### Data Visualization
- Data can be represented as variables/data points, vectors, and matrices
- Histograms: count data in each of K bins; summarize the data as a length K vector of counts (& plot)
- Scatterplots: illustrates the relationship between two features

### Regression vs. Classification
- Regression: predicting a real number (ex. 4.2), target is along vertical axis
- Classification: discrete (ex. (0,1), (blue, red) ), can flatten the data and separate it by colors when plotted
- Simple, optimal classifier: f(x ; θ)
  - Maps observations x to predicted target values
  - **Optimal decisions**: if you know the probabilites, if you don't know them estimate it from data
    - Don't want to make decisions based on too few observations  
    
    | Feature | spam  | keep |
    |---------|:-----:|:----:|
    |X = 0    | 0.6   | 0.4 |   <- we know that if X = 0, most likely to be spam
    |X = 1    | 0.1   | 0.9 |   <- we know that if X = 1, high probability we keep the mail
   
## II. Supervised Learning
- Supervised learning is when we train the model to reach/predict a target value
- How machine learning works:
  - "Meta-programming": predict --> score --> learn
  - Trainig data is given to the program ("learner") that predicts something. That prediction is scored and the learning algorithm is changed (θ) to help the model improve performance. This "trains" the model
- Notation:
  - Features x
  - Targets y 
  - Predictions ŷ = f(x ; q)
  - Parameters θ
### Nearest Neighbor
- When given a new feature, check the database and find the data that's most similar to the feature; return its value
- There is a decision boundary determined by midpoints --> peacewise linear boundary
- Voronoi tessellation
- More data points will still produce a peacewise linear boundary 

### K-Nearest Neighbor
- Find the k nearest neighbors to x in the data; select a set of k vectors closest to x
- Regression: average the y-values of the k closest training examples
- Classification: pick the class label that is most common in a set
- Training is trivial but testing can be computationally expensive, therefore not ideal for larger datasets
- Increasing k simplifies the decision boundary:
  - Less emphasis on individual point, care more about the area around points
  - Less sensitive to exact individual data points and simplifies the function
- Error rates
  - When k=1 there is no error (spit out the closest data point always), since data is memorized
