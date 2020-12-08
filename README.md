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
Added a new function daily_totals(), with an option input for the state, to either return a dataframe of national totals.
If a state is the input, it will return the cases and deaths for that state. 
