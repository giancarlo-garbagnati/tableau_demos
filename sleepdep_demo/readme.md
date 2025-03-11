# Sleep deprivation study data dashboard  

https://public.tableau.com/views/sleepdep/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link  

This was a simple (and not quite complete) dashboard build from a Kaggle dataset that was featured when I was looking around for a new Tableau project and grabbed my science lizard brain. I wanted to see if this data could show any insights into sleep habits and lifestyle choices and their affects on sleep and cognition. A disclaimer, as before, I am not a doctor or healthcare professional or behavior scientist - I'm just a data enthusiast.  

*A note on this project and the dataset*: As mentioned, I found it on Kaggle and believed (at first sight) that it looked like an interesting dataset and potentially fascinating project. However, upon chewing through the data, I was disappointed to note just how small the dataset was (60 records), which didn't seem to be large enough to show any meaningful insights from the features. Additionally, it wasn't clear how many of the features were empirically-derived (most or all of the cognitive metrics must have been somehow measured) or which (if any) were subjective or self-assigned by the participants or researchers. The Kaggle page wasn't clear on what study this data was coming from and a quick search on Google scholar and PubMed did not locate a paper from which this could be from (I suppose there's always the chance that it is from some research that's ongoing and/or unpublished, which might make more sense given the small number of records). For all of those reasons, I'm leaving the dashboard in a somewhat "unfinished" state.  

## Dashboard  

The dashboard is only formatted for desktop and as mentioned is in an "unfinished" state. The KPIs highlight:  
- `Avg Sleep Hours` - Average hours of sleep a night for the participants of the study.  
- `Avg Sleep Quality Score` - The average sleep quality score for the participants (measured on a 0-20 scale).  
- `Avg Daytime Sleepiness` - Average sleepiness rating for the participants (measured on a 0-24 scale).  
There are interactive filters for the different categories in: `Age Group`, `Gender`, `BMI`, `Stress Level`, `Physical Activity`, and `Caffeine` intake for more granular looks at different demographics. There's an average sleep hours graph, separated by age group and gender, a pie chart of genders, a sleep quality histogram (still on that 0-24 scale), and finally a scatterplot of sleep hours against sleep quality score (trying to see if there are any apparent relationships between sleep and sleep quality as seen from this dataset).  

## Dataset  

1) Sleep Deprivation & Cognition Performance - https://www.kaggle.com/datasets/sacramentotechnology/sleep-deprivation-and-cognitive-performance/data?select=sleep_deprivation_dataset_detailed.csv  

Features:
- `Participant_ID` - A unique identifier for the people  
- `Sleep_Hours` - Number of hours the participant slept throughout the night  
- `Sleep_Quality_Score` - A score from 0-20 of the quality of sleep for the participant. It's unclear to me if this is somehow empirically-derived score or a self-assigned score (this is a reoccurring theme that will bother me with this dataset)  
- `Daytime_Sleepiness` - A score from 0-24 measuring daytime sleepiness for the participant (I'm guessing it has to do with hours feeling sleepiness?)  
- Cognitive Performance Metrics (I'd take a guess at least these are empirical)  
  - `Stroop_Task_Reaction_Time` - Cognitive psychological test that measures selection attention, cognitive flexibility, and processing speed. Measured in seconds (reaction time to correctly identify the color of a word printed in ink) and lower typically is a better result  
  - `N_Back_Accuracy` - Cognitive test measuring working memory and executive function. A percentage accuracy of correct responses, higher is better.  
  - `PVT_Reaction_Time` - A cognitive test measuring sustained attention and vigilance. Measured in seconds (reaction time to react to a visual stimulus) and lower typically is a better result (similarly to Stroop)  
- `Emotion_Regulation_Score` - A metric used to assess an individual's ability to manage and respond to emotional experiences in a healthy and adaptive way. A score from some kind of questionnaire or some scale (higher scores typically mean better emotional regulation)  
- Lifestyle Factors (other than BMI, I'm guessing these are likely self-reported)  
  - `BMI` - Body mass index, a measure of body fat based on height and weight  
  - `Caffeine_Intake` - Amount of caffeine intake, on a scale from 0-5  
  - `Physical_Activity_Level` - Amount of physical activity, on a scale from 0-10  
  - `Stress_Level` - Amount of stress, unsure of the exact scale but the range in this dataset falls between 0-40  
- Demographic factors  
  - `Age` - participant's age, ages range from 18-43  
  - `Gender` - participant's gender, 37:23 male:female split  

## Preprocessing  

From the initial dataset downloaded on Kaggle, a few of the features were added, converted from other features that had a numerical scale and converted into categorical groups. Namely:  
- `Age` was converted into 3 age ranges (18-25, 26-35, 36-45)
- `BMI` was converted into underweight/normal/overweight/obese based on WHO guidelines.  
- The other three lifestyle factors (`Caffeine_Intake`, `Physical_Activity_Level`, `Stress_Level`) were all some numerical scale and was made into groups (low, moderate, high).  

There was no missing data in any cell, so it was clean in that regard. Overall, looking at the data, there appears to be almost no correlation between variables.  
![CorrMatrix](https://raw.githubusercontent.com/giancarlo-garbagnati/tableau_demos/refs/heads/main/sleepdep_demo/correlationmatrix.png)  

## To Do List
- Nothing. If they update the dataset with more records, I might consider revisiting this, but as it stands now, doesn't seem worth the time.