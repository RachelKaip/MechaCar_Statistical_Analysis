# MechaCar Statistical Analysis in R 
In this assignment, we leveraged the dplyr library within R to perform a series of statistical analyses on a new prototype vehicle, the MechaCar.  The analysis consisted of four deliverables: 
1. A multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes.
2. Creating multiple DataFrames  that present summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots.
3. t-tests to determine if the manufacturing lots are statistically different from the mean population.
4. A statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. For each statistical analysis, you’ll write a summary interpretation of the findings.

Each deliverable's summary and results are listed below.  

## Linear Regression to Predict MPG
Using both the summary() and lm() functions, we designed a linear model  that predicts the mpg the prototypes.  For this, we passed using all 6 variables from the mecha_mpg_df using mgp as the dependant variable.  

insert image

##### Summary Highlights
1. **Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?**
Based on the Pr(>|t|) values calculated with the summary() funtion, vehicle_length, vehicle_weight, and ground_clearance are the variables that will provide a non-random amount of variance.  

2. **Is the slope of the linear model considered to be zero? Why or why not?**
We should not consider the slope of this linear model to be 0 since the p-value is 5.35e-11. Since the p-value is smaller than our assumed significance level of 0.05, we have enough evidence to state that there is a statistical significance between these variables and to reject the null hypothesis. 

3. **Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?**
Yes.  Based on our r-squared value of 0.7149, we can approximate that 71% of predications can correctly be made by this model. 

## Summary Statistics on Suspension Coils
To determine if the manufacturing process of suspension coils is consistent across all three lots, we created two summary statistics DataFrames using the funtions summary() group_by(), mean(), median(), var() and sd(). The first outlined the suspension coil’s PSI continuous variable across all manufacturing lots- 

insert image

-while the second broke these metrics out for each individual lot. 

insert image

##### Summary Highlights 
1. **The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?**
Based on the first image above, the toal variance comes out to 62.29356, which make all three lots compliant in the 100 PSI variance maximum when evaluated as a group.  However, in the second image, you can see that while lots 1 & 2 are producing suspension coils with variences within the maximum, lot 3 exceeds the 100 PSI limit with a variation of 170.2861224.  Thus, not every lot is individually meeting the design specifications.  

## T-Tests on Suspension Coils
Using one-sample t-tests, we tested to see if the manufacturing lots collectively, and each lot individually, are statistically different from the population mean of 1,500 pounds per square inch.  

Looking at the three lots all together, out t-test tells us that they *are* statistically similar to the established population mean, 1500 PSI.  

insert image

We know this based on the p-value created by the t-test calculating out to about 0.06.  This is larger than our assumed significance level of 0.05, thus, we do not have enough evidence to reject the null hypothesis, which makes them statistically similar.  

Looking at each lot individually, we find that lots 1 & 2 have the saem outcome.  With p-values of 1 and 0.06 respectively, we do not have enough evidence to reject the null hypothesis, making them statistically similar with the established population mean, 1500 PSI.  However, based on the image below, that is not teh case for lot 3.  

insert image 

When we run the t-test for lot three individually, we get a p-value of 0.04, which is less than our assumed significance level of 0.05.  We also find the true mean of x to be 1496.14  which varies from its sister lots.  This tells us to reject the null hypothesis and that lot 3 is statistically different.  

## Study Design: MechaCar vs Competition
As the MechaCar preapres to hit the market, it is critical that it's performance measures up to, and hopefully exceeds, that of its competitors.  In this section, I'm dreaming up a study that can be used to compare this prototype to other cars in the market.  

##### Metrics
In today's economy, consumers may be more interested in features that allow them to go further on less energy.  Thus, I reccomend comparing the following metrics that measure a car's efficiency: 

1. Miles per Gallon (MPG) 
2. Cost ($)

##### Hypotheses

With MPG and Engine Type as our indepedent variables and cost as our dependant, my hypotheses are as follows:

1. Null Hypothesis: The MechaCar has a compararble price to other cars with similar efficiency features.  
2. Alternative Hypothesis: The MechaCar does not have a compararble price to other cars with similar efficiency features.

##### Testing
For this analysis, I'd reccomend a single-linear regression test that predicts what prices cars of cars in related classes should be based on their MPG efficinecy.  This will help MechCar decide if they are adequately pricing their vehicle and prove one of the hypotheses above.    


##### Needed Data
In order to conduct such a study, one would need to have MPG and cost data on every car within similar classes that has come out in the past 2 years as well as the ones that are launching in the same year as MechaCar.  