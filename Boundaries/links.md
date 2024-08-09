## SECID PERMNO link
scores:

1       =       8-digit cusip historical matching

2       =       historical ticker matching plus 6-digit cusips and similar company names (spedis < 30)

3       =       historical ticker matching plus 6-digit cusips and company names are different

4       =       historical ticker matching and similar company name (spedis < 30) but 6-digit cusips are different

5       =       historical ticker matching but 6-digit cusips and company names are different

6       =       no matching

CUSIP (Committee on Uniform Securities Identification Procedures) identifiers can be reused, particularly under certain circumstances.

- Reassignment After Corporate Actions: CUSIP codes can be reused after certain corporate actions, such as mergers, acquisitions, or the dissolution of a company. For example, if a company ceases to exist (e.g., due to a merger or bankruptcy), its CUSIP might be reassigned to a different security in the future.
- Limited CUSIP Space: The CUSIP system has a finite number of possible combinations (approximately 9 million), so to manage the identifier space efficiently, older or retired CUSIPs can be recycled.
- Implications for Data Analysis: The potential for CUSIP reuse means that when working with historical financial data, it's important to be cautious. Analysts often need to cross-reference other identifiers (like PERMNO, GVKEY, or ISIN) to ensure accurate tracking of securities over time.
- Historical Tracking: In databases like CRSP or Compustat, where historical tracking of securities is essential, additional identifiers like PERMNO (which is never reused) are used to provide consistent tracking over time, even if the CUSIP changes or is reused.
- Because of this potential for reuse, CUSIP is not ideal for long-term tracking of securities without additional context or supplementary identifiers.
