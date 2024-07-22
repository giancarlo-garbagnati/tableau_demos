## COVID Cases and Mortality in the United States from Jan 2020 to May 2023

https://public.tableau.com/views/Book1_17216412705640/Dashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

This is a demo dashboard built in Tableau Public and published to the link above made as a weekend project to try to learn Tableau. The aim was to build a simple dashboard that showcases a few different graphs/charts, KPIs, and interactive filters and the dashboard is formatted for desktop and phones (not tablets). As a disclaimer, I am not a doctor or a healthcare professional.

The KPIs highlighted:
- 'Total Cases' - total number of COVID cases (note: this is the only part of the dashboard that doesn't seem to work with the filters, something I'll need to fix)
- 'Total Deaths' - total confirmed deaths from COVID during the selected time filters
- 'Hospitalization' - hospitalization percentage rate from COVID symptoms
- 'ICU Rate' - percentage rate at which patients were admitted to the ICU with COVID symptoms
- 'Mortality' - mortality percetange from COVID

On the right (in desktop), there are two maps which indicate the COVID rates (case rate and confirmed COVID deaths) across states (and some US provinces). At the bottom left (in desktop), there's a line graph of cases and deaths over time from 01/2020 - 05/2023 (or some period within if you're using the filters). Above these is a bar graph for hospitalization/ICU/mortality rates aggregated by age group followed by a similar bar graph aggregated by race/ethnicity. Then finally we have the filters for year and month.

## Datasets

The data was sourced from the CDC from two of their public datasets: 
1. COVID-19 Case Surveillance Public Use Data - https://data.cdc.gov/Case-Surveillance/COVID-19-Case-Surveillance-Public-Use-Data/vbim-akqf/about_data
2. Weekly United States COVID-19 Cases and Deaths by State - https://data.cdc.gov/Case-Surveillance/Weekly-United-States-COVID-19-Cases-and-Deaths-by-/pwn4-m3yp/about_data

## Preprocessing



