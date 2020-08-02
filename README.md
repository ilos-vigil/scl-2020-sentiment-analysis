# Shopee Code League 2020 - Sentiment Analysis

This is source code/solution for 12th place (top 4%) in Private LB with score 0.63747 of [[Student] Shopee Code League 2020 - Sentiment Analysis](https://www.kaggle.com/c/student-shopee-code-league-sentiment-analysis). Check [Overview Archive](https://archive.is/t4Ukw) and [Leaderboard Archive](https://archive.is/BYZx5) if Kaggle is down or the link is invalid.

## Disclaimer

* This is work of Cocoa team, we **DO NOT** represent any organization.
* There's no reproducibility guarantee for notebook which uses GPU
* Although we use License "The Unlicense", dataset and generated dataset falls under Shopee Terms and Conditions which can be seen on [Kaggle](https://www.kaggle.com/c/student-shopee-code-league-sentiment-analysis/rules)

## Our works in nutshell

1. Additional dataset from https://www.kaggle.com/shymammoth/shopee-reviews, with total training data about 10.2x higher than total training data provider by Shopee
2. NLTK Tweet Tokenizer
3. `DistilRoBERTa-base` model
4. [ktrain](https://github.com/amaiya/ktrain) library

## Environment List

> Some of the notebook are run on different environment

| Environment Name | Description                            |
| ---------------- | -------------------------------------- |
| Kaggle CPU       | 2C/4T CPU, 16GB RAM                    |
| Kaggle GPU       | 2C/4T CPU, 16GB RAM, Nvidia Tesla P100 |

## Notebook description

> Jupyter notebook on `extra_notebook` directory isn't used on the competition

| Filename            | Link to Kaggle Kernel                                                                            | Environment | Description                                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------ | ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| 00_check_leak.ipynb | https://www.kaggle.com/ilosvigil/scl-2020-6-check-leak-on-external-data?scriptVersionId=39882862 | Kaggle CPU  | Check exact string match between Shopee's test dataset and external dataset                                              |
| 01_clean.ipynb      | https://www.kaggle.com/ilosvigil/scl-2020-6-clean-text?scriptVersionId=39820359                  | Kaggle CPU  | Perform case lower/upper, stemming/lematization and tokenization                                                         |
| 02a_ktrain.ipynb    | https://www.kaggle.com/ilosvigil/scl-2020-6-ktrain?scriptVersionId=39927650                      | Kaggle GPU  | Fine-tuning `DistilRoBERTa-base` using [ktrain](https://github.com/amaiya/ktrain) library                                |
| 02b_lightgbm.ipynb  | https://www.kaggle.com/ilosvigil/scl-2020-6-lightgbm?scriptVersionId=39890235                    | Kaggle CPU  | Create Gradient Boosting model with [LightGBM](https://github.com/Microsoft/LightGBM) library & 3-gram TF-IDF as feature |
| 02c_sklearn.ipynb   | https://www.kaggle.com/ilosvigil/scl-2020-6-lightgbm?scriptVersionId=39890235                    | Kaggle CPU  | Create Naive Bayes model with Scikit-Learn library & 3-gram TF-IDF as feature                                            |


## Dataset

The dataset is available on this repository and/or Kaggle datasets platform.

| Created By                                   | Filename/directory path       | Link to Kaggle datasets                                                     |
| -------------------------------------------- | ----------------------------- | --------------------------------------------------------------------------- |
| Shopee                                       | `data/csv/train.csv`          | https://www.kaggle.com/c/student-shopee-code-league-sentiment-analysis/data |
|                                              | `data/csv/test.csv`           | https://www.kaggle.com/c/student-shopee-code-league-sentiment-analysis/data |
| [Tony Ng](https://www.kaggle.com/shymammoth) | `data/csv/shopee_reviews.csv` | https://www.kaggle.com/shymammoth/shopee-reviews                            |
| Notebook : 01_clean.ipynb                    | `data/parquet`                | https://www.kaggle.com/ilosvigil/shopee-review-cleaned                      |

## Leaderboard (LB) Score

| Notebook filename  | Submission filename                      | Used for Final Score | Public LB   | Private LB  |
| ------------------ | ---------------------------------------- | -------------------- | ----------- | ----------- |
| 02a_ktrain.ipynb   | submission_preprocess_text.csv           | Yes                  | **0.62994** | **0.63747** |
| 02a_ktrain.ipynb   | submission_preprocess_text_mod_proba.csv | No                   | 0.62994     | 0.63747     |
| 02a_ktrain.ipynb   | submission_raw_text.csv                  | No                   | 0.61835     | 0.62609     |
| 02b_lightgbm.ipynb | submission_tweak_proba.csv               | No                   | 0.49230     | 0.50066     |
| 02b_lightgbm.ipynb | submission.csv                           | No                   | 0.43415     | 0.43874     |
| 02c_sklearn.ipynb  | submission_MultinomialNB.csv             | No                   | 0.42649     | 0.43494     |
| 02c_sklearn.ipynb  | submission_ComplementNB.csv              | No                   | 0.42654     | 0.43721     |

## Guide

1. Run `01_clean.ipynb`
2. Run `02a_ktrain.ipynb`, `02b_lightgbm.ipynb` or `02c_sklearn.ipynb`
