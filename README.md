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

mport seaborn as sns

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

# Files 

student.ipynb : Complete analysis containing all files, dataframes and visualizations. Useful for seeing the project workflow from start to finish. 

Budgets_Genres_MostProfitable.ipynb: Analysis of most profitable movies, relationship between profit and gross and high performing genres

Studios_Reviews.ipynb: Analysis of top performing studios. Analysis of reviews.

# Data Cleaning and Processing

Data cleaning has been performed on all datasets. 

# Budgets, Genres & Most Profitable 

Files Cleaned: tn_movies_budgets, title basics

1. Objects converted to int64 and floats depending on data type and output
    Completed using a function called def_clean()
2. Created gross profit and profit margin columns 
3. Performed a join function to merge genre from imdb basics to tn_movie_budgets 

# Studios & Reviews 

Files Cleaned: bom_movie_gross, tmdb_movies

1. Converted foreign gross column to a float64
2. Created a new column for total_gross 
3. Created a new dataframe containing studios by total_gross 
4. Created a time series graph 


# Question 1 : What is the distribution of profits and revenue across the film industry and why does it matter? What are their relationships? 

![hist_total_gross_bom.png](images/hist_total_gross_bom.png)

![dist_total_gross.png](images/dist_total_gross.png)

![dist_profit_margins.png](images/dist_profit_margins.png)

![boxplot_total_gross.png](images/boxplot_total_gross.png)

![boxplot_production_budget.png](images/boxplot_production_budget.png)

![scatter_prod_budg_total_gross.png](images/scatter_prod_budg_total_gross.png)

![scatter_dom_foreign_gross_bom.png](images/scatter_dom_foreign_gross_bom.png)

![regplot_tn_movies.png](images/regplot_tn_movies.png)

![regression_prod_vs_gross.png](images/regression_prod_vs_gross.png)

# Is there a correlation between the top 100 grossing films and their budgets? 

![regression%20plot%20of%20budget%20vs%20total%20gross.png](attachment:regression%20plot%20of%20budget%20vs%20total%20gross.png)![scatter%20budget%20vs%20gross.png](attachment:scatter%20budget%20vs%20gross.png)![budget%20vs%20gross%20line%20graph.png](attachment:budget%20vs%20gross%20line%20graph.png)


# Question 2 : What are the most successful studios and their distribution of revenue and profit?

![dist_sum_of_studio_earnings.png](images/dist_sum_of_studio_earnings.png)

![studio_total_gross_dist.png](images/studio_total_gross_dist.png)

![top_5_studios_violin_plot.png](images/top_5_studios_violin_plot.png)

The Average studio in the top 5 made 15.97 movies per year from 2010-2018

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

The large spread of success and failure in the film industry is clearly present in the datasets analyzed above. The range of the data is interesting because it indicates clear winners and losers both in films and studios. ccesses would be a great start to a next phase of analysis. 

# Recommendations 

Allocate a budget for multiple movies and adjust it based on genre

Budget for a breakout feature but be very careful of putting all your eggs in 1 basket. the top 5 studios made multiple films with a breakaway success enabling their high level of profit

Horror films are consistently showing high profit margins.


```python
import os
import glob
```


```python
filepath = "C:/Users/User/Desktop/*.png"
```


```python
images = glob.glob(filepath)
images
```




    ['C:/Users/User/Desktop\\avg_votes_popularity.png',
     'C:/Users/User/Desktop\\avg_vote_vote_count.png',
     'C:/Users/User/Desktop\\boxplot_production_budget.png',
     'C:/Users/User/Desktop\\boxplot_total_gross.png',
     'C:/Users/User/Desktop\\budget vs gross line graph.png',
     'C:/Users/User/Desktop\\change_directories_git.png',
     'C:/Users/User/Desktop\\dist_avg_votes_per_film.png',
     'C:/Users/User/Desktop\\dist_profit_margins.png',
     'C:/Users/User/Desktop\\dist_sum_of_studio_earnings.png',
     'C:/Users/User/Desktop\\dist_total_gross.png',
     'C:/Users/User/Desktop\\genre_count_most_profitable_movies.png',
     'C:/Users/User/Desktop\\hist_total_gross_bom.png',
     'C:/Users/User/Desktop\\regplot_tn_movies.png',
     'C:/Users/User/Desktop\\regression plot of budget vs total gross.png',
     'C:/Users/User/Desktop\\regression_popularity_vote_count.png',
     'C:/Users/User/Desktop\\regression_prod_vs_gross.png',
     'C:/Users/User/Desktop\\regression_vote_popularity.png',
     'C:/Users/User/Desktop\\reg_budget_prod_100.png',
     'C:/Users/User/Desktop\\scatter budget vs gross.png',
     'C:/Users/User/Desktop\\scatter_dom_foreign_gross_bom.png',
     'C:/Users/User/Desktop\\scatter_prod_budg_total_gross.png',
     'C:/Users/User/Desktop\\Screenshot_1.png',
     'C:/Users/User/Desktop\\Screenshot_10.png',
     'C:/Users/User/Desktop\\Screenshot_2.png',
     'C:/Users/User/Desktop\\Screenshot_3.png',
     'C:/Users/User/Desktop\\Screenshot_4.png',
     'C:/Users/User/Desktop\\Screenshot_5.png',
     'C:/Users/User/Desktop\\Screenshot_6.png',
     'C:/Users/User/Desktop\\Screenshot_7.png',
     'C:/Users/User/Desktop\\Screenshot_8.png',
     'C:/Users/User/Desktop\\Screenshot_9.png',
     'C:/Users/User/Desktop\\studio_total_gross_dist.png',
     'C:/Users/User/Desktop\\top_5_studios_violin_plot.png']




```python
important_images = [i for i in images if "Screenshot" not in i]
important_images
```




    ['C:/Users/User/Desktop\\avg_votes_popularity.png',
     'C:/Users/User/Desktop\\avg_vote_vote_count.png',
     'C:/Users/User/Desktop\\boxplot_production_budget.png',
     'C:/Users/User/Desktop\\boxplot_total_gross.png',
     'C:/Users/User/Desktop\\budget vs gross line graph.png',
     'C:/Users/User/Desktop\\change_directories_git.png',
     'C:/Users/User/Desktop\\dist_avg_votes_per_film.png',
     'C:/Users/User/Desktop\\dist_profit_margins.png',
     'C:/Users/User/Desktop\\dist_sum_of_studio_earnings.png',
     'C:/Users/User/Desktop\\dist_total_gross.png',
     'C:/Users/User/Desktop\\genre_count_most_profitable_movies.png',
     'C:/Users/User/Desktop\\hist_total_gross_bom.png',
     'C:/Users/User/Desktop\\regplot_tn_movies.png',
     'C:/Users/User/Desktop\\regression plot of budget vs total gross.png',
     'C:/Users/User/Desktop\\regression_popularity_vote_count.png',
     'C:/Users/User/Desktop\\regression_prod_vs_gross.png',
     'C:/Users/User/Desktop\\regression_vote_popularity.png',
     'C:/Users/User/Desktop\\reg_budget_prod_100.png',
     'C:/Users/User/Desktop\\scatter budget vs gross.png',
     'C:/Users/User/Desktop\\scatter_dom_foreign_gross_bom.png',
     'C:/Users/User/Desktop\\scatter_prod_budg_total_gross.png',
     'C:/Users/User/Desktop\\studio_total_gross_dist.png',
     'C:/Users/User/Desktop\\top_5_studios_violin_plot.png']




```python
filepath_source = filepath.replace("*.png", "")
filepath_source
```




    'C:/Users/User/Desktop/'




```python
filepath_dest = "./images/"
```


```python
image0 = important_images[0]
image0
```




    'C:/Users/User/Desktop\\avg_votes_popularity.png'




```python
for image in important_images:
    os.system(f"cp {image} {filepath_dest}")
```


```python
files = """![hist_total_gross_bom.png](attachment:hist_total_gross_bom.png)

![dist_total_gross.png](attachment:dist_total_gross.png)

![dist_profit_margins.png](attachment:dist_profit_margins.png)

![boxplot_total_gross.png](attachment:boxplot_total_gross.png)

![boxplot_production_budget.png](attachment:boxplot_production_budget.png)

![scatter_prod_budg_total_gross.png](attachment:scatter_prod_budg_total_gross.png)

![scatter_dom_foreign_gross_bom.png](attachment:scatter_dom_foreign_gross_bom.png)

![regplot_tn_movies.png](attachment:regplot_tn_movies.png)

![regression_prod_vs_gross.png](attachment:regression_prod_vs_gross.png"""
```


```python
for f in files.split("\n"):
    print(f.replace("attachment:", "images/"))
```

    ![hist_total_gross_bom.png](images/hist_total_gross_bom.png)
    
    ![dist_total_gross.png](images/dist_total_gross.png)
    
    ![dist_profit_margins.png](images/dist_profit_margins.png)
    
    ![boxplot_total_gross.png](images/boxplot_total_gross.png)
    
    ![boxplot_production_budget.png](images/boxplot_production_budget.png)
    
    ![scatter_prod_budg_total_gross.png](images/scatter_prod_budg_total_gross.png)
    
    ![scatter_dom_foreign_gross_bom.png](images/scatter_dom_foreign_gross_bom.png)
    
    ![regplot_tn_movies.png](images/regplot_tn_movies.png)
    
    ![regression_prod_vs_gross.png](images/regression_prod_vs_gross.png
    


```python
# put them in a string 

files = """![dist_sum_of_studio_earnings.png](attachment:dist_sum_of_studio_earnings.png)

![studio_total_gross_dist.png](attachment:studio_total_gross_dist.png)

![top_5_studios_violin_plot.png](attachment:top_5_studios_violin_plot.png)"""
```


```python
for f in files.split("\n"):
    print(f.replace("attachment:", "images/"))
```

    ![dist_sum_of_studio_earnings.png](images/dist_sum_of_studio_earnings.png)
    
    ![studio_total_gross_dist.png](images/studio_total_gross_dist.png)
    
    ![top_5_studios_violin_plot.png](images/top_5_studios_violin_plot.png)
    


```python
files  = """![dist_sum_of_studio_earnings.png](images/dist_sum_of_studio_earnings.png)

![studio_total_gross_dist.png](images/studio_total_gross_dist.png)

![top_5_studios_violin_plot.png](images/top_5_studios_violin_plot.png)"""
```


```python
for f in files.split("\n"):
    print(f.replace("attachment:", "images/"))
```

    ![dist_sum_of_studio_earnings.png](images/dist_sum_of_studio_earnings.png)
    
    ![studio_total_gross_dist.png](images/studio_total_gross_dist.png)
    
    ![top_5_studios_violin_plot.png](images/top_5_studios_violin_plot.png)
    


```python

```
