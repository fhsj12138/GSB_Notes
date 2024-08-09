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


Multiple SECID values can be matched to the same PERMNO 

1. Stock Splits and Reverse Splits:
If a company undergoes a stock split or reverse split, the CRSP database might create a new SECID to reflect the change in the number of shares, even though the underlying security (tracked by PERMNO) remains the same.
2. Mergers and Acquisitions:
After a merger or acquisition, the acquiring company may issue new securities to replace those of the acquired company. In some cases, this might result in a new SECID being assigned to the new security issued by the same underlying company (same PERMNO).
3. Reorganizations:
In the case of a corporate reorganization, such as a spinoff or restructuring, the company might issue new securities with new SECIDs, but the original PERMNO remains the same for the underlying company.
4. Ticker and CUSIP Changes:
If a company changes its ticker symbol or CUSIP, CRSP might assign a new SECID to reflect this change, but the PERMNO remains the same because the underlying company hasn't changed.
5. Multiple Share Classes:
A company might have multiple share classes (e.g., Class A and Class B shares). Each share class might have a different SECID, but they could be associated with the same PERMNO if they represent the same underlying company.
Summary:
While PERMNO is a permanent and unique identifier that consistently tracks a company over time, SECID can change in response to corporate actions or structural changes in the security. Therefore, it’s possible for multiple SECIDs to be associated with the same PERMNO when different aspects or changes of a single underlying security or company are being tracked.
