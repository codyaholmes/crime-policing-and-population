# Crime-Policing-Population Analysis
A collection of data to be used for comparing crime statistics and policing incidents by population groups against U.S. population distribution by race.

## Crime Data
The FBI_UCR_2015-2018.csv file comprises of multiple tables from the FBI's Uniform Crime Reporting (UCR) website. I reorganized the source data in a format that is more conducive to visualization tools. I also excluded all ethnicity counts. Ethnicity counts were unreliable given that not all police departments report them, nor can they be related to measures of race. This exclusion effectively means that Hispanic or Latino total arrests cannot be derived when comparing against all other races because the way federal organizations track them are independent of race. Hispanics can be of any race. So there is no way to determine how many Hispanics are in white, black, etc. population groups. Listed below are the source tables by year and url location:

* [2015 Crime in the United States: Table 43A](https://ucr.fbi.gov/crime-in-the-u.s/2015/crime-in-the-u.s.-2015/tables/table-43)
* [2016 Crime in the United States: Table 21A](https://ucr.fbi.gov/crime-in-the-u.s/2016/crime-in-the-u.s.-2016/topic-pages/tables/table-21)
* [2017 Crime in the United States: Table 43A](https://ucr.fbi.gov/crime-in-the-u.s/2017/crime-in-the-u.s.-2017/topic-pages/tables/table-43)
* [2018 Crime in the United States: Table 43A](https://ucr.fbi.gov/crime-in-the-u.s/2018/crime-in-the-u.s.-2018/topic-pages/tables/table-43)

Years prior to 2015 were not included in the current dataset, but I am planning to add those soon. Years after 2018 are not included due to data not being available.

## Future Policing and Population Data
I plan to collect, clean, and prepare U.S. Census Bureau population distribution data to be used in comparison against the above FBI's UCR crime data. I will post that dataset here once completed.

Additionally, the Washington Post's police incident reporting database can be found [here](https://github.com/washingtonpost/data-police-shootings/blob/master/fatal-police-shootings-data.csv).
