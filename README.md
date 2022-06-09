# Understanding The Impacts Race Has On Student Loan Repayment 

## Data cleaning for analysis: 

The Obama administration aimed to increase the transparency of the higher education system by releasing vast pools of data through the college scorecard. The scorecard provides data which is sufficient for us to be able to measure discrepancies influencing higher education through gender, race, and social class. Our project looks to utilise this availability of big data to understand the impacts that race has on the various educational outcomes of university students, specifically looking at how student loans discriminate against various races. 

The nature of the college scorecard dataset that we are using is not in the rawest form since it has been aggregated at the school level, however, the astounding volume of null and missing values meant that the dataset was very tedious to work with. The contents of this dataset include 1805 variables for 7149 universities across the United States which spans from 1996 to 2015. When initially exploring the raw data, we found there to be a large volume of missing values and inconsistencies in the attributes which were recorded over the years as many were discontinued. All these variations within the data frame have the potential to skew the data. In order to prevent biases in our base data that lead to invalid results, we look to conduct basic visualizations of the shape of our data.

### Percentage null values for various attributes: observing the gaps in the data 

![one year attributes null count percent](https://user-images.githubusercontent.com/98602884/172902450-65b9ff89-0fb7-4711-a38d-bf97ff7fc1e1.png)


We have initially visualised the shape and the contents of our data by showcasing the proportion of missing values with seaborn displot. We had prior narrowed down the attributes which related to race and the various factors we wished to compare. This displot shows how the various attributes are hereby concentrated with null values especially C150_4_NHPI which showcases an above 90% of values within the attribute are null.

### Percentage of null values for each attribute analysed: time series 

![multi year attributes null count percent over time](https://user-images.githubusercontent.com/98602884/172902609-1cfc0f7f-40a7-466e-b39a-e16e8c93eff8.png)

As illustrated by the above visualisation, we can see the discontinuation of certain attributes being replaced such as UGDS_ASIAN which only has records after 2008. Through conducting these types of visualisations, we were better able to understand how to clean our data.

By reading academic papers and literature, we found there to be various justifications for the methods of preparing the data for analysis. We firstly analysed our data by categorising the values that we have into the various types of missing values: (MCAR) missing completely at random, (MAR) missing at random, and (MNAR) missing not at random. In order to avoid omitting data points of statistical significance, we categorised the null values. For deletion of values, we are able to use listwise deletion and pairwise deletion depending on the type of missing value. We used listwise deletion when we faced MCAR data points since this approach can be taken due to the large size of our dataset, however, using this type of deletion was done very carefully; only attributes which were completely discontinued were dealt with in this manner. Another issue which has prevented us from replacing the missing value with the mean would be that the multidimensionality of our data frame means that taking this approach in analysing the data isn’t the most practical. The missing values can’t be replaced in such a manner especially since each institution’s data points are affected by multiple factors and therefore taking a state-level average may not be appropriate. We also looked to using pairwise deletion where the procedure cannot include a particular variable when it has a missing value, but it can still use the case when analysing other variables with non-missing values. 

Through constructing a series of descriptive visualisations exploring the shape of the college scorecard dataset we were able to conclude that the best way for processing the data for analysis would come from using pairwise deletion of rows (institutions) for null values in order to avoid bias and ensure that the analysis is valid. 

After researching other projects which have made use of the student data scorecard, we have found that on average the data cleaning aspects of the project simply tend to drop null values or discontinued rows using the pairwise deletion approach to data-cleaning. 

When aggregating the data for the institutions on a state level, we realized that if we only limited our analysis to schools that did not have any null values for the particular attributes we were interested in, we would end up with very restrictive sample size. Thus, we instead chose to examine each attribute on its own. For example, if we were interested in determining the average default rate in New York and the four-year completion percentage for Asian students in 2013, we would first look at all the institutions in New York that had data on their default rate and determine the process. We would then look at all the institutions in New York that had the completion percentage data and average those results. This means that we would be taking the average for each attribute across two different lists of institutions. While this raises some potential data integrity questions, we felt that across all the states, no matter what attribute we looked at in isolation, there were enough schools without null values in the data that the results were likely a representative sample. 

We have attached the function we wrote to perform the state aggregation:

"Add picture"

## Methodology:

During the initial stages of our project, we chose a very broad question which aimed to understand whether federal student loans are still significant, however, we found this question to be rather too farfetched. In order to have a more appropriate project which didn’t have too many variables, we chose to look specifically into how racial differences affect those taking out student loans.

We have focused our research on comparing loan usage and college achievement of students of different races to evaluate the implications of racial educational inequality. The aim of our project is structured toward answering how race impacts competition rates for students, how the average debt incurred throughout their studies varied with race and how the students of different backgrounds are distributed across the states. In order to decide on how to analyse the data and which attributes we need to use, we manually screened the data to see which attributes are significant for analysing the impacts of race. 

### Correlation matrix which aggregates raw data from 2013 for key attributes into a state-level basis 

### Correlation matrix which aggregates raw data from 2013 for key attributes into an institution level basis – using clean data  

We have initially created a heatmap correlation matrix for 2013 for the attributes of interest relating to race using the seaborne library on python. Through creating this correlation matrix, we were able to utilise the Pearson correlation coefficient to observe any linear relationship between two attributes. We were also able to use this table in order to identify any multicollinearity in case we wished to incorporate machine learning into our project. 


correlation=(Cov(x,y))/(σx*σy)

This matrix is especially important when we are conducting such multivariate analysis. Through observing strong correlations or lack of correlations, we were able to pick our appropriate attributes for conducting further analysis and see if the values showed any relationship which would answer our question of how race impacts educational outcomes.

In order to analyse our data, we used python: pandas, NumPy, matplotlib, seaborn and tableau. We have decided to use these modules since we felt they suited our data best. 

## Descriptive statistics:

It is apparent that there are rising costs of tuition fees within the United States. The average tuition fees have been spiralling out of control and this is evident in the rising costs of both in-state and out-of-state tuition costs. Through conducting initial descriptive statistics on our cleaned dataset, we found the trend line to be clearly rising. As illustrated by the line graphs below there is a strong upwards trend for tuition fees all-round for institutions. Through filtering down to the top 11 states' fees, we look to explore further whether factors such as race, family income, and average intake criteria play a significant part in the rising costs to students. 
 
INSERT GRAPHS 

## Preparation for the final product: 

For our final outcome, we wished to highlight whether the racial distribution across the states showed any correlation with the average default rate within the state. In order to understand the relationship between these factors, we have decided to use heat maps of the USA as we felt that this visualization was most effective in showing state-level changes. We initially experimented with Tableau for creating these map visualisations, yet, we felt that the geographic maps would be much clearer and cleaner for the final product by using geomaps using Plotly in python. This module produced graphs which were much clearer for observing any correlations.
 
Academic literature suggests that Black college students are more likely to take out student loans than white students. In order to better understand the impacts that race plays on the average default rate we initially created a histogram which showed the distribution of the default rate.

### Histogram of default rates across universities, 2013 

The CDR3 is representative of the 3-year cohort default rate for each institution. A cohort default rate is the percentage of a school's borrowers who enter repayment on certain Federal Family Education Loan (FFEL) Program or William D. Ford Federal Direct Loan (Direct Loan) Program loans during a particular federal fiscal year (FY) and default or meet other specified conditions prior to the end of the second following fiscal year.

We find that through plotting this histogram, the distribution for the default rate is positively skewed. The shape of the histogram does not follow the natural shape of a normal distribution suggesting that the overall default rates are low on average, ranging between 0.0% to 40.0% under the IQR. 

INSERT GRAPH

This map shows the spread of default rates across the states. We can observe that there is significant variation in the default rate across the US with the top 3 defaulting states being: Nevada, Wyoming, and New Mexico and the lowest defaulting states being: Nebraska, North Dakota, and Vermont. We wish to compare the default rates of each state with respect to the average competition rate for each race. 

We have chosen to use the Completion rate for first-time, full-time students at four-year institutions (150% of the expected time to completion) for white, black and Asian students for drawing comparisons. This attribute holds value since program completion can determine whether a borrower will make progress in paying down their loans. Students who are unable to complete their degrees bear a greater burden of paying back the loans. Third Way, a centre-left think tank, finds that “students who complete a degree or certificate are 20 percentage points more likely to begin paying down their loan principal than non-completers in each year after leaving campus ”. Through categorising the competition rate by race we aim to observe the effects that competition by race has on repayment in order to see if there is some observable trend which could suggest that black students with similar competition rates experience higher default rates compared to white students or Asian students. 

## Results

#### Part 1 

We have produces a series containing geographic heat plots for the completion rates for Black, White and Asian students for our analysis. We have limited our visualisations to these groups to cover the top three groups for which we have data. 

INSERT GRAPH 

We can observe from this diagram that the 4year competition percentage for Asian students is high across the board. States with a high percentage of Asian population such as California and the North East exhibit on average higher completion percentages. This pattern may be evident  due to utilising a larger sample size in these regions, exaggerating the average Asian educational attainment. Furthermore, there could be innate differences in the migration patterns which results in a higher completion rate on average. Again, states in the Deep South have a larger percentage of non-Indian, non-Chinese population migrants from Indochina, the Philippines and Central Asia. The generations of migration within these regions uniquely impact their socio-economic conditions, so variability within the Asian community needs to be considered before making any inferences from this visualisation alone. Also, it is important to account for states which have an extremely small population such as Wyoming, Nebraska, New Mexico and Georgia for not showing an accurate depiction of the cross-geographical distribution of the Asian Completion percentages.  

With reference to the completion rates for the black students, the differences, within the Deep South regions which contain large black populations, provide interesting insights. For example, Michigan and Wisconsin, which have a demographic makeup of predominantly black students, show relatively low levels of undergraduate completion. This may be justified by the large automobile driven economy of those states that has led to the emergence of large inner-city poverty and a strong black-hood neighbourhood. These socio-economic factors thereby play a large role in loan repayment. Within the northern states, the low completion rate may be justified by the small population which exists within those regions.

White students overall have exhibited lower percentage completion rates across the board and the variation seems to be rather limited. Pennsylvania and the tri-state area containing Delaware, Rhode Island and Connecticut are observable anomalies with relatively high completion rates. These outlier states may demonstrate this nature due to the variation in the volume of universities and institutions within those areas. Areas which contain large concentrations of colleges have some influence on the average educational attainment of the population. For example, Mid-region states tend to have fewer universities which therefore leads to lower completion rates. Beyond accounting for the population sizes there are many external factors and error terms, which need to be taken into consideration when making claims about this visualisation. 

#### Part 2 

After assessing each of the attributes separately, we have then completed a series of scatter plots in order to get a true understanding of any correlation which exists between the default rates and the competition rate for each of the races. Using the skitlearn module, we have built a regression model which creates a line of best fit with the following regression formulae. Within our model, we wish to make the independent variable y to be the default rate and the dependent variable component X_1 as the 4-year competition percentage for each race.  

y=β_0+β_1 X_1+ ε

In order to create the most appropriate line of best fit for interpolating and making inferences, we used the R^2 formula to optimise the sum of least squares to find the best fitting line for the data we have at hand. Whilst we considered conducting the scatterplot on a state-level aggregation, we felt that this produced too few data points to be able to interpolate in an effective and economically significant manner. Therefore we decided to include all the data points on the institutional level for the scatter plot. 
 
R^2=1-  RSS/TSS

### Asian 4-year completion percentage vs default rate

The 4-year completion percentage of Asian students versus default rate analysis indicates that there is no real strong correlation between these two variables. The Asian student regression has both the least steep line and also tapers off relatively quickly, which is indicative of the fact that Asian students are accordingly more likely to pay off their debts despite not completing their degree relative to black or white students. This can bring into consideration that debt forgiveness has a lower impact on Asian students’ future incomes relative to other races. 

### Black 4-year completion percentage vs default rate

### White 4 year completion percentage vs default rate

Whereas we can more clearly see that there is a clear causal relationship which exists between White and Black students. The observable trend meets expectations since it is presumed that as the completion rate of the student increases, the average rate of default should fall; the students should be able to earn a sizeable income to pay off their debt. The trend which we observe for the Black students does not display an extremely strong correlation with the points all centred around the line of best fit. Instead, we see a series of points in a vertical line which may be indicative of no correlation at some levels of completion as default rates are very multifaceted. After a certain percentage of completion rates is achieved there is no longer such a linear impact from this attribute alone. This phenomenon is also strongly prevalent in the Asian student scatter plot. With reference to the white completion rate scatter plot, in particular, an interesting observation can be made from the grouping in the bottom right corner of the graph. This high concentration cluster of points suggests that those with a higher percentage of completion are more likely to pay off their loans however there are points which extend far away from this cluster which suggests that there is an omitted variable. Differences in the labour market may be impacting the correlation between completion and the likelihood of default. It can be theorized that factors such as the choice of degree play a role here. Stem-related fields tend to yield higher salaries in the job market as a pose to non-stem fields of study. Furthermore, the differences in fees between instate vs. out-of-state tuition and private vs. public colleges have significant impacts on the two variables of interest. It is therefore important to consider these external factors which justify the lack of normal distribution of people’s ability to pay back loans. 

## Conclusion:

In conclusion, the journey we have taken in order to better understand the student loan crisis focusing on how race has an impact on the student's ability to pay back has been partially achieved. Recalling from earlier, we looked to explore how race impacts competition rates for students, how the average debt incurred throughout their studies varied with race and how the students of different backgrounds are distributed across the states. I believe we were able to achieve this to a reasonable level through employing various tools within data science. The use of the geomaps and the scatter plots with regressions provided great insight into some overarching trends that are observable. 

Although we were able to produce this level of analysis through these visualisations, there are a number of limitations to our visualisations. Firstly, as mentioned in the analysis the completion rate for students of different states with respect to race has many different determinants since firstly the migration patterns of the different races have huge impacts on their standard of living and therefore educational attainment. Furthermore, students can move states for higher education purposes meaning that comparing regions with a large black population to the average default rate within the specific region may not have economical significance. There are also inherent shortfalls of the dataset itself by aggregating the data on an institution-level rather than by each individual’s data. For future improvements on the analysis we have conducted it may be necessary to scale the default rates based on the size of the institution and the cohort size.

This project began by attempting to unpack the complex and multi-faceted nature of indebtedness and college education in the US. Drawing on a diverse set of open-source data this paper utilised data visualisation skills to attempt to draw inferences as to regional and ethnic variations in university completion and default rates. The lack of qualitative research precludes us from making strong inferences as to causal mechanisms or attempting to push for policy proposals. However, the availability of such datasets is a long term catalyst for such research that the authors of this paper believe would be useful in understanding how best policies surrounding the recent loan-forgiveness debate could be best structured to help at-risk communities. 

## Appendix:
Link for github page: 
Repository:



