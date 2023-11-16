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

Box Office Mojo Worldwide Yearly Box Office Dataset:
    
Our initial analyses showed that for 90% of the movies present in the CMU Movie Summary Corpus the box office revenue data is missing. We do need this data for the first two research questions, as such we have opted to use the Box Office Mojo database to fill composite 

Budget Dataset

Validate language count - revenue positive linear relation as confounder.