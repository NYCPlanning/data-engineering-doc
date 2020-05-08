# Developements Database

The goal of the developments database is to provide a detailed view of both residential and non-residential development that has occured since the 2010 census. The core of the developments data base is a compilation of NYC DOB job and permit information. This data captures changes in units resulting from new buildings, major alterations, and demolitions. Rough timelines of development are captured in the [DOB job status dates](https://www1.nyc.gov/assets/buildings/pdf/bisjobstatus.pdf). To more reliably capture development completion, the database also includes dates associated with certificates of occupancy. Where possible, the database also tracks Housing New York affordable units created as part of each development.

We provide context for each development record by geocoding, then merging the data with various political, geographic, and administrative boundaries. Lot-level zoning and land-use information comes from [PLUTO](/products/pluto).

## Source data

The majority of the data contained in the developments database comes from NYC DOB. These include permit issuance data, job application records, and new certificates of occupancy. Housing New York affordable housing unit information comes from HPD. Administrative and geographic boundary information primarily comes from DCP. Other contextual data comes from [PLUTO](/products/pluto)

## Data dictionary

### job_number

- **Longform Name**: `DOB Job Number`
- **Description**: The DOB job application number assigned when the applicant begins the application.This is the unique identifier for the application submitted to the Department of Buildings (DOB). It may contain several work types, and more work types may be added as the application review and the work continues. It is a 9-digit number where the first digit indicates the borough where the building is located.

### job_type

- **Longform Name**: `DOB Job Type`
- **Description**: DOB's type category for the job application. The following types are included in this database:
  + New Building (NB): an application to build a new structure. “NB” cannot be selected if any existing building elements are to remain. For example a part of an old foundation, a portion of a façade that will be incorporated into the construction, etc.
  + Alteration (A1): a major alteration that will change the use, egress, or occupancy of the building.
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

### occ_category

- **Longform Name**: `Occupancy category`
- **Description**: A value of "Residential" indicates that the job affects the number of residential units through new construction, alteration, or demolition. Note that mixed-use buildings containing residential units may have been filed as either residential or another occupancy type. Those filed under another occupancy type are not necessarily captured in this database. Certain records have been reclassified by DCP in extensive manual research and QAQC. Examples of manual adjustments include filtering for hotel permit applications. Non-residential occupancy categories are indicated by "Other"

### completed_year

- **Longform Name**: `Completed Year`
- **Description**: Year the job was completed. For new buildings and alterations, this is defined as the year of the first certificate of occupancy issuance. For demolitions, this is the year that the demolition was permitted (reached status Q).

### permit_year

- **Longform Name**: `Permitted Year`
- **Description**: Year the job was permitted. For all job types, this is defined as year a job has status Q.

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

### bin

- **Longform Name**: `BIN`
- **Description**: Building Identification Number, as assigned by DOB

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
- **Description**: Indicates that the building has been designated as a landmark building by the Landmarks Preservation Commission. 'Y' for landmark, 'N' for not a landmark.

### cityowned

- **Longform Name**: `City Owned`
- **Description**: Indicates whether or not the building is owned by New York City. 'Y' indicates city-owned.

### owner_type

- **Longform Name**: `Owner Type`
- **Description**: The Owner Type selected by the applicant.

### owner_nonprof

- **Longform Name**: `Owner Non-Profit`
- **Description**: The applicant has indicated that the owner is a non-profit organization. 'Y' indicates non-profit, 'N' not a non-profit.

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
- **Description**: The existing number of floors in the building, as reported by the applicant.

### stories_prop

- **Longform Name**: `Stories Proposed`
- **Description**: The number of stories/floors expected in the building after the work is done, as reported by the applicant.

### height_init

- **Longform Name**: `Height Initial`
- **Description**: The height of the existing building in feet, as reported by the applicant.

### height_prop

- **Longform Name**: `Height Proposed`
- **Description**: The proposed height of the building in feet after the proposed work has been completed, as reported by the applicant.

### zoningsf_init

- **Longform Name**: `Zoning SqFt Initial`
- **Description**: The total zoning floor area for the existing building, if any. This is only required for new buildings and alterations.

### zoningsf_prop

- **Longform Name**: `Zoning SqFt Proposed`
- **Description**: The total zoning floor area for the building after the proposed work is completed. This is only required for new buildings and alterations.

### constructnsf

- **Longform Name**: `Total Construction SqFt`
- **Description**: The square footage of the floor area of the construction.

### enlrg_horiz

- **Longform Name**: `Enlargement Horizontal`
- **Description**: This indicates if the work to be done under the application will result in a larger footprint for the building. 'Y' indicates an expected footprint increase.

### enlrg_vert

- **Longform Name**: `Enlargement Vertical`
- **Description**: This indicates if the work to be done under the application will result in a taller building. 'Y' indicates an expected height increase.

### enlargementsf

- **Longform Name**: `Enlargement SqFt`
- **Description**: The additional square footage added by the construction enlargement, if any.

### costestimate

- **Longform Name**: `Cost Estimate`
- **Description**: Dollar amount that indicates the applicant's estimate for how much the job will cost.

### mixedusebldg

- **Longform Name**: `Mixed-use Building`
- **Description**:

### mixedusebldg

- **Longform Name**: `Mixed-use Building`
- **Description**: Job application appears to be for a building that contains both residential and hotel uses. This is inferred from the job description and other DCP research. 'Mixed Use' indicates that this application is likely for a mixed-use building.

### loftboardcert

- **Longform Name**: `Loft Board Certification`
- **Description**: Indicates that the job application involves a interim multiple dwelling (IMD) building. A loft board certificate is required for alteration of a registered IMD building. 'Y' indicates an IMD building, 'N' indicates not an IMD building.

### edesignation

- **Longform Name**: `e-Designation`
- **Description**: 'Y' or 'N' indicates whether or not the lot is designated with an “E” on the Zoning Maps of the City of New York for potential hazardous material contamination, air and/or noise quality impacts.
  + Little “E” or RD Site: Anytime there is an environmental cleanup in the City of New York, the location is identified as “E” on DCP zoning maps. The Department of Environmental Protection must approve proposed work to ensure that the work satisfies environmental requirements.

### curbcut

- **Longform Name**: `Curb Cut`
- **Description**: 'X' Indicates that the job application includes curb cut work. An angled drop cut to the curb in the roadway, street, public right of way, or similar, which provides access to the zoning or tax lot.

### tracthomes

- **Longform Name**: `Tract Homes`
- **Description**: This indicates that a job filing is part of a housing development where all buildings will be built following a single set of paperwork and plans. This was a common practice in historical development booms. Expected values include are D, N, P, Y.

### hny_id

- **Longform Name**: `Housing New York ID`
- **Description**: Hash relating DOB record to Housing New York projects

### hny_jobrelate

- **Longform Name**: `Housing New York to DOB Job Join Relationship`
- **Description**: Indicates how many Housing New York records relate to DOB records. Values are:
  + 1-to-many
  + 1-to-1
  + many-to-1

### job_desc

- **Longform Name**: `DOB Job Description`
- **Description**: The general description of the work being applied for. This field is free-form text, and is filled out by the applicant.

### bctcb2010

- **Longform Name**: `BCTCB 2010`
- **Description**: Borough code, census tract, and census block ID in which the building is located, based on 2010 census geography. First character is the borough code, the second seven digits are the FIPs code for the census tract, and the final four the census block FIPs code.

### bct2010

- **Longform Name**: `BCTCB 2010`
- **Description**: Borough code and census tract in which the building is located, based on 2010 census geography. First character is the borough code, and the second seven digits are the FIPs code for the census tract.

### nta2010

- **Longform Name**: `NTA2010`
- **Description**: ID of the Neighborhood Tabulation Area in which the building is located. The first two characters indicate the Borough.

### communitydist

- **Longform Name**: `Community District`
- **Description**: Three-digit ID of the community district in which the building is located, where the first digit is the borough code.

### councildist

- **Longform Name**: `Council District`
- **Description**: Two digit ID of the council district in which the building is located

### schoolsubdist

- **Longform Name**: `School Subdistrict`
- **Description**: Two digit ID of the school subdistrict in which the building is located

### policeprecnct

- **Longform Name**: `Police Precinct`
- **Description**: Three digit ID of the police precinct in which the building is located

### latitute

- **Longform Name**: `Latitude`
- **Description**: Latitude in WGS84 / SRID:4326

### longitude

- **Longform Name**: `Longitude`
- **Description**: Longitude in WGS84 / SRID:4326

### geomsource

- **Longform Name**: `Geography Source`
- **Description**: Source of the geographic coordinates for the record.
  + Lat/Long geosupport: Center of the lot, identified by geocoding the record's address
  + BBL geosupport MapPLUTO: Center of the lot, identified using MapPLUTO's lot geometry for the BBL found by geocoding the record's address
  + BBL DOB MapPLUTO: Center of the lot, identified using MapPLUTO's lot geometry for the BBL provided by DOB
  + BBL DOB DTM: Center of the lot, identified using DOF's Digital Tax Map

### dcpedited

- **Longform Name**: `DCPEdited`
- **Description**: Flagged as 'Edited' if DCP overwrote value, and blank if application data is unchanged

### version

- **Longform Name**: `Version`
- **Description**: Indicates quarterly update. Of the form 2019Q4

### PLUTO fields

The developments database also contains several fields from [PLUTO](/products/pluto). These include:

+ [`pluto_unitres`: Units Residential](/products/pluto?id=unitsres)
+ [`pluto_bldgsf`: Building Area](/products/pluto?id=bldgarea)
+ [`pluto_comsf`: Commercial Area](/products/pluto?id=comarea)
+ [`pluto_offcsf`: Office Area](/products/pluto?id=officearea)
+ [`pluto_retlsf`: Retail Area](/products/pluto?id=retainarea)
+ [`pluto_ressf`: Residential Area](/products/pluto?id=resarea)
+ [`pluto_yrbuilt`: Year Built](/products/pluto?id=yearbuilt)
+ [`pluto_yralt1`: Most Recent Alteraton Year](/products/pluto?id=yearalter1)
+ [`pluto_yralt2`: Second Most Recent Alteration Year](/products/pluto?id=yearalter2)
+ [`pluto_bldgcls`: Building Class](/products/pluto?id=bldgclass)
+ [`pluto_landuse`: Land Use](/products/pluto?id=landuse)
+ [`pluto_owner`: Owner Name](/products/pluto?id=ownername)
+ [`pluto_owntype`: Ownership Type](/products/pluto?id=ownertype)
+ [`pluto_condo`: Condominium Number](/products/pluto?id=bldgclass)
+ [`pluto_bldgs`: Number of Buildings](/products/pluto?id=numbldgs)
+ [`pluto_floors`: Number of Floors](/products/pluto?id=numfloors)
+ [`pluto_firm07`: FIRM07_FLA](/products/pluto?id=firm07_fla)
+ [`pluto_pfirm15`: PFIRM15_FL](/products/pluto?id=pfirm15_fl)
+ [`pluto_version`: Version](/products/pluto?id=version)

For more thorough descriptions of each field, see the PLUTO documentation.
