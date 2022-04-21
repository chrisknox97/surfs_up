# Surfs Up With Advanced Storage Retrieval

## Overview of Analysis

### To use Python programming language, SQLAlchemy, and Pandas DataFrames to retrieve and filter average weather temperatures for June and December from the ``hawaii.sqlite`` database with the express purpose of conducting a thorough comparitive analysis. 

## Weather Analysis 

### Process

To conduct this comparitive analysis, we first had to write a two queries, one each to filter for the specified months (June, December) that we would convert into a list. 

* June Query
    
        june_temps = session.query(Measurement.date, Measurement.tobs). \
        filter(extract('month', Measurement.date) ==6).all()
    
* December Query

        december_temps = session.query(Measurement.date, Measurement.tobs). \
        filter(extract('month', Measurement.date) ==6).all()
    
From here, the list is converted into a Pandas DataFrame, denoting the columns with their respective  ``Date`` and ``Month Temp`` labels, and dropping the unnecessary index column. 

* June DataFrame

        june_temps_df = pd.DataFrame(june_temps, columns = ('Date', 'June Temps'))
        june_daily_temps_df = june_temps_df.set_index('Date')
    
* December DataFrame

        december_temps_df = pd.DataFrame(december_temps, columns = ('Date', 'June Temps'))
        december_daily_temps_df = december_temps_df.set_index('Date')
    
Finally, from these DataFrames, we can retrieve summary statistics for each month. 

* June Summary Statistics

        june_daily_temps_df.describe()

* December Summary Statistics

        december_daily_temps_df.describe()

### Results

Having written the above Python script, we can now clearly see the differences in temperature between June and December. These findings are listed below:

* Mean Temperature

        The Mean Temperature for June (74.94) was higher than that of December (71.04). 
        
* Minimum Temperature

        The Minimal Temperature for December (56) was eight degrees lower than June (64). 
 
* Maximum Temperature

        Yet, the Maximum Temperature for December (83) was only two degrees lower than June (85). 
 
* Standard Deviation

        Because December has a significantly lower Minimum Temperature, yet only a marginally lower Maximum Temperature, 
        its standard deviation (3.75) is understandably greater than that for June (3.26). 

## Summary

###
