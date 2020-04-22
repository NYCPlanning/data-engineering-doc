# PLUTO and MapPLUTO
![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/NYCPlanning/db-pluto?label=version) ![CI](https://github.com/NYCPlanning/db-pluto/workflows/CI/badge.svg)

## About

The Primary Land Use Tax Lot Output (PLUTO™) data file contains extensive land use and
geographic data at the tax lot level in a comma-delimited file.
The PLUTO tax lot data files contain over seventy data fields derived from data files maintained
by the Department of City Planning (DCP), Department of Fice (DOF), Department of
Citywide Administrative Services (DCAS), and Landmarks Preservation Commission (LPC).
DCP has created additional fields based on data obtained from one or more of the major data
sources. PLUTO data files contain three basic types of data:
* Tax Lot Characteristics;
* Building Characteristics; and
* Geographic/Political/Administrative Districts.

There are two idiosyncrasies regarding the tax lot data. The PLUTO data contain one record
per tax lot except for condominiums. PLUTO data contain one record per condominium
complex instead of records for each condominium unit tax lot. A tax lot is usually a parcel of
real property. The parcel can be under water, vacant, or contain one or more buildings or
structures. The Department of Fice assigns a tax lot number to each condominium unit and
a billing tax lot number to the Condominium Complex. A Condominium Complex is defined as
one or more structures or properties under the auspices of the same condominium association.
DCP summarizes DOF's condominium unit tax lot data so that each Condominium Complex
within a tax block is represented by only one record. The Condominium Complex record is
assigned the billing tax lot number when one exists. When the billing tax lot number has not
yet been assigned by DOF, the lowest tax lot number within the tax block of the Condominium
Complex is assigned.
The second idiosyncrasy is related to borough and community district geography. Two portions
of the City, Marble Hill and Rikers Island, are legally located in one borough but are serviced by
another borough. Specifically, Marble Hill is legally located in Manhattan but is serviced by The
Bronx, while Rikers Island is legally part of The Bronx but is serviced by Queens. Therefore,
Marble Hill tax lots are located in the Manhattan borough file and Rikers Island tax lots are in
The Bronx borough file.

## Sources

|**SOURCE**|**DATE OF DATA**|
|---|---|
|Department of City Planning - Political and Administrative Districts|January 15, 2018|
|Department of Fice - Digital Tax Map|April 5, 2018|
|Department of City Planning - NYC GIS Zoning Features|Oct 26, 2018|
|Department of City Planning - E Designations|May 15, 2018|
|Department of Citywide Administrative Services - City Ownership Code|April 20, 2018|
|Department of Fice - RAPD Master File|May 18, 2018|
|Department of Fice - Mass Appraisal System|May 4, 2018|
|Landmarks Preservation Commission - Historic Districts|April 12, 2018|
|Landmarks Preservation Commission - Landmarks|April 12, 2018|

City Planning also merges the PLUTO data with the DCP modified version of the DOF’s Digital
tax map to create MapPLUTO for use with various geographic information systems. For more
information on MapPLUTO see the DCP web site www.nyc.gov/planning.

**PLUTO is being provided by the Department of City Planning (DCP) on DCP’s website for
informational purposes only. DCP does not warranty the completeness, accuracy,
content, or fitness for any particular purpose or use of PLUTO, nor are any such
warranties to be implied or inferred with respect to PLUTO as furnished on the website.
DCP and the City are not liable for any deficiencies in the completeness, accuracy,
content, or fitness for any particular purpose or use of PLUTO, or applications utilizing
PLUTO, provided by any third party.**

If you have any questions concerning the data, please click on http://www.nyc.gov/open-data-feedback
to submit your questions.

## Data Dictionary
### Borough
- **Longform Name** : `Borough`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: BX, BK, MN, QN, SI
- **Description**: The borough in which the tax lot is located

Two portions of the city, Marble Hill and Rikers Island, are each legally located in one borough but are serviced by different boroughs. The BOROUGH abbreviations associated with these areas are the boroughs in which they are legally located. Specifically, Marble Hill is serviced by the Bronx but is legally located in Manhattan and has a Manhattan BOROUGH code. Rikers Island has a Bronx BOROUGH code because it is legally located in the Bronx although it is serviced by Queens.
    

### Block
- **Longform Name** : `Block`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The tax block in which the tax lot is located. Each tax block is unique within a borough (see BOROUGH).


    

### Lot
- **Longform Name** : `Lot`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The number of the tax lot. Each tax lot is unique within a tax block (see BLOCK).

Each unit in a building that is a condominium is defined by the Department of Fice as a separate tax lot. To make condominium information more compatible with parcel information, the Department of City Planning aggregated condominium unit tax lot information so that each condominium complex within a tax block is represented by only one tax lot record. A condominium complex is defined as one or more structures or properties under the auspicies of the same condominium association. The Department of City Planning then assigned the condominium billing tax lot number to the condominium complex tax lot record. If the Department of Fice has not yet assigned a billing tax lot number to the condominium complex then the lowest tax lot number within the condominium complex was used. The Department of Fice DTM uses the formerly known as (FKA) Tax Lot number for Condominiums. The Department of City Planning has modified the Tax Lot number of DOF DTM by replacing the FKA with the condominiums billing tax lot number. Often the tax lot number can tell you the type of tax lot. Of course there are exceptions to each convention. Usually tax lot number '1-999' correspond with traditional tax lots; '1001-6999' correspond with condominium unit lots; '7501-7599' correspond with condominium billing lots; '8000-8899' correspond with subterranean tax lots; '8900-8999' correspond with DTM dummy tax lots; '9000-9899' correspond with air right tax lots. The Air Rights Tax Lot goes with the base Tax Lot or Donating Tax Lot. For example: If Tax Lot 32 has Air Rights, those Air Rights would be identified as 9032. When the structure is built the Air Rights Tax Lot is retired. Property owners do not have to create an Air Rights Tax Lot to transfer development rights.
    

### CD
- **Longform Name** : `Community District`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
    - `101-112`: Manhattan Community Districts 
    - `164`: Central Park (JIA)
    - `201-212`: Bronx Community District 
    - `226`: Van Cortlandt Park (JIA)
    - `227`: Bronx Park (JIA)
    - `228`: Pelham Bay Park (JIA)
    - `301-318`: Brooklyn Community Districts
    - `355`: Prospect Park (JIA)
    - `356`: Brooklyn Gateway National Recreation Area (JIA)
    - `401-414`: Queens Community Districts
    - `480`: LaGuardia Airport (JIA)
    - `481`: Flushing Meadow / Corona Park (JIA)
    - `482`: Forest Park (JIA) 
    - `483`: JFK International Airport (JIA)
    - `484`: Queens Gateway National Recreation Area (JIA)
    - `501-503`: Staten Island Community Districts
    - `595`: Staten Island Gateway National Recreation Area (JIA)
- **Description**: The community district (CD) or joint interest area (JIA) the tax lot is located in, or partially located.

The Department of City Planning - CD Layer for the DTM is used as the source when it identifies a community district for a tax lot. If a tax lot is split among more than one community district then PLUTO uses one of the community district numbers. If the Department of City Planning - CD Layer for the DTM does not identify a community district, the district is obtained from the Department of City Planning Geosupport System. If the community district is not available from the Geosupport System the DOF-RPAD Master file is used. If a tax lot is split by a community district boundary, only one community district is retained. Two portions of the city, Marble Hill and Rikers Island, are legally located in one borough and are each serviced by different boroughs. The COMMUNITY DISTRICT codes associated with these areas are the community districts they are serviced by. Specifically, Marble Hill is legally located in Manhattan but is serviced by the Bronx and has Bronx COMMUNITY DISTRICT codes of 207 or 208. Rikers Island has a Queens COMMUNITY DISTRICT code of 401 since it is serviced by Queens even though it is legally located in the Bronx.
    

### CT2010
- **Longform Name** : `Census Tract 2010`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The 2010 US Census Tract in which the tax lot is located. Each census tract is unique within a borough.

2010 census tracts a geographic areas defined by the US Census Bureau for the 2010 Census. If a tax lot is split by a census tract boundary, only one census tract is retained.
    

### CB2010
- **Longform Name** : `Census Block 2010`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The 2010 US Census Block in which the tax lot is located. Each census block is unique within a census tract (see CT2010).

2010 census blocks are the smallest geographic areas reported on by the U.S. Census Bureau for the 2010 census. If a tax lot is split by a census block boundary, only one census block is retained.
    

### SchoolDist
- **Longform Name** : `School District`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - 1-6, 10: Manhattan School District 
    - 7-12: Bronx School District 
    - 13-23, 32: Brooklyn School District 
    - 24-30: Queens School District 
    - 31: Staten Island School District
- **Description**: The community school district in which the tax lot is located.

If a tax lot is split by a school district boundary, only one school district is retained.
    

### Council
- **Longform Name** : `Council`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
    - 1-10: Manhattan City Council Districts 
    - 8, 11-18, 22: Bronx City Council Districts 
    - 33-48, 50: Brooklyn City Council Districts 
    - 19-32, 34: Queens City Council Districts 
    - 49-51: Staten Island City Council Districts
- **Description**: The city council district in which the tax lot is located.

There are currently 51 city council districts in the City, which serve as administrative districts for the legislative branch of city government. If a tax lot is split by a city council district boundary, only one city council district is retained.
    

### ZipCode
- **Longform Name** : `ZipCode`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The zip code that the tax lot is located in.

The zip code is obtained from the Department of City Planning- Geosupport System. If the zip code is not available from Geosupport, the DOF-RPAD Master File is used. If a tax lot is split by a zip code boundary, only one zip code is retained.
    

### FireComp
- **Longform Name** : `Fire Company`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - 001, 003-010, 014-016, 021-024, 026, 028, 033-035, 037, 039, 040, 044, 047,053-055, 058, 059, 065, 067, 069, 074, 076, 080, 084, 091, 093, 095: Manhattan Fire Company District - Engine 
    - 001-016, 018, 020-026, 028, 030, 034-036, 040, 043, 045: Manhattan Fire Company Districts - Ladder 
    - 038, 042, 043, 045, 046, 048, 050, 052, 060, 062-064, 066, 068, 070-073, 075, 079,081-083, 088, 089, 090, 092, 094, 096, 097: Bronx Fire Company Districts  - Engine 
    - 017, 019, 027, 029, 031-033, 037-039, 041, 042, 044, 046-056, 058, 059, 061: Bronx Fire Company Districts - Ladder 
    - 201, 202, 205-207, 210, 211, 214, 216-222, 224-231, 233-243, 245-250, 253-255, 257, 271, 276, 277, 279-284, 290, 309, 310, 318, 321, 323, 330, 332: Brooklyn Fire Company Districts - Engine 
    - 101-114, 118-120, 122-124, 131, 132, 146-149, 153, 156, 157, 159, 161, 166, 168-170, 172, 174-176: Brooklyn Fire Company District - Ladder 
    - 251, 258-260, 262-266, 268, 273-275, 285-287, 289, 291-295, 297-299, 301-308,311-317, 319, 320, 324-326, 328, 329, 331: Queens Fire Company Districts - Engine 
    - 115-117, 121, 125-130, 133-138, 140, 142-144, 150-152, 154, 155, 158, 160, 162-165, 167, 173: Queens Fire Company Districts - Ladder 
    - 151-168: Staten Island Fire Company Districts - Engine 
    - 077-087: Staten Island Fire Company Districts - Ladder
- **Description**: The fire company that services the tax lot. This field consists of four characters, the first of which is an alphabetic code identifying the type of Fire Company, where E stands for Engine and L stands for Ladder. The type code is followed by a one to three digit fire company number which is preceded with leading zeros if the company number is less than three digits.

N\A
    

### PolicePrct
- **Longform Name** : `Police Precinct`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
    - 001, 005-007, 009, 010, 013, 014, 017, 018: Manhattan - South Police Precincts 
    - 019, 020, 023-026, 028, 030, 032-034: Manhattan - North Police Precincts 
    - 040-049, 052: Bronx - Police Precincts 
    - 050: Bronx - Marble Hill Police Precincts 
    - 060-063, 066-072, 078: Brooklyn - South Police Precincts 
    - 076: Brooklyn - South Police Precincts 
    -  073, 075, 077, 079, 081, 083, 088, 090, 094: Brooklyn - North Police Precincts 
    - 084: Brooklyn - North Piers Police Precincts 
    - 100-113, 115: Queens - Police Precincts 
    - 1114: Queens - Roosevelt Island Police Precincts 
    - 120, 122, 123: Staten Island - Police Precincts
- **Description**: The police precinct in which the tax lot is located.

If a tax lot is split by a police precinct boundary, only one police precinct is retained.
    

### HealthCent
- **Longform Name** : `Health Center District`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
    - 11-17: Manhattan 
    - 21-26: Bronx 
    - 41-46: Queens 
    - 30-39: Brooklyn 
    - 51: Staten Island
- **Description**: The health center district that the tax lot is located in.


    

### HealthArea
- **Longform Name** : `Health Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
    - 0110-2100, 2310-2600, 2810, 2820, 3110-5000, 5200,5300, 5500-6800, 7400,7600-7800, 8000-9100: Manhattan 
    - 0100-4500, 4700-4800: Bronx 
    - 0110-3900: Queens 
    - 0100-5020, 5200-9120, 9300: Brooklyn 
    - 0100-0800, 0910, 0920: Staten Island
- **Description**: The health area that the tax lot is located in.

This field contains a four digit health area number, which is preceded with leading zeros when the health area is less than four digits. There is an implied decimal point after the first two digits. If a tax lot is split by a health area boundary, only one health area is retained.
    

### SanitBoro
- **Longform Name** : `Sanitation Borough District`
- **DataType**: `Number`
- **Expected/Allowed Values**: 1: Manhattan - 2: Bronx - 3: Brooklyn - 4: Queens - 5: Staten Island
- **Description**: The Boro of the Sanitation District that services the tax lot.


    

### SanitDist
- **Longform Name** : `Sanitation District`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Sanitation District that services the tax lot.


    

### SanitSub
- **Longform Name** : `Sanitation Subsection`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Subsection of the Sanitation District that services the tax lot.


    

### Address
- **Longform Name** : `Address`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: An address for the tax lot.

The general format is house number or low house number, if there is a house number range, and a space followed by a street name. Queens house numbers contain a hyphen. Some tax lots, such as vacant lots or parks, have a street name and no house number.
    

### ZoneDist1
- **Longform Name** : `Zoning District 1`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - R1-1 - R10H: Residential Districts 
    - C1-6 - C8-4: Commercial Districts 
    - M1-1 - M3-2: Manufacturing Districts 
    - NZS & Blank: Zoning Unknown (DOF Zoning File) 
    - BPC: Battery Park City 
    - PARK: New York City Parks 
    - PARKNYS: New York State Parks 
    - M1-1/R5 - M1-6/R10: Mixed Manufacturing & Residential Districts 
    - DROP LOT: DOF RPAD Tax Lot Only 
    - ZR11-151: See Section 11-151 of the Zoning Resolution for special requirements for selected properties in Queens 
    - PARKUS: United States Parks - ZNA: Zoning Not Applicable
- **Description**: The zoning district classification of the tax lot. If the tax lot is divided by a zoning boundary line, ZoneDist1 represents the primary zoning district classification occupying the greatest percentage of the tax lot's area. Properties under the jurisdiction of NYC Department of Parks and Recreation are coded PARK. Properties under the jurisdiction of NYS Office of Parks, Recreation, and Historic Preservation are coded PARKNY. DROPLOT is a designation that City Planning devised to identify tax lots that no longer exist in the DCP version of the Digital Tax Map but have not yet been removed from the Department of Fice RPAD File. RPAD retains tax lots that have been dropped, due to merger, reapportionment or conversion to condominium, until the end of the City's Fiscal Year. To avoid confusion DROP LOT was created to identify these lots.

See SplitZone to determine if the tax lot is divided.
    

### ZoneDist2
- **Longform Name** : `Zoning District 2`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: Same as ZoneDist1
- **Description**: If the tax lot is divided by zoning boundary lines, ZoneDist2 represents the primary zoning classification occupying the second greatest percentage of the tax lot's area. If the tax lot is not divided by a zoning boundary line, the field is blank.

See SplitZone to determine if the tax lot is divided
    

### ZoneDist3
- **Longform Name** : `Zoning District 3`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: Same as ZoneDist1
- **Description**: If the tax lot is divided by zoning boundary lines, ZoneDist3 represents the primary zoning classification occupying the third greatest percentage of the tax lot's area. If the tax lot is not divided by a zoning boundary line, the field is blank.

See SplitZone to determine if the tax lot is divided.
    

### ZoneDist4
- **Longform Name** : `Zoning District 4`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: Same as ZoneDist1
- **Description**: If the tax lot is divided by zoning boundary lines, ZoneDist4 represents the primary zoning classification occupying the fourth greatest percentage of the tax lot's area. If the tax lot is not divided by a zoning boundary line, the field is blank.

See SplitZone to determine if the tax lot is divided.
    

### Overlay1
- **Longform Name** : `Overlay1`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The commercial overlay assigned to the tax lot.

See split zone to determine if the tax lot is divided.
    

### Overlay2
- **Longform Name** : `Overlay2`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The commercial overlay associated with the with the tax lot.

See split zone to determine if the tax lot is divided.
    

### SPDist1
- **Longform Name** : `Special District 1`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - `125`: 125th Street District 
    - `BPC`: Battery Park City District 
    - `BR`: Bay Ridge District  
    - `CD`: City Island District  
    - `CI`: Coney Island District
    - `CL`: Clinton District  
    - `CP`: College Point  
    - `CR-1`: Special Coastal Risk District 1 Broad Channel at Queens  
    - `CR-2`: Special Coastal Risk District 2 Hamilton Beach at Queens  
    - `CR-3`: Special Coastal Risk District 3 Buyout Areas at Staten Island  
    - `CO`: Coney Island Mixed Use Disitrct  
    - `DB`: Downtown Brooklyn District  
    - `DFR`: Downtown Far Rockaway District  
    - `DJ`: Downtown Jamaica 
    - `EC-1`: Enhanced Commercial District 1 (Fourth Avenue, BK) 
    - `EC-2`: Enhanced Commercial District 2 (Columbus and Amsterdam Avenue) 
    - `EC-3`: Enhanced Commercial District 3 (Broadway, MN) 
    - `EC-4`: Enhanced Commercial District 4 (Bedford Stuyvesant) 
    - `EC-5`: Enhanced Commercial District 5 (BK) 
    - `EC-6`: Enhanced Commercial District 6 (BK) 
    - `FH`: Forest Hills District 
    - `GC`: Garment Center District 
    - `C`: Grand Concourse Preservation District 
    - `HS`: Hillsides Preservation District 
    - `HSQ`: Hudson Square District 
    - `HRP`: Hudson River Park 
    - `HY`: Hudson Yards District 
    - `HP`: Hunts Point Special District 
    - `J`: Jerome Corridor District 
    - `HRW`: Harlem River Waterfront District 
    - `LC`: Limited Commercial District 
    - `L`: Lincoln Square District 
    - `LI`: Little Italy District 
    - `LIC`: Long Island City Mixed Use District 
    - `LM`: Lower Manhattan District 
    - `MP`: Madison Avenue Preservation District 
    - `MID`: Midtown District 
    - `MMU`: Manhattanville Mixed Use District 
    - `MX-1`: Mixed Use District-1 Port Morris (BX) 
    - `MX-2`: Mixed Use District-2 Dubmo (BK) 
    - `MX-4`: Mixed Use District-4 Flushing/Bedford (BK) 
    - `MX-5`: Mixed Use District-5 Red Hook (BK) 
    - `MX-6`: Mixed Use District-6 Hudson Square (MN) 
    - `MX-7`: Mixed Use District-7 Morrisania (BX) 
    - `MX-8`: Mixed Use District-8 Greenpoint Williamsburg (BK) 
    - `MX-9`: Mixed Use District-9 Northern Hunters Point Waterfront (BK) 
    - `MX-10`: Mixed Use District-10 Atlantic and Howard Avenues (BK) 
    - `MX-11`: Mixed Use District-11 Gowanus (BK) 
    - `MX-12`: Mixed Use District-12 Borough Park (BK) 
    - `MX-13`: Mixed Use District-13 Lower Concourse (BX) 
    - `MX-14`: Mixed Use District-14 Third Avenue/Tremont Avenue (BX) 
    - `MX-15`: Mixed Use District-15 West Harlem (MN) 
    - `MX-16`: Mixed Use District-16 Ocean Hill/East New York (BK) 
    - `NA-1`: Natural Area District-1 
    - `NA-2`: Natural Area District-2 
    - `NA-3`: Natural Area District-3 
    - `NA-4`: Natural Area District-4 
    - `OP`: Ocean Parkway District 
    - `PI`: Park Improvement District 
    - `PC`: Planned Community Preservation District 
    - `SV-1`: Scenic View District 
    - `SB`: Sheepshead Bay District 
    - `SHP`: Southern Hunters Point District 
    - `SG`: St. Geogrge District 
    - `SRD`: South Richmond Development District 
    - `SRI`: Southern Roosevelt Island District 
    - `TA`: Transit Land Use District 
    - `TMU`: Tribeca Mixed Use District
    - `US`: Union Square District 
    - `U`: United Nations Development District 
    - `WCH`: West CHelsea 
    - `WP`: Willets Point District
- **Description**: The special purpose district assigned to the tax lot.

See SplitZone to determine if the tax lot is divided.
    

### SPDist2
- **Longform Name** : `Special District 2`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: Same as SPDist1
- **Description**: The special purpose district assigned to the tax lot.

See SplitZone to determine if the tax lot is divided.
    

### SPDist3
- **Longform Name** : `Special District 3`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: Same as SPDist1
- **Description**: The special purpose district assigned to the tax lot.

See SplitZone to determine if the tax lot is divided.
    

### LtdHeight
- **Longform Name** : `Limited Height District`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - LH-1: Limited Height District No. 1 (Gramercy Park/Brooklyn Heights/Cobble Hill) 
    - LH-1A: Limited Height District No. 1A (Upper East Side) 
    - LH-2: Limited Height District No. 2 
    - LH-3: Limited Height District No. 3
- **Description**: The limited height district assigned to a tax lot.

If the tax lot is divided by zoning boundary lines, ZONING, LIMITED HEIGHT DISTRICT could be associated with any of the ZONING, ZONING DISTRICT fields. Limited height districts are coded using the three to five character district symbols that are listed in Appendix B: Special Purpose and Limited Height Districts.
    

### SplitZone
- **Longform Name** : `SplitZone`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - Y: Lot is split 
    - N: Lot is not split 
    - (blank): Unknown
- **Description**: A code indicating whether the tax lot is split by one or more zoning boundary lines.


    

### BldgClass
- **Longform Name** : `Building Class`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - `A`: One Family Dwellings
    - `A0`: Cape Cod
    - `A1`: Two Story Detached (Small or Moderate Size, With or Without Attic)
    - `A2`: One Story (Permanent Living Quarters)
    - `A3`: Large Suburban Residence
    - `A4`: City Residence
    - `A5`: Attached or Semi-detached
    - `A6`: Summer Cottages
    - `A7`: Mansion Type or Town House
    - `A8`: Bungalow Colony / Land Coop Owned
    - `A9`: Miscellaneous
    - `B`: Two Family Dwellings
    - `B1`: Brick
    - `B2`: Frame
    - `B3`: Converted (From One Family)
    - `B9`: Miscellaneous
    - `C`: Walk Up Apartments
    - `C0`: Three Families
    - `C1`: Over Six Families Without Stores
    - `C2`: Five to Six Families
    - `C3`: Four Families
    - `C4`: Old Law Tenements
    - `C5`: Converted Dwelling or Rooming House
    - `C6`: Cooperative
    - `C7`: Over Six Families with Stores
    - `C8`: Co-op Conversion from Loft / Warehouse
    - `C9`: Garden Apartments
    - `CM`: Mobile Homes/Trailer Parks
    - `D`: Co-op Conversion from Loft/Warehouse
    - `D1`: Semi-fireproff (Without Stores)
    - `D2`: Artists in Residence
    - `D3`: Fireproof (Standard Construction Without Stores)
    - `D4`: Cooperatives (Other Than Condominiums)
    - `D5`: Converted
    - `D6`: Fireproof With Stores
    - `D7`: Semi-fireproof With Stores
    - `D8`: Luxury Type
    - `D9`: Miscellaneous
    - `E`: Warehouses
    - `E1`: Fireproof
    - `E2`: Contractors Warehouse
    - `E3`: Semi-fireproof
    - `E4`: Frame, metal
    - `E6`: Governmental Warehouses
    - `E7`: Warehouse, Self Storage
    - `E9`: Miscellaneous
    - `F`: Factory and Industrial Buildings
    - `F1`: Heavy Manufacturing (Fireproof)
    - `F2`: Special Construction (Printing Plant, etc, Fireproof)
    - `F4`: Semi-Fireproof
    - `F5`: Light Manufacturing
    - `F8`: Tank Farms
    - `F(`: Miscellaneous
    - `G`: Garages and Gasoline Stations
    - `G0`: Residential Tax Class 1 Garage
    - `G1`: All Parking Garages
    - `G2`: Auto Body/Collision or Auto Repair
    - `G3`: Gas Station with Retail Store
    - `G4`: Gas Station with Service/Auto Repain
    - `G5`: Gas Station only with/without Small Kiosk
    - `G6`: Licensed Parking Lot
    - `G7`: Unlicensed Parking Lot Garage with Showroom
    - `G9`: Miscellaneous
    - `GU`: Car Sales/Rental without Showroom
    - `H`: Hotels
    - `H2`: Full Service Hotel
    - `H3`: Limited Services Many Affiliated with National Chain
    - `H4`: Motels
    - `H5`: Private Club, Luxury Type
    - `H6`: Apartment Hotels
    - `H7`: Apartment Hotels Co-Op Owned
    - `H8`: Dormitories
    - `H9`: Miscellaneous
    - `HB`: Boutique 10-100 Rooms, with Luxury Facilities, Themes, Stylish, with Full Service Accomodations
    - `HH`: Hostel-Bed Rental in Dorm Like Setting with Shared Rooms and Bathrooms
    - `HR`: SRO-1 or 2 People Housed in Individual Rooms in Multiple Dwelling Affordable Housing
    - `HS`: Extended Stay/Suite Amenities Similar to Apt., Typically Charge Weekly Rates and Less Expensive than Full Service Hotel
    - `I`: Hospitals and Health
    - `I1`: Hospitals, Sanitariusm, Mental Institutions
    - `I2`: Infirmary
    - `I3`: Dispensary
    - `I4`: Staff Facilities
    - `I5`: Health Center, Child Center, Clinic
    - `I6`: Nursing Homes
    - `I7`: Adult Care Facilities
    - `I9`: Miscellaneous
    - `J`: Theaters
    - `J1`: Art Type (Seating Capacity Under 400 Seats)
    - `J2`: Art Type (Seating Capacity Over 400 Seats)
    - `J3`: Motion Picture Theater with Balcony
    - `J4`: Legitimate Theaters (Theater Sole Use of Building)
    - `J5`: Theatre in Mixed Use Building
    - `J6`: T.V. Studio
    - `J8`: Multiplex Picture Theatre
    - `J7`: Off-Broadway Type
    - `J8`: Multiplex Picture Theatre
    - `J9`: Miscellaneous
    - `K`: Store Buildings (Taxpayers Included)
    - `K1`: One Story Retail Building
    - `K2`: Multi-Story Retail Building
    - `K3`: Department Stores, Multi-Story
    - `K4`: Predomit Retail with Other Uses
    - `K5`: Stand Alone Food Establishment
    - `K6`: Shopping Centers With or Without Parking
    - `K7`: Banking Facilities With or Without Parking
    - `K8`: Big Box Retail Not Affixed and Standing On Own Lot with Parking
    - `K9`: Miscellaneous
    - `L`: Loft Buildings
    - `L1`: Over Eight Stores (Mid-Manhattan Type)
    - `L2`: Fireproof and Storage Type (Without Stores)
    - `L3`: Semi-Fireproof
    - `L8`: With Retail Stores (Other than Type 1)
    - `L9`: Miscellaneous
    - `M`: Churches, Synagogues, Etc.
    - `M1`: Church, Synagogue, Chapel
    - `M2`: Mission House (Non-Residential)
    - `M3`: Parsonage, Rectory
    - `M4`: Convents
    - `M9`: Miscellaneous
    - `N`: Asylums and Homes
    - `N1`: Asylums
    - `N2`: Homes for Indigent Children, Aged, Homeless
    - `N3`: Orphanages
    - `N4`: Detention House For Wayward Girls
    - `N9`: Miscellaneous
    - `O`: Office Buildings
    - `O1`: Office Only - 1 Story
    - `O2`: Office Only - 2 to 6 Stories
    - `O3`: Office Only - 7 to 9 Stories
    - `O4`: Office Only or Office with Comm - 20 Stories or More
    - `O5`: Office with Comm - 1 to 6 Stories
    - `O6`: Office with Comm - 7 to 19 Stories
    - `O7`: Professional Buildings/Stand Alone Funeral Homes
    - `O8`: Office with Apartments Only (No Comm)
    - `O9`: Miscellaneous and Oly Style Bank Bldgs
    - `P`: Places of Public Assembly (Indoor) and Cultural
    - `P1`: Concert Halls
    - `P2`: Lodge Rooms
    - `P3`: YWCA, YMCA, YWHA, YMHA, PAL
    - `P4`: Beach Club
    - `P5`: Community Center
    - `P6`: Amusement Places, Bathhouses, Boat Houses
    - `P7`: Museum
    - `P8`: Library
    - `P9`: Miscellaneous Including Riding Academies and Stables
    - `Q`: Outdoor Recreation Facilities
    - `Q0`: Open Spaces
    - `Q1`: Parks/Recreation Facilities
    - `Q2`: Playgrounds
    - `Q3`: Outdoor Pools
    - `Q4`: Beaches
    - `Q5`: Golf Courses
    - `Q6`: Stadium, Race Tracks, Baseball Fields
    - `Q7`: Tennis Courts
    - `Q8`: Marinas/Yacht Clubs
    - `Q9`: Miscellaneous
    - `R`: Condominiums
    - `R0`: Condo Billing Lot
    - `R1`: Residential Unit in 2-10 Unit Bldg
    - `R2`: Residential Unit in Walk-Up Bldg
    - `R3`: Residential Unit in 1-3 Story Bldg
    - `R4`: Residential Unit in Elevator Bldg
    - `R5`: Miscellaneous Commercial
    - `R6`: Residential Unit of 1-3 Unit Bldg-Orig Class 1
    - `R7`: Commercial Unit of 1-3 Units Bldg-Orig Class 1
    - `R8`: Commercial Unit of 2-10 Unit Bldg
    - `R9`: Co-op within a Condominium
    - `RA`: Cultural, Medical, Educational, etc
    - `RB`: Office Space
    - `RC`: Commercial Building (Mixed Commercial Condo Building Classification Codes)
    - `RD`: Residential Building (Mixed Residential Condo Building Classification Codes)
    - `RG`: Indoor Parking
    - `RH`: Hotel, Boatel
    - `RI`: Mixed Warehouse, Factory, Industrial, Commercial
    - `RK`: Retail Space
    - `RM`: Mixed Residential & Commercial Building (Mixed Residential & Commercial Condo Building Classification Codes)
    - `RP`: Outdoor Parking
    - `RR`: Condominium Rental
    - `RS`: Non-Business Storage Space
    - `RT`: Terraces/Gardens/Cabanas
    - `RW`: Warehouse,Factory,Industrial
    - `RX`: Mixed Residential, Commercial, Industrial
    - `RZ`: Mixed Residential,Warehouse
    - `S`: Resident -Multiple Use
    - `S0`: Primarily One Family with Two Stores or Offices
    - `S1`: Primarily One Family with One Store or Office
    - `S2`: Primarily Two Family with One Store or Office
    - `S3`: Primarily Three Family with One Store or Office
    - `S4`: Primarily Four Family with One Store or Office
    - `S5`: Primarily Five to Six Family with One Store or Office
    - `S9`: Single or Multiple Dwelling with Stores or Offices
    - `T`: Transportation Facilities (Assessed in ORE)
    - `T1`: Airports, Air Fields, Terminals
    - `T2`: Piers, Docks, Bulkheads
    - `T9`: Miscellaneous
    - `U`: Utility Bureau Properties
    - `U0`: Utility Company Land and Buildings
    - `U1`: Bridges, Tunnels, Highways
    - `U2`: Electric Utilities, Gas
    - `U3`: Ceiling R.R.
    - `U4`: Telephone Utilities
    - `U5`: Communications Facilities (Other than Telephone)
    - `U6`: Railroad, Private Ownership
    - `U8`: Revocable Consents
    - `U9`: Miscellaneous
    - `V`: Vacant Land
    - `V0`: Zoned Residential; Not Manhattan
    - `V1`: Zoned Commercial or Manhattan Residential
    - `V2`: Zoned Commercial Adjacent to Class 1 Dwelling; Not Manhattan
    - `V3`: Zoned Primarily Residential; Not Manhattan
    - `V4`: Police or Fire Department
    - `V5`: School Site or Yard
    - `V6`: Library, Hospitals, or Museums
    - `V7`: Port Authority of NY and NJ
    - `V8`: State & US
    - `V9`: Miscellaneous
    - `W`: Educational Structures
    - `W1`: Public Elementary Junior and Senior High Schools
    - `W2`: Parochial Schools, Yeshivas
    - `W3`: Schools or Academies
    - `W4`: Training Schools
    - `W5`: City University
    - `W6`: Other Colleges and Universities
    - `W7`: Theological Seminaries
    - `W8`: Other Private Schools
    - `W9`: Miscellaneous
    - `Y`: Selected Government Installations (Excluding Office Buildings, Training Schools, Academic, Garages, Warehouses, Piers, Air Fields, Vacant Land, Vacant Sites, and Land Under Water and Easements)
    - `Y1`: Fire Department
    - `Y2`: Police Department
    - `Y3`: Prisons, Jails, Houses of Detention
    - `Y4`: Military and Naval
    - `Y5`: Department of Real Estate
    - `Y6`: Department of Sanitation
    - `Y7`: Department of Ports and Terminals
    - `Y8`: Department of Public Works
    - `Y9`: Department of Environmental Protection
    - `Z`: Miscellaneous
    - `Z0`: Tennis Court, Pool, Shed, Etc
    - `Z1`: Court House
    - `Z2`: Public Parking Areas
    - `Z3`: Post Office
    - `Z4`: Foreign Governments
    - `Z5`: United Nations
    - `Z6`: Land Under Water
    - `Z7`: Easements
    - `Z8`: Cemeteries
    - `Z9`: Other
- **Description**: A code describing the major use of structures on the tax lot.

If there are multiple uses or buildings on a tax lot, the building class describes the use with the greatest square footage on the tax lot. Several building classes describe mixed use buildings (combinations of residential and office or retail uses). A tax lot changes from a vacant to non-vacant building class: 1. With the issuance of Selected Department of Buildings Permits including New Building, Demolitions; and Alterations where there are changes to use, square footage, type and the neighborhood where the permit is issued; 2. When the Assessors sees change in the field; and 3. Feedback from the public.
    

### LandUse
- **Longform Name** : `Land Use`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - `01`: One & Two Family Buildings
    - `02`: Multi - Family Walk - Up Buildings
    - `03`: Multi - Family Elevator Buildings
    - `03`: Mixed Residential and Commercial Buildings
    - `05`: Commercial and Office Buildings
    - `06`: Industrial and Manufacturing
    - `07`: Transportation and Utility
    - `08`: Public Facilities and Institutions
    - `09`: Open Space and Outdoor Recreation
    - `10`: Parking Facilities
    - `11`: Vacant Land
- **Description**: A code for the tax lot's land use category, modified for display of parks, New York City Department of Parks and Recreation properties and New York State Office of Parks, Recreation and Historic Preservation properties in the appropriate category on land use maps.

A tax lot's land use category is derived from the lot's building class (see BldgClass). The Department of City Planning assigned building classes to the most appropriate land use category. Park properties were identified using data sources other than the DOF Building Classes and, where appropriate, were classified with a Land Use Category of 09- Open Space and Outdoor Recreation, regardless of the tax lot's building class.
    

### Easements
- **Longform Name** : `Easements`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The number of easements on the tax lot. If the number is zero, the tax lot has no easement.


    

### OwnerType
- **Longform Name** : `Owner Type`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- `C`: City Ownership
- `M`: Mixed City and Private Ownership
- `Other`: Public Authority, State or Federal Ownership
- `P`: Private Ownership - Either the tax lot has started an "in rem" action or it was once city owned.
- `X`: Mixed (Excludes property with a C, M, O, or P ownership code). Fully tax exempt property that could be owned by the city, state, or federal government; a public authority; or a private institution.
- `blank`: Unknown (Usually Private Ownership)
- **Description**: A code indicating type of ownership for the tax lot

It is recommended that OwnerName be referenced to verify the type of ownership, specifically when state and federal government and public authority ownership is important.
    

### OwnerName
- **Longform Name** : `Owner Name`
- **DataType**: `Plaint Text`
- **Expected/Allowed Values**: 
- **Description**: The name of the owner of the tax lot.


    

### LotArea
- **Longform Name** : `Lot Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: Total area of the tax lot, expressed in square feet rounded to the nearest

Lot Area contains street beds when the tax lot contains paper streets, i.e. streets mapped but not built. If the tax lot is not an irregularly shaped lot (IrrLotCode) the Department of Fice derives the Lot Area by multiplying the Lot Frontage by the Lot Depth. If the tax lot is irregularly shaped Fice manually calculates the Lot Area from the Tax Maps. If the lot area is zero, data is not available for the tax lot
    

### BldgArea
- **Longform Name** : `Building Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: N\A
- **Description**: The total gross area in square feet

Only one data source is used per tax lot (See FLOOR AREA, TOTAL BUILDING SOURCE CODE) except for condo measurements which come from the Condo Declaration and are net square footage not gross. If FLOOR AREA, TOTAL BUILDING SOURCE CODE field has a code of 2 or 7, the TOTAL BUILDING FLOOR AREA is based on gross building area also known as total gross square feet. The TOTAL FLOOR AREA is for all of the structures on the tax lot, including stairwells, halls, elevator shafts, attics and extensions such as attached garages. Measurements are based on exterior dimensions and does take into account setbacks. If the FLOOR AREA, TOTAL BUILDING SOURCE CODE field has a value of 5, the floor area was calculated from the DOF RPAD Master File using the building dimensions and number of stories for ONLY the largest structure on the tax lot. NOTE: This is a rough estimate of the gross building floor area and does not necessarily take into account all the criteria for calculating floor area as defined in section 12-10 of the Zoning Resolution. If a roof is used for parking/garden/playground the square footage is not included in the Floor Area.The two main things that trigger an update is the issuance of a Department of Buildings permit and a request from the owner to update the data.The sum of COMMERCIAL and RESIDENTIAL FLOOR AREA does not always equal TOTAL BUILDING FLOOR AREA.If the FLOOR AREA, TOTAL BUILDING SOURCE CODE is 2, the TOTAL BUILDING FLOOR AREA contains the Common Area for condominiums. If the FLOOR AREA, TOTAL BUILDING SOURCE CODE is 7, the TOTAL BUILDING FLOOR AREA does not include finished basement below grade. A TOTAL BUILDING FLOOR AREA of zero can mean it is either not available or not applicable. If NUMBER OF BUILDINGS is greater than zero, then a TOTAL BUILDING FLOOR AREA of zero means it is not available. If NUMBER OF BUILDINGS is zero, then a TOTAL BUILDING FLOOR AREA of zero means it is not applicable.
    

### ComArea
- **Longform Name** : `Commercial Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for commercial use.

Originally Square Footage came from sketches but for both New Construction and Alterations it comes from site visits. An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.A COMMERCIAL FLOOR AREA of zero can mean it is either not available or not applicable.The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. COMMERCIAL FLOOR AREA does not contain a condominiums Common Area.
    

### ResArea
- **Longform Name** : `Residential Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for residential use.

An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.A RESIDENTIAL FLOOR AREA of zero can mean it is either not available or not applicable.The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. RESIDENTIAL FLOOR AREA does not contain a condominiums Common Area.
    

### OfficeArea
- **Longform Name** : `Office Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for office use.

The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. An OFFICE FLOOR AREA of zero can mean it is either not available or not applicable. This information is NOT available for one, two or three family structures.An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.
    

### RetailArea
- **Longform Name** : `Retail Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for retail use.

The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. A RETAIL FLOOR AREA of zero can mean it is either not available or not applicable. This information is NOT available for one, two or three family structures. An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.
    

### GarageArea
- **Longform Name** : `Garage Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for garage use.

The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. A GARAGE FLOOR AREA of zero can mean it is either not available or not applicable. This information is NOT available for one, two or three family structures. An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.
    

### StrgArea
- **Longform Name** : `Storage Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for storage or loft purposes.

This information is NOT available for one, two or three family structures. A STORAGE FLOOR AREA of zero can mean it is either not available or not applicable. The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.
    

### FactryArea
- **Longform Name** : `Factory Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for factory, warehouse or loft use.

This information is NOT available for one, two or three family structures. A FACTORY FLOOR AREA of zero can mean it is either not available or not applicable. The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.
    

### OtherArea
- **Longform Name** : `Other Area`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: An estimate of the exterior dimensions of the portion of the structure(s) allocated for other than Residential, Office, Retail, Garage, Storage, Loft or Factory use.

The sum of the various FLOOR AREAs does not always equal TOTAL BUILDING FLOOR AREA. An OTHER FLOOR AREA of zero can mean it is either not available or not applicable. This information is NOT available for one, two or three family structures. An update to the Floor Area is triggered by the issuance of a Department of Buildings Permit, feedback from the public and scheduled visits by the Department of Fice assessors.
    

### AreaSource
- **Longform Name** : `Area Source`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 0: Not Available - 2: Department of Fice's RPAD File - 3: One or more Building Dimensions are non-numeric. Total Building Floor Area is 0. - 4: Building Class is 'V' and Number of Buildings is 0. Total Building Floor Area is 0. - 5: Total Building Floor Area is calculated from RPAD Building Dimensions and Number of Stories for largest building only. - 6: Unknown - 7: Department of Fice's Mass Appraisal System - 9: User
- **Description**: A code indicating the source file that was used to determine the tax lot's total building floor area.


    

### NumBldgs
- **Longform Name** : `Number of Buildings`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The number of buildings on the tax lot.

Only one data source is used per tax lot. If the tax lot is in Geosupport, the Geosupport Number of Structures field is used. If the tax lot is not in Geosupport, the DOF RPAD Master File Number of Buildings field is used. With few exceptions, buildings are permanent structures. If an assessor values a semi-permanent structure, such as a parking attendants building, then it is considered a building. NUMBER OF BUILDINGS does not include extensions.
    

### NumFloors
- **Longform Name** : `Number of Floors`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: In the tallest building on the tax lot, the number of full and partial stories starting from the ground floor.

Above ground Basements are not included in the Number of Floors. A roof used for parking, farming, playground, etc. is not included in Number of Floors. If the number of floors (NumFloors) is zero and the number of buildings(NumBldgs) is greater than zero, the number of floors(NumFloors) is not available for the tax lot. If the number of floors (NumFloors) is zero and the number of buildings is zero, then the number of floors is not applicable for the tax lot.
    

### UnitsRes
- **Longform Name** : `Residential Units`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The sum of residential units in all buildings on the tax lot.

Hotels/motels, nursing homes and SROs do not have residential units, while boarding houses do have residential units. An update to Residential Units is triggered by the issuance of a Department of Buildings permit.If Building value is zero then the dwelling units represent what is on the Department of Buildings permit. Does DOF included the Supers apartment as a residential unit if that apartment is in the basement? Yes, DOF would include a Supers apartment in the basement as a residential unit.
    

### UnitsTotal
- **Longform Name** : `Total Units`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The sum of residential and non-residential (offices, retail sotres, etc.) units in all buildings on the tax lot.

The count of non-residential units is sometimes not available if the building contains residential units.Non-residential units are units with a separate use. If a building has 25 different offices it would be counted as 1 unit because they have the same use. Updates to Residential and Non-Residential Units is triggered by the issuance of a Department of Buildings permit.
    

### LotFront
- **Longform Name** : `Lot Front`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The tax lot's frontage measured in feet.


    

### LotDepth
- **Longform Name** : `Lot Depth`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The tax lot's depth measured in feet.


    

### BldgFront
- **Longform Name** : `Building Frontage`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The building's frontage along the street measured in feet.


    

### BldgDepth
- **Longform Name** : `Building Depth`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The building's depth, which is the effective perpendicular distance, measured in feet.


    

### Ext
- **Longform Name** : `Extension`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: A code identifying whether there is an extension or free standing structure on the lot which is not the primary structure.


    

### ProxCode
- **Longform Name** : `ProxCode`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 1: Detached - 2: Semi-Attached - 3: Attached
- **Description**: The physical relationship of the building to neighboring buildings.


    

### IrrLotCode
- **Longform Name** : `Irregular Lot Code`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: Y: Irregularly Shaped Lot - N: Not an Irregularly Shaped Lot - (blank): Unknown
- **Description**: A code indicating whether the tax lot is irregularly shaped.


    

### LotType
- **Longform Name** : `Lot Type`
- **DataType**: `Number`
- **Expected/Allowed Values**: 0: Mixed or Unknown - 1: Block Assemblage - A tax lot which encompasses an entire block. - 2: Waterfront - A tax lot bordering on a body of water. Waterfront lots may contain a small amount of submerged land. - 3: Corner - A tax lot bordering on two intersecting streets - 4: Through - A tax lot which connects two streets and fronts on both streets. A lot with two frontages is not necessarily a through lot. For example, an L-shaped lot with two frontages would be coded as an Inside Lot (5). - 5: Inside - A tax lot which is not an assemblage, waterfront, corner, through, interior, island, alley or submerged lot. - 6: Interior Lot - A tax lot that has no street frontage - 7: Island Lot - A tax lot that is entirely surrounded by water. - 8: Alley Lot - A tax lot that is too narrow to accommodate a building. The lot is usually 12 feet or less in width. - 9: Submerged Land Lot - A tax lot that is totally or almost completely submerged.
- **Description**: A code indicating the location of the tax lot to another tax lot and/or the water.

N\A
    

### BsmtCode
- **Longform Name** : `Basement Code`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
    - `0`: None/No Basement
    - `1`: Full Basement that is Above Grade. The basement is 75% or more of the area of the first floor and the basement walls are at least 4 feet high on at least two sides.
    - `2`: Full Basement that is Below Grade. The basement is 75% or more of the area of the first floor and the basement walls are fully submerged or are less than 4 feet on at least three sides.
    - `3`: Partial Basement that is Above Grade. The basement is between 25% and 75% of the area of the first floor and the basement walls are at least 4 feet high on at least two sides.
    - `4`: Partial Basement that is Below Grade. The basement is between 25% and 75% of the area of the first floor and the basement walls are fully submerged or are less than 4 feet on at least three sides.
    - `5`: Unknown
- **Description**: A code describing the basement type/grade.

All basements in brownstones, high ranches, split-levels and attached row houses are Above Grade. A fully exposed basement garage door does not, in itself, satisfy the criteria for Above Grade.A finished basement must be at least four feet above ground to be considered a Finished Basement Above grade (FBA).A Finished Basement Below grade (FBB) is not included in living area square footage.A cellar is below a basement and not habitable.
    

### AssessLand
- **Longform Name** : `Assess Land`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The final tentative assessed land value for Fiscal Year 2019

The Department of Fice calculates the assessed value by multiplying the tax lot's estimated full market land value, determined as if vacant and unimproved, by a uniform percentage for the property's tax class.
    

### AssessTot
- **Longform Name** : `Assess Total`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The final tentative assessed total value for Fiscal Year 2019

The Department of Fice calculates the assessed value by multiplying the tax lot estimated full market value by a uniform percentage for the propertys tax class.Property value is assessed as of January 5th. If a site is not completed by April 14th the assessed building value is 0 and the Building Class reverts to Vacant.
    

### ExemptLand
- **Longform Name** : `Exempt Land`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The final tentative exempt land value, which is determined differently for each exemption program, is the dollar amount related to that portion of the tax lot that has received an exemption or abatement for Fiscal Year 2019.


    

### ExemptTot
- **Longform Name** : `Exempt Total`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The final tentative exempt total value, which is determined differently for each exemption program, is the dollar amount related to that portion of the tax lot that has received an exemption or abatement for Fiscal Year 2019.


    

### YearBuilt
- **Longform Name** : `Year Built`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The year construction of the building was completed.Year Built comes from Department of Buildings Permits. Year Built is accurate for the decade but not necessarily for the specific year. Two outliers which are 1910 and 1920. Structures built between 1800s and early 1900s usually have a Year Built date of either 1910 or 1920.


    

### YearAlter1
- **Longform Name** : `Year Altered 1`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**:  The year of the most recent alteration.

If the alteration spanned more than one year, YearAlter1 is the year the alteration began, otherwise it is the year the alteration was completed. The date can either be the actual date or an estimate. Year Altered comes from Department of Buildings Permits. The Department of Fice defines modifications to the structure that, according to the assesor, changes the value of the real property.
    

### YearAlter2
- **Longform Name** : `Year Altered 2`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The year of the second most recent alteration.

If the alteration spanned more than one year, YearAlter2 is the year the alteration began, otherwise it is the year the alteration was completed. The date can either be the actual date or an estimate. Year Altered comes from Department of Buildings Permits. The Department of Fice defines modifications to the structure that, according to the assesor, changes the value of the real property.
    

### HistDist
- **Longform Name** : `Historic District`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The name of the Historic District as designated by the New York City Landmarks Preservation Commission.


    

### Landmark
- **Longform Name** : `Landmark`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The name of an individual landmark, landmark site( e.g. Richmondtown Restoration) or an interior landmark, as designated by the New York City Landmarks Preservation Commission)


    

### BuiltFAR
- **Longform Name** : `Built Floor Area Ratio`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Built Floor Area Ratio (FAR) is the total building floor area divided by the area of the tax lot.

This is an estimate by City Planning based on rough building area and lot area measurements provided by the Department Of Fice. FAR is calculated using the TOTAL BUILDING FLOOR AREA and the LOT AREA. The TOTAL BUILDING FLOOR AREA is either based on gross building area also known as total gross square feet for all of the structures on the tax lot, including basements, attics and extensions such as attached garages, detached garages, pool houses and greenhouse OR the floor area was calculated from the DOF RPAD Master File using the building dimensions and number of stories for ONLY the largest structure on the tax lot depending on the source available. The LotArea contains street beds when the lot contains paper streets, i.e., streets mapped but not built.
    

### ResidFAR
- **Longform Name** : `Maximum Allowable Residential Floor Area Ratio`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Maximum Allowable Residential Floor Area Ratio (FAR). This field contains from one to four numeric digits with an imbedded decimal after the second digit.

The Maximum Allowable Floor Area Ratios are exclusive of bonuses for plazas, plazaconnected open areas, arcades or other amenities. For properties zoned R6, R7, R7-1, R8 or R9 the Maximum Allowable Floor Area reflects the maximum achievable floor area under ideal conditions. For properties in Mixed Use Special Districts, PLUTO uses the wide street Maximum Allowable Floor Area Ratio. Since the Maximum Allowable Floor Area Ratio in Mixed Use Special Districts is actually determined by whether the property is located on a wide street or a narrow street, users should consult Section 23-145 of the Zoning Resolution.
    

### CommFAR
- **Longform Name** : `Maximum Allowable Commercial Floor Area Ratio`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Maximum Allowable Commercial Floor Area Ratio (FAR) . This field contains from one to four numeric digits with an imbedded decimal after the second digit.

The Maximum Allowable Floor Area Ratios are exclusive of bonuses for plazas, plazaconnected open areas, arcades or other amenities. For properties in Mixed Use Special Districts, PLUTO uses the wide street Maximum Allowable Floor Area Ratio. Since the Maximum Allowable Floor Area Ratio in Mixed Use Special Districts is actually determined by whether the property is located on a wide street or a narrow street, users should consult Section 23-145 of the Zoning Resolution.
    

### FacilFAR
- **Longform Name** : `Maximum Allowable Community Facility Floor Area Ratio`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Maximum Allowable Facility Floor Area Ratio (FAR). This field contains from one to four numeric digits with an imbedded decimal after the second digit.

The Maximum Allowable Floor Area Ratios are exclusive of bonuses for plazas, plazaconnected open areas, arcades or other amenities. For properties in Mixed Use Special Districts, PLUTO uses the wide street Maximum Allowable Floor Area Ratio. Since the Maximum Allowable Floor Area Ratio in Mixed Use Special Districts is actually determined by whether the property is located on a wide street or a narrow street, users should consult Section 23-145 of the Zoning Resolution.
    

### BoroCode
- **Longform Name** : `Boro Code`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
    - `1`: Manhattan 
    - `2`: Bronx 
    - `3`: Brooklyn 
    - `4`: Queens 
    - `5`: Staten Island
- **Description**: The borough the tax lot is located in.

Two portions of the city, Marble Hill and Rikers Island, are each legally located in one borough but are serviced by different boroughs. The BoroCode associated with these areas are the boroughs they are legally located in. Specifically, Marble Hill is serviced by the Bronx but is legally located in Manhattan and has a Manhattan BoroCode. Rikers Island has a Bronx BoroCode because it is legally located in the Bronx although it is serviced by Queens.
    

### BBL
- **Longform Name** : `BBL`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: A concatenation of the BoroCode, TaxBlock and the corresponding TaxLot. This field consists of the tax block followed by the tax lot. The tax block is one to five numeric digits, preceded with leading zeros when the block is less than five digits. The tax lot is one to four digits and is preceded with leading zeros when the lot is less than four digits.


    

### CondoNo
- **Longform Name** : `Condo Number`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The condominium number assigned to the complex.


    

### Tract2010
- **Longform Name** : `Tract 2010`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The 2010 census tract that the tax lot is located in.

2010 Census Tracts geographic areas defined by the US Census Bureau for the 2010 Census. If a tax lot is split by a census tract boundary, only one census tract is retained.
    

### XCoord
- **Longform Name** : `X Coordinate`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The X coordinate of the XY coordinate pair which depicts the approximate location of the address.

The XY coordinates are expressed in the New York- Long Island State Plane Coordinate System (NAD83).
    

### YCoord
- **Longform Name** : `Y Coordinate`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The Y coordinate of the XY coordinate pair which depicts the approximate location of the address.

The Y coordinate of the XY coordinate pair which depicts the approximate location of the address.
    

### ZoneMap
- **Longform Name** : `Zone Map #`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The Department of City Planning Zoning Map Number associated with the tax lots X and Y coordinates.


    

### ZMCode
- **Longform Name** : `Zoning Map Code`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: A code(Y) identifies a border Tax Lot, i.e. a Tax Lot on the border of two or more Zoning Maps.


    

### Sanborn
- **Longform Name** : `Sanborn Map #`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The Sanborn Map Company map number associated with the tax block and lot. Sanborn map number format is Borough Code / Volume Number / Page Number.


    

### TaxMap
- **Longform Name** : `Tax Map #`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The Department of Fice paper tax map Volume Number associated with the tax block and lot. Tax map number format is Borough Code / Volume Number / Page Number. The Department of Fice no longer updates their paper tax maps.


    

### EDesigNum
- **Longform Name** : `E Designation Number`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The E-Designation number assigned to the tax lot.


    

### APPBBL
- **Longform Name** : `Apportionment BBL`
- **DataType**: `Number`
- **Expected/Allowed Values**: 
- **Description**: The originating Borough, Tax Block and Tax Lot from the apportionment prior to the merge, split or property's conversion to a condominium. The Apportionment BBL is only available for mergers, splits and conversions since 1984.


    

### APPDate
- **Longform Name** : `Apportionment Date`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The date of the Apportionment in the format MM/DD/YYYY.


    

### PLUTOMapID
- **Longform Name** : `PLUTOMap ID`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 1: In PLUTO Data File and DOF Modified DTM Tax Block and Lot Clipped to the Shoreline File. - 2: In PLUTO Data File Only. - 3: In DOF Modified DTM Tax Block and Lot Clipped to the Shoreline File but NOT in PLUTO. - 4: In PLUTO Data File and in DOF Modified DTM File but NOT in DOF Modified DTM Tax Block and Lot Clipped to the Shoreline File, therefore the tax lot is totally under water. 5: In DOF Modified DTM but NOT in PLUTO, therefore the tax lot is totally under water.
- **Description**: A code indicating whether the tax lot is in the PLUTO file and/or the modified DTM and/or the modified DTM Clipped to the Shoreline File.

The tax lot will not appear in the MapPLUTO geodatabase if the lot is found only in the PLUTO data file. If the tax lot has a PLUTO-Base Map Indicator code of 3 or 5, then the PLUTO record will only contain data in the borough, tax block, tax lot, community district and PLUTO-Base Map Indicator fields.
    

### FIRM07_FLA
- **Longform Name** : `FIRM07_FLA`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: 2007 FLOOD INSURANCE RATE MAP INDICATOR. Code of 1 means that some portion of the tax lot falls within the 1 percent annual chance floodplain as determined by FEMAs 2007 Floord Insurance Rate Map. It does not always mean that a building or group of buildings on that tax lot is within the 1 percent annual chance floodplain.


    

### PFIRM15_FL
- **Longform Name** : `PFIRM15_FL`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: 2015 PRELIMINARY FLOOD INSURANCE RATE MAP INDICATOR. Code of 1 means that some portion of the tax lot falls within the 1 percent annual chance floodplain as determined by FEMAs 2015 Preliminary Flood Insurance Rate Map. It does not always mean that a building or group of buildings on that tax lot is within the 1 percent annual chance floodplain.


    

### Version
- **Longform Name** : `Version`
- **DataType**: `Plain Text`
- **Expected/Allowed Values**: 
- **Description**: The Version Number related to the release of PLUTO.