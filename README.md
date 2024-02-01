# R-programming

## Chapter 1. Data Analysis and Data Cleaning
### 2.6 Feature Engineering
Creating new variable using variables from the present dataset.

### 3.1 Exploratory Data Analysis
Exploring the data normally using Max, Min, Median, Mean, and Mode.
We need to understand the implied phenomenon embedded in the data to resolve the problem correctly.

Check NA or outliers in single variable and if there are any NAs or outliers then clean it.
To check the data distribution, summarise the variable simply and see the data distribution using Box Plot or Stem-and-Leaf Plot.

More than two variables' relationship can be caputured by Scatter Plot.
Scatter Plot let us know how much the data spread, linear relationship, and cluster existence.

### 4. Data Analysis
1) Statistical Hypothesis
  Analysis method will be determined by hypothesis and variable types.

2) Machine Learning
   We compare the algorithm for prediction and classfication model and use the well performing algorithm.

3) Data Visualization
   
### 4.1. Statistical Hypothesis Testing
From the exploratory data analysis stage, we clarify the problem.
In the data analysis stage, we need to find the algorithm to resolve the clarified problems.

When we analyze the data we need to focus on "if the analysis result will bring us a profit."
We cannot get the information more than understading the phenomenon with obtained data such as customer's gender, age, and geographical infromation. 
We at least need to know which factor will make profit of our service, if it is possible to change the factor, and if net profit can be produced compared to cost.

### 4.2. Machine Learning
There are mainly three machine learning methods: supervised learning (Purpose of classification or numerical prediction), unsupervised learning (Purpose of subdividing a specific group through clustering), reinforcement learning (The purpose is to observe the environment and find optimized goals through rewards and penalties).

1) Supervised Learning
   Supervised learning is a method of providing answers and training, and is used for classification models and regression models.
   Mainly predict the uncoming event or issue using past data.

   It predict or estimate an output (response) from various inputs (predictors)
   Statistical tools: better understanding about the relationship between the response and the predi tors (inference)
   Maching learning tools: better (prediction accuracy)
   --> Most widely used tools: regression, classification, text analytics, recommendation systems, time series

2) Unsupervised Learning
   Unsupervised learning is a method of training without answers, and is used to explore data to find properties similar to the structure and classify them.
   For example, we can classify customers to one cluster who has similar buying pattern of specific products and accomplish the goal to increase the profit providing promotion to     
   induce the repurchase of the product (Cluster Analysis or Association Rule).
   We can use Principal Component Analysis or Kernel PCA to reduce the dimensionality of the data.

   Tools for understanding data, with no target attribute (no labels). Usually organize into some natural groups.
   Difficult to know how well your are doing; useful as a pre-processing step for supervised learning.
   --> Most widely used tools: PCA, clustering/segmentation, association rules

3) Reinforcement Learning
   Training the agent to receive as many rewards as possible within a given environment by its action.
   For example, it is used to create AI players in the game industry or to develop autonomous driving in cars (ex. AlphaGo).

4) Others: semi-supervised learning, optimization, simulation, . . .

### 4.3. Visualization
Data visualization is the process of finding hidden patterns in the complex and disorderly flow of data and processing them concisely, clearly, and visually to convey them.

### 4.4. Making conclusion
The analysis report is the result of organizing business plans, policy proposals, and ideas into a report according to requirements.
In the introduction, the background of the analysis and the contents of the analysis are generally written.
Main contents include how the analysis was performed and what the analysis results were.
In the conclusion, a solution to the analysis topic using the analysis results is presented and the expected effects are written accordingly to increase justification.
Lastly, we conclude by presenting future projects(or plans) on what projects will be performed in the future.

## Chapter 2
### 5. What happened in the cafe for last 1 year.
### 5.1. readxl package
> install.packages("readxl")
> library("readxl")
> read_xlsx()

## References
Resource github: http://github.com/bjpublic/R_data
Advanced Modeling slides at UC3M Computation Social Science 2023/2024 academic year
The book:
• G. James, D. Witten, T. Hastie and R. Tibshirani.
An Introduction to Statistical Learning with Applications in R second edition available here: https://www.statlearning.com
Other references:
• K. Murphy
Machine Learning, A Probabilistic Perspective
• David Spiegelhalter
The Art of Statistics: Learning from Data
• C. Bishop
Pattern Recognition and Machine Learning








