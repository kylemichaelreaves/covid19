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

__update__ 12082020
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
