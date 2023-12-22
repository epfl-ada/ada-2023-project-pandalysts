# The Effect of Languages on Movies: The Multi-Faceted Story of a Single Parameter
### *By Filip Mikovíny, Eylül İpçi, Minghui Li, Aybüke Çalık, Aral Arbatlı*


## Abstract

Languages are an important part of a movie, helping us infer production and plot context, availability and historical or artistic references. Yet it can tell us a much bigger story, one of utility, cultural blending and genre-specific expectations. We will study the relationship between the languages present in a movie and the box office revenue, understand if languages present in a country's movies will align with known cultural interactions and test if certain languages dominate certain genres. Data cocnerning a cohort of approximately 80'000 movies from the CMU Movie Summary Corpus datatset, released between 1888 and 2016 and appropriately enriched, is to be considered. We will fit a linear model to predict the box office revenue of a movie given its language composition, and will attempt to test certain stereotypes pertaining to the Martial Arts, Romance and Gangster movie genres while making similar assessments in the War and LGBT tagged movies.

## Research Questions

This project studies four central questions about the place of languages in movies:  
- Q1: Is there a correlation between the language variety in a movie and its box office revenue? 
- Q2: The use of which languages are associated with higher box office revenues? 
- Q3: Which languages a country's movies have other the native one? 
    
    - Taking the US, India and the UK into account
- Q4: Which languages are more present in a specific genre?
    
    - Considering the following genres (stereotypes to validate in parantheses): 
        - Martial Arts (East Asian Languages)
        - Samurai (Japanese)
        - Romance (French)
        - Gangster (Italian)
        - War
        - LGBT

## Additional Datasets

**1. Box Office Mojo Worldwide Yearly Box Office Dataset:**
    
Our initial analyses showed that for 90% of the movies present in the CMU Movie Summary Corpus the box office revenue data is missing. We do need this data for the first two research questions, as such we have opted to use the Box Office Mojo database to increase our box office revenue data. 

**2. The Movies Dataset:**

We want to see if the budget size of a movie is a possible confounder for the relation between box office revenue and the number of languages present in a movie. As a result, The Movies Dataset, a dataset that includes budget data on 45'000 movies from 2017 and before, was used to extract budget data. We merged the main movie.metadata.csv dataframe from the CMU Database with the movies_metadata.csv from the Movies Dataset, on a left join by combining the `Movie_name`, `Movie_release_year` and `Movie_runtime` columns to ensure unique indexing for all movies. 

## Methods

### 1. OLS Linear Regression
We used linear regression to understand the correlation between individuals languages and `Movie_box_office_revenue`, and to establish a linear regression equation to predict revenue from the language profile of a movie. We also used linear regression plots to establish the correlation between budget size and the box office revenue.

### 2. T-tests
We will be using t-tests to understand if there are statistically significant changes between the general language distribution in the dataset and the language distribution in a chosen genre. For example, the Hindi language is the second most prevalent language in the dataset as a whole, but is that the case for war movies as well? The same will be done for the genre distribution in general and the genre distribution in a given language.

### 3. Matching on Budget, Genre and Runtime
After assessing the percentage of data availability and the distribution of certain features across the dataset, performing a matched study by matching for the `Movie_runtime`,`budget` and `Movie_genres` variables was decided to be pertinent for a more rigorous analysis. We used a condition of having at least one matching element for the genre variable (since it is a list of multiple applicable genre tags per movie), and defined a percentage difference similarity function with a threshold of 20% to assess the matching of the runtime and budget continuous variables. We then performed our statistical tests again on the matched samples.

For Q4, we identified the presence of the language, whose stereotype in the genre is being evalauted, as the treatment condition for control-treatment group separation.

## Project Flow
### Step 1: Data Preprocessing and Scraping
We incorporated all the relevant datasets and assess what data we have. The distribution and the missing data percentage is calculated for all variables, and the distribution was plotted for the language, revenue, genre and budget data. We then merge the additional revenue and budget datasets into the original CMU Movie dataset to assess the overall available data in the end. 

We extract the year of release for all movies and deposit them in the new `Movie_release_year` column. The language data was also converted into `list` objects for better accessibility and use (every movie has a list object where every language present in the movie is listed). For further analyses we filtered out the missing values.

### Step 2: Data Visualisation and Correlations
The relevant data stated in the Q1-Q4 (language, genre, revenue and budget) were first visualised to assess their overall distribution within the dataset. This would give us the normative status to compare with for the genre-language analyses, but also account for possible bias in data. 

Indeed, given the overwhelming dominance of English in the language distribution, we decided to look beyond English and compare the secondary languages amongst themselves as well for the genre-language relations (Q4).

In fact, the pairs of data compared in each research question are as follows:

- Q1: Box office revenue and total langauge count per movie, budget as a possible confounder
- Q2: Box office revenue and different languages
- Q3: Language and country of production
- Q4: Genre and unique language counts

We then plotted the relevant data pairs in each research question against each other to detect possible correlations and trends. For Q3, we also plot the evolution of the secodary language counts in movies over the years to analyse for cultural interaction trends (for example, how does the presence of Spanish in American evolve over the years?).

### Step 3: Linear Regression and Initial Statistical Tests

In order to determine which languages are associated with a higher box office revenue and to be able to predict a box office revenue using the language composition of a movie, we implemented the Ordinary Least Squares Linear Regression to determine the coefficients of each language present in the dataset and the p-value they came with. The languages showing statistically significant association with revenue (positively or negatively) were then selected as languages of interest. 

We performed a t-test alongside a Pearson's correlation to examine the correlation between the language count in movies and the box office revenue, which was determined in the data visualisation initially. Having found a strong correlation, we did the same with the budget, and obtained a strong correlation as well. This then led us to consider the budget as a possible covariate in Step 4 to assess.

### Step 4: Data Balancing and Further Statistical Tests

Given the skewed distribution of the languages and the dominant presence of the English language, we looked for ways to balance the data and mitigate potential biases. Especially in the case of Genre - Movie association, we took the decision to disregard the English language given its sheer dominance, and compare the other languages amongst each other, per case. 

After identifying the budget as a potential covariate while assessing connections between languages and box office revenue, we decided to run a Standard Mean Difference on another continuous variable, the runtime, as well. We saw that it wasn't balanced across the dataset, and decided to perform matching on it as well. Genre was matched as well, given the very varied distribution accross the dataset.

### Step 5: Compiling the Overall Results of the Research Questions

After obtaining the data visualisations and the results of the statistical test we employed in certain research questions, we  evaluated the overall outcome of the each research question and interpret them. The linear regression models, (in)validated stereotypes of genre-language relationships and our other answers were finalised

### Step 6: Data Story

We displayed all our findings in a blog-post to tell a coherent story about languages in movies and its diverse, multi-faceted impact on this industry and art.

## Proposed Timeline

**Steps 1-3:**   17.11.2023 P2 Deadline 

**Step 4:** 08.12.2023

**Step 5:** 15.12.2023

**Step 6:** 22.12.2023

## Team Organisation

| Team Member   | Tasks         | 
| ------------- |:-------------:|
| Filip Mikovíny | <ul><li>In charge of Q2 Analysis (Language - Revenue)</li><li>Mojo Dataset Preprocessing</li><li>Performing Linear Regressions</li><li>Data Visualisation</li><li>Matching for Budget, Genre and Runtime for Q2 Analysis</li></ul> |
| Eylül İpçi    | <ul><li>In charge of Q4 Analysis (Language - Genre)</li><li>Data Visualisation</li><li>Performing the T-tests on language and genre distributions</li><li>Matching on Budget for Q4 Analysis</li></ul>     |   
| Minghui Li |    <ul><li>In charge of Q1 analysis (Language Count - Revenue)</li><li>Data Visualisation</li><li>Data Scrapping and Preprocessing</li><li> Data Story Template Preparation</li><li>Matching on Budget, Genre and Runtime for Q1</li></ul>  |    
| Aybüke Çalık |    <ul><li>In charge of Q3 analysis (Language - Country)</li><li>Data Visualisation</li><li>Data Exploration</li><li>Data Commentary</li></ul>  |    
| Aral Arbatlı |    <ul><li>In charge of Q1 - Budget subsection analysis</li><li>Data Visualisation</li><li>Budget Dataset Preprocessing</li><li>Writing the Readme and the Data Story Text</li><li>Matching and SMD Analysis</li></ul>  |  
