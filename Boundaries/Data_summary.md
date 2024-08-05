## replicate v13
- note data only until 2012 oct 31
- use secid 110627 as example to test replication first
## OptionMetrics
IvyDB contains historical data for all US listed equities(only looked at). 1996-present. 
Compared IV values for option secid 110627 in year 2012 between different files to match data used in permno_match_implied_vol_update_v13
### Std_Option_Price File *
- Information on standardized/interpolated options(standardised option only included if there is enough option price data on that date to interpolate values with)
- At-the-money-forward options with expirations of 10,..., 730 days. 
- Implied volatility is derived by linear interpolation from Volatility_Surface file.
- One _interpolated_ IV for each secid, date, day to expiration
  - Interpolation: forward price of underlying security is calculated with zero curve and the projected distributions. Then the volatility surface points are linearly interpolated to the forward price and the target expiration to give at-the-money-forward implied volatility.
- 4,224 obs for 110627 in year 2012
- Figure 4: "standardised at the money options with 30 day maturity"
- some discrepency with the permno_match_implied_vol_update_v13, collapsed moneyness
### Volatility_Surface File 
- Interpolated volatility surface for each security each day methodology based on kernel smoothing algorithm.
- Implied volatility surface is function of how IV varies with call-equivalent delta(moneyness) and days to expiration.
- Standardized options, calls and puts, expirations 10, .., 730 days, various deltas at 0.05 increments, positive(call), negative(put)
- 71,808 obs for 110627 in year 2012, incremented moneyness and expiration in Kernel distribution
### Option_Price
- Each security that is traded, the implied volatility is (not standardised by days to expiration and moneyness), calculated either with Black-Scholes for European Options or Cox-Ross-Rubinstein (CRR) for American Options.
- 78,406 obs for 110627 in year 2012 as it lists all options, not simplified to certain increments of expiration and moneyness.
### Option_Sig *
- From WRDS Option Suite, CRSP Common Stock Space or Entire OptionMetrics Universe, two files, US option level output and stock level output
- use options file as includes time to expiration filter
- use only common stock space as only includes options of individual firm stocks not derivatives
- can select days to maturity etc, but data is very incomplete, skip days for 30 day maturity  
- stock level data: one observation each day for each security, firm, sort by the moneyness, variables are IV_CATM(IV for _near the money_ call option) and NOPT_CATM(number of options used to get the _near the money_ call IV)
### Conclusion
- Use data from Std_Option_Price
- Note non of the data files have quantity data, our regression does not use quantity data or any form of aggregation. 
### Questions 
- Method to account for the discrepency between std_option_price and permno_iv?
### Factors/filters 
- If use option_sig:
  - At the money, moneyness range? defined as near the money 0.95-1.05(currently)?
  - weight by open interest? (represents number of outstanding contracts for an option, liquidity, more weight to options with higher market participation, reducing impact of outliers.
  - ?(check if matters) number of days used to calculate historical volatility, now use 10
- If use standardised, then did we implicitly use 0.95-1.05 as the moneyness for ATM? (cross check with option_sig option level data file)
#### options_std put
<img width="970" alt="std_v13_p_110627_2012" src="https://github.com/user-attachments/assets/9994c80c-f0e4-4ad2-b424-a4cbd8f5a46f">
#### options_std call
<img width="970" alt="std_v13_c_110627_2012" src="https://github.com/user-attachments/assets/8dabf4d3-88b9-4cbb-99ac-18a1b6aa435b">
#### options_sig put
<img width="970" alt="sig_v13_p_110627_2012" src="https://github.com/user-attachments/assets/7a0a7ae3-84c2-4389-8509-1ca2a8b37bfe">
#### options_sig call
<img width="970" alt="sig_v13_c_110627_2012" src="https://github.com/user-attachments/assets/f51e5d7f-acf6-41af-834c-0c5ddfa132b0">

