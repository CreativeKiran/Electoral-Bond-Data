# 📊 Electoral Bond Data Analysis
This project creates a database from electoral bond data and explores SQL queries for EDA to enhance political funding transparency in India.

# 📁 Project Description
In this repository, we are creating a database on electoral bond data and writing SQL queries to perform Exploratory Data Analysis (EDA).

# 🎯 What Are We Accomplishing?
We are transforming raw data into a database and exploring SQL queries to analyze this data.

# 📄 Electoral Bond Data
## Description
In a significant development affecting political transparency in India, the Supreme Court struck down the Electoral Bond scheme, emphasizing that anonymity in political funding undermines voters' right to information. This decision mandates transparency in political party funding, aligning with democratic values.

Following the ruling, the Election Commission of India (ECI) released comprehensive data on March 21, 2024, through the State Bank of India (SBI). This dataset includes information on donors and recipients from April 12, 2019, to January 11, 2024, with bond numbers for matching purchasers and recipients. Additional data from the Enforcement Directorate supplements this dataset.

The ECI published two separate lists of donors and recipients on its website in accordance with a Supreme Court order.

# 🔗 Data Sources
These are the official sites where the data is released by the government:

Election Commission of India
Enforcement Directorate (Data available only since 2021)
Comptroller and Auditor General of India (Data extracted from 2018)
Income Tax Department (Data extracted from 2010)
Central Bureau of Investigation (Data extracted from 2018)
Ministry of Corporate Affairs
The bank codes details have been extracted from various official sources. Only a few SBI branches are authorized to issue electoral bonds, and this table contains the details of those branches.

Note: We obtained the dataset from Kaggle, available in comma-separated format (CSV). This data, unlike the official PDFs, is in a more accessible format for analysis and processing.

## Kaggle Source:

Kaggle Dataset
# 🗂 Data Dictionary
Our data consists of three tables:

### 1. Donor Data
No	Column Name	Description
1	SNo	Serial number. A sequential number assigned to each record.
2	Urn	Unique reference number.
3	JournalDate	Date of journal entry.
4	PurchaseDate	Date of bond purchase.
5	ExpiryDate	Expiry date of the bond.
6	Purchaser	Name of the purchaser.
7	Prefix	Prefix code associated with the bond.
8	BondNumber	A number followed by the prefix code.
9	Denominations	Value of the bond. Possible values: [1K, 10K, 1L, 10L, 1Cr].
10	PayBranchCode	Payment branch code (IFSC Code) where the bond is issued.
11	PayTeller	Teller ID who issued the bond.
### 2. Recipient Data
No	Column Name	Description
1	SNo	Serial number. A sequential number assigned to each record.
2	DateEncashment	Date of bond encashment.
3	PartyName	Name of the political party (recipient).
4	AccountNum	Account number of the party. Only the last four digits are visible for privacy.
5	Prefix	Prefix code associated with the bond.
6	BondNumber	A number followed by the prefix code.
7	Denominations	Value of the bond. Possible values: [1K, 10K, 1L, 10L, 1Cr].
8	PayBranchCode	Payment branch code (IFSC Code) where the bond is encashed.
9	PayTeller	Teller ID who encashed the bond.
### 3. Bank Branch Data
No	Column Name	Description
1	Sl.No.	Serial number. A sequential number assigned to each record.
2	State/UT	State/UT where the bank is located.
3	Name of the Branch & Address	Complete address of the bank.
4	City	City where the bank branch is located.
5	Branch Code No	IFSC Code. A unique code assigned to each branch.
# 🌐 Domain Knowledge
Each bond is characterized by a prefix and a bond number. Together, they form a unique identification ID. By matching these codes across tables, we can identify the source of monetary donations to specific political parties.

In the donor and recipient tables, we have branch codes indicating the bond issuing and encashing branches. By joining these tables with bank branch data, we can track money flow from city to city.

Every bond has a 14-day validity before expiration. If not encashed, the amount is transferred to the Prime Minister's fund.

The data released by the government is incomplete, as the record counts in the donor and recipient tables do not match. This discrepancy is considered in our analysis.

Certain companies have acquired bonds under slightly varied names. We address these discrepancies in the data cleaning section of the code.

# 📂 File Structure
graphql
Copy code
EDA SQL electoral bonddata
│
├───Data Cleaning
│       Data Cleaning.xlsx
│       README.md
│
├───FinalData
│       bankdata.tsv
│       bonddata.csv
│       total_allDonorData.csv
│       total_allReciverData.csv
│
├───RawData
│       Bankcodes.tsv
│       bank_data.xlsx
│       donor_data.csv
│       reciver_data.csv
│
└───Schema
        Final Schema.png
        Final Schema.svg
        README.md
        Schema.xlsx
electoralbonddata_database.sql 
Final_database_data.ipynb
Queries.pdf
queries.sql
README.md
Data Cleaning Folder: Contains files related to data cleaning.
RawData Folder: Contains raw data files.
FinalData Folder: Contains final data files used to create the database, which are the output from Final_database_data.ipynb.
Schema Folder: Contains files explaining the schema we designed.
queries.sql: SQL file with queries written on the database.
Queries.pdf: PDF version of queries.sql for easy reference.
electoralbonddata_database.sql: Self-contained database file.
