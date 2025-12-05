# EPSY 8264 Fall 2025

## Assignment 6  
### Cross-Validation

The goal of this assignment is to give you experience using cross-validation. This assignment is worth 15 points. Each question is worth 1 point unless otherwise noted. Your syntax will be evaluated based on the rubric at the end of the assignment. This will count for 2 pts. of the assignment score.

### Instructions

Submit a PDF document of your responses to the following questions. In questions that ask you to “use matrix algebra” to solve the problem, you can either show your syntax and output from carrying out the matrix operations, or you can use Equation Editor to input the matrices involved in your calculations. Also submit the commented script file that you used in the assignment.

---

## Part I: Minneapolis Violent Crime

For the first part of this assignment, you will use the data provided in the file `mpls-violent-crime.csv` to build a model that examines the trend in violent crime rate over time. Use this data to create a variable that indicates the number of years since 2000. Use this variable in all analyses for Part I rather than the year variable.

1. Create a scatterplot showing the violent crime rate as a function of time.

2. Based on the plot, describe the trend in violent crime rate over time.

3. If you were going to fit a polynomial model to these data, what degree polynomial would you fit? Explain.

Use p-value methods for model selection.

4. Fit a series of polynomial models starting with a linear model, and then models that also include higher order polynomials that allow you to evaluate your response to Question #3. Be sure to fit models up to degree *k + 1*, where *k* is the degree you hypothesized in Question #3. Analyze each of the polynomial terms (including the linear term) by using a series of nested F-tests. Report these results in an ANOVA table.  
   *(Note: If you need a refresher on fitting polynomial models and carrying out a nested F-test, see the Polynomial Effects chapter from* Advanced Modeling and Reproducibility for Educational Scientists*.)*

5. Based on these results, which polynomial model would you adopt? Explain.

### Using LOOCV for Model Selection

In this section of the assignment, you are going to use LOOCV to evaluate the MSE for the same set of polynomial models you evaluated in Question #4.

6. Write the syntax that will carry out the LOOCV. No need to include it in your PDF—just include it in your script file.

7. Report the cross-validated MSE for each of the models in your set of polynomial models.

8. Based on these results, which degree polynomial model should be adopted? Explain.

---

## Part II: Course Evaluations

For the second part of this assignment, you will use the data provided in the file `evaluations.csv` to build a model that predicts variation in course evaluation scores. Begin by fitting a model that predicts average course evaluation score using the following predictors:

- beauty  
- number of courses for which the professor has evaluations  
- whether the professor is a native English speaker  
- whether the professor is female  

9. Using average course evaluation scores (*y*) and the predicted values from the model (*ŷ*), compute:  
   a. the total sum of squares (SST);  
   b. the sum of squared errors (SSE); and  
   c. the model \(R^2\) value using the formula  
   \[
   R^2 = 1 - \frac{\text{SSE}}{\text{SST}}.
   \]  
   Show your work.

---

## Using k-Fold Cross-Validation to Estimate \(R^2\)

As we know, the estimate for \(R^2\) is biased. We can obtain a better estimate of \(R^2\) by using cross-validation. You will use 5-fold cross-validation to estimate the \(R^2\) value. The algorithm for this will be:

- Randomly divide the evaluations data into 5 folds.
- Hold out 1 fold as your validation data and use the remaining 4 folds as your training data.
  - Fit the model to the training data.
  - Use the estimated coefficients from those fits to compute *ŷ* values using the validation data.
  - Compute the SST and SSE values for the validation data, and use those to compute \(R^2\) based on the formula  
    \[
    R^2 = 1 - \frac{\text{SSE}}{\text{SST}}.
    \]  
    (Note that sometimes the \(R^2\) may be negative when we compute it in this manner.)
- Repeat for each fold.
- Compute the cross-validated \(R^2\) by finding the mean of the five \(R^2\)s from the cross-validations.

10. Write the syntax that will carry out the 5-fold cross-validation. In this syntax use `set.seed(1000)` so that you and the answer key will get the same results. (This website may be useful in using the `{purrr}` package to obtain the *y*- and *ŷ*-values in order to compute the SST and SSE values.) No need to include it in your PDF—just include it in your script file.

11. Report the five \(R^2\) values from your analysis and the cross-validated \(R^2\) value.

12. How does this value compare to the \(R^2\) value you computed in Question #11, based on the data.

13. Explain why the cross-validated estimate of \(R^2\) is a better estimate than the data-based \(R^2\).

---

## Rubric for Evaluating Student Syntax

### Documentation

Is the syntax well annotated to aid communication to other educational scientists and researchers?

- Holistic comments are used to describe the purpose of chunks of syntax (or usage of `label:` in QMD chunks).
- Comments are liberally included to explain smaller pieces of syntax (especially where non-common code is used).
- Object names accurately describe the intent of the object (e.g., `pew_data` rather than `x`).
- Plots should include a comment that provides the caption (or usage of `fig-cap:` in QMD).

### Structure and Presentation

Is the syntax organized and structured to be "readable" and easy to follow for other educational scientists and researchers?

- Consistent use of case (e.g., lower-case, camel-case) for all objects.
- Consistent use of operators throughout the code (e.g., always using `<-` or `=` for assignment).
- Spacing is included for readability (e.g., `lm.1 = lm(...)` rather than `lm.1=lm(...)`).
- Indentation and line breaks are included in long code (e.g., when using `|>` or when a function has many arguments), especially in `{dplyr}` and `{ggplot}` syntax.

---

## How do I submit the assignment?

Create a PDF of your responses and submit the PDF and R script file (the `.R` file) via email to both the instructor and TA. Also cc any group members. Before you submit the assignment check that:

- All group members’ names are on the assignment.  
- All tables are numbered and have a caption.  
- All figures are numbered and have a caption and are re-sized to not take up more page space than is necessary to read them.  
- No R syntax is included in the assignment responses unless the question specifically asks for the syntax to be included. If there is R syntax included, be sure that it is typeset in a monospaced font (e.g., Courier, Inconsolata).

© EPSY 8264, 2025
