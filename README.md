# Surfs Up With Advanced Storage Retrieval

## Overview of Analysis

### To use Python programming language, SQLAlchemy, and Pandas DataFrames to retrieve and filter average weather temperatures for June and December from the ``hawaii.sqlite`` database with the express purpose of conducting a thorough comparative analysis. 

## Weather Analysis 

### Process

To conduct this comparative analysis, we first had to write a two queries, one each to filter for the specified months (June, December) that we would convert into a list. 

<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/June_List.png" width ="500" height="125">

* June Query
    
        june_temps = session.query(Measurement.date, Measurement.tobs). \
        filter(extract('month', Measurement.date) ==6).all()
        
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/Dec_List.png" width ="500" height="125">
    
* December Query

        december_temps = session.query(Measurement.date, Measurement.tobs). \
        filter(extract('month', Measurement.date) ==6).all()
    
From here, the list is converted into a Pandas DataFrame, denoting the columns with their respective ``Date`` and ``Month Temp`` labels, and dropping the unnecessary index column. 

<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/June_DF.png" width ="200" height="300">
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/Dec_DF.png" width ="200" height="300">

* June DataFrame

        june_temps_df = pd.DataFrame(june_temps, columns = ('Date', 'June Temps'))
        june_daily_temps_df = june_temps_df.set_index('Date')
    
* December DataFrame

        december_temps_df = pd.DataFrame(december_temps, columns = ('Date', 'June Temps'))
        december_daily_temps_df = december_temps_df.set_index('Date')
    
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/June_Stats.png" width ="200" height="300">
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/Dec_Stats.png" width ="200" height="300">

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

        The Minimum Temperature for December (56) was eight degrees lower than June (64). 
 
* Maximum Temperature

        Yet, the Maximum Temperature for December (83) was only two degrees lower than June (85). 
 
* Standard Deviation

        Because December has a significantly lower Minimum Temperature, yet only a marginally lower Maximum Temperature, 
        its standard deviation (3.75) is understandably greater than that for June (3.26). 

## A Summary of Seasonal Differences

### Conclusion

The DataFrame statistics summaries help visually demonstrate that the month of June typically has higher temperatures than December; and that due to December's higher standard deviation, that month's temperature can vary more starkly. Both of these conclusions align with the fact that the Summer season begins in late June, lending itself to warmer temperatures; while the Winter season starts in late December contributing to its increasingly lower temperatures. 

### Additional Queries

While this analysis is a good start in understanding differences in June and December weather, additional queries could be written to garner more insight. For example, if we were interested in finding the differences in June and December precipitation, we could write the following queries. 
 
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/June_PRCP_DF.png" width ="200" height="325">
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/June_PRCP_Stats.png" width ="200" height="325">

* June Precipitation Query 

        june_prcp = session.query(Measurement.date, Measurement.prcp).\
        filter(extract('month', Measurement.date) ==6)
        
* June DataFrame & Summary Statistics
        
        june_prcp_df = pd.DataFrame(results, columns =('Date', 'June Prcp'))
        june_daily_prcp_df = results_df.set_index('Date')
        
        june_daily_prcp_df.describe()
        
       
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/Dec_PRCP_DF.png" width ="200" height="325"> 
<img align="right" src="https://github.com/chrisknox97/surfs_up/blob/main/PNGS/Dec_PRCP_Stats.png" width ="200" height="325">

* December Precipitation Query

        december_prcp = session.query(Measurement.date, Measurement.prcp).\
        filter(extract('month', Measurement.date) ==12)
        
* December DataFrame & Summary Statistics

         december_prcp_df = pd.DataFrame(results, columns =('Date', 'Dec Prcp'))
         december_daily_prcp_df = results_df.set_index('Date')
         
         december_daily_prcp_df.describe()
        
