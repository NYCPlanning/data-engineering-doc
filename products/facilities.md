# Facilities database ![CI](https://github.com/NYCPlanning/db-facilities-tmp/workflows/CI/badge.svg)

## About

The City Planning Facilities Database aggregates more than 35,000 records from 52 different public data sources provided by City, State, and Federal agencies.

While each source agency classifies its facilities according to their own naming systems, we have grouped all facilities and program sites into the following seven categories to help planners navigate the data more easily:

* Health and Human Services
* Education, Child Welfare, and Youth
* Parks, Gardens, and Historical Sites
* Libraries and Cultural Programs
* Public Safety, Emergency Services, and Administration of Justice
* Core Infrastructure and Transportation
* Administration of Government

Within each of these domains, each record is further categorized into a set of facility groups, subgroups, and types that are intended to make the data easy to navigate and more useful for specific planning purposes. Facility types and names appear as they do in source datasets, wherever possible. A full listing of the facility categories is provided in the data dictionary.

### Sources

DCP, DOT, DSNY, HRA, NYPL, NYSED, NYSOPRHP, SBS, HHC, DYCD, NYCHA, NYCDOE, NYSDEC, QPL, NYCDOE, DoiTT, NYSOMH, DCAS, DCLA, NYSOPWDD, BPL, USNPS, DPR, NYSDOH, DCA, DFTA, DOHMH, MOEO, USCOURTS, NYSOASAS, NYSDOCCS, NYCOURTS, NYCDOC, ACS, AMTRAK, BBPC, HRPT, MTA, NYSDOT, PANYNJ, TGI, RIOC

### Disclaimer

The facilities database is being provided by the Department of City Planning (DCP) on the GitHub website for informational purposes only. DCP does not warrant the completeness, accuracy, content, or fitness for any particular purpose or use of the dataset, nor are any such warranties to be implied or inferred with respect to the dataset as furnished on the website

DCP and the City are not liable for any deficiencies in the completeness, accuracy, content, or fitness for any particular purpose or use of the dataset, or applications utilizing Dataset, provided by any third party. The City Planning Facilities Database (FacDB) is only as good as the source data it aggregates, and the Department of City Planning cannot verify the accuracy of all records. Please read more about specific data and analysis limitations before using this data.

### Compilation Process

Since the facility records are aggregated from many datasets designed for different purposes, the data will be transformed over several stages to reach its final state. The stages are described below and all the scripts used are available on the [NYC Planning GitHub page](https://github.com/NYCPlanning/db-facilities).

### Data Quality

This database and its [interactive map](http://capitalplanning.nyc.gov/facilities) build upon and replace City Planning’s decades-old work on the Selected Facilities and Program Sites Database. Improvements include more facility types, improved data quality, and a restructured database for easier use. We have also automated our data-update processes for the majority of sources. Please read more about the Caveats.

### Caveats

**Analysis Limitations.** As a result of the data limitations and inconsistencies listed below users should be careful in their use of this database so as to avoid developing suspect analyses. For example, a comparison of the density or accessibility of facilities across neighborhoods should recognize that some of the facilities included are organizational headquarters rather than service sites and that this database is not authoritatively comprehensive. In addition, we rely on source data from other agencies to populate the database, and some of these sources may fall out-of-date. Users can find the date of each source dataset’s latest update in the source data dictionary.

**Missing Records.** Currently, FacDB is the most comprehensive spatial data resource available for facilities run by public and non-public entities in NYC, but it does not claim to capture every facility within the specified domains. Some facilities are deliberately excluded from the data that source agencies provide in order to protect the safety and privacy of their clients. Also, many records could not be geocoded. To learn more about how the data are processed, please review the Data Sources and Compilation Process.

**Duplicates.** Please be aware that this beta version of the database includes cases of duplicate records for the same facility because several source datasets have content that overlaps with other datasets.

**Administrative Addresses.** There are known to be cases when the address provided in the source data is for a headquarters office rather than the facility site location. Unfortunately, these could not be systematically verified. For more detailed information on a specific facility reach out to the respective oversight agency.

**Public Accessibility of Sites.** DCP is unable to verify the public accessibility of all sites. For example, some playgrounds or playing fields may only be accessible to participants in certain programs.

## Data Dictionary

### uid

- **Longform Name**: `ID`
- **Description**: Unique ID of the record

### facname

- **Longform Name**: `Facility name`
- **Description**: Name of the facility in proper case as received from the source data

### factype

- **Longform Name**: `Type`
- **Description**: Value representing the specific type of facility, which the most granular category of facilities.  This value is often taken directly from the source data

### facsubgrp

- **Longform Name**: `Subgroup`
- **Description**: Value identifying the subgroup the facility belongs to based on the facility type.  Subgroup values are assigned by DCP

### facgroup

- **Longform Name**: `Group`
- **Description**: Value identifying the group the facility belongs to based on the subgroup

### facdomain

- **Longform Name**: `Domain`
- **Description**: Value identifying the domain the facility belongs to based on the group.  Domain is the broadest categorical grouping

### servarea

- **Longform Name**: `Service area`
- **Description**: Value identifying whether the extent of the area the facility serves is local or regional

### opname

- **Longform Name**: `Operator name`
- **Description**: Name of the operating entity

### opabbrev

- **Longform Name**: `Operator acronym`
- **Description**: Abbreviation for the operating entity

### optype

- **Longform Name**: `Operator type`
- **Description**: Indicates whether the operating entity is public or non-public

### overagency

- **Longform Name**: `Oversight agency name`
- **Description**: Value identifying the domain the facility belongs to based on the group.  Domain is the broadest categorical grouping

### overabbrev

- **Longform Name**: `Oversight agency acronym`
- **Description**: Abbreviation for the oversight agency

### overlevel

- **Longform Name**: `Oversight level`
- **Description**: The level of government of the oversight agency: City, State, City-State, Federal, or Non-public Oversight

### capacity

- **Longform Name**: `Capacity`
- **Description**: How many of capacity type/unit the facility is intended to hold.

### captype

- **Longform Name**: `Capacity type`
- **Description**: Value representing the unit type of capacity, such as beds, visitors, seats, etc.

### proptype

- **Longform Name**: `Property type`
- **Description**: x

### addressnum

- **Longform Name**: `House number`
- **Description**: Address number of where the facility is located according to GeoSupport

### streetname

- **Longform Name**: `Street name`
- **Description**: Street name where the facility is located, according to GeoSupport

### address

- **Longform Name**: `Address`
- **Description**: Concatenated value of AddressNumber and StreetName of where the facility is located

### city

- **Longform Name**: `City`
- **Description**: City name where the facility is located according to GeoSupport

### zipcode

- **Longform Name**: `Zipcode`
- **Description**: Zip code of address from GeoSupport

### boro

- **Longform Name**: `Borough`
- **Description**: Full name of the borough the facility is within

### bin

- **Longform Name**: `BIN`
- **Description**: BIN value of the building the facility is located in.  If the facility spans multiple buildings only one BIN is reported

### bbl

- **Longform Name**: `BBL`
- **Description**: BBL values for the tax lots the facility is located on.  If the facility spans multiple lots only one BBL is reported

### latitude

- **Longform Name**: `Latitude`
- **Description**: Latitude of the location as returned by Geosupport, or calculated using the coordinates in or geometry from the source data

### longitude

- **Longform Name**: `Longitude`
- **Description**: Longitude of the location as returned by Geosupport, or calculated using the coordinates in or geometry from the source data

### xcoord

- **Longform Name**: `X coord`
- **Description**: X Coordinate of the location as returned by Geosupport, or calculated using the coordinates in or geometry from the source data

### ycoord

- **Longform Name**: `Y coord`
- **Description**: Concatenated value of House Number and Street Name of where the facility is located

### commboard

- **Longform Name**: `Community district`
- **Description**: Community District the facility is within according to Geosupport

### nta

- **Longform Name**: `NTA code`
- **Description**: Code of the NTA the facility is within according to Geosupport

### council

- **Longform Name**: `Council district`
- **Description**: Council district the facility is within according to Geosupport

### censtract

- **Longform Name**: `Census tract`
- **Description**: Census tract of the NTA the facility is within according to Geosupport

### datasource

- **Longform Name**: `Source dataset`
- **Description**: Name of the dataset the record came from

### geom

- **Longform Name**: `Geometry`
- **Description**: Spatial data component
