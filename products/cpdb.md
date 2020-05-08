# Capital Projects Database

## About

The Capital Projects Database (CPDB), a data product produced by the New York City (NYC) Department of City Planning (DCP) Capital Planning division, captures key data points on potential, planned, and ongoing capital projects sponsored or managed by a capital agency in and around NYC.

Information reported in the Capital Commitment Plan published by the NYC Office of Management and Budget (OMB) three times per year is the foundation that CPDB is then built off of; therefore, only the capital projects that appear in the Capital Commitment Plan are reflected in CPDB. Other open data resources are also leveraged to map the capital projects.

CPDB supports the most comprehensive map of potential, planned, and ongoing capital projects taking place across NYC enabling Planners to better understand and communicate New York City’s capital project portfolio within and across particular agencies. This integrated but not exhaustive view provides a broad understanding of what projects are taking place within a certain area, and a starting point to discovering opportunities for strategic neighborhood planning.

## Data Dictionary -- Projects

?> The source data used to build CPDB determines what attributes are reported by the final product. Using FMS data from FISA provides the greatest level of detail and accuracy, and outputs the most attributes. Attributes marked with a `*` are exclusive to FISA source data.  
The tables that compose CPDB are all related by the **FMS ID**.

> **Projects(cpdb_projects)**: Reports information from the Capital Commitment Plan at the project level. A project is a unique FMS ID.

### maprojid

- **Longform Name**: `FMS ID`
- **Description**: Unique identifier that defines a discrete project. The maprojid is a concatenation of magency and projectid and it is the primary key.

### magency

- **Longform Name**: `Managing Agency`
- **Description**: Three digit code of the distinct City agency managing the project.

### projectid

- **Longform Name**: `Project ID`
- **Description**: Alphanumeric code created by the sponsor agency that identifies a distinct project. A Project ID must be unique within a managing agency.

### description

- **Longform Name**: `Description`
- **Description**: Short description of the project as described by the sponsor agency. If one FMS ID had many descriptions the longest description is reported by CPDB.

### ccnonexempt

- **Longform Name**: `$ City Cost (Non-Exempt) *`
- **Description**: Sum of City Cost (Non-Exempt) funding across all commitments associated with the project.

### ccexempt

- **Longform Name**: `$ City Cost (Exempt) *`
- **Description**: funding across all commitments associated with the project.

### citycost

- **Longform Name**: `$ City Cost`
- **Description**: Sum of City funding across all commitments associated with the project. (If FISA is the source data $ City Cost is the sum of $ City Cost (Exempt) and $ City Cost (Non-Exempt)).

### nccstate

- **Longform Name**: `$ Non-City Cost State *`
- **Description**: Sum of State funding across all commitments associated with the project.

### nccfederal

- **Longform Name**: `$ Non-City Cost Federal *`
- **Description**: Sum of Federal funding across all commitments associated with the project.

### nccother

- **Longform Name**: `$ Non-City Cost Other *`
- **Description**: Sum of Other funding across all commitments associated with the project.

### noncitycost

- **Longform Name**: `$ Non-City Cost`
- **Description**: Sum of Non-City funding across all commitments associated with the project. (If FISA is the source data $ Non-City Cost is the sum of $ Non-City Cost State, $ Non-City Cost Federal, and $ Non-City Cost Other).

### nccother

- **Longform Name**: `$ Non-City Cost Other *`
- **Description**:

### totalcost

- **Longform Name**: `$ Total Planned Commitments`
- **Description**: Sum of $ City Cost and $ Non-City Cost, which reports the total planned commitments for the project allocated in the Capital Commitment Plan.

### magencyacro

- **Longform Name**: `Managing Agency Acronym`
- **Description**: Common acronym of the city agency managing the project. This value is derived from the three digit managing agency code.

### magencyname

- **Longform Name**: `Managing Agency Name`
- **Description**: Common name for the city agency mananging the project. This value is derived from the three digit managing agency code.

### ccpversion

- **Longform Name**: `Capital Commitment Plan version`
- **Description**: Reports the version of the Capital Commitment Plan which the record is based on.

## Data Dictionary -- Budgets

> **Budgets (cpdb_budgets)**: Reports information from the Capital Commitment Plan for projects at the budget level. One project can be funded by many budgets.

### maprojid

- **Longform Name**: `FMS ID`
- **Description**: Unique identifier that defines a discrete project. The maprojid is a concatenation of magency and projectid and it is the foreign key.

### magency

- **Longform Name**: `Managing Agency`
- **Description**: Three digit code of the distinct City agency managing the project.

### projectid

- **Longform Name**: `Project ID`
- **Description**: Alphanumeric code created by the sponsor agency that identifies a distinct project. A Project ID must be unique within a managing agency.

### budgetline

- **Longform Name**: `Budget Line`
- **Description**: Unique identifier of the budget used to fund the project.

### projecttype

- **Longform Name**: `Project type`
- **Description**: Short description of the type of project based on the budget funding the project.

### sagencyacro

- **Longform Name**: `Sponsor Agency Acronym`
- **Description**: Common acronym of the city agency sponsoring the project. This value is derived from the budget line.

### sagencyname

- **Longform Name**: `Sponsor Agency Name`
- **Description**: Common name for the city agency sponsoring the project. This value is derived from the budget line.

### ccnonexempt

- **Longform Name**: `$ City Cost (Non-Exempt) *`
- **Description**: Sum of City Cost (Non-Exempt) funding across all commitments associated with the project drawn from the specified budget line.

### ccexempt

- **Longform Name**: `$ City Cost (Exempt) *`
- **Description**: Sum of City Cost (Exempt) funding across all commitments associated with the project drawn from the specified budget line.

### citycost

- **Longform Name**: `$ City Cost`
- **Description**: Sum of City funding across all commitments associated with the project drawn from the specified budget line. (If FISA is the source data $ City Cost is the sum of $ City Cost (Exempt) and $ City Cost (Non-Exempt)).

### nccstate

- **Longform Name**: `$ Non-City Cost State *`
- **Description**: Sum of State funding across all commitments associated with the project drawn from the specified budget line.

### nccfederal

- **Longform Name**: `$ Non-City Cost Federal *`
- **Description**: Sum of Federal funding across all commitments associated with the project drawn from the specified budget line.

### nccother

- **Longform Name**: `$ Non-City Cost Other *`
- **Description**: Sum of Other funding across all commitments associated with the project drawn from the specified budget line.

### noncitycost

- **Longform Name**: `$ Non-City Cost`
- **Description**: Sum of Non-City funding across all commitments associated with the project drawn from the specified budget line. (If FISA is the source data $ Non-City Cost is the sum of $ Non-City Cost State, $ Non-City Cost Federal, and $ Non-City Cost Other).

### totalcost

- **Longform Name**: `$ Total Planned Commitments`
- **Description**: Sum of $ City Cost and $ Non-City Cost, which reports the total planned commitments drawn from the specified budget line for the project allocated in the Capital Commitment Plan.

### ccpversion

- **Longform Name**: `Capital Commitment Plan version`
- **Description**: Reports the version of the Capital Commitment Plan which the record is based on.

## Data Dictionary -- Commitments

>**Commitments (cpdb_commitments)**: Reports information from the Capital Commitment Plan at the commitment level. Many commitments can fund one project.

### maprojid

- **Longform Name**: `FMS ID`
- **Description**: Unique identifier that defines a discrete project. The maprojid is a concatenation of magency and projectid and it is the foreign key.

### magency

- **Longform Name**: `Managing Agency`
- **Description**: Three digit code of the distinct City agency managing the project.

### projectid

- **Longform Name**: `Project ID`
- **Description**: Alphanumeric code created by the sponsor agency that identifies a distinct project. A Project ID must be unique within a managing agency.

### budgetline

- **Longform Name**: `Budget Line`
- **Description**: Unique identifier of the budget used to fund the project.

### plancommdate

- **Longform Name**: `Planned Commit Date`
- **Description**: Month and year of when the planned commitment is projected to be committed.

### commitmentdescription

- **Longform Name**: `Commitment Description`
- **Description**: Short description of what the planned commtiment will specifically fund. Not all commitments have descriptions.

### commitmentcode

- **Longform Name**: `Commitment Code`
- **Description**: Four letter or digit code indicating what part of the project the associated funding is for, such as design, construction, or contingency.

### typc

- **Longform Name**: `Ten Year Plan Categroy *`
- **Description**: Three leter code indicating what ten year plan category the planned commitment supports.

### typcname

- **Longform Name**: `Ten Year Plan Categroy Name *`
- **Description**: Ten year plan category the planned commitment supports.

### ccnonexempt

- **Longform Name**: `$ City Cost (Non-Exempt) *`
- **Description**: Amount City Cost (Non-Exempt) funding associated with the commitment.

### ccexempt

- **Longform Name**: `$ City Cost (Exempt) *`
- **Description**: Amount of City Cost (Exempt) funding associated with the commitment.

### citycost

- **Longform Name**: `$ City Cost`
- **Description**: Amount of City funding associated with the commitment. (If FISA is the source data $ City Cost is the sum of $ City Cost (Exempt) and $ City Cost (Non-Exempt)).

### nccstate

- **Longform Name**: `$ Non-City Cost State *`
- **Description**: Amount of State funding associated with the commitment.

### nccfederal

- **Longform Name**: `$ Non-City Cost Federal *`
- **Description**: Amount of Federal funding associated with the commitment.

### nccother

- **Longform Name**: `$ Non-City Cost Other *`
- **Description**: Amount of Other funding associated with the commitment.

### noncitycost

- **Longform Name**: `$ Non-City Cost`
- **Description**: Amount of Non-City funding associated with the commitment. (If FISA is the source data $ Non-City Cost is the sum of $ Non-City Cost State, $ Non-City Cost Federal, and $ Non-City Cost Other).

### totalcost

- **Longform Name**: `$ Total Planned Commitments`
- **Description**: Sum of $ City Cost and $ Non-City Cost, which reports the total planned commitments associated with the commitment for the project allocated in the Capital Commitment Plan.

### ccpversion

- **Longform Name**: `Capital Commitment Plan version`
- **Description**: Reports the version of the Capital Commitment Plan which the record is based on.

## Data Dictionary -- DCP Attributes

> **DCP Attributes (cpdb_dcpattributes)**: Reports information generated by DPC, including spatial data, at the project level. These data are published as two tables _pts and _poly where data are separated based on the geometry type.

### maprojid

- **Longform Name**: `FMS ID`
- **Description**: Unique identifier that defines a discrete project. The maprojid is a concatenation of magency and projectid and it is the primary key.

### magency

- **Longform Name**: `Managing Agency`
- **Description**: Three digit code of the distinct City agency managing the project.

### projectid

- **Longform Name**: `Project ID`
- **Description**: Alphanumeric code created by the sponsor agency that identifies a distinct project. A Project ID must be unique within a managing agency.

### magencyacro

- **Longform Name**: `Managing Agency Acronym`
- **Description**: Common acronym of the city agency managing the project. This value is derived from the three digit managing agency code.

### description

- **Longform Name**: `Description`
- **Description**: Short description of the project as described by the sponsor agency. If one FMS ID had many descriptions the longest description is reported by CPDB.

### typecategory

- **Longform Name**: `Category`
- **Description**: Classification given by DCP based on keywords found in the short description describing if a projects is Fixed Asset, Lump Sum, or ITT, Vehicles, and Equipment.

### geomsource

- **Longform Name**: `Geometry Source`
- **Description**: Description of where the geometry associated with the project came from.

### dataname

- **Longform Name**: `Data Name`
- **Description**: Name of the dataset where the geometry associated with the project came from.

### datasource

- **Longform Name**: `Data Source`
- **Description**: Acronym of the agency that supplied the dataset from which the geometry associated with the project came from.

### datadate

- **Longform Name**: `Data Date`
- **Description**: Date the geometry was updated.

### ccpversion

- **Longform Name**: `Capital Commitment Plan version`
- **Description**: Reports the version of the Capital Commitment Plan which the record is associated with.

### geom

- **Longform Name**: `Geometry`
- **Description**: Spatial data information.

## Data Dictionary -- Project Combined

> **Project Combined (cpdb_projects_combined)**: Master flat file used to power the Capital Projects Explorer that aggregates and reports data at the project level.

### maprojid

- **Longform Name**: `FMS ID`
- **Description**: Unique identifier that defines a discrete project. The maprojid is a concatenation of magency and projectid and it is the primary key.

### magency

- **Longform Name**: `Managing Agency`
- **Description**: Three digit code of the distinct City agency managing the project.

### projectid

- **Longform Name**: `Project ID`
- **Description**: Alphanumeric code created by the sponsor agency that identifies a distinct project. A Project ID must be unique within a managing agency.

### magencyacro

- **Longform Name**: `Managing Agency Acronym`
- **Description**: Common acronym of the city agency managing the project. This value is derived from the three digit managing agency code.

### description

- **Longform Name**: `Description`
- **Description**: Short description of the project as described by the sponsor agency. If one FMS ID had many descriptions the longest description is reported by CPDB.

### typecategory

- **Longform Name**: `Category`
- **Description**: Classification given by DCP based on keywords found in the short description describing if a projects is Fixed Asset, Lump Sum, or ITT, Vehicles, and Equipment.

### geomsource

- **Longform Name**: `Geometry Source`
- **Description**: Description of where the geometry associated with the project came from.

### dataname

- **Longform Name**: `Data Name`
- **Description**: Name of the dataset where the geometry associated with the project came from.

### datasource

- **Longform Name**: `Data Source`
- **Description**: Acronym of the agency that supplied the dataset from which the geometry associated with the project came from.

### datadate

- **Longform Name**: `Data Date`
- **Description**: Date the geometry was updated.

### ccpversion

- **Longform Name**: `Capital Commitment Plan version`
- **Description**: Reports the version of the Capital Commitment Plan which the record is associated with.

### geom

- **Longform Name**: `Geometry`
- **Description**: Spatial data information.

## Disclaimer

CPDB is only as good as the source data it extracts and aggregates; therefore, CPDB includes data on current and planned NYC capital projects reported in OMB's Capital Commitment Plan and it does not capture all historic, current, or future capital projects.

CPDB is not a project or financial management system. Data on project timeline may be incorrect and budgetary information may be incomplete since all monies committed to or spent on a project may not be captured. CPDB does capture planned commitments allocated to projects that may never come to fruition; these instances are most frequent for projects funded by discretionary funding sources, such as council member funding.

Currently, CPDB is the most comprehensive spatial data resource of current and planned City capital projects, but the spatial data are not 100% reliable, accurate, or exhaustive.

The map of capital projects is incomplete because many capital projects could not be spatially referenced due to vague descriptions not including the name of a site.

Some projects are mapped incorrectly. Some projects are geocoded to agency's headquarters rather than the site where the capital investment and construction is taking place. Other projects are mapped to the wrong site as a result of two places having the same name or similar names. Unfortunately, these records cannot be systematically verified and corrected.

Through user feedback we look to resolve these limitation over time.

For more detailed information on a specific capital project please reach out to the respective managing or sponsor agency.

As a result of these limitations and inconsistencies, CPDB should not be used for quantitative analyses. CPDB should be used for planning coordination and information purposes only. If CPDB is used for any spatial analyses it is crucial to recognize that not all of the projects are spatially referenced, projects may be incorrectly spatially referenced, one project can span across many locations, and this database is not authoritatively comprehensive.

If you have any questions about or comments on these data please contact the NYC DCP Capital Planning team at CapitalPlanning_DL@planning.nyc.gov
