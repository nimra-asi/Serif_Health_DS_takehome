# Serif_Health_DS_takehome
List of files with descriptions:
* Serif_Health_DS_Takehome_Nimra_Asi.ipynb: Jupyter notebook containing Python code used for data analysis. Code is commented and provides additional thought process behind particular decisions made.
* matched_data.csv: this is a csv file containing selected columns as well as rates for data where a match was found between the hospital and payer extracts
* hospital_extract_unmatched_rows.csv: csv file containing the hospital_extract data that was not matched to any data in the payer_extract
* payer_extract_unmatched_rows.csv: csv file containing the payer_extract data that was not matched to any data in the hospital extract

# How to Run:
Update the "hospital_extract_data_loc" and "payer_extract_data_loc" variables with the location of the hospital and payer data location respectively. Update the "output_loc" variable with the location where you would like any output files to be saved (in Jupyter notebook, cell 2).

# Results Overview
* 33 rows in the hospital data were not matched out of 222 total rows in hospital extract (match rate: 85%)
* 21 rows in the payer data were not matched out of 265 total unique rows (from relevant payers i.e. payers present in the hospital data) in the payer extract (match rate: 92%).
* The columns used for matching were: code, payer, hospital_name (by mapping EIN in hospital data to the releveant hospital name). This was possible with some quick Googling since we only had 3 unique hospitals/EINs present in this dataset.
* Although we do have additional columns that may be used for matching (explored in the dataset) ultimately decided to only match only on the 3 columns above that we have the most confidence in, especially since the match rate is already pretty high using these alone.

# TO DO:
* This solution is only possible because we only have a few EINs present that can be quickly researched. Ideally, would like like to have a comprehensive EIN to hospital_name crosswalk file rather than manual inputs (as was performed here).
* I have varying levels of confidence in the data assumptions made currently. For instance am pretty confident that "IPPS" in the "cms_baseline_schedule" column in the hospital data can match to "inpatient" in the "setting" column in the payer data but less confident about the mapping of other entries. Given more time, would like to add a confidence score (high=3, medium=2, and low=2) for assumptions made and then take the minimum confidence across all assumptions made for a particular row to be the overall confidence level for that particular row if matched.
* Would like to try and get a sense (possibly from historical data or research) for the range of variation possible from the cms_baseline_rate for particular services. Thus, one way to identify mismatched data, or build confidence in the outputs would be be to check if the suggested rate is within that "expected" range of variation.
* Given more time, I would like to look further into the plans/ network columns since there may be a way to match between the datasets based on that. Maybe try and obtain a reference for all plans administered by a particular network.
