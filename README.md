# Analysis of DSNY OATH Sanitation Database — 10/2021 to 10/2026


## Data

This analysis uses two spreadsheets.

The spreadsheets come from the following sources:

- NYC Open Data - OATH Hearings Division:
  - `New_DSNY_Sanitation_Oath_Database_20261019.csv`: Raw data of NYC sanitation violations, penalties and oustanding balances 

- NYC Department of City Planning:
  - `Primary_Land_Use_Tax_Lot_Output_(PLUTO)_20261026.csv`: Property data including building characteristics and property ZIP codes

Each of the spreadsheets contain, among others, the following columns relevant to the analysis:

- `BBL` — Borough, block, lot identifier created from the OATH data and used to match PLUTO and OATH data
- `Violation Date` — Date sanitation violation was issued
- `Total Violation Amount` — Original violation amount
- `Penalty Imposed` — Total amount assessed including original violation amount
- `Balance Due` — Remaining unpaid balance
- `unitsres` — Number of residential units in property
- `postcode` — Property zip code


## Methodology

The notebook [`dsny_sanitation_analysis.ipynb`](Notebooks/dsny_sanitation_analysis.ipynb) performs the following analyses:

##### Part 1: Data Cleaning and Merging 

- Filtered the OATH sanitation data to a five year period from October 14, 2021 to October 14, 2026
- Created a BBL identifier using borough, block, and lot information to match PLUTO column
- Merged OATH and PLUTO datasets using BBL
- Filtered the merged dataset to residential properties with 1-3 units 


##### Part 2: Analysis of Sanitation Fines

- Grouped sanitation violations by property ZIP 
- Calculated oustanding fine balances by ZIP 
- Counted unique residential properties (by BBL) with at least one oustanding sanitation fine
- Identified tickets where total penalty exceeded original violation amount 
- Examined number of escalated penalties that had oustanding balance and additional amounts assessed across ZIP 


## Outputs

The notebooks output this spreadsheet which contains: Zip code level summary of sanitation violations, penalty escalation, and additional amounts assessed for residential properties with 1-3 units. [`penalty_zipz_1_3_units.csv`](Output/penalty_zipz_1_3_units.csv).

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3.14.3
- Jupyter Notebook
- pandas


## Feedback / Questions?

Contact Macy Hanzlik-Barend at macyhb@gmail.com
