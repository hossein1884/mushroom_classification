
# Mushroom Classification Using Decision Tree

## Project Overview

In this project, I developed a Machine Learning model to classify mushrooms into two categories: Edible and Poisonous.

The main goal was to build a Decision Tree classifier using Scikit-learn and improve its performance through hyperparameter optimization.

I focused particularly on the F1-Score of the Poisonous class because correctly identifying poisonous mushrooms is an important part of this classification problem.

## Dataset

The Mushroom dataset contains information about different physical characteristics of mushrooms.

Each row represents a mushroom, and the dataset includes features such as:

- Cap shape, surface, and color
- Bruises and odor
- Gill attachment, spacing, size, and color
- Stalk shape, root, and surface
- Ring number and ring type
- Spore print color
- Population and habitat

### Target Variable

The target column is `class`, which contains two possible values:

| Value | Meaning |
|---|---|
| e | Edible |
| p | Poisonous |

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib

## Project Workflow

### 1. Data Exploration

First, I loaded the dataset using Pandas and explored its structure.

I checked:
- Dataset dimensions
- Column names and data types
- Missing values
- Duplicate records
- Distribution of edible and poisonous mushrooms

This helped me understand the dataset before building the model.

### 2. Data Cleaning

Some values in the dataset were represented by `?`, indicating unknown information.

I replaced these values with NaN so they could be handled during preprocessing.

Instead of deleting rows with missing values, I used a SimpleImputer to replace missing categorical values with the most frequent value in each feature.

### 3. Feature Encoding

Since the dataset contains categorical features, they needed to be converted into numerical values before being used by the Decision Tree model.

I used OneHotEncoder to transform categorical values into numerical binary features.

For example, different cap shapes were converted into separate columns.

### 4. Train-Test Split

I divided the dataset into two parts:

- 80% for training
- 20% for testing

I used stratify=y to maintain the original class distribution in both sets.

The random_state parameter was set to 42 to make the experiment reproducible.

### 5. Building the Decision Tree

I used DecisionTreeClassifier from Scikit-learn.

A Decision Tree learns a series of decision rules based on the input features and uses them to classify new samples.

The model was integrated into a Pipeline together with the preprocessing steps.

This ensured that preprocessing was performed correctly during training and cross-validation.

### 6. Hyperparameter Optimization

To improve the model, I used GridSearchCV to test different combinations of hyperparameters.

The parameters included:

| Parameter | Description |
|---|---|
| criterion | Determines how the best split is selected |
| max_depth | Controls the maximum depth of the tree |
| min_samples_split | Minimum number of samples required to split a node |
| min_samples_leaf | Minimum number of samples required in a leaf |
| class_weight | Controls the relative importance of each class |

I used StratifiedKFold with 5 folds for cross-validation.

### Why F1-Score?

Instead of optimizing only Accuracy, I selected F1-Score as the main evaluation metric.

F1-Score combines Precision and Recall into a single metric.

I specifically used the Poisonous class (`p`) as the positive class.

This allowed the optimization process to focus on correctly identifying poisonous mushrooms.

## Model Evaluation

After finding the best hyperparameters, I evaluated the final model using the test dataset.

### Evaluation Results

| Metric | Score |
|---|---:|
| Training F1-Score | 1.0000 |
| Testing F1-Score | 1.0000 |
| Poisonous F1-Score | 1.0000 |
| Macro F1-Score | 1.0000 |
| Weighted F1-Score | 1.0000 |
| Poisonous Recall | 1.0000 |
| Overfitting Gap | 0.0000 |

### Prediction Results

| Metric | Result |
|---|---:|
|Total Test Samples | 1,625 |
| Correct Predictions | 1,625 |
| Incorrect Predictions | 0 |
| Poisonous Predicted as Edible | 0 |

The model correctly classified all test samples in this experiment.

### Confusion Matrix

The Confusion Matrix was used to examine the number of correct and incorrect predictions for both classes.

In the test results, the model made no classification errors.

### Training vs Testing Performance

I also compared the Training F1-Score with the Testing F1-Score.

Both scores were 1.0000, resulting in an Overfitting Gap of 0.0000.

This indicates that there was no observed performance drop between the training and test sets in this experiment.

## Best Hyperparameters

GridSearchCV selected the following configuration:

| Parameter | Best Value |
|---|---|
| criterion | gini |
| max_depth | None |
| min_samples_split | 2 |
| min_samples_leaf | 2 |
| class_weight | balanced |

Interestingly, although max_depth was set to None, the resulting tree had a depth of only 6.

## Decision Tree Complexity

The final Decision Tree had the following structure:

| Metric | Value |
|---|---:|
| Tree Depth | 6 |
| Number of Leaves | 19 |
| Number of Nodes | 37 |

This shows that the model achieved perfect classification on the test set without requiring a very large tree.

## Feature Importance

I used the Feature Importance attribute of the trained Decision Tree to investigate which categorical features contributed most to its predictions.

The results were visualized using Matplotlib.

This provided a better understanding of how the model made its classification decisions.

## Visualizations

The project includes several visualizations to better understand the data and model performance:

1. Mushroom Class Distribution
2. Confusion Matrix
3. Evaluation Metrics Comparison
4. Feature Importance
5. Decision Tree Structure
6. Training vs Testing F1-Score

## Conclusion

In this project, I implemented a complete classification workflow using the Decision Tree algorithm.

I performed data exploration, handled missing values, encoded categorical features, and optimized the model using GridSearchCV and F1-Score.

The final model achieved an F1-Score of 1.00 on the test dataset and correctly classified all 1,625 test samples.

One of the interesting findings was that the model achieved these results with a relatively compact tree containing only 37 nodes and a depth of 6.

This project helped me better understand Decision Tree classification, categorical data preprocessing, cross-validation, hyperparameter optimization, and model evaluation.

**Note:** These results represent performance on the selected dataset split. Further validation on independent datasets is necessary before making claims about generalization. This model is for educational purposes only and must not be used to determine whether real mushrooms are safe to consume.
