# Crime-Policing-Population Analysis
A collection of data to be used for comparing crime statistics and policing incidents by population groups against the U.S. population distribution by race. For comments, improvements, or general questions, please reach out to me via my [LinkedIn page](https://www.linkedin.com/in/cody-a-holmes/).

## Crime Data
The **FBI UCR 2004-2018 data.csv** file comprises of multiple tables from the Federal Bureau of Investigation's (FBI) Uniform Crime Reporting (UCR) website. Specifically, the data consist of Table 43 (Total Arrests by Race and Ethnicity) by year except for the year 2016, which was labeled Table 21 for an unknown reason. The scope of Table 21 for 2016, nonetheless, is the exact same as the Table 43s of all other years. The FBI published the data via PDF before 2004, and thus I do not include it for difficulty of extraction.

I have reorganized all of the source data in a format that is more conducive to visualization tools and data analysis. I also excluded all ethnicity counts. Ethnicity counts were unreliable given that not all police departments report them (as noted on the FBI's website) nor can ethnicity counts be direclty related to measures of race. This exclusion effectively means that Hispanic or Latino total arrests cannot be derived when comparing against all other races because the way federal organizations track them are independent of race. Hispanics can be of any race. So there is no way to determine how many Hispanics are in the population groups of White, Black, Asian, etc. Additionally, I had to combine the population groups of Asian and Native Hawaiin or Pacific Islander into the combined classification group of Asian or Pacific Islander because that is how pre-2010 FBI statistics classified the said population groups. All data after 2010, therefore, had to be reduced to this commonality in consideration of data reliability.

Lastly, it is extremely important to recognize that the FBI's crime data is based on *arrests* and not *convictions*. Simply because one population group has more total arrests may not mean they were convicted at the same rates.

The **FBI UCR 2004-2018 URLs.csv** file provides the source links for each table-year of data. It should be noted that the source links prior to 2010 direct users to a page with embedded material and does not immediately present the source tables. To navigate to those, the user will have to go to the "Persons Arrested" section of the embedded frame, select "Go to Arrest Tables," and then select the "Table 43" link on the right-hand side of the embedded page.

## Population Data
The **USCB ACS Pop Estimates 2015-2018.csv** file combines total population estimates and percentage estimates, along with margin of error statistics, by race from the U.S. Census Bureau's (USCB) 5-Year American Community Survey (ACS). For purposes of comparisons with the other data sources, the ethnicity of Hispanic or Latino was left out. Ethnicity and race are intertwined. The USCB allows Hispanics to identify as any race, but it should be noted that a large majority of Hispanics will select White as their race. The link to the USCB's ACS Demographic and Housing Estimate source table can be found [here](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2018.DP05&vintage=2010).

## Police Shooting Data
The **WP Fatal Police Shootings 2015-2018.csv** file is a static snapshot of the Washington Post-maintained database. I have included a snapshot of the years 2015-2018 so that apple-to-apple comparisons could be drawn with the other two datasets. The current Washinton Post dataset can be found [here](https://github.com/washingtonpost/data-police-shootings) with credits to the authors and maintainers. I have updated some of the attribute codes to their explicit meanings. The code of "W" for race, for example, was updated to "White", "B" for "Black," etc. The Washington Post provides the explicit meanings for these codes on their GitHub page—where I derived them.

It should be noted that the Washington Post's classification of race within their dataset is not consistent with the FBI's and USCB's. For instance, both the FBI and USCB either clarified the distinction of Asian and Pacific Islanders or made their combined groupings explicit. For this reason, I was able to combine the groups into the classification of Asian or Pacific Islander, as noted previously. The Washington Post database does not make any distinctions or groupings clear. Users must consider this discrepancy when making conclusions from any data analysis.

Additionally, the Washington Post dataset includes the race of Hispanic whereas the other two sources do not. As noted above, federal organizations consider Hispanic or Latino as an ethnicity, which can identify as any race. Ultimately, this makes dataset comparisons and disparity calculations difficult and much more ambiguous.

## Recommended Disparity Calculation
To consider whether a race has a disparity of fatal police shootings, three elements are necessary for a completely contextual analysis. Those three elements are crime rates by race, fatal police shootings by race, and the U.S. population distribution by race, which is why I have provided the three relevant data sources above.

I derived a formula, which I call the *Disparity Rate*, that considers all three elements:

> #### Disparity Rate = Xpd - ( Xpd * ( Xcr / Xfps ) )
> where...  
> X = target race  
> pd = population distribution  
> cr = crime rate  
> fps = fatal police shooting

A negative disparity rate means that a targeted race is killed in fatal police shootings at higher rates in relation to the rate at which the race commits crimes and their population distribution. A positive disparity rate means the exact opposite, namely that a race is killed by police shootings at a lower rate in relation to the race's crime rate and population distribution. A rate of zero signifies no disparity. For better context, consider the following examples:

#### Positive Disparity Rates
Let's suppose a race committed 10% of the crimes, and their U.S. population distribution was also 10%. Suppose that this race, however, consisted of 30% of fatal police shootings. Without any calculations, the disparity is obvious. The calculation would yield 6.7%: 10-10(10/30). Therefore, a positive number should be seen as a prevalent unfavorable disparity. The conclusion would follow, "The ratio of the race's crime rate to the number of their fatal police shootings is 6.7% higher than their national population distribution."

#### Negative Disparity Rates
Now let's suppose that a race committed 50% of the crimes in the U.S., and they make up only 25% of the population. Despite the their high rate of crimes, let's imagine that the race only made up 10% of fatal police shootings. Like the previous scenario, the disparity is obvious but obvious on the other spectrum. This disparity is favorable to the race. The disparity rate would yield a whopping -100%: 25-25(50/10). A negative number, then, should be seen as a favorable disparity. The conclusion would thus follow, "The ratio of this race's crime rate to the number of their fatal police shootings is 100% lower than their national population distribution."

#### Zero Disparity Rate
At this point, a disparity rate of zero should be obvious. If a race comprised 25% of the population, committed 25% of crimes, and was killed by police 25% of the time (relative to other races), then the disparity rate would yield 0%: 25-25(25/25).

## Dashboard
A live dashboard with the three sources of data with disparity rate calculations can be found [here](https://app.powerbigov.us/view?r=eyJrIjoiMmZlNzU0OGQtZjYxOC00Njg3LWI3ZjMtYjIwMmM2ZjVmMTdjIiwidCI6Ijg0NDRiZDJiLWFiM2EtNGQ2Yi1iYWMwLWE5NmZlNjJlOWQyYSJ9). The **Police Shooting Disparity Analysis.pbix** file is the Power BI source file, which possesses live connections to this repository of open use and validation. DAX calculations of the disparity rates can be explored in the source file as well. It should be noted that the only two comparable levels of granularity between the data sources are Race (or Population Group) and Year. The Washington Post, for example, has qualitative data by U.S. state, but states cannot be compared in the disparity calculations because the FBI and USCB datasets do not possess the granularity of state. The same applies to many of the other descriptive measures in the Washington Post dataset.
