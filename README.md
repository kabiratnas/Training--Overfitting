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
install.packages("rpart.plot")
```

## Usage
### Simulating Training Data
```r
# Load necessary libraries
library(ggplot2)

# Generate a uniform distribution for x1 and x2
x1 <- runif(n = 1000, min = 0, max = 20)
x2 <- runif(n = 1000, min = 0, max = 20)

# Add the values of x1 and x2 to the data frame
Replica_group_1_x <- rnorm(510, 5, 2)
Replica_group_1_y <- rnorm(510, 14, 3)

Replica_group_2_x <- rnorm(510, 10, 2)
Replica_group_2_y <- rnorm(510, 6, 4)

Replica_group_3_x <- rnorm(510, 16, 2)
Replica_group_3_y <- rnorm(510, 14, 4)

# Create scatter plot
plot(x1, x2, lwd = 2, xlab = 'x1', ylab = 'x2', pch = 3,
     main = 'Replica Training Set', xlim = c(10,20), ylim = c(10,20))

# Add points for the replica groups
points(Replica_group_1_x, Replica_group_1_y, lwd = 3)
points(Replica_group_2_x, Replica_group_2_y, lwd = 3)
points(Replica_group_3_x, Replica_group_3_y, lwd = 3)
```

### Creating Decision Trees
```r
# Load required libraries
library(rpart)
library(rpart.plot)

# Convert labels to factor (required for classification)
data$labels <- as.factor(data$labels)

# Build a simple decision tree model
simple_tree <- rpart(labels ~ x1 + x2, data = data, method = "class", control = rpart.control(cp = 0.05))

# Build a complex decision tree model
complex_tree <- rpart(labels ~ x1 + x2, data = data, method = "class", control = rpart.control(cp = 0.001))

# Plot the simple tree
par(mfrow=c(1,2))  # Set up a 1x2 plot layout
rpart.plot(simple_tree, main = "Simple Decision Tree")

# Plot the complex tree
rpart.plot(complex_tree, main = "Complex Decision Tree")
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
## References
- Borshchev, A. (2013). *The Big Book of Simulation Modeling*. AnyLogic.
- Favero, L. P., & Belfiore, P. (2019). *Data Science for Business and Decision Making*. Elsevier S & T.

## License
This project is open-source and can be freely used and modified.
user-attachments/assets/60e91fad-1da5-4c53-a0ed-794080412298)

