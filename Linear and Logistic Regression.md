## 1. Linear Regression

- **Concepts**
  - **Dependent and Independent Variables**:
    - Dependent variable: The outcome or target variable that the model aims to predict.
    - Independent variables: The input features used to predict the dependent variable.
    - Example: Predicting house prices (dependent) based on size, location, and number of bedrooms (independent variables).
  - **Assumptions**:
    - A linear relationship exists between dependent and independent variables.
    - The residuals (differences between predicted and actual values) are normally distributed.

- **Regression Equation and Modeling**
  - Equation:
    - \( $y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n + \epsilon$ \)
      - \( y \): Dependent variable.
      - \( $x_1, x_2, \ldots, x_n$ \): Independent variables.
      - \( $\beta_0$ \): Intercept.
      - \( $\beta_1, \beta_2, \ldots, \beta_n$ \): Coefficients for each independent variable.
      - \( $\epsilon$ \): Error term.
  - **Objective**:
    - Find the coefficients (\( \beta \)) that minimize the sum of squared residuals (Least Squares Method).

- **Applications in Prediction and Data Analysis**
  - **Prediction**:
    - Estimating continuous outcomes such as sales, temperatures, or demand.
  - **Data Analysis**:
    - Understanding the strength and type of relationships between variables.
    - Example: Analyzing the impact of advertising spend on sales performance.

## 2. Logistic Regression
- **Sigmoid Function for Binary Classification**
  - Logistic regression predicts probabilities for binary outcomes (e.g., success/failure, yes/no).
  - **Sigmoid Function**:
    - Maps any real-valued number to a range between 0 and 1.
    - Equation:
      - \( P(y=1|x) = \frac{1}{1 + e^{-z}} \), where \( z = \beta_0 + \beta_1 x_1 + \ldots + \beta_n x_n \).
    - Output:
      - Values close to 0: Predicted class is 0.
      - Values close to 1: Predicted class is 1.

- **Logistic Regression for Multi-Class Classification**
  - Extended to handle more than two classes using techniques such as:
    - **One-vs-Rest (OvR)**:
      - Trains a separate binary classifier for each class against all others.
    - **Softmax Regression**:
      - Computes probabilities for each class simultaneously by normalizing logits across all classes.
      - Suitable for mutually exclusive classes (e.g., types of flowers, species).

- **Practical Examples**
  - **Classification Using the Iris Dataset**:
    - Iris dataset includes features like sepal length, sepal width, petal length, and petal width to classify flowers into three species:
      - Iris-setosa, Iris-versicolor, and Iris-virginica.
    - Logistic regression is used to model the probabilities of each species based on input features.
  - **Binary Classification**:
    - Example: Determining whether an email is spam or not based on text features.

- **Comparison of Odds and Probabilities**
  - **Odds**:
    - Definition: The ratio of the probability of an event occurring to the probability of it not occurring.
    - Formula: \( \text{Odds} = \frac{P}{1-P} \), where \( P \) is the probability of the event.
  - **Probability**:
    - Definition: The likelihood of an event occurring, ranging between 0 and 1.
  - **Log Odds (Logit)**:
    - Logistic regression predicts log odds, which can be converted to probabilities using the sigmoid function.
  - Example:
    - Probability: \( P = 0.8 \).
    - Odds: \( \text{Odds} = \frac{0.8}{1-0.8} = 4 \) (event is 4 times more likely to occur than not).
