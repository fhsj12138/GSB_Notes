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
- Time between now and option expiration divided into N sub-periods. Across each sub-period, security price assumed to move either up or down. Size of security price move is determined by implied volatility and size of the sub-period. Security price at the end of sub-period i is given by one of:

  $$S^{up}_{i+1} = S_i u \equiv S_i exp(\sigma \sqrt{h})$$

  $$S^{down}_{i+1} = S_i d \equiv S_i exp(-\sigma \sqrt{h})$$

  where $h \equiv T/N$ is the size of the sub-period, and $S_i$ is the security price at the beginning of the sub-period

- Price of a call option at the begining of each sub-period is dependent on its price at the end of the sub-period, given by
  $$ C_i = max ( (pC^{up}_{i+1} + (1-p) C^{down} _{i+1} ) /R , S_i - K) $$
  likewise for put option. r interest rate, q option implied borrow rate, $R \equiv exp((r-q)h)$, $C^{up} _{i=1}$  $C^{down} _{i=1}$ are the price of the option at the end of the sub-period, depending on whether securit price moves up or down, risk-neutral probability $p$ is given by $p = {R-d}\over {u-d}$
- Start at current security price S and build a tree of all the possible security prices at the end of each sub-period, under the assumption that the security can only move up or down. Tree up to time T, option expiration.
- Then option is priced at expiration by setting the option expiration value equal to exercise value $C = max(S_K, 0)$ and $P = max(K-S,0)$. Option price at the beginning of each sub-period is determind by the option prices at the end of the sub-period. Calculated price of the optoin at time $i=0$ is the theoretical model price
- Compute _implied volatility_ of an option given price, model run iteratively with new values of $\sigma$ until model price of the option converges to its market price, defined as the midpoint of the option's best closing bid and best closing offer prices.
- CRR model requires very large number of sub-periods to achieve good results, $N>1000$

<img width="377" alt="Screenshot 2024-08-27 at 1 42 48 PM" src="https://github.com/user-attachments/assets/6eda885c-e3e7-4d45-a1cf-4e3d3cdd8e41">

  
