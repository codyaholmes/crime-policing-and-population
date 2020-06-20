# Crime-Policing-Population Analysis
A collection of data to be used for comparing crime statistics and policing incidents by population groups against the U.S. population distribution by race.

## Crime Data
The **FBI UCR 2004-2018 data.csv** file comprises of multiple tables from the Federal Bureau of Investigation's (FBI) Uniform Crime Reporting (UCR) website. Specifically, the data consist of Table 43 (Total Arrests by Race and Ethnicity) by year except for the year 2016, which was labeled Table 21 for an unknown reason. The scope of Table 21 for 2016, nonetheless, is the exact same as the Table 43s of all other years. The FBI published the data via PDF before 2004, and thus I do not include it for difficulty of extraction.

I have reorganized all of the source data in a format that is more conducive to visualization tools and data analysis. I also excluded all ethnicity counts. Ethnicity counts were unreliable given that not all police departments report them, as noted on the FBI's website, nor can ethnicity counts be direclty related to measures of race. This exclusion effectively means that *Hispanic or Latino* total arrests cannot be derived when comparing against all other races because the way federal organizations track them are independent of race. Hispanics can be of any race. So there is no way to determine how many Hispanics are in the population groups of *White*, *Black*, etc. Additionally, I had to combine the population groups of *Asian* and *Native Hawaiin or Pacific Islander* into the classification group of *Asian or Pacific Islander* because that is how pre-2010 FBI statistics classified the said population groups. All data after 2010, therefore, had to be reduced to this commonality in consideration of data reliability.

The **FBI UCR 2004-2018 URLs.csv** file provides the source links for each table-year of data. It should be noted that the source links prior to 2010 direct users to a page with embedded material and does not immediately present the source tables. To navigate to those, the user will have to go to the "Persons Arrested" section of the embedded frame, select "Go to Arrest Tables," and then select the "Table 43" link on the right-hand side of the embedded page.

## Population Data
The **USCB ACS Pop Estimates 2015-2018.csv** file combines total population estimates and percentage estimates, along with margin of error statistics, by race from the U.S. Census Bureau's (USCB) American Community Survey (ACS). For purposes of comparisons with the other data sources, the ethnicity of *Hispanic or Latino* was left out. Ethnicity and race are intertwined. The USCB allows Hispanics to identify as any race, but it should be noted that a large majority of Hispanics will select *White* as their race. The link to the USCB's ACS Demographic and Housing Estimate source table can be found [here](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2018.DP05&vintage=2010).

## Police Shooting Data
The **WP Fatal Police Shootings 2015-2018.csv** file is a static snapshot of the Washington Post-maintained database. I have included a snapshot of the years 2015-2018 so that apple-to-apple comparisons could be drawn with the other two datasets. The current Washinton Post dataset can be found [here](https://github.com/washingtonpost/data-police-shootings) with credits to the authors and maintainers. I have updated some of the attribute codes to their explicit meanings. The code of "W" for race, for example, was updated to "White", "B" for "Black," etc. The Washington Post provides the explicit meanings for the codes on their GitHub page.

It should be noted that the Washington Post's classification of race within their dataset is not consistent with the FBI and USCB. For instance, both the FBI and USCB clarified either the distinction of *Asian* and *Pacific Islanders* or made their groupings explicit. For this reason, I was able to combine the groups into the classification of *Asian or Pacific Islander*. The Washington Post database does not make any distinctions or groupings clear. Users must consider this discrepancy when making conclusions from any data analysis.

Additionally, the Washington Post dataset includes the race of *Hispanic* whereas the other two sources do not. As noted above, federal organizations consider *Hispanic or Latino* as an ethnicity, which can identify as any race. Ultimately, this makes dataset comparisons and disparity calculations difficult and much more ambiguous.

## Recommended Disparity Calculation
To consider whether a race has a disparity of fatal police shootings, three elements are necessary for a completely contextual analysis. Those three elements are crime rates by race, fatal police shootings by race, and the U.S. population distribution by race, which is why I have provided the relevant data sources above.

I derived a formula, which I call the "Disparity Rate," that considers all three elements:
> #### Disparity Rate = Xpd - ( Xpd * ( Xcr / Xfps ) )
> where...
> X = target race
> pd = populatoin distribution
> cr = crime rate
> fps = fatal police shooting
A negative disparity rate means that a targeted race is killed in fatal police shootings, considering the rate at which they commit crimes and their relative population distribution. A positive disparity rate means the exact opposite, and a rate of zero signifies no disparity.
