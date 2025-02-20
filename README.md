# Training--Overfitting
# Overfitting and Training Models Analysis

## Overview
This study explores **training models and overfitting** using **scatter plots and decision trees**. The analysis includes:
- Generating **replica training data** to simulate classification problems.
- Comparing **decision trees** with different complexity levels.
- Simulating **classification data** for testing overfitting scenarios.
- Visualizing **decision boundaries** and classification results.

## Key Features
- **Training Model Analysis**:
  - Scatter plot visualization of training set classification.
  - Analysis of clustered vs. dispersed data points.
- **Decision Tree Complexity**:
  - Comparison between **simple and complex decision trees**.
  - Evaluating overfitting risk and model interpretability.
- **Simulated Classification Data**:
  - Creating synthetic datasets for classification modeling.
  - Evaluating the impact of different splits in decision trees.

## Installation
Ensure you have R installed and required packages:
```r
install.packages("ggplot2")
install.packages("rpart")
```

## Usage
### Simulating Training Data
```r
set.seed(1)
x1 <- runif(100, min = 0, max = 20)
x2 <- runif(100, min = 0, max = 20)
labels <- sample(c("+", "o"), 100, replace = TRUE)
plot(x1, x2, col=ifelse(labels == "+", "red", "blue"), pch=19,
     main="Replica Training Set", xlab="x1", ylab="x2")
```

### Creating Decision Trees
```r
library(rpart)
data <- data.frame(x1, x2, labels)
tree <- rpart(labels ~ x1 + x2, data = data, method = "class")
plot(tree)
text(tree, use.n = TRUE)
```

## Results
### **Training Data Scatter Plot**
- The dataset consists of two **classification categories**.
- **Dispersed and clustered patterns** indicate different decision boundaries.

### **Decision Tree Comparison**
- **Simple Decision Tree**: **11 leaf nodes**, better generalization.
- **Complex Decision Tree**: **24 leaf nodes**, higher risk of overfitting.
- **Overfitting occurs when** the tree learns noise rather than patterns.

## Visualization
### Training Data Classification
![Training Data Scatter Plot](images/training_data_scatter.png)

### Decision Tree Models
![Simple Decision Tree](images/simple_decision_tree.png)
![Complex Decision Tree](images/complex_decision_tree.png)

## References
- Borshchev, A. (2013). *The Big Book of Simulation Modeling*. AnyLogic.
- Favero, L. P., & Belfiore, P. (2019). *Data Science for Business and Decision Making*. Elsevier S & T.

## License
This project is open-source and can be freely used and modified.
