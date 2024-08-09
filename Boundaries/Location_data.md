## Reference USA 
- For all, check if data download is possible, else use integrated R
### 2001-2016
- 3 pairs of lat long, some small difference in the hundredth digit after decimal even in same year's observation, call to ask them the difference?
- ABI does not uniquely identify a company, changes with a different year's filing, company name is better identifier, or use Company name to merge with compustat etc for a GVKEY (have code for LLM to merge strings)
- 6 decimal places: Can identify a location within about 0.11 meters (approximately 4.3 inches).

### 2017
- ABI mostly uniquely identify company
- CLean, usable, 6-decimal lat long with year recorded, scope: 2020 onwards

## D&B
- In densely populated urban areas, a ZIP+4 code might cover an area as small as a single building or a city block, which could be around 100 to 300 meters on each side. In less densely populated suburban or rural areas, a ZIP+4 code might cover a larger area, potentially ranging from 300 meters up to 1,000 meters or more. ZIP+4 code might typically cover an area from about 100 to 1,000 meters.
- 94% obs have zip+4
- DUNSNO uniquely identifies company

## Conclusion
- Potential approaches
  1) use ReferenceUSA for all
     - Pros: 6 decimal lat long
     - Cons: data cleaning and merge two different sets of data. 2000-2016 data may be incomplete. need to check discrepencies between certain long lat data; crosswalk with 2020-2023 file to see if ABI links; check inconsistencies in company name and ABI for 2000-2016
  2) use RefernceUSA for 2020-2023, and D&B for 2000-2016
     - Pros: very complete firms zip +4 from 2000
     - Cons: need to merge between two datasets by firm name to crosswalk and long lat 
  3) use D&B for 2000-2016
     - Pros: very complete firms zip +4 from 2000, 
     - Cons: need to convert to long lat 
     
