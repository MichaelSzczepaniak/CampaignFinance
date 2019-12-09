# Project Goal
Explores historical US presidential and US senate races during presidential election years.  The two main reseach questions driving the analysis were the following:

1. Does the difference between how much a presidential or US senate candidate raises vs their opponent tend to be larger or smaller when the race is against an incumbent vs when the race is between 2 non-incumbents?

2. How well does a logistic regression model that only controls for how much a campaign raises and whether they are an incumbent or not do to predict whether a presidential or US senate candidate will win?


# Data Used for Project

## Presidential Elections - data/USPresidentialOverall.tsv

Tab delimited data file of US presidential elections from 1980 thru 2016 for the top two candidates.  This file has the following columns:

### Year
 - **Description**: year of the election
### Candidate1
 - **Description**: last name, first initial of first candidate
### Candidate2
 - **Description**: last name, first initial of second candidate
### Party1
 - **Description**: party of Candidate1
### Party2
 - **Description**: party of Candidate1
### Winner
 - **Description**: last name, first initial of the winner
### CampaignRaised1
 - **Description**: amount of money Candidate1 raised in US dollars
### CampaignRaised2
 - **Description**: amount of money Candidate2 raised in US dollars
### PopularVote1
 - **Description**: number of popular votes received by Candidate1
### PopularVote2
 - **Description**: number of popular votes received by Candidate2
### Incumbent
 - **Description**: indicator of whether race was between an incumbent and a challenger: 0 if both candidates were challengers, 1 if Candidate1 was an incumbent, 2 if Candidate2 was an incumbent

### Source
First 8 columns:  [FEC website](https://www.fec.gov/data/raising-bythenumbers/)  
Columns 9, 10 and 11:  [Encyclopedia Britanica website](https://www.britannica.com/topic/United-States-Presidential-Election-Results-1788863)  

## Presidential Elections - data/USPresidentialOverall2.tsv

Same data as **data/USPresidentialOverall2.tsv**, but restructured (pivotted) .  This file has the following columns:

### Year
 - **Description**: year of the election
### Candidate
 - **Description**: last name, first 1 or 2 initials of each candidate
### Party
 - **Description**: party of each candidate: Democrat or Republican
### Won
 - **Description**: 1 if they were the winner, 0 if they were the loser
### Raised
 - **Description**: amount of money each candidate raised in US dollars
### isIncumbent
 - **Description**: 1 if candidate was an incumbent, 0 if they were not
### isIncumbentRace
 - **Description**: 1 if the race was against an incumbent, 0 if the race was against two non-incumbent challengers
### RaisedTop2Total
 - **Description**: amount of money raised by the top 2 candidates in a race in US dollars

### Source
same as **data/USPresidentialOverall.tsv**

## Senate Elections - data/1980-2016-SenateElections.csv

Comma delimited data file of US senate elections in presidential election years from 1980 thru 2016.  This file has the following columns:

###year
 - **Description**: year in which election was held
 
---------------

###state
 - **Description**: state name

 ---------------
 
###state_po
 - **Description**: U.S. postal code state abbreviation

 ---------------
 
###state_fips
 - **Description**: State FIPS code

----------------

###state_cen
 - **Description**: U.S. Census state code

 ---------------
 
### state_ic
 - **Description**: ICPSR state code

 --------------- 
 
###office
- **Description**: U.S. Senate (constant)
  
---------------

### district
 - **Description**: statewide (constant)

---------------

### stage
 - **Description**: electoral stage
 - **Coding**: 

| code | definition |
|:---|:---|
| "gen" | general elections |
| "pri" | primary elections |

 - **Note**: Only appears in special cases. Consult original House Clerk report for these cases.

----------------

### special
- **Description**: special election
- Coding  

| code | definition |
|:---|:---|
| "TRUE" | special elections |
| "FALSE" | regular elections |

----------------

### candidate
  - **Description**: name of the candidate
  - **Note**: The name is as it appears in the House Clerk report.

----------------

### party
- **Description**: party of the candidate (always entirely lowercase)
  - **Note**: Parties are as they appear in the House Clerk report.  In states that allow candidates to appear on multiple party lines, separate vote totals are indicated for each party.  Therefore, for analysis that involves candidate totals, it will be necessary to aggregate across all party lines within a district.  For analysis that focuses on two-party vote totals, it will be necessary to account for major party candidates who receive votes under multiple party labels. Minnesota party labels are given as they appear on the Minnesota ballots. Future versions of this file will include codes for candidates who are endorsed by major parties, regardless of the party label under which they receive votes.
	
----------------
	
### writein
- **Description**: vote totals associated with write-in candidates
- **Coding**:

| code | definition |
|:---|:---|
| "TRUE" | write-in candidates |
| "FALSE" | non-write-in candidates |

-----------------

### mode
- **Description**: mode of voting; states with data that doesn't break down returns by mode are marked as "total"

----------------
	
### candidatevotes 
 - **Description**: votes received by this candidate for this particular party

----------------

### totalvotes
 - **Description**: total number of votes cast for this election

 ----------------

### unofficial
- **Description**: TRUE/FALSE indicator for unofficial result (to be updated later); this appears only for 2018 data in some cases

----------------

### version  
- **Description**: date when this dataset was finalize

### Source
[MIT Election Data Science Lab](http://electionlab.mit.edu/) using the interface hosted by [Harvard Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/PEJ5QU)

## Senate Elections - data/df_sen_all_manually_fixed2.csv

Comma delimited data file of US senate elections in presidential election years from 1980 thru 2016.  This file is a manually edited version of **data/1980-2016-SenateElections.csv**.  The manual edits are described in the **Quality Check on Merged Data** and **More Manual Fixing** sections of the notebook.  This file has the following columns:

###year
 - **Description**: year in which election was held
 
---------------

###state_name
 - **Description**: full state name
 
---------------

###state
 - **Description**: 2 letter state acronym

----------------

### candidate
  - **Description**: name of the candidate first name, last name

----------------

### party_name
- **Description**: full name of the party of the candidate (always entirely lowercase)

----------------

### candidatevotes 
 - **Description**: votes received by this candidate for this particular party

----------------

### totalvotes
 - **Description**: total number of votes cast for this election race

 ----------------

### Won
- **Description**: 1 if the the candidate won the race, 0 if they lost

----------------

### party
- **Description**: first 3 letters of the party of the candidate (upper case)

----------------

### StripName
  - **Description**: name of the candidate first name, last name with leading and trailing spaces removed

----------------

### CAND_NAME
  - **Description**: name of the candidate as it appeared in the financial data (upper case)
  - **Note**: missing names exist due to issue related to joining of election and financial data.

----------------

### CAND_IC
  - **Description**: an indicator of whether a candidate was an incumbent or not
  - **Note**: missing values generally indicate that candidate was a challenger

----------------

### TTL_RECEIPTS
- **Description**: total amount the candidate raised for this race in US dollars

### Source
- same as **data/1980-2016-SenateElections.csv**