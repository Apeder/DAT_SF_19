
#Overview 

[Circa Victor](https://circavictor.com/) has scraped data from the [Federal Election Commission's API](https://18f.gsa.gov/2015/07/08/openfec-api/) describing 123 million filings from 2010 to present that document approximately 23 million transactions between Political Action Comittees (PACs) and their vendors. 





#Analytical Approach
Go to ipython notebook and write some record examples as .csv that can be pushed to github and referenced in this doc

https://github.com/mplewis/csvtomd

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
ACTRIGHT                                                                   


#Workplan


What is the question you hope to answer? What data are you planning to use to answer that question? What do you know about the data so far? Why did you choose this topic?



Example:

* I'm planning to predict passenger survival on the Titanic.
* I have Kaggle's Titanic dataset with 10 passenger characteristics.
* I know that many of the fields have missing values, that some of the text fields are messy and will require cleaning, and that about 38% of the passengers in the training set survive.
* I chose this topic because I'm fascinated by the history of the Titanic.
