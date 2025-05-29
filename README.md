# Movie-Industry
# Overview
This project analyzes a movie industry dataset to explore the relationship between movie budgets and gross earnings, along with other factors influencing financial performance.

# Data Cleaning
Handling Missing Values:
Numerical Columns:

budget (28% missing): Imputed with 0 (df['budget'].fillna(0, inplace=True)).

gross (2% missing): Imputed with 0 (df['gross'].fillna(0, inplace=True)).

votes and runtime: Imputed with 0 for missing values in later rows.

Categorical Columns:

rating (1% missing): Imputed with the mode (df['rating'].fillna(df['rating'].mode()[0], inplace=True)).

company: Left as NaN for missing values.

Data Type Correction:

Converted votes to int64 after imputation: df['votes'] = df['votes'].astype('int64').

Kept budget, gross, and runtime as float64 (post-imputation, some appear as integers due to 0 values).

Categorical columns (rating, genre, country, company) remained as object but could be converted to category for efficiency.

Handling Duplicates:
Checked for duplicates with df.duplicated().sum() and removed them: df.drop_duplicates(inplace=True).


# Key Insights

# Budget and Gross Relationship:
A positive but non-linear correlation exists between budget and gross. High-budget films (e.g., "Star Wars: Episode V" with $18M budget and $538M gross) often yield high earnings, but low-budget films (e.g., "Airplane!" with $3.5M budget and $83M gross) can also achieve strong returns.

Variability in gross earnings for similar budgets suggests other factors (e.g., genre, director, studio) significantly impact performance.

# Data Quality:

Imputing missing budget and gross with 0 (28% and 2% missing, respectively) may underestimate financial performance, particularly for recent films (e.g., 2020 releases with 0 gross).

Inconsistent month names in monthcorrect (e.g., "Octo", "Febr") required correction for accurate temporal analysis.
# Temporal Patterns:

Movies from 1980–2020 show evolving budget and gross trends, with older blockbusters achieving high returns on modest budgets.
Summer releases (June, July) are common, likely targeting peak audience seasons.
# Business Recommendations:
Investment: High budgets increase potential returns but carry risks due to variability. Low-budget films in popular genres (e.g., Comedy, Action) can yield high returns on investment.
Release Strategy: Prioritize summer releases (June, July) for maximum audience reach.
Data Improvement: Use median imputation by genre or year for budget and gross to avoid skew from 0 imputation.
Studio and Genre Focus: Major studios (e.g., Warner Bros., Lucasfilm) and genres like Action and Comedy tend to have higher gross earnings.
