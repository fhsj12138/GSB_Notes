## OptionMetrics
Compared IV values for option secid 110627 in year 2012 between different files to match data used in permno_match_implied_vol_update_v13
### Std_Option_Price File
- Information on standardized/interpolated options(standardised option only included if there is enough option price data on that date to interpolate values with)
- At-the-money-forward options with expirations of 10,..., 730 days. 
- Implied volatility is derived by linear interpolation from Volatility_Surface file.
- One _interpolated_ IV for each secid, date, day to expiration
  - Interpolation: forward price of underlying security is calculated with zero curve adn the projected distributions. Then the volatility surface points are linearly interpolated to the forward price and the target expiration to give at-the-money-forward implied volatility. 
- large discrepency with the permno_match_implied_vol_update_v13
### Volatility_Surface File 
- Interpolated volatility surface for each security each day methodology based on kernel smoothing algorithm.
- Implied volatility surface is function of how IV varies with call-equivalent delta(moneyness) and days to expiration.
- Standardized options, calls and puts, expirations 10, .., 730 days, various deltas at 0.05 increments, positive(call), negative(put)
- Check how the permno_iv dataset grouped values for each secid, date and days to expiration. is it weighted average by the number of security?
- Generated the average(non-weighted) matches permno_iv data better than  
