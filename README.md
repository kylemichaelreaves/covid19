# covid19
A data analysis project which extracts, loads, and tranforms covid-19 data from the NYTimes GitHub repo; 
Multi-conditional list comprehensions are used to return daily totals for cases and deaths on the county, state, and national level.

Special attention was given to returns on the county level. Given there are many counties of the same name which appear in multiple states,
data validation, and an optional state input, was built in to the county_df() function. For example:

    county_df("York")
    "York appears in ['Maine' 'South Carolina' 'Virginia' 'Nebraska' 'Pennsylvania']; please specify."
