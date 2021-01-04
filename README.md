# covid19
A data analysis project which extracts, loads, and tranforms covid-19 data from the NYTimes GitHub repo; 
Multi-conditional list comprehensions are used to return daily totals for cases and deaths on the county, state, and national level.

Special attention was given to returns on the county level. Given there are many counties of the same name which appear in multiple states,
data validation, and an optional state input, was built into the county_df() function. For example:

    county_df("York")
    "York appears in ['Maine' 'South Carolina' 'Virginia' 'Nebraska' 'Pennsylvania']; please specify."

The same validation was built into state_df(). If the input is outside of a list used for validation, 
an error is raised: 
    
    state_df("Victoria")
    'Victoria is not in database.'


__update__ 01-03-2021

monthly_df was relying on looping through df.month.unique(), which no longer worked.

The function was rewritten with a MultiIndex using years and months. 


__update__ 12-13-2020

Added functions weekly_df and monthly_df to return dataframes for monthly and weekly cases and deaths. 
        
        weekly_df()

        weekly cases 	weekly deaths
    50 	1356998.0 	15658.0
    49 	1380238.0 	15555.0
    48 	1134127.0 	10161.0
    47 	1199731.0 	10514.0
    46 	1052521.0 	8035.0
    45 	783697.0 	7389.0
    
        monthly_df()

        monthly cases 	monthly deaths
    month 		
    12 	2569475.0 	29948.0
    11 	4412061.0 	37791.0
    10 	1946627.0 	23653.0
    9 	1217119.0 	23376.0
    8 	1473763.0 	29612.0


__update__ 12-08-2020

Added a new function daily_totals(), with an optional state input.

Without an input, it will return cases and deaths by day for the entire US. 
    
    daily_totals()
                cases 	deaths
    date 		
    2020-12-07 	202332.0 	1522.0
    2020-12-06 	173109.0 	1111.0
    2020-12-05 	205543.0 	2190.0
    
If a state is the input, it will return the cases and deaths for that state. 
    
    daily_totals("New Jersey")
                cases 	deaths
    date 		
    2020-12-07 	3563.0 	15.0
    2020-12-06 	6030.0 	15.0
    2020-12-05 	5324.0 	51.0
    
The datatype for the state and county columns were changed from object to category, to optimize performance. 
