# Project Overview
# Market Analysis Report for National Clothing Chain <br>
**Project Description**<br>
An online national clothing chain needs your help creating a targeted marketing campaign. Sales have been flat and they want to lure lost customers back. They want to advertise specific products to specific customers in specific locations, but they don’t know who to target. They have three products in mind:
Shirt: $25 <br>
Sweater: $100 <br>
Leather Bag: $1,000 <br>
They need you to conduct an analysis to determine the best product to advertise to each customer. <br>
Image Information<br>

"fashionistas" by [ embr ] is licensed under CC BY-NC-SA 2.0<br>
"French Connection @ Shopper's Stop, Garuda Mall" by teemus is licensed under CC BY-NC-SA 2.0<br>
All work for the project will be completed using the Microsoft Power BI desktop application.<br>

For viewing the raw spreadsheet data outside of that platform, students will need to use Google Sheets or Microsoft Excel.<br>

The project will use a variety of data sources, including<br>

# US Census Bureau<br>
Average income<br>
location<br>
population<br>
industry<br>
# Business Data<br>
Product inventory<br>
Product prices<br>
Customer rating<br>
Product return rate<br>
# Customer Data<br>
Customer ID<br>
Names<br>
Location<br>
Date of birth<br>
Purchase history<br>
# Additional Data<br>
Weather<br>
Economics<br>
Demographics<br>
Competition<br>
You can get the additional data from public data sources, here I choose **Weather** data as additional data since it affect clothigs purchasesaccording to the seasons. <br>
![EXTRA](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/8f99679d-914f-4c8d-aacb-3fe0a9344704)<br>


# Project Instructions
In this project, you will use population statistics from the US Census Bureau to determine where the greatest income exists around the country and whether there is a correlation between sales and income. We don’t know the incomes of our customers, but we should be able to predict it by looking at their purchase history and locations and comparing that against the census data. Additionally, we want to analyze our inventory, specifically customer ratings and return rate and see if there’s a correlation between the two.
<br>
# Draw conclusions<br>
Draw conclusions from your analysis and use visuals to answer the following questions:<br>

# Analysis Questions <br>

What is the correlation (R2 value) between sales and income?<br>
What is the correlation (R2 value) between customer ratings and product return rate?<br>
What are the linear regression formulas to predict customer sales and customer incomes?<br>
Which customer do you predict has the highest income?<br>
Which product will be advertised the most?<br>
# Present your analysis<br>
You’ll need to present your analysis as a 1 page written summary and visual report in Power BI. Use the following visuals to present your data:<br>

Income Distribution: Histogram<br>
Household Income by Location: Map<br>
Correlations: Scatter Plot with Trendline and Card with R^2 value<br>
Use other visuals as-needed to further present the results of your analysis.<br>

# Histogram
Although you will need to determine the parameters of the histogram(s) for your project, think about what a histogram is intended to do. In the example below, you can see that the histogram gives you a clear understanding of the distribution of values and helps you visualize the shape of the data. We can see here that it's a right-skewed distribution with a peak of around $40k and an average that is probably a bit to the right of the peak.
<br>
Your histogram(s) should also convey important statistics about the data you analyze, so you'll probably want to have at minimum 4 columns but preferably more.
<br>
Additionally, although there is a histogram visual you can download from the Power BI marketplace (if you have access to that resource) it's recommended that you use a column chart instead so that you can use a DAX formula to specify the ranges and number of columns (more on this in the detailed instructions).<br>
# Detailed Instructions

1- Import the census data, customer list, purchase list, and state list into Power BI. <br>
There should be 7 total tables:<br>
Avg Income by State<br>
Customer List<br>
Incomes by State<br>
Industries<br>
Product Inventory<br>
Purchase List<br>
State List<br>
2- Set up the data in Power Query so that all the columns are correctly formatted and structured. Some of the tables will require steps in Power Query to be correctly set up.<br>
3- Set up your table relationships. All tables you import should be tied into the table relationships. Avoid many-to-many relationships as they’re not needed and will cause issues with cross-filtering.<br>
4- Review the table relationships and confirm if they are properly set up. Most of the tables should follow a star schema and the overall set up should look similar to the sample image:<br>
5.Create a map to visualize the distribution of average household income across the country.

6.Create a new ‘Regression Table’ from the ‘Customer List’ to summarize the average customer sales by state and set up the following calculated columns for your regression formula:

y = average sales by state (read the note below)
y2 = Y^2
x = average income by state (read the note below)
x2 = X^2
xy = X*Y
NOTE: You'll need to use this data to calculate predicted customer incomes, and this can be set up in 1 of 2 ways. Either (1) set up income as x and use x = b-y/-m to predict customer income, or (2) set up sales as x and use y = mx +b to predict customer income. The results will be very similar.

7.Create a scatterplot with a trendline to analyze the relationship between average incomes and average sales.

8.Create the remainder of the regression formula variables as calculated measures: b (y-intercept), m (slope), n, Sum of X, Sum of Y, Sum of XY, Sum of X2, Sum of Y2

9.Create a calculated column in your customer table for your predicted customer incomes.

10.Use DAX formulas to categorize the predicted incomes into ranges and to determine the best product fit for each customer. Present this data with a histogram and other visuals.<br>
<br>11.Perform additional analysis using 1-2 other variables of your choosing. These variables can be part of the provided data set or data that you find from additional sources. Think about variables that may help you better understand the customer demographics and market conditions and that will allow creating a more rigorous analysis.

12.Write a brief 1 page summary of your findings, citing the visuals and tables you created as evidence. The summary should address the 5 analysis questions described on the Instructions Overview page and provide an overview of your resulting marketing strategy.<br>
# Measures
**You need to create a regression table** <br>
It well explained in the classroom and it is very easy to follow steps, but for further information check this: https://iterationinsights.com/article/linear-regression-in-power-bi/ <br>
![reg](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/fad10b6e-0f68-4cb3-b845-48d215c4b5bb)<br>

1- Age categories (bins):<br><br>
`Age Category = IF([Customer Age]<20,20, IF([Customer Age]>=20 && [Customer Age]<30, 25,
IF([Customer Age]>=30 && [Customer Age]<40, 35,
IF([Customer Age]>=40 && [Customer Age]<50, 45,
IF([Customer Age]>=50 && [Customer Age]<60, 55,
IF([Customer Age]>=60 && [Customer Age]<70, 65,
IF([Customer Age]>=70 && [Customer Age]<80, 75,
IF([Customer Age]>=80 && [Customer Age]<90, 85,90))))))))` <br><br>
2- Find out the predicted income.<br><br>
`predicted customer income = 72.43*[X]+72640.0` <br><br>
3- creating bins for predicted customer's income.<br><br>
`Bin = IF([predicted customer income]>=110000,110000,
IF([predicted customer income]<110000 &&[predicted customer income]>=100000,100000,
IF([predicted customer income]<100000 &&[predicted customer income]>=90000,90000,
IF([predicted customer income]<90000 &&[predicted customer income]>=80000,80000,
IF([predicted customer income]<80000 &&[predicted customer income]>=70000,70000,0)))))` <br><br>
4- Calculating Standard deviation for income; to helps us understand how spread out the data points are from the average.<br><br>
`stdv income = STDEV.P('Avg Income by State'[Average Income])` <br><br>
5- use rules to find out the suggested products for each customers but I did it in tradioal way using bins. <br><br><br>
![re6](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/036d9525-9e90-4afc-abcf-7bf8d5b2b385)<br>
# The Report Insights.<br><br>
![re1](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/3cfb6f5b-1e5b-4ebe-bce5-70c6ef05050b)<br><br>
![re2](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/890cd213-c7a7-446c-93fa-8a205c8b7df9)<br><br>
![re3](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/78769cf8-3563-42d5-ad2c-acdbe2d3d72b)<br><br>
![re4](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/93800311-2c4c-4cbc-a62b-85cc1444effa)<br><br>
![re5](https://github.com/NailaAbdalla/Project-Market-Analysis-Report-for-National-Clothing-Chain/assets/151609042/7d48e758-c906-4aa9-98af-0bcbbe9c291b)<br><br>
# Important Notes:
**Why do we use linear regression and created a regression table accordingly** <br> 
1- Linear regression help us determine the strength between a dependent variable and a series of other independent variables.<br>
2- Also help in creating models to make predictions, such as predicting a customer's income.<br>
3- Further more, helps in predicting future outcomes or identifying the missing data.<br>
4- lastly, spotting errors in a dataset, identifying or estimating the correct values.<br>
Determine the strength of predictors, forecast an effect, and trend forecasting.





