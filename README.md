# Kickstarting with Excel

## Overview of Project
Louise is a rising playwrite who is hoping to fund her new play, Fever. She has a campaign Kickstarter dataset to use to determine what factors play into what makes a fundraising campaign successful. This dataset contains data about thousands of campaigns. As a result, it is virtually meaningless at first glance. By utilizing Excel to perform various analyses, I can help Louise gain insight on how well campaigns perform based on their launch dates and funding goals. 

### Purpose
As a student, the purpose of this project is to become familiarized with the powerful analytical tools Excel provides. Although Excel is a very commonly used tool, a lot of the concepts and tools presented in this course were unfamiliar to me. It was very interesting to see the wide variety of tools Excel provides to perfrom data analysis. In my current role as a data engineer I mainly analyze data stored in databases, not Excel, so learning about pivot tables, vlookups, countifs, etc. was very helpful.

As an analyst brought in by Louise, the purpose of this project was to make some sense of the Kicktarter dataset. Data can hold a wealth of information if you are given the tools. This project was successful in that we were able to provide Louise with a clearer path she might take for her next fundraising campaign.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

To perform the analysis of theater outcomes based on launch date we need to create a pivot table containing counts of outcomes based on month of launch date. To do this, we first need to create a derived years column by using the =YEAR() function on the Date Created Conversion column. From there we can generate a pivot table by dropping the outcome field into both Columns and Values, dropping Parent Category and Years into Filters, and by dropping Years into Rows. To get a monhtly comparison we need to group the columns by month, instead of year. Next, since we're only interested in theater campaigns, we need to filter the Parent Category to only show results for theater. Finally, we can generate a line chart as shown below:

![Theater_Outcomes](https://github.com/kimcheese33/kickstarter-analysis-mod1/blob/master/Theater_Outcomes_vs_Launch.png)



### Analysis of Outcomes Based on Goals

To perform the analysis of play outcomes based on goals we first need to set up our sheet. We need to set up our goal ranges in the first column then set up subsequent columns to store the count of successful, failed, and canceled outcomes, the total number of projects, and the percentage for each kind of outcome. After we have our sheet set up we can use the COUNTIFS() function to get the outcome type (successful, failed, or canceled), the goal range, and then filter the count based on subcategory (plays). Here is an example of what our function looks like:

=COUNTIFS(Kickstarter!F:F,"successful",Kickstarter!D:D,">=1000",Kickstarter!D:D,"<5000",Kickstarter!O:O,"plays")

We edit this function for each outcome and goal. Then we need to calculate the total projects by adding the counts for each outcome using SUM(). Finally, we calculate the percentage by dividing the outcome count by the total count and setting the cell type to Percentage. Now that we have our data set up the way we want we can generate a line chart as shown below:

![image_name](https://github.com/kimcheese33/kickstarter-analysis-mod1/blob/master/Outcomes_vs_Goals.png)



### Challenges and Difficulties Encountered

During this challenge, there were no significant difficulties encountered. The analysis was simple to perform and the results were simple to deduce. Some possible difficulties one might encounter could be if the data was not uniform. For example, if there were values in the outcomes column that were not successful, failed, canceled, or live. When datasets contain user input errors or system generation errors that can cause problems. Another challenge could arise if the data didn't present clear outcomes. Luckily, we could easily see what the data was telling us. However, if the data was all over the place with no clear story to tell, that could make making an informed decision more difficult. Another challenge could arise if the data were not all in one place. Conveniently for us, the Kickstarter data was in one sheet. Oftentimes, data will be stored in different sheets or in a different system entirely.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

Looking at the outcomes based on launch date for theater campaigns it is clear that we get the most successful outcomes during May and June. Thus, if Louise were to start a theater campaign project she should do so in May, preferably, or June. From that point on, the likelihood she will have a successful outcomes steadily declines as the year goes on. There is a slight spike in October for both successes and failures. However, we would not recommend she start in October, because there is about a 50% chance she would have a negative outcome. If May or June is not possible for whatever reason, the next month we might recommend is February as there is about a 60% chance she would have a positive outcome.

- What can you conclude about the Outcomes based on Goals?

Looking at outcomes based on goals for plays we can see that there is an inverse relationship between the percentage of failed vs sucessful outcomes based on goal. There were no outcomes for canceled plays. Based on our analysis, we can see that for the number of outcomes the highest percentage of success occurs when the goal is set at $5000 or less. This makes sense, because the lower the goal the easier it is to reach. We can also see that if there is a goal set for $45,000 or higher the chances for a successful outcome drastically declines.

- What are some limitations of this dataset?

One limitation is that not all countries are represented in this dataset. Only 21 countries were included in this dataset for reasons unknown. Did Kickstarter have no campaigns in other countries or were other countries just filtered out? 
Another limitation is that we only have data for 2009 up until 2017. Assuming Louise is trying to fundraise her play in a more current year, it would be a limitation to not have more current data.


- What are some other possible tables and/or graphs that we could create?

We could create a line graph showing outcomes based on how long a campaign runs. Perhaps the longer a campaign runs the more successful it is or vice versa. To create a graph like this we could follow a similar process to Outcomes Based on Goal except using month ranges instead of goal ranges. We could also create a stacked bar graph showing campaign outcomes for plays based on country. Perhaps plays are more successful in the US versus Australia. Lastly, we could produce a stacked bar graph showing outcomes for plays based on whether it was a staff pick. Staff pick wasn't a column that was mentioned throughout this exercise, but it could play a role in the outcome. Perhaps campaigns that get staff pick approval are more successful, perhaps not.


