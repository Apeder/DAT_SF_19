
#Overview 

[Circa Victor](https://circavictor.com/) has scraped data from the [Federal Election Commission's API](https://18f.gsa.gov/2015/07/08/openfec-api/) describing 123 million filings from 2010 to present that document approximately 23 million transactions between Political Action Comittees (PACs) and their vendors. 

Though the beta API was only released in summer of 2015, it has already attracted some major third party development:

* https://api.open.fec.gov/developers/
  * https://github.com/18F/openFEC
  * https://18f.gsa.gov/
  * https://github.com/Apeder/openFEC/tree/develop/data
* http://sunlightlabs.github.io/realtime-docs/
  * https://sunlightfoundation.com/blog/2015/07/08/openfec-makes-campaign-finance-data-more-accessible-with-new-api-heres-how-to-get-started/
  * http://influenceexplorer.com/
* http://developer.nytimes.com/docs/campaign_finance_api/

This project seeks to explore, visualize and model this data as an entity-based graph to attempt to predict what groups will spend money on what kind of services on which race at a given time.  Exact predictive capabilities and accuracy will not be known until specific features are extracted from the dataset and several machine learning models are trained and tested. 

##Questions
1. What does the network of PACs, candidates and vendors look like? 
  1. How does money move through this network? What trends and patterns are noticeable? 
2. How does behavior in this network vary over time? 
  2. What clusters can we observe? Do clusters have features that can reliably predict behavior based on entity attributes and time? 
3. How much data about election cycle spending is necessary to make accurate predictions? Is it possible to expand the datasets timeseries to comprise all knwon US elections, or is data before 2010 completely unavailable? 


#Analytical Approach
When the data is narrowed to the approximately 3515 organizations that have >100 total filings, we retain about 95% of the data. At first glance the distribution of transactions by organization resembles a "long tail" Pareto distribution in which a smaller number of groups at the "head" of the distribution account for the majority of total values in the dataset.  

The analysis will proceed in three phases: 

1. The exploratory phase will include connecting to the 500GB PostgreSQL instance on AWS that adds records from the FEC API in realtime as filings are made. 

2. Visualize

3. Model and learn

https://github.com/mplewis/csvtomd - note only for Python 3

```sh
csvtomd active-row-count.csv
```

PAC Name                                                                                                                                                                               |  Number of Filings in DB    
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------
ActBlue                                                                                                                                                                            |  16835880
EMILYs List                                                                                                                                                                        |  463077  
MOVEON.ORG POLITICAL ACTION                                                                                                                                                        |  359442  
Senate Conservatives Fund                                                                                                                                                          |  295687  
DCCC                                                                                                                                                                               |  149169  
Obama for America                                                                                                                                                                  |  142330  
DNC Services Corp./Dem. Natl Committee                                                                                                                                             |  102418  
CLUB FOR GROWTH PAC                                                                                                                                                                |  78544   
Council for a Livable World Candidate Fund                                                                                                                                         |  77220   
ROMNEY FOR PRESIDENT, INC.                                                                                                                                                         |  73624   
Michigan Democratic State Central Commitee                                                                                                                                         |  69171   
Ohio Democratic Party                                                                                                                                                              |  54440   
LaRouche Political Action Committee                                                                                                                                                |  52183   
Democracy Engine, Inc., PAC                                                                                                                                                        |  51887   
WOMEN SPEAK OUT PAC                                                                                                                                                                |  45443   
League of Conservation Voters Action Fund                                                                                                                                          |  44471   
NRCC                                                                                                                                                                               |  39676   
ACTRIGHT                                                      |  35043

#Workplan
Do a lot of munging, build entity objects and graph, then see if we can predict data before it's filed every day. 
