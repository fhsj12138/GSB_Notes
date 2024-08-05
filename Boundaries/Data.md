## Reference USA 

ReferenceUSA (now known as Data Axle Reference Solutions) is a comprehensive database that provides detailed information on businesses and consumers in the United States and Canada. 
### Key Features and Data Components
#### Business Data:
- Business Listings: Provides detailed information on over 15 million businesses in the U.S. and Canada, including small businesses, corporations, and non-profits.
- Company Information: Includes company names, addresses, phone numbers, executive names and titles, employee size, sales volume, SIC/NAICS codes, and business types.
- Industry Data: Detailed industry information, including market research and analysis, industry trends, and competitive landscapes.
- Business Profiles: Comprehensive profiles for each business, including historical data, business expenditures, and credit ratings.
#### Consumer Data:
- Residential Listings: Information on over 260 million consumers in the U.S., including names, addresses, phone numbers, and demographics.
- Demographic Data: Detailed demographic information, such as age, income, household size, marital status, and home ownership.
- Lifestyle and Interest Data: Insights into consumer lifestyles, purchasing behavior, and interests.
#### Mapping and Geospatial Data:
- Geospatial Analysis: Tools for mapping and visualizing business and consumer data geographically, which can be used for market analysis, location planning, and demographic studies.
#### Customizable Searches:
- Advanced Search Features: Users can perform highly customized searches using various criteria, such as geography, industry, business size, sales volume, and demographics.
- Exporting Data: Ability to export search results into various formats for further analysis and use.

## CRSP Dataset
historical data on U.S. financial markets, enabling detailed analysis of market behavior, asset pricing, investment strategies, and more.

### Key Features and Components
#### Stock Data:
- Daily and Monthly Stock Prices: Historical data on stock prices, trading volumes, and returns for all U.S. exchange-listed stocks.
- Corporate Actions: Information on stock splits, dividends, mergers, and other corporate actions.
- Identifiers: Unique identifiers for securities, such as PERMNO and PERMCO, which facilitate longitudinal studies and data consistency.
#### Index Data:
- Market Indices: Historical data on major U.S. stock market indices, including the S&P 500, NASDAQ, and others.
- Index Returns: Daily, monthly, and annual returns data for market indices, facilitating market-wide analysis.
#### Mutual Fund Data:
- Fund Performance: Detailed historical performance data for mutual funds, including returns, NAVs (Net Asset Values), and expense ratios.
- Fund Attributes: Information on fund attributes such as investment objectives, management companies, and fund inception dates.
#### Treasury and Bond Data:
- Treasury Securities: Historical data on U.S. Treasury securities, including bills, notes, and bonds.
- Bond Prices and Yields: Data on corporate bond prices, yields, and other bond-related metrics.
#### Survivorship-Bias-Free Data:
- Inclusion of Delisted Securities: CRSP includes data on securities that have been delisted, providing a more accurate historical record and avoiding survivorship bias.
#### Cross-Sectional and Time-Series Data:
Comprehensive Coverage: Data spans several decades, providing both cross-sectional and time-series datasets suitable for a wide range of research applications.

## ArcGIS 
Geographic information system (GIS) developed by Esri that enables users to create, manage, analyze, and visualize spatial data. 
Used across various industries for mapping and spatial analysis, providing tools and capabilities for working with geographic data in both 2D and 3D environments.

# Variables 
### Delta
- interpretation: approximation of the probability that the option will end up ITM at expiration
  - ITM: for call, when current price of underlying asset (S) is above strike price(K); delta > 0.5; for put, S < K, delta < - 0.5 
  - ATM: S = K; for call delta ~ 0.5, for put, delta ~ -0.5
  - OTM: S < K; for call 0 < delta < 0.5, for put -0.5 < delta < 0
### Moneyness 
- $(K/S -1) x 100%$
- in option_sig, seemed to have calculated as K/S

