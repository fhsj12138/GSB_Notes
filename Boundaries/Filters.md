Features of the Optionmetrics data that should be noted when selecting filters
### Missing Values
- OPTION_PRICE STD_OPTION_PRICE VOLATILITY_SURFACE
- OPTION_PRICE: IV set to -99.99 if option is special settlement, midpoint of bid/ask price is below intrinsic value, implied volatility calculation fails to converge, underlying price is not available
- STD_OPTION_PRICE VOLATILITY_SURFACE implied volatility set to -99.99 if insufficient number of option data points to interpolate with.

### Calculation of IV 
#### European Options 
- Only can exercise at expiration date, commonly used in financial markets for indices and some currency options
- Priced lower than American options as less flexibility, Black_Scholes model simpler as do not need to account for the possibility of early exercise

$$C = Se^{-qT}N(d_1) - Ke^{-rT}N(d_2)$$

$$P = Ke^{-rT}N(-d_2) - Se^{-qT}N(-d_1)$$ 

where
$d_1 = [ln(S/K) +(r - q + {1 \over 2} \sigma ^2 )T]/\sigma \sqrt{T}$
$d_2 = d_1 - \sigma \sqrt{T}$
C is price of call option, P price of put option, S current underlying security price, K strike prie of option, T time in years remaining to option expiration, r continuously-compounded interest rate, q option implied borrow rate, $\sigma$ implied volatility, $N(d_1)$ is CDF of normal distribution with mean 0 and standard deviation 1. 
- To calculate implied volatilities and associated option sensitivities, theoretical option price set equal to midpoint of best closing bid price and best closing offer price for option. Formula is inverted using a numerical search technique to calculate the IV. 

#### American Options 
- Exercisable at any time before expiration, stock options and ETFs
- More complex pricing models, such as Binomial Tree model, to account for the possibility of early exercise
- Priced using propretary pricing algorithm based on industry-standard Cox-Ross-Rubinstein (CRR) binomial tree model. Accomodate underlying securities with either discrete dividend payments or continuous dividend yield.
- 
