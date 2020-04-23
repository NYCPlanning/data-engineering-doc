# Developements Database

The goal of the developments database is to provide a detailed view of both residential and non-residential development that has occured since the 2010 census. The core of the developments data base is a compilation of NYC DOB job and permit information. This data captures changes in units resulting from new buildings, major alterations, and demolitions. Rough timelines of development are captured in the [DOB job status dates](https://www1.nyc.gov/assets/buildings/pdf/bisjobstatus.pdf). To more reliably capture development completion, the database also includes dates associated with certificates of occupancy. Where possible, the database also tracks Housing New York affordable units created as part of each development. 

We provide context for each development record by geocoding, then merging the data with various political, geographic, and administrative boundaries. Lot-level zoning and land-use information comes from [PLUTO](/_content/pluto).

## Source data

The majority of the data contained in the developments database comes from NYC DOB. These include permit issuance data, job application records, and new certificates of occupancy. Housing New York affordable housing unit information comes from HPD. Administrative and geographic boundary information primarily comes from DCP. Other contextual data comes from [PLUTO](/_content/pluto).


## Data dictionary -- DOB and Housing New York fields

### job_number
- **Longform Name**: `DOB Job Number`
- **Description**: The DOB job application number assigned when the applicant begins the application.This is the unique identifier for the application submitted to the Department of Buildings (DOB). It may contain several work types, and more work types may be added as the application review and the work continues. It is a 9-digit number where the first digit indicates the borough where the building is located.

### job_type
- **Longform Name**: `DOB Job Type`
- **Description**: DOB's type category for the job application. The following types are included in this database:
    + New Building (NB): an application to build a new structure. “NB” cannot be selected if any existing building elements are to remain. For example a part of an old foundation, a portion of a façade that will be incorporated into the construction, etc.
    + Alteration Type I (A1): a major alteration that will change the use, egress, or occupancy of the building.
    + Demolition (DM): an application to fully or partially demolish an existing building. Note that many demolition permits are only for partial demolitions and for garages (these are also captured).
    For more information see [NYC DOB Permits Documentation](https://www1.nyc.gov/site/buildings/homeowner/permits.page).

### job_status
- **Longform Name**: `DOB Job Status`
- **Description**: DCP recode of the DOB status label.  Jobs typically move through status A through X over time as they reach certain approval milestones. 
    + Filed: A job application has status A - G at the time of publication. In these cases, an application submitted by review is not yet in progress. 
    + In Progress: An application has status H - P, excluding J. Plan examination is in progress, but is not yet approved. 
    + In Progress (last plan disapproved): An application has status J
    + Permit Issued: An application has status Q or R
    + Complete: An application has status U or X, or a certificate of occupancy (CO) has been issued for a new building or major alteration
    + Complete (demolition): An application has status Q and is a demolition. Note that we mark demolitions as complete when they receive a permit (status Q). This date is likely when the building must be vacated, and it appears that many buildings are physically demolished some time before receiving sign off (status X).
    + Withdrawn: An application has status 3

    More details on each DOB status (letter codes) are available in the [DOB Job Status Documentation](https://www1.nyc.gov/assets/buildings/pdf/bisjobstatus.pdf).

### job_inactive
- **Longform Name**: `Job Inactive`
- **Description**: Flag for job applications that are likely inactive.  This definition is probability-base, and therefore can not capture all permits that may eventually become inactive. 

Jobs are flagged "inactive" by DCP in the following cases:
    1. If status is "filed" or "in progress" and the application's status hasn’t changed in 3 years
    2. If status is "In progress (last plan disapproved)" and the application's status hasn’t changed in 2 years

### residential_flag
- **Longform Name**: `Residential Flag`
- **Description**: A value of "residential" indicates that the job affects the number of residential units through new construction, alteration, or demolition. Note that mixed-use buildings containing residential units may have been filed as either residential or another occupancy type. Those filed under another occupancy type are not necessarily captured in this database. Certain records have been reclassified by DCP in extensive manual research and QAQC. Examples of manual adjustments include filtering for hotel permit applications.

### completed_year
- **Longform Name**: `Completed Year`
- **Description**: Year the job was completed. For new buildings and alterations, this is defined as the year of the first certificate of occupancy issuance. For demolitions, this is the year that the demolition was permitted (reached status Q).

### completed_qtr
- **Longform Name**: `Completed Quarter`
- **Description**: The quarter of job completion, following the same criteria for completion as in `completed_year`

### permit_year
- **Longform Name**: `Permitted Year`
- **Description**: Year the job was permitted. For all job types, this is defined as year a job has status Q.

### permit_quarter
- **Longform Name**: `Permitted Quarter`
- **Description**: Year and quarter the job was permitted. For all job types, this is defined as year a job has status Q.

### units_initial
- **Longform Name**: `Units Initial`
- **Description**: Number of units that initially existed in building at time of job application, as reported by the applicant.

### units_prop
- **Longform Name**: `Units Proposed`
- **Description**: Number of final units proposed in job application, as reported by the applicant.

### units_net
- **Longform Name**: `Units Net Change`
- **Description**: "Net change in unit count between the number of units existing at the time of application and the number of units proposed.

### units_complet
- **Longform Name**: `Units Completed`
- **Description**: Cumulative number of proposed units that have been completed at the time of publication, based on number of units having received temporary or final certificates of occupancy.

### units_incompl
- **Longform Name**: `Units Incomplete`
- **Description**: Number of proposed units that have not yet been completed at the time of publication.

### units_hnyaff
- **Longform Name**: `Units Affordable in Housing NY`
- **Description**: The total number of affordable units, counted towards the Housing New York plan, that are in the building.

### boro
- **Longform Name**: `Borough`
- **Description**: The full name of the NYC borough where the proposed work will take place.

### bbl
- **Longform Name**: `BBL`
- **Description**: Borough-Block-Lot tax ID number. This field consists of the borough code followed by the tax block followed by the tax lot. The borough code is one numeric digit. The tax block is one to five numeric digits, preceded with leading zeros when the block is less than five digits. The tax lot is one to four digits and is preceded with leading zeros when the lot is less than four digits. Each unit in a building that is a condominium is defined by the Department of Finance as a separate tax lot. To make condominium information more compatible with parcel information, the Department of City Planning aggregated condominium unit tax lot information so that each condominium complex within a tax block is represented by only one tax lot record. A condominium complex is defined as one or more structures or properties under the auspices of the same condominium association. The Department of City Planning then assigned the condominium billing tax lot number to the condominium complex tax lot record. If the Department of Finance had not yet assigned a billing tax lot number to the condominium complex then the lowest tax lot number within the condominium complex was used.

### address_numbr
- **Longform Name**: `Street Number`
- **Description**: The house number for the building where the proposed work will take place.

### address_st
- **Longform Name**: `Street Name`
- **Description**: The street name for the building where the proposed work will take place.

### address
- **Longform Name**: `Address`
- **Description**: Concatenated street number and street name for the building where the proposed work will take place.

### date_filed
- **Longform Name**: `Date Filed (Status A)`
- **Description**: Date of job status A (pre-filing application). This is the first step in the process for all job applications. The job application ID is assigned at this status. This occurs when the applicant submits any part of the application (even a single form), either in person or electronically.

### date_statusd
- **Longform Name**: `Status D`
- **Description**: Date of job status D (completed application on file). This is when all data entry is complete and payments have been made.

### date_statusp
- **Longform Name**: `Status P`
- **Description**: Date of job status P (plan examination approval). This is when the entire job has been approved by the plan examiner. The applicant can now apply for a permit.

### date_permittd
- **Longform Name**: `Date Permitted (Status Q)`
- **Description**: Date of job status Q (first partial permit issuance). This is when construction work may begin. This field should be used for identifying the number of permits approved in a given year.

### date_statusr
- **Longform Name**: `Status R`
- **Description**: Date of job status R (full permit issuance). This is when all necessary permits have been approved for a job.

### date_statusx
- **Longform Name**: `Status X`
- **Description**: Date of job status X (job completion). For new buildings and alterations, the date associated with the earliest certificate of occupancy issuance (date_complete) is a more reliable job completion date.

### date_lastupdt
- **Longform Name**: `Date Last Status`
- **Description**: The date of the last update to the DOB record for the job filing.

### date_complete
- **Longform Name**: `Date Completed (First CO)`
- **Description**: DCP's best estimate of completion date for all jobs. For new buildings and alterations, date complete is equal to the date of the earliest certificate of occupancy. For demolitions, `date complete` is equal to status Q (permit issued), since demolitions do not receive certificates of occupancy. Blank indicates no certificate of occupancy has been issued. Typically, a building can be considered complete at this stage. Large buildings with many units may have units receiving certificates of occupancy over a longer period of time. 

### occ_initial
- **Longform Name**: `Occupancy Initial`
- **Description**: DCP categorization of existing occupancy type at time of job application. This indicates a site's use, prior to the proposed job. It is a simplified recode of [DOB's initial occupancy type](http://www1.nyc.gov/assets/buildings/pdf/pw1_userguide.pdf) of the building. 
 
### occ_proposed
- **Longform Name**: `Occupancy Proposed`
- **Description**: DCP categorization of proposed occupancy type. This indicates what the site will be used for after the proposed job is complete. 

### zoningdist1
- **Longform Name**: `Zoning District 1`
- **Description**: The primary [zoning district](http://www1.nyc.gov/site/planning/zoning/about-zoning.page) of the tax lot per the applicant at time of application.

### zoningdist2
- **Longform Name**: `Zoning District 2`
- **Description**: The secondary [zoning district](http://www1.nyc.gov/site/planning/zoning/about-zoning.page) of the tax lot per the applicant at time of application.

### zoningdist3
- **Longform Name**: `Zoning District 3`
- **Description**: The tertiary [zoning district](http://www1.nyc.gov/site/planning/zoning/about-zoning.page) of the tax lot per the applicant at time of application.

### specialdist1
- **Longform Name**: `Special District 1`
- **Description**: The primary [special zoning district](http://www1.nyc.gov/site/planning/zoning/districts-tools/special-purpose-districts.page) of the tax lot per the applicant at time of application. Other zoning designations may appear in this field, such as industrial buziness zones (IBZ), mandatory inclusionary housing (MIH) areas, or other zoning designations. This is field is provided by the applicant, and so is likely inconsistent.  

The City Planning Commission designates special zoning districts to achieve specific planning and urban design objectives in defined areas with unique characteristics. Special districts respond to specific conditions; each special district designated by the Commission stipulates zoning requirements and/or zoning incentives tailored to distinctive qualities that may not lend themselves to generalized zoning and standard development. 

### specialdist2
- **Longform Name**: `Special District 2`
- **Description**: The secondary [special zoning district](http://www1.nyc.gov/site/planning/zoning/districts-tools/special-purpose-districts.page) of the tax lot per the applicant at time of application.

### landmark
- **Longform Name**: `Landmark`
- **Description**: Indicates that the building has been designated as a landmark building by the Landmarks Preservation Commission. 'Y'  indicates a landmark building.

### cityowned
- **Longform Name**: `City Owned`
- **Description**: Indicates whether or not the building is owned by New York City. 'Y' indicates city-owned.

### owner_type
- **Longform Name**: `Owner Type`
- **Description**: The Owner Type selected by the applicant.

### owner_nonprof
- **Longform Name**: `Owner Non-Profit`
- **Description**: The applicant has indicated that the owner is a non-profit organization. 'Y' indicates non-profit.

### owner_firstnm
- **Longform Name**: `Owner First Name`
- **Description**: First name of building owner

### owner_lastnm
- **Longform Name**: `Owner Last Name`
- **Description**: Last name of building owner

### owner_biznm
- **Longform Name**: `Owner Business Name`
- **Description**: Business name of building owner

### owner_address
- **Longform Name**: `Owner Address`
- **Description**: The house number and street for the building owner's address

### owner_zipcode
- **Longform Name**: `Owner Zip Code`
- **Description**: The zip code for the building owner's address

### owner_phone
- **Longform Name**: `Owner Phone`
- **Description**: The building owner's phone number

### stories_init
- **Longform Name**: `Stories Initial`
- **Description**: 

### stories_prop
- **Longform Name**: `Stories Proposed`
- **Description**: 

### height_init
- **Longform Name**: `Height Initial`
- **Description**: 

### height_prop
- **Longform Name**: `Height Proposed`
- **Description**: 

### zoningsf_init
- **Longform Name**: `Zoning SqFt Initial`
- **Description**: 

### zoningsf_prop
- **Longform Name**: `Zoning SqFt Proposed`
- **Description**: 

### constructnsf
- **Longform Name**: `Total Construction SqFt`
- **Description**: 

### enlrg_horiz
- **Longform Name**: `Enlargement Horizontal`
- **Description**: 

### enlrg_vert
- **Longform Name**: `Enlargement Vertical`
- **Description**: 

### enlargementsf
- **Longform Name**: `Enlargement SqFt`
- **Description**: 

### costestimate
- **Longform Name**: `Cost Estimate`
- **Description**: 

### mixedusebldg
- **Longform Name**: `Mixed-use Building`
- **Description**: 

### mixedusebldg
- **Longform Name**: `Mixed-use Building`
- **Description**: 

### loftboardcert
- **Longform Name**: `Loft Board Certification`
- **Description**: 

### edesignation
- **Longform Name**: `e-Designation`
- **Description**: 

### curbcut
- **Longform Name**: `Curb Cut`
- **Description**: 

### tracthomes
- **Longform Name**: `Tract Homes`
- **Description**: 

### hny_id
- **Longform Name**: `Housing New York ID`
- **Description**: 

### hny_jobrelate
- **Longform Name**: `Housing New York to DOB Job Join Relationship`
- **Description**: 

### job_desc
- **Longform Name**: `DOB Job Description`
- **Description**: 

### cenblock2010
- **Longform Name**: `FIPS Census Block 2010`
- **Description**: 

### nta2010
- **Longform Name**: `NTA2010`
- **Description**: 

### ntaname2010
- **Longform Name**: `NTA Name 2010`
- **Description**: 

### puma2010
- **Longform Name**: `PUMA 2010`
- **Description**:

### communitydist
- **Longform Name**: `Community District`
- **Description**:

### councildist
- **Longform Name**: `Council District`
- **Description**:

### schoolsubdist
- **Longform Name**: `School Subdistrict`
- **Description**:

### schoolcommnty
- **Longform Name**: `Community School District`
- **Description**:

### schoolelmntry
- **Longform Name**: `Elementary School Zone`
- **Description**:

### schoolmiddle
- **Longform Name**: `Middle School Zone`
- **Description**:

### firecompany
- **Longform Name**: `Fire Company`
- **Description**:

### firebattalion
- **Longform Name**: `Fire Battalion`
- **Description**:

### firedivision
- **Longform Name**: `Fire Division`
- **Description**:

### policeprecnct
- **Longform Name**: `Police Precinct`
- **Description**:

### depdrainarea
- **Longform Name**: `DEP Drainage Planning Area`
- **Description**:

### deppumpstatn
- **Longform Name**: `DEP Pump Station`
- **Description**:

### nymtc_taz2012
- **Longform Name**: `Traffic Analysis Zone 2012`
- **Description**:

### latitute
- **Longform Name**: `Latitude`
- **Description**:

### longitude
- **Longform Name**: `Longitude`
- **Description**:

### geomsource
- **Longform Name**: `Geography Source`
- **Description**: Source of the geographic coordinates for the record.
    + GBAT A: x/y coordinates relate to centroid of BBL
    + GEOCLIENT: x/y coordinates relate to the segment of the street center line associated with the Block and Lot
    + GEOCLIENT - BBL CENTROID: x/y coordinates relate to centroid of BBL
    + GEOCLIENT - BIN CENTROID: x/y coordinates relate to centroid of building
    + PLUTO:  x/y coordinates relate to centroid of BBL
    + PLUTO-APP:  x/y coordinates relate to centroid of BBL
    + MANUAL [name of DCP staffer]: x/y coordinates relate to BBL

### dcpedited
- **Longform Name**: `DCPEdited`
- **Description**: Flagged as TRUE if DCP overwrote value (see x_reason for why), and blank if application data is unchanged

### dcpeditfields
- **Longform Name**: `DCPEdited`
- **Description**: List of fields that were edited by DCP. This only lists fields where original DOB source data was overwritten by DCP, and doesn't include fields where DCP recodes data as part of the standard methodology. 

### version
- **Longform Name**: `Version`
- **Description**: 


### Data Dictionary -- PLUTO fields

The developments database also contains several fields from [PLUTO](/_content/pluto). These include:
+ Units Residential
+ Building SqFt
+ Commercial SqFt
+ Office SqFt
+ Retail SqFt
+ Residential SqFt
+ Year Built
+ Most Recent Alteraton Year
+ Second Most Recent Alteration Year
+ Building Class
+ Land Use
+ Owner Name
+ Ownership Type
+ Condominium Number
+ Number of Buildings
+ Number of Floors
 For more thorough descriptions of each field, see the PLUTO documentation.
