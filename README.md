# Surfs Up With Advanced Storage Retrieval

## Overview of Analysis

### To use Python programming language, SQLAlchemy, and Pandas DataFrames to retrieve and filter average weather temperatures for June and December from the ``hawaii.sqlite`` database with the express purpose of conducting a thorough comparitive analysis. 

## Weather Analysis 

### Process

* To conduct this comparitive analysis, we first had to write a two queries, one each to filter for the specified months (June, December) that we would convert into a list. 

June Query
    
    june_temps = session.query(Measurement.date, Measurement.tobs). \
    filter(extract('month', Measurement.date) ==6).all()
    
December Query

    december_temps = session.query(Measurement.date, Measurement.tobs). \
    filter(extract('month', Measurement.date) ==6).all()
    
* From here, the list is converted into a Pandas DataFrame, denoting the columns with their respective  ``Date`` and ``Month Temp`` labels, and dropping the unnecessary index column. 

June DataFrame

    june_temps_df = pd.DataFrame(june_temps, columns = ('Date', 'June Temps'))
    june_daily_temps_df = june_temps_df.set_index('Date')
    
December DataFrame

    december_temps_df = pd.DataFrame(december_temps, columns = ('Date', 'June Temps'))
    december_daily_temps_df = december_temps_df.set_index('Date')
    
* Finally, from these DataFrames, we can retrieve summary statistics for each month. 

June Summary Statistics

    june_daily_temps_df.describe()

December Summary Statistics

    december_daily_temps_df.describe()

### Results


## Summary

###
