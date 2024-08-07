### Kelly, 2016 IVD Calculations 
- Let $IV_{t,m}$ denote the implied volatlity at time $t$ of an ATM option maturing at time $m>t$.
- Implied volatility calculated by OptionMetrics (Kelly summarizes information in the pdf file, could be using either option_prices or another file).
- Interested in options whose live span dates of political events, $\tau$, interest in $IV_{t, m}$ for $t< \tau < m$.
- Equity options expire on a regular monthly grid, in the US, expiration date is the Saturday that follows the third Friday of each month.
- Find the location of each political event $\tau$ relative to the grid.
- Lable expiration dates, one before and one after $\tau$, as $a, b$, such that $a < \tau < b$.
- _Filter 1_: Drop if implied volatilities exceed 100% 
- _Filter 2_: If this distance more than 5 days, choose $a, b$ that are one month apart. $b = a+1$ month. If $\tau$ is within 5 days of the nearest expiration date, choose $a, b$ two months apart so neither is within 5 day window.
  - Some uncertainty is just noise? could be resolved a few days before or after the event
  - Avoid using ultra-short-maturity options, never uses options with 6 or fewer days to maturity. Ultra-short maturity options have very small time premiums, and their IV are inaccurate due to high sensitivity to price nonsynchronicity and other measurement errors. Beber and Brandt (2006) also exclude options with less than a week to maturity 
- Define $c$ as the expiration date immediately following $b$, so $b$ and $c$ are 1 month apart.
- Interested in $IV_{b-s,b}$ where $b-s < \tau < b$
- To create more robust $IV_{b-s,b}$
   1. subtract average $IV$ of the same country's options with neighboring expiration dates by computing $IV_{b-s,b} - {1 \over 2}(IV_{a-s,a}+IV_{c-s,c})$. To adjust for cross-country difference in volatility, ie same as country fixed effects. Also eliminates slow-moving fixed-effect approach
   2. replace $IV_{a-s,a}, IV_{b-s,b}, IV_{c-s,c}$ for any given $s$ by averages of $IV$ values across multiple values of $s$ to reduce noise in the estimation.
- For each political event $\tau$ define _implied volatility difference_, $IVD_{\tau}$ as
  $IVD_{\tau} = \bar{IV}_b - {1 \over 2} (\bar{IV_a} +\bar{IV_c})$
  where $\bar{IV_i}$ $i=a,b,c$  are square roots of averages of implied variances computed across all acceptable put and call options expiring at times $a, b, c$ respectively
- _Filter 3_: Criteria for acceptable options
  1. ATM options, defined as with deltas $0.4 < |\Delta| < 0.5$ to obtain a liquid set of ATM options $^1$. If multiple options satisfy this ATM definition, all used in average.
  2. acceptable options have positive open interest $^2$. Excption US data prior to 1996, require positive volumn as pre-1996 data come from a different source (MDR).
  3. acceptable options have $s$ days until expiration where $s$ belongs to a given time window
     - Define $\bar{IV_b}$ as $\bar{IV_b}=Mean ( IV_{b-s,b}: b - s \in [\tau -20, \tau-1])$ which is the equal-weighted average of $IV_{b-s, b}$ across the values of $s$ for which $b-s$ is in the 20-trading-day window preceding time $\tau$.
     - Choose 20 trading days (about 1 month) to smooth out noisy day-to-day fluctuations in option prices.
- Thus, $\bar{IV_{b-s,b}}$ is the average implied volatility across all ATM options with open interest that expire at time $b$ and whose values are computed in the month _before_ $\tau$.
- Similarly for $\bar{IV_{a-s,a}}$, $\bar{IV_{c-s,c}}$, choose 20-day windows that end $b- \tau +1$ trading days before $a$ and $c$, respectively, such that the times to maturity for options entering into $\bar{IV_a}$, $\bar{IV_b}$, $\bar{IV_c}$ are fully comparable.
- A positive value of $IVD_{\tau}$ indicates options whose lives span time $\tau$ are more expensive on average than the neighboring options whose lives do not span $\tau$. 


$^1$ Liquidity ATM> OTM > ITM. ATM's are most sensitive to small changs in the price of the underlying asset.
| Type/Delta values | Call | Put |
| ---- | ---- | --- |
|ATM|+0.5|-0.5|
|ITM|+1|-1|
|OTM|0|0|

$^2$ total number of outstanding contracts not settled or closed to ensure it is actively traded and gives reliable price data 
