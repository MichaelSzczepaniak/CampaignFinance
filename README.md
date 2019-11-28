


# Data Compile for Project

## Presidential Elections

data/USPresidentialOverall.tsv

Tab delimited data file of US presidential elections from 1980 thru 2016 for the top two candidates.  This file has the following columns:

###Year
 - **Description**: year of the election
###Candidate1
 - **Description**: last name, first initial of first candidate
###Candidate2
 - **Description**: last name, first initial of second candidate
###Party1
 - **Description**: party of Candidate1
###Party2
 - **Description**: party of Candidate1
###Winner
 - **Description**: last name, first initial of the winner
###CampaignRaised1
 - **Description**: amount of money Candidate1 raised in US dollars
###CampaignRaised2
 - **Description**: amount of money Candidate2 raised in US dollars
###PopularVote1
 - **Description**: number of popular votes received by Candidate1
###PopularVote2
 - **Description**: number of popular votes received by Candidate2
###Incumbent
 - **Description**: indicator of whether race was between an incumbent and a challenger: 0 if both candidates were challengers, 1 if Candidate1 was an incumbent, 2 if Candidate2 was an incumbent

###Source
First 8 columns:  [FEC website](https://www.fec.gov/data/raising-bythenumbers/)  
Columns 9, 10 and 11:  [Encyclopedia Britanica website](https://www.britannica.com/topic/United-States-Presidential-Election-Results-1788863)  

## Senate Elections

data/1980-2016-SenateElections.csv

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

###Source
[MIT Election Data Science Lab](http://electionlab.mit.edu/) using the interface hosted by (Harvard Dataverse)[https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/PEJ5QU]