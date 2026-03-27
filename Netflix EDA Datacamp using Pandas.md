# Netflix 1990s Exploratory Data Analysis 🍿

## Project Overview
What started in 1997 as a DVD rental service has since exploded into one of the largest entertainment and media companies. Given the large number of movies and series available on the platform, this project flexes exploratory data analysis skills to dive into the entertainment industry.

Assuming the role of a data analyst for a production company that specializes in nostalgic styles, this project researches movies released in the 1990s. By delving into Netflix data and performing exploratory data analysis, we can better understand the trends of this awesome movie decade!

### Objectives
1. **Find the most frequent movie duration** in the 1990s (saved as `duration`).
2. **Count the number of short action movies** (less than 90 minutes) released in the 1990s (saved as `short_movie_count`).

---

## The Data (`netflix_data.csv`)

| Column | Description |
| :--- | :--- |
| **show_id** | The ID of the show |
| **type** | Type of show (Movie or TV Show) |
| **title** | Title of the show |
| **director** | Director of the show |
| **cast** | Cast of the show |
| **country** | Country of origin |
| **date_added** | Date added to Netflix |
| **release_year** | Year of Netflix release |
| **duration** | Duration of the show in minutes |
| **description** | Description of the show |
| **genre** | Show genre |

---

## Python Solution

Below is the code used to perform the analysis and extract the requested insights:

```python
# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

"""
Question 1: What was the most frequent movie duration in the 1990s? 
Save an approximate answer as an integer called duration (use 1990 as the decade's start year).
"""
# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")

# Exploratory data analysis
print(netflix_df.head(), "\n", netflix_df.dtypes , "\n", netflix_df.info())

#------------------------------------------------------------------
# Filter for movies released between 1990 and 1999
movies_since_1990s = netflix_df[(netflix_df['type'] == "Movie") & 
                                (netflix_df['release_year'] >= 1990) & 
                                (netflix_df['release_year'] <= 1999)]
print(movies_since_1990s)

# Calculate the mode of the duration
duration = int(movies_since_1990s['duration'].mode()[0])

print("Most frequent duration in the 1990s:", duration)

#------------------------------------------------------------------

"""
Question 2: A movie is considered short if it is less than 90 minutes. 
Count the number of short action movies released in the 1990s and save this integer as short_movie_count.
""" 
short_movie_count = len(netflix_df[(netflix_df['genre'] == 'Action') &
                                (netflix_df['release_year'] >= 1990) & 
                                (netflix_df['release_year'] <= 1999) &
                                (netflix_df['duration'] < 90)])

print("Number of short action movies in the 1990s:", short_movie_count)
