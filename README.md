# Microsoft Movie Studio Analysis

![download (2)](https://github.com/Sdec30/Phase1_ProjectDAT7_MicrosoftMovieAnalysis/assets/140704907/c11ecbbc-c7c1-4a8e-a738-8a669bce511c)

Author: **Sneha Bhaskar**

Date: 12 August 2023

 # <font color='red' > Overview </font>

In response to the growing trend of big companies investing in movie studios. Microsoft has decided to enter the entertainment arena by establishing a new movie studio. However, lacking experience in the film industry, Microsoft company wants to seek valuable insights before embarking on its cinematic journey. As part of this exploratory phase, I have been given a task to analyze the current state of the box office and identify the most successful film genres. This research aims to provide actionable insights to assist the head of Microsoft's new movie studio in making informed decisions regarding the types of films to create.

I will analyze the data provided to identify what attributes the top-performing films have in common using my data analysis, statistics, and visualizations. Through my analysis, I have been able to identify the top genres, average runtime for a movie, and correlation between domestic gross with variables like runtime, genres, and production budget. Based on these findings, I have made recommendations to consider top genres while also exploring why other genres are not making success in terms of revenue, to stick with average runtime, and aim for the highest production budget to yield high returns because quality matters the most when it comes to success.

# <font color='red' > Business Problem </font>

As big companies like Universal Pictures, Paramount, Warner Bros, and Disney are investing in original video content and Microsoft company is looking to join this trend by creating its very own "MOVIE STUDIO". But they are currently facing the challenge of navigating an unfamiliar industry. With no prior experience in creating movies, Microsoft seeks insights into the most successful film genres currently dominating the box office.


As part of this exploration, my role is to analyze box office trends and translate these findings into actionable strategies that the head of Microsoft's movie studio can use to make informed decisions on the types of films they want to produce.

Questions to consider:

- What is the top-ranking movie genre?
- What should be the average length of the movie?
- Correlation between domestic gross profit and other variables like runtime, genres, and production budget?
  
By finding answers to these questions, I believe I can provide valuable insight to Microsoft to identify the gaps they have been looking to produce a successful launch of their movie studio. 

 # <font color='red' > Data Understanding </font>

 For this analysis, I utilized datasets from BoxOffice Mojo, IMDB, and The Numbers to get accurate actionable insights to the head of Microsoft's new movie studio. 


<font color='Green' >Background information on datasets; </font>

**IMDB** is the Internet Movie Database that provides a wealth of information about movies, television shows, video games, and all aspects of the entertainment industry. However, for this analysis, I used IMDB for gathering information on movies only as this is the main aspect of this project. The most primary categories of information you can find on the IMDB website for most films are;
- Title and Year
- Top 250 Movies
- Most popular movies
- Genres
- Runtime
- Number of votes
- Top Box office

The IMDB datasets used in this project were categorized into two data's

1. Title Basics Dataset - Had 146,144 items focusing on titles, genres, runtime, year. These datasets contained duplicates of titles and missing values for runtime, which were discussed in the data preparation section. 
2. Title Rating Dataset - Had 73,856 items focusing on average ratings and number of votes. This dataset had no duplicates or missing values.

**Box Office Mojo** is an online movie publication and box office reporting service. Its primary function is to track box office revenue in a systematic, algorithmic way. The most common information we can find about movies from this website is;
- Domestic gross
- Foreign gross
- Top 10 domestic/foreign gross
- Distributer or studios
- Box office showdowns

The dataset used for this had 3387 items. For this dataset my main focus was domestic gross for analysis, the data type for this was in float which was converted to integer for better understanding.  

**The Number** is another online platform that provides the financial analysis for each movie in terms of;
- Investor scenarios
- Domestic and international analysis
- Production Budget
- Comparison between different films' financial status

The dataset used for this had 5782 items focusing on the title, release date, production budget, domestic gross, and worldwide gross. My main interest was the production budget and domestic gross, which had a '$' string value in front of the number that was covered to float and then to integer (the full method is explained in data preparation). 


Using pieces of information from these datasets, I was able to answer my questions proposed in business problems based on the target variables (Genres, Runtime, Domestic Gross, Production Budget)

 # <font color='red' > Data Preparation </font>

After importing and reviewing the datasets, I found that there were missing values, duplicates, incorrect data types, and outliers for many variables that were interesting for this project. 
 

- For the df1 Dataset, I first converted domestic_gross datatype from float to integer. The reason why I chose to correct the datatype for the targeted variable was that floating numbers can suffer precision issues like rounding errors. By representing money as an integer it can avoid this imprecision, therefore it's easier to perform any arithmetic functions. 
- For the df2 Dataset, I found duplicated titles in the form of primary_title and original_title. By removing the duplicates we can avoid skewing the data analysis and giving misleading results. I also found there were missing values for runtime_minutes, which were replaced with zero (0), replacing them with zero instead of dropping or deleting them can save us from losing other valuable information from that row for example genres. 
- For the df3 Dataset, there were no missing values or duplicates were detected. 
- For the df4 Dataset, I again converted production_budget, domestic_gross and worldwide_gross from string to float to integer. For this data cleaning, I used the Stackerflow platform to figure out how to remove the string element "dollar sign". This mission was achieved first by using the 'locale' module in Python to convert string representations of numbers into actual float numbers. The 'locale.atof()' function is used to convert string with locale-aware formatting (e.g. currency symbols) into a float which was then easy to convert into integers. 

After cleaning the datasets, I merged df1,df2, and df3 datasets together to answer what are the top-ranking movie genres, what should be the average runtime for a movie and whether is there any correlation between domestic gross, runtime, and genres. 

For this I limited the number of values in this merged dataset to 2000 in order to collect a meaningful value of reviewed films and expanded the genres column into subsets of genres to get a better understanding of top-ranking genres Microsoft company should focus on to get a blockbuster movie and increase in profit. Also did last-minute data cleaning for the final merged dataset, where I detected duplicate columns for a year. 

I did further narrow this scope as my analysis progressed to the top 1500 films ranked by number of votes to figure out; 
- Top Ranking genres
- Average runtime in minutes 
- Correlation between domestic gross and variables like genres, runtime, and production budget. 

The correlation between the production budget and domestic gross was purely done using the df4 dataset. 

 # <font color='red' > Data Modeling </font>

 As I completed my cleaning steps of the dataframes, I utilised the visualizations below to see the correlation that exists between the variables in the datasets. 

### **GENRES**

I selected the top 1,500 domestic films based on the number of votes and average rating they received. After ranking them by their ratings/votes (highest_rated_domestic), I was able to determine at least the top 5 genres that performed the best at the box office from 2010 to 2018. 

For analyzing the top genres I preferred using a bar plot as this gives a clear visual representation of the data. As bar plots are designed to represent categorical data on one axis and quantitative on the other. Below I used x = genre_count_ranks.index which is plotted on the horizontal axis, representing the name of genres (Categorical) and y genre_count_ranks. values represent genres and their total count (quantitative). 

- From 2010 to 2018, an examination of movie popularity by genre revealed a clear hierarchy of audience preference. Drama films stood at the forefront, captivating audiences with their compelling narratives and relatable themes. Following closely behind, comedies consistently brought laughter to theatres, securing their place as the second most preferred genre. Romance movies, with their heartwarming and often heart-wrenching tales, clinched the third spot, while action-packed films, though thrilling and adrenaline-fueled, settled in fourth. Documentaries were close to action suggesting that there is a population that prefers real-based documentaries for example about a celebrity or politicians or even about athletes' life. The ranking suggests a significant preference for story-driven genres, indicating a potential trend in audience desire to watch.

  
![Top ranking movie genres](https://github.com/Sdec30/Phase1_ProjectDAT7_MicrosoftMovieAnalysis/assets/140704907/b951e2b6-f832-46d3-8c9a-054e9780e00b)

### **RUNTIME**

If Microsoft decides to open a movie studio and is trying to gauge the ideal movie length, it might be wise to start with a standard runtime (100 minutes) to play it safe. 

I achieved this by targeting runtimes for each genre and then finding the average runtime required. 

Using a bar plot to analyze the relationship between genre and runtime in minutes offers a clear visual presentation of data, allowing for each comparison between different genres. 
- Most of the genres like horror, thriller, drama, and adventure ranged from 90-100 minutes, however, the action, romance, sport, and biography ranged from 101-116 minutes. There were a few genres like family, sci-fi, and documentaries ranging from 29-87 minutes. 
- However, when we look at the average runtime for these genres, it suggests that a movie should run for at least 100 minutes.

![Medium runtime for movie genres](https://github.com/Sdec30/Phase1_ProjectDAT7_MicrosoftMovieAnalysis/assets/140704907/cc4be6c6-e07a-4554-b1c8-ff804b5b8ebd)

### **Correlation between domestic_gross and runtime in minutes profit?**

To check the correlation between domestic gross and runtime I preferred using a scatter plot. A scatter plot is the best fit for representing the correlation between two quantitative values.

- The scatter plot between the domestic gross in millions and the runtime (length in minutes) of movies shows a weak correlation, it means that there isn't a strong linear relationship between these two variables (horizontal line of best fit = weaker correlation). 
- There isn't a universally "perfect" length of a movie. some shorter films (e.g. under 90 minutes) can be incredibly successful while some longer films (e.g. over 120 minutes) can be hit too. Conversely, movies by length can also be box office flops. 
- Therefore some points to consider from here is that if runtime is not the best factor for figuring out the success of a movie then what are other factors to consider for a movie's financial success?  Is the quality of the storyline, is it the genre, the actors involved, the direction, marketing, time of the year? 

![Profit made by movie length](https://github.com/Sdec30/Phase1_ProjectDAT7_MicrosoftMovieAnalysis/assets/140704907/48834f3c-ab89-497e-8b0f-588a3aa41223)

### **Correlation between domestic gross and movie genres ?**
- I used a horizontal bar plot to analyze the correlation between domestic gross and movie genres which involved displaying the average domestic gross for each genre. 

This plot gave insight into what genres are currently more popular or preferred by the domestic audience. 

- The bar plot showed that the Drama and Comedy genres generated the highest box office revenue of 3.0 to 3.5 million in the given domestic market. 
- Genres like adventure, documentary, crime, action, horror, and biography showed 0.1 to 2.5 million hits at the box office.  
- While Sci-fi, family, fantasy, animation and thriller were among the lowest generated box office revenue
- Also some genres like romance, mystery, music and sport shows no box office revenue

![Profit made by genres](https://github.com/Sdec30/Phase1_ProjectDAT7_MicrosoftMovieAnalysis/assets/140704907/ff0a3d67-f6df-4cee-bc2b-23b079b3135a)

### **Correlation between Production budget and Domestic gross?**

Does this mean the more money that is put into making a movie, the more money that movie will make? 

- Using a scatter plot we can see from the figure below, that there are a lot of dot points in the lower left portion of the graph and fewer movies in the top right portion of the graph. Higher budget movies appear to have higher revenue but how much higher and stronger is that relationship, is something to consider. This can be achieved by calculating the linear regression analysis.
- The slope of the line is positive and steep indicating a strong positive correlation between production budget and domestic gross. 

![budget vs profit](https://github.com/Sdec30/Phase1_ProjectDAT7_MicrosoftMovieAnalysis/assets/140704907/5f1b9bec-c57b-46d8-b168-9bfed8ee9951)

 # <font color='red' > Evaluation </font>

The analysis offers a comprehensive view of movie preferences by genre, average runtime, and box office revenue. Below is a concise evaluation of my findings: 

**GENRE PREFERENCE** 
- Drama takes the lead in terms of popularity, suggesting audiences appreciate in-depth storylines and emotions that they can resonate with.
- Comedies are the second most preferred, emphasizing the value of entertainment and laughter.
- Romance and Action films come next, suggesting audiences are diversified in their taste, seeking both emotional connection and adrenaline-pumping sequences.
- Some audiences also like Documentaries which indicates an interest in real-life narratives and educational content. 

**MOVIE RUNTIME**
- A majority of movie genres span between 90-116 minutes. Despite the range, the average runtime for most films is around 100 minutes.

**DOMESTIC GROSS**
- There is a weak correlation between runtime and domestic gross which signifies that the length of a movie doesn't necessarily predict its financial success. 
- Drama and Comedy movies unsurprisingly given their popularity, lead in terms of revenue. Interestingly, despite action films being fourth in terms of preferences, they aren't among the top-grossing genres. This might be due to production cost or market saturation. Genres like romance, mystery, music and sport not generating any revenue are surprising and may warrant further investigation. This could be due to fewer films being produced in these genres or issues with data collection.
- A positive correlation between a movie's budget and its revenue suggests that investment in production tends to lead to higher returns. 

 # <font color='red' > Conclusions </font>

In examining the movie industry from 2010 to 2018, it's evident that genre plays a pivotal role in a film's success with Drama and Comedy leading in audience preferences and revenue generation. While the average runtime of the film gravitates around 1 hour 40 minutes, the length isn't a direct predictor of financial success. Instead, the correlation between a movie's production budget and its gross indicates that investment in production often results in better returns.

Business Recommendation to Microsoft Company

Diversify Portfolio: While Drama and Comedy have shown strong results, it's important to maintain a diversified portfolio of movie genres to cater to varied audiences' preferences and mitigate risks.
Budget Allocation: Allocate the budget wisely, focusing on key areas like story quality, casting and post-production. A higher budget often correlates with higher returns, but it is crucial to ensure the budget is used effectively.
Market Research: Conduct more in-depth market research to understand why genres such as romance, mystery, and music aren't generating revenue. This will help in making informed decisions for future projects.
Movie marketing: With a movie runtime not being a direct predictor of success in terms of revenue, marketing strategies can play a pivotal role in the movie's success.
Some of the reasons to consider for analysis might not fully solve the business problems:

The data only span from 2010 to 2018, which might not capture the most recent trends.
Factors like the quality of the storyline, directorial talent, and cast performances might not be quantified easily but plays a huge role in a movie's success
The role of marketing, production, and release strategies is not captured in these datasets but can significantly impact a movie's success
Future improvements for these datasets

Regularly updating data can give a comprehensive view of current trends.
Incorporate additional data like critical reviews, audience feedback and competition between movies released in the same year to give a holistic view of the factors influencing movie success.
In conclusion, while the analysis provides valuable insights, the movie industry's complexity requires a multifaceted approach, considering both quantifiable metrics and qualitative factors to run a successful movie studio.
  
