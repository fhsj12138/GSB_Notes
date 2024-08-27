Features of the Optionmetrics data that should be noted when selecting filters
### Missing Values
- OPTION_PRICE STD_OPTION_PRICE VOLATILITY_SURFACE
- OPTION_PRICE: IV set to -99.99 if option is special settlement, midpoint of bid/ask price is below intrinsic value, implied volatility calculation fails to converge, underlying price is not available
- STD_OPTION_PRICE VOLATILITY_SURFACE implied volatility set to -99.99 if insufficient number of option data points to interpolate with.

### Calculation of IV 
#### European Options 
- Only can exercise at expiration date, commonly used in financial markets for indices and some currency options
- Priced lower than American options as less flexibility, Black_Scholes model simpler as do not need to account for the possibility of early exercise
$C = Se^{-qT}N(d_1) - Ke^{-rT}N(d_2)$
$P = Ke^{-rT}N(-d_2) - Se^{-qT}N(-d_1)$
where

$$d_1 = [ln(S/K) +(r - q + {1 /over 2} \sigma ^2 )T]/\sigma \sqrt{T}$$
#### American Options 
- Exercisable at any time before expiration, stock options and ETFs
- More complex pricing models, such as Binomial Tree model, to account for the possibility of early exercise
- 
