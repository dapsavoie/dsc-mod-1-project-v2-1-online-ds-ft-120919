# Film Industry Analysis 

# Outline

# Prerequisites

You will need to install the following packages in python in order to create the development environment of this project 

Packages To Install: 

import os 
import numpy as np
import pandas as pd
from glob import glob 
import sqlite3
import seaborn as sns
import matplotlib.pyplot as plt

from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"


# The Project 

The two notebooks in this folder contain my analysis of multiple movie data sets.

The goal is to analyze these datasets to create a high level overview of the industry, drill into success cases and explore next steps for future analysis. 


# The Datasets

All movie related data from the following sources: 

* Box Office Mojo
* IMDB
* Rotten Tomatoes
* TheMovieDB.org

# Data Cleaning and Processing

Data cleaning has been performed on all datasets. 

# Budgets, Genres & Most Profitable ( (tn_movies_budgets, title basics)

1. Objects converted to int64 and floats depending on data type and output
    Completed using a function called def clean()
2. Created gross profit and profit margin columns 
3. Performed a join function to merge genre from imdb basics to tn_movie_budgets 

# Studios & Reviews (bom_movie_gross, tmdb_movies)
1. Converted foreign gross column to a float64
2. Created a new column for total_gross 
3. Created a new dataframe containing studios by total_gross 


# Question 1 : What is the distribution of profits and revenue across the film industry and why does it matter? What are their relationships? 

![hist_total_gross_bom.png](attachment:hist_total_gross_bom.png)

![dist_total_gross.png](attachment:dist_total_gross.png)

![dist_profit_margins.png](attachment:dist_profit_margins.png)

![boxplot_total_gross.png](attachment:boxplot_total_gross.png)

![boxplot_production_budget.png](attachment:boxplot_production_budget.png)

![scatter_prod_budg_total_gross.png](attachment:scatter_prod_budg_total_gross.png)

![scatter_dom_foreign_gross_bom.png](attachment:scatter_dom_foreign_gross_bom.png)

![regplot_tn_movies.png](attachment:regplot_tn_movies.png)

![regression_prod_vs_gross.png](attachment:regression_prod_vs_gross.png)


# Is there a correlation between the top 100 grossing films and their budgets? 

![regression%20plot%20of%20budget%20vs%20total%20gross.png](attachment:regression%20plot%20of%20budget%20vs%20total%20gross.png)![scatter%20budget%20vs%20gross.png](attachment:scatter%20budget%20vs%20gross.png)![budget%20vs%20gross%20line%20graph.png](attachment:budget%20vs%20gross%20line%20graph.png)


# Question 2 : What are the most successful studios and their distribution of revenue and profit?

![dist_sum_of_studio_earnings.png](attachment:dist_sum_of_studio_earnings.png)

![studio_total_gross_dist.png](attachment:studio_total_gross_dist.png)

![top_5_studios_violin_plot.png](attachment:top_5_studios_violin_plot.png)

# Question 3 : What are the top 50 highest grossing movies and genres?  

**Sum of Hundred Highest Grossing Movies:
138567941696 $**

**Sum of All Movies:
771092074906 $

**Percentage of Total Revenue Represented by the top 100 Movies
17.970349612644135 %**

**Percentage Contribution of the top 100 Production budgets**
11.944070765619085**

**Top 10 Movies by Total Gross : ** 

Avatar
Star Wars Ep. VII: The Force Awakens
Titanic
Titanic
Avengers: Infinity War
Jurassic World
The Avengers
Black Panther
Furious 7
Incredibles 2
Star Wars Ep. VIII: The Last Jedi

**Top 10 Movies by Most Profitable:**

Deep Throat
Paranormal Activity
The Blair Witch Project
The Gallows
El Mariachi
Mad Max
Super Size Me
Bambi
The Brothers McMullen
The Texas Chainsaw Massacre

![genre_count_most_profitable_movies.png](attachment:genre_count_most_profitable_movies.png)

# Relationship between reviews and vote counts from imdb movie data set

![avg_vote_vote_count.png](attachment:avg_vote_vote_count.png)

![dist_avg_votes_per_film.png](attachment:dist_avg_votes_per_film.png)

![avg_votes_popularity.png](attachment:avg_votes_popularity.png)

![regression_popularity_vote_count.png](attachment:regression_popularity_vote_count.png)


# Conclusion

The large spread of success and failure in the film industry is clearly present in the datasets analyzed above. The range of the data is interesting because it indicates clear winners and losers both in films and studios. This indicates a high risk profile in this industry and the disproportionate successes of big grossing films are in stark contrast to a densely mediocre performing bottom 75%. When you decide to allocate budgets, it is important to generate enough films in a year to accomodate the chance of mediocre performance and maximize the chance of a breakaway success. 

There is a clear relationship between the production budget of the top 100 films indicating that if you are looking to make a big movie, it is advisable to spend more to earn more. However, this is not a guaranteed success with the top production budgets and top earners being break away successes. My recommendation would be to set a minimal threshold for all films produced to ensure a quality of production competitive with success cases. 

Studios show similar spreads with big winners and lots of diverse outcomes in terms of profits and losses. The top 5 highest performing studios all had a breakway success as shown in the violin plot. If you are looking to enter into the top 5 studios, a breakaway success that tops box office is necessary. 

The final concrete insight of this analysis is the huge profitability of the action and adventure genres as indicated in the histogram above. Though multiple genres show strong levels of profitability, action and adventure top the list. The 3rd highest is 'not listed' indicating further data entichment is needed to label these films correctly for a more accurate analysis. 

Overall, the film industry is not low risk with a high chance of failure even when a large budget is allocated. By looking at certain categories such as action & adventure as well as further analysis into breakaway successes would be a great start to a next phase of analysis. 






