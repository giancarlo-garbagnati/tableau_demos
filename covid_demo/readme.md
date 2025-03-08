## COVID Cases and Mortality in the United States from Jan 2020 to May 2023

https://public.tableau.com/views/Book1_17216412705640/Dashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

This is a demo dashboard built in Tableau Public and published to the link above made as a weekend project to learn Tableau. The aim was to build a simple dashboard that showcases a few different graphs/charts, KPIs, and interactive filters and the dashboard is formatted for desktop and phones (not tablets). As a disclaimer, I am not a doctor or a healthcare professional.

The KPIs highlighted:
- 'Total Cases' - total number of COVID cases (note: this is the only part of the dashboard that doesn't seem to work with the filters, something I'll need to fix)
- 'Total Deaths' - total confirmed deaths from COVID during the selected time filters
- 'Hospitalization' - hospitalization percentage rate from COVID symptoms
- 'ICU Rate' - percentage rate at which patients were admitted to the ICU with COVID symptoms
- 'Mortality' - mortality percentage from COVID

On the right (in desktop), there are two maps which indicate the COVID rates (case rate and confirmed COVID deaths) across states (and some US provinces). At the bottom left (in desktop), there's a line graph of cases and deaths over time from 01/2020 - 05/2023 (or some period within if you're using the filters). Above these is a bar graph for hospitalization/ICU/mortality rates aggregated by age group followed by a similar bar graph aggregated by race/ethnicity. Then finally we have the filters for year and month.

## Datasets

The data was sourced from the CDC from two of their public datasets: 
1. COVID-19 Case Surveillance Public Use Data - https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf/about_data
2. Weekly United States COVID-19 Cases and Deaths by State - https://data.cdc.gov/Case-Surveillance/Weekly-United-States-COVID-19-Cases-and-Deaths-by-/pwn4-m3yp/about_data

The COVID-19 Case Surveillance Public Use Data dataset is a case-by-case dataset of each reported case of COVID from the start of the pandemic (Jan 2020) to present (even though the dataset's documentation purportedly stopped updates). However, since the second dataset did not resume updates, all dates were filtered after May 2023 to match time spans. The dataset includes (among a few other features) the date of reporting, sex, race/ethnicity, age group, and information if the person was hospitalized, admitted to the ICU, or died.

The Weekly United States COVID-19 Cases and Deaths by State dataset is a weekly update of new COVID cases and deaths in each US state (or province), in addition to a running total of both numbers. 

## Preprocessing

The COVID-19 Case Surveillance Public Use Data dataset was initially filtered through the CDC's query system: removing any unnecessary columns and any rows in the 'sex'/'age_group'/'race_ethnicity_combined' columns that had any 'Missing'/'Unknown'/'NA'/'Other' data. This brought down the initially massive >100m row and >10gb dataset down to about ~35m rows and ~5gb (but still way too large for Tableau Public's cap of 15m rows). Cleaning up and shortening some of the string categories in the data, filtering out date ranges beyond 05-2023, then filtering out and rows with missing data in the hospitalization, icu, mortality rate columns got me down to which leaves me with 1.7m rows.

The Weekly United States COVID-19 Cases and Deaths by State dataset was much easier to handle and process. Raw, it came to about <10000 rows and <600kb in size. After removing unnecessary columns and aggregating the weekly data into monthly data, it ended up with under 2500 rows.

## To Do List
1. Figure out why "Total Cases" KPI isn't updating with the year/month filters.
