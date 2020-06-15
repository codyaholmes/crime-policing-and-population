# Crime-Policing-Population Analysis
A collection of data to be used for comparing crime statistics and policing incidents by population groups against U.S. population distribution by race.

## Crime Data
The "FBI_UCR_2015-2018.csv" file comprises of multiple tables from the FBI's Uniform Crime Reporting (UCR) website. I reorganized the source data in a format that is more conducive to visualization tools. I also excluded all ethnicity counts. Ethnicity counts were unreliable given that not all police departments report them, nor can they be related to measures of race. This exclusion effectively means that Hispanic or Latino total arrests cannot be derived when comparing against all other races because the way federal organizations track them are independent of race. Hispanics can be of any race. So there is no way to determine how many Hispanics are in white, black, etc. population groups. Listed below are the source tables by year and url location:

* [2015 Crime in the United States: Table 43A](https://ucr.fbi.gov/crime-in-the-u.s/2015/crime-in-the-u.s.-2015/tables/table-43)
* [2016 Crime in the United States: Table 21A](https://ucr.fbi.gov/crime-in-the-u.s/2016/crime-in-the-u.s.-2016/topic-pages/tables/table-21)
* [2017 Crime in the United States: Table 43A](https://ucr.fbi.gov/crime-in-the-u.s/2017/crime-in-the-u.s.-2017/topic-pages/tables/table-43)
* [2018 Crime in the United States: Table 43A](https://ucr.fbi.gov/crime-in-the-u.s/2018/crime-in-the-u.s.-2018/topic-pages/tables/table-43)

Years prior to 2015 were not included in the current dataset, but I am planning to add those soon. Years after 2018 are not included due to data not being available.

## Population Data
The "USCB_ACS_Demographic_Housing_Estimates_2015-2018.csv" file combines total population estimates and percentage estimates, along with margin of error statistics, by race from the U.S. Census Bureau's website. For purposes of comparisons with the other data sources, the ethnicity of "Hispanic or Latino" was left out. Ethnicity and race are intertwined, but they cannot be used for side-by-side comparisons among the complete datasets. Listed below are the source tables by year and url location:

* [2015: ACS 5-Year Estimates Data Profiles](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2015.DP05&vintage=2016)
* [2016: ACS 5-Year Estimates Data Profiles](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2016.DP05&vintage=2016)
* [2017: ACS 5-Year Estimates Data Profiles](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2017.DP05&vintage=2016)
* [2018: ACS 5-Year Estimates Data Profiles](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2018.DP05&vintage=2016)

## Police Shooting Data
The "WP_Fatal_Police_Shootings_2015-2018.csv" file is a static snapshot of the Washington Post-maintained database. I have included a snapshot of the years 2015-2018 so that apple-to-apple comparisons could be drawn with the other two datasets. The current Washinton Post dataset can be found [here](https://github.com/washingtonpost/data-police-shootings) with credits to the authors and maintainers. I have updated some of the attribute codes to their explicit meanings. The code of "W" for race, for example, was updated to "White", etc. The codes for race can also be found on the Washington Post GitHub page.

The crime and population datasets include the race of "Pacific Islander" whereas the police shooting data does not. The Washington Post database lumps Pacific Islander into the race group of "Other". Additionally, the Washington Post dataset includes the race of "Hispanic" where the other two sources do not. These differences are a result of the method in which the Washington Post classified race. Ultimately, this makes dataset comparisons difficult, but fair comparisons are still possible since the Washington Post considered the race groups of white and black independent of Hispanic ethnicity (much like the FBI's and U.S. Census Bureau's sources).
