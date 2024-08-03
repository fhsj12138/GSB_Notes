## OptionMetrics
IvyDB contains historical data for all US listed equities(only looked at). 1996-present. 
Compared IV values for option secid 110627 in year 2012 between different files to match data used in permno_match_implied_vol_update_v13
### Std_Option_Price File
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
### Conclusion
- Use data from Std_Option_Price
- Note non of the data files have quantity data, our regression does not use quantity data or any form of aggregation. 
### Questions 
- Method to account for the discrepency between std_option_price and permno_iv? 

  
