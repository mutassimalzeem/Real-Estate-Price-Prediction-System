# Modeling Strategy

## Objective

The modeling objective is to predict house sale prices as accurately as possible while keeping the workflow understandable and explainable.

## Target Transformation

House prices are usually right-skewed. A few very expensive homes can distort the distribution and make regression harder.

The notebook applies a log transformation using `log1p`:

```python
SalePrice = np.log1p(SalePrice)
```

This makes the target distribution more stable and easier for regression models to learn.

Final predictions are converted back using:

```python
np.expm1(predictions)
```

## Model Families Used

The notebook compares multiple model families:

- Linear Regression
- Lasso Regression
- Random Forest
- Gradient Boosting
- XGBoost
- Ridge / ElasticNet-style regularized models
- Extra Trees

## Why Multiple Models?

Different models learn different patterns.

Linear models are strong when relationships are mostly additive. Tree-based models are better at nonlinear interactions. Boosting methods often perform well on tabular data because they correct mistakes gradually.

## Cross-Validation

Cross-validation is used to evaluate models more reliably than a single train/test split.

This reduces the chance of trusting a model that only performed well on one lucky split.

## Ensemble Prediction

The final prediction strategy uses weighted averaging from strong models.

This is useful because model averaging often reduces variance and improves generalization.

## Engineering Mindset

The modeling approach is intentionally practical:

- start simple
- validate properly
- add stronger models gradually
- keep preprocessing consistent
- avoid overcomplicating the project too early
