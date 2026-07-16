# Data Science Portfolio

**Alasya Zeweldi** | B.A. Economics, B.S. Data Science, American University (May 2026) | Washington, DC

A collection of applied projects in machine learning, NLP, and policy-relevant data analysis, built in R and Python. My work focuses on questions at the intersection of economics and data: who has access to health insurance, what drives workplace absenteeism, and whether financial distress can be detected in real-world text.

## Executive Summary

| Project | Question | Methods | Best Result |
|---|---|---|---|
| [Predicting Workplace Absenteeism | Can we predict how much and how often employees are absent? | Multiple linear regression, KNN, logistic regression, decision trees (R) | Pruned decision tree, 78% test accuracy |
| [Financial Stress Detection | Can deep learning detect financial stress in Reddit posts? | Custom Word2Vec embeddings, CNN, BiLSTM (PyTorch) | CNN, 64.3% accuracy / 0.640 F1 |
| [Health Insurance Coverage in the US Which groups are most likely to lack health insurance? | EDA and logistic regression on ACS microdata (R) | Veteran status, employment, and marriage strongly predict coverage; Hispanic individuals and men less likely to be insured |
| [Topic Modeling on Amazon Reviews | What themes emerge from 20,000 product reviews? | TF-IDF, NMF, LDA (Python) | Five interpretable topics recovered without labels |

**Tools:** R (tidyverse, ggplot2), Python (PyTorch, scikit-learn, gensim, NLTK, pandas), Stata, SQL

---

## Projects

### 1. Predicting Workplace Absenteeism
*R | Regression and classification*

**Problem.** Unplanned absence is costly for employers. Using an HR dataset of employee absences, I asked two questions: can we predict the number of hours an employee will be absent (regression), and can we classify employees as high or low absence risk (classification)?

**Methodology.** After exploratory analysis of absence patterns by day of week, season, and education level, I built four models on a 70/30 train-test split:
- Multiple linear regression as a baseline (adjusted R² of 0.23, test RMSE of 13.4 hours)
- KNN classifier with scaled features and K tuned over odd values from 3 to 31 (best K = 27, 75% accuracy)
- Logistic regression using median absence time as the cutoff (64.7% accuracy; transportation expense was the only significant predictor)
- Decision tree, grown to 16 nodes then pruned to 6 using 10-fold cross-validation (78.1% test accuracy, the best classifier)

**Takeaways.** Tree-based methods handled the nonlinear structure best. Health-related absence reasons, transportation expense, and age emerged as the strongest drivers of absenteeism.

**Skills:** model comparison, cross-validation, feature preprocessing, avoiding data leakage in train/test scaling, communicating tradeoffs between accuracy and interpretability.

📄 [Project slides (PDF)](./predicting-workplace-absenteeism.pdf)

### 2. Financial Stress Detection Using Reddit Data
*Python, PyTorch | Deep learning NLP*

**Problem.** Financial stress is understudied in text-based mental health detection compared to anxiety or trauma. Using the Dreaddit corpus (3,553 Reddit posts across 10 subreddits, with a 717-post finance subset from r/assistance, r/homeless, and similar communities), I tested whether deep learning models can classify posts as stressed or not stressed.

**Methodology.**
- Cleaned and tokenized posts, then trained custom Word2Vec embeddings on the corpus (6,873-word vocabulary, 100 dimensions)
- Built a CNN with three parallel Conv1D filters (kernel sizes 2, 3, 4) capturing bigram through 4-gram patterns, with max-over-time pooling and dropout
- Built a 2-layer BiLSTM (hidden dim 128) to capture long-range, bidirectional context
- Compared models on accuracy, F1, precision, and recall, with confusion matrices, training curves, and error analysis

**Takeaways.** The CNN edged out the BiLSTM (64.3% vs 63.4% accuracy), suggesting local phrase patterns matter more than sequence for short posts. Both models overfit quickly on the small dataset, and error analysis showed they rely on keywords rather than context. Financial stress proved harder to detect than general stress, partly due to class imbalance in the finance subset.

**Skills:** neural network architecture design, embedding training, overfitting diagnosis, error analysis, honest reporting of model limitations.

📄 [Project slides (PDF)](./financial-stress-detection-slides.pdf) · 💻 [Full notebook (HTML)](https://htmlpreview.github.io/?https://github.com/Alasya-Z/Portfolio-Projects-Data-Science-/blob/main/financial-stress-detection-notebook.html)

### 3. Health Insurance Coverage in the US
*R | EDA and logistic regression on survey microdata*

**Problem.** Access to health insurance shapes both health outcomes and financial security. Using 2021 American Community Survey microdata from IPUMS USA (over 10 million records before cleaning), this project identifies which demographic and socioeconomic groups are least likely to be insured. Completed with a partner for Data 413.

**Methodology.**
- Built a custom IPUMS extract with variables on coverage, income, employment, citizenship, and demographics
- Cleaned placeholder codes and missing values, then recoded categorical variables into analysis-ready binary formats
- Ran exploratory analysis of coverage rates across income, race, sex, and employment groups
- Fit a logistic regression predicting insurance coverage and interpret coefficients in policy terms

**Takeaways.** Veteran status, employment, and marriage show the strongest positive effects on coverage. Hispanic individuals and men are less likely to be insured even after controlling for income and age. Income itself matters less than expected, likely because Medicaid covers many low-income individuals. The results point to specific communities that could benefit from targeted outreach.

**Skills:** large-scale survey microdata (IPUMS/ACS), data cleaning and recoding, EDA, regression interpretation, translating statistical results into policy implications.

📄 [Written report (HTML)](https://htmlpreview.github.io/?https://github.com/Alasya-Z/Portfolio-Projects-Data-Science-/blob/main/health-insurance-coverage-report.html)

### 4. Topic Modeling on Amazon Reviews
*Python | Unsupervised NLP (side project)*

**Problem.** Can unsupervised learning surface meaningful themes from raw product reviews without any labels?

**Methodology.** Vectorized 20,000 Amazon food reviews with TF-IDF (14,546-term vocabulary, filtering terms that appear in over 80% of reviews), then fit and compared NMF and LDA topic models, examining the top terms per topic for interpretability.

**Skills:** text vectorization, dimensionality reduction, unsupervised learning, model interpretability.

📄 [Notebook (HTML)](https://htmlpreview.github.io/?https://github.com/Alasya-Z/Portfolio-Projects-Data-Science-/blob/main/topic-modeling-amazon-reviews.html)

---

## About Me

I graduated from American University in May 2026 with degrees in Economics and Data Science. My interests center on labor markets, economic mobility, housing, and income inequality, and I like projects where careful data work leads to conclusions people can actually act on.

**Contact:** az5922a@american.edu · alasyaz123@gmail.com 

