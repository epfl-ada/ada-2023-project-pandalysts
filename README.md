# The Effect of Languages on Movies: The Multi-Faceted Story of a Single Parameter
### *By Filip Mikovíny, Eylül İpçi, Minghui Li, Aybüke Çalık, Aral Arbatlı*


## Abstract

Languages are an important part of a movie, helping us infer production and plot context, availability and historical or artistic references. Yet it can tell us a much bigger story, one of utility, cultural blending and genre-specific expectations. We will study the relationship between the languages present in a movie and the box office revenue, understand if languages present in a country's movies will align with known cultural interactions and test if certain languages dominate certain genres. Data cocnerning a cohort of approximately 80'000 movies from the CMU Movie Summary Corpus datatset, released between 1888 and 2016 and appropriately enriched, is to be considered. We will fit a linear model to predict the box office revenue of a movie given its language composition, and will attempt to test certain stereotypes pertaining to the Martial Arts, Romance and Gangster movie genres while making similar assessments in the War and LGBT tagged movies.

## Research Questions

This project studies four central questions about the place of languages in movies:  
1. Is there a correlation between the language variety in a movie and its box office revenue? 
2. The use of which languages are associated with higher box office revenues? 
3. Which languages a country's movies have other the native one? 
    
    - Taking the US, India and [insert 3rd] to account
4. Which languages are more present in a specific genre?
    
    - Considering the following genres: 
        - Martial Arts
        - Romance
        - Gangster
        - War
        - LGBT

## Additional Datasets

**1. Box Office Mojo Worldwide Yearly Box Office Dataset:**
    
Our initial analyses showed that for 90% of the movies present in the CMU Movie Summary Corpus the box office revenue data is missing. We do need this data for the first two research questions, as such we have opted to use the Box Office Mojo database to increase our box office revenue data. 

**2. The Movies Dataset:**

We want to see if the budget size of a movie is a possible confounder for the relation between box office revenue and the number of languages present in a movie. As a result, The Movies Dataset, a dataset that includes budget data on 45'000 movies from 2017 and before, was used to extract budget data. We merged the main movie.metadata.csv dataframe from the CMU Database with the movies_metadata.csv from the Movies Dataset, on a left join by combining the `Movie_name`, `Movie_release_year` and `Movie_runtime` columns to ensure unique indexing for all movies. 

## Methods

### 1. Linear Regression
We used linear regression to understand the correlation between individuals languages and `Movie_box_office_revenue`, and to establish a linear regression equation to predict revenue from the language profile of a movie. We also used linear regression plots to establish the correlation between budget size and the box office revenue.

### 2. T-tests
We will be using t-tests to understand if there are statistically significant changes between the general language distribution in the dataset and the language distribution in a chosen genre. For example, the Hindi language is the second most prevalent language in the dataset as a whole, but is that the case for war movies as well? The same will be done for the genre distribution in general and the genre distribution in a given language.



