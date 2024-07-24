## Yen folder
aseru-banking/code/

### hmda_regressions
#### hmda_annual
- from raw to panel data
- Note: 2018 variable change; 2008 after more complete data
#### hmda_analysis 
- ignore missing asset block
- want to argue the decline in securitisation rate, but data trend is not obvious, method?
- lender identifier <-- respondent id: check `lar_record`
- group mortgage by bank
#### Avery dataset
- [Avery](https://sites.google.com/site/neilbhutta/data)
- HMDA ID matched to FRB's NIC system, FFIEC or TFR Call Reports for each year , also matched to HUD's list of manufactured home and subprime lenders (1993-2005). and FFIEC's list of CRA wholesale and limited purpose institutions , check `hmdadoc2017.pdf`
- 2017 and before lumped together, afterwards, by year 
- variable charter gives type of institution, excluded credit union as is non-bank
- HMDA data prior to 2018, `respondent_id` is lender identifier -- macthed in Avery file under `hmprid`; Lenders rssdid variables under `ENTITYyy`
- HMDA after 2018, `lei` is lender identifier -- matched in Avery file under `lei`; Lenders rssdid under RSSDyy
- RSSD: Federal Reserve Board Entity number (RSSD9001) for the HMDA filer as
provided by the FFIEC.
  


### hmdacll
- confirming loan limit by region, may change over years
- see it from abnk balance sheet more securitisation if limit increases as more GSE loans 
- HMDA_Match_updated.pdf
- change multi unit to one unit
- no need to replicate cll_process
- cll_annual is section 2, replicate
    - regionxyear
      - cll_analysis
- matching: not restricted to the same year bank, can change in replication
- section 3: securities_cll
  - individual loan, not aggre
  - hmda, avery, cll, aggre by bank, get exposure as independent variable, then get info from bank call report for independent variables
  - matching is restricted to same year, fine
  - call report: //data_collection_temp/balance_sheet/balancesheet panel
      - read debt security 

 ## Questions 
 - where used hmda_year_needed
 - Avery file comes with XXXXyy, why redo `for (variable in c('NAME', 'ASSETS', 'CHARTR', 'RSSD')) {
		variable_year <- paste0(variable, substr(year, 3, 4))`
## Notes
- good to test the data before manipulation
  `colnames() table() 
  
