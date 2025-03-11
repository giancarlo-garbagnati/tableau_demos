# Consumer Financial Protection Bureau (CFPB) Consumer Complaint Dashboard  

Dashboard link

This dashboard displays some information regarding the complaints filed with the CFPB from its beginning in late 2011 to Feb 20, 2025. It covers the kinds of complaints filed, to whom (which companies) they're filed against, and when and where the complaints are filed from.  
  
The [CFPB](https://en.wikipedia.org/wiki/Consumer_Financial_Protection_Bureau) (Consumer Financial Protection Bureau) is an independent agency of the United States that monitors and helps police financial institutions and (notably for this project) collects consumer complaints towards these institutions. It creation (authorized as part of the 2010 Dodd-Frank Wall Street Reform and Consumer Protection Act as part of a legislative reaction to the 2008 financial crisis. It will most likely cease most of its operations by Q2 of 2025.  

## Dashboard  

KPIs highlighted are:  
- Number of complaints  
- Percentage of timely responses from companies  
- Percentage of complaints with a write-up  
- Top 3 complaints types  
There are two interactive filters for selecting a time range and a way to specify a single company to focus on. The visualizations include a cloropleth map for complaint density across the US, a treetop for the companies that have complaints against them, stacked bar chart showing complaint volume by product with each bar segmented by issue type, and number of complaints issued each day over time.  

## Dataset  

1) Consumer Financial Protection Bureau (CFPB) - https://www.consumerfinance.gov/data-research/consumer-complaints/#download-the-data  

The raw file is 5.03 gb (compressed to 1.05 gb) with 7,848,317 records. After processing this reduces down to 1.06 gb and 7,638,765 records. The final features of the dataset:  
- `Date received` - Datetime, date (month/day/year) when the complaint was made  
- `Month received` - Categorical, month when the complaint was made (derived from `Date received`)  
- `Year received` - Numerical, year when the complaint was made (derived from `Date received`)  
- `Product` - Categorical, the product type of the complaint (for example, bank account, credit reporting, debt collection, mortgages, etc)  
- `Sub-product` - Categorical, more specific product category  
- `Issue` - Categorical, the issue type of the complaint  
- `Sub-issue` - Categorical, more specific issue category  
- `Has consumer complaint narrative` - Boolean, if the consumer has a write-up regarding their compliant  
- `Company response` - Categorical, company response type  
- `Company` - Categorical, the company's name  
- `State` - Categorical, the state from which this complaint was filed  
- `ZIP code` - Numerical, the ZIP code from which this complaint was filed  
- `Submitted via` - Categorical, from what means (online, phone, mail, etc) this complaint was filed  
- `Company response to consumer` - Categorical, whether or not the company responded with relief to the consumer  
- `Timely response?` - Yes/no, if the company responded within a "timely" manner  

## Preprocessing  

From the initial set downloaded from CFPB's website, then uncompressed, a few features were added, others removed, and some categories cleaned up and simplified.
- `Month` and `Year` were derived from `Date received`  
- `Product`, `Company public response`, and `Company response to consumer` categories were consolidated and simplified (`Company public response` renamed to `Company response`).  
- `Has consumer complaint narrative` was created from `Consumer complaint narrative`, changing the long test write-ups to if there was a narrative write-up or not.  
- Any `State` not in the 50 US states + DC had their records removed (to simplify creating a cloropeth map) (apologies to those in the territories or armed services abroad, etc).  
- Any "unknown" `ZIP code` (listed as "XXXXX") had their record removed.  
- Removed: `Consumer complaint narrative`, `Tags`, `Consumer consent provided?`, `Date sent to company`, `Consumer disputed?`, `Complaint ID`  

## To Do List  
1. Write a script to update the data (pull from CFPB website and process). As far as I know, I'd have to manually update the Tableau dashboard itself. I could theoretically get Tableau to automatically update if I use a Google Sheet instead of just a .csv. However, since the processed dataset (up to 2/20) is 1.7gb, I don't think I'll use up my precious Google space with this. The other "blocker" could be that the CFPB just stops existing (or stops updating and/or taking any complaints) rendering any update script kind of moot.
2. Format the dashboard for mobile use.