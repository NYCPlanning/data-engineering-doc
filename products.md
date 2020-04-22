## Products Overview {docsify-ignore}

Data Engineering builds and maintains a variety of data products. Many of these products support the work of other teams within DCP and serve as inputs to public-facing applications. Products are in various phases of development, so version-to-version stability differs.

+ **Stable:** These products are routinely updated. Code changes and enhancements do not happen with every release, and instead occur in scheduled sprints. Users can expect version-to-version schemas to remain consistent. Updates of these data products are largely automated and transfered to the business owner.
+ **Frequent enhancements:** While these products get produced regularly, few updates occur without hands-on tweaking of the code. The production of these datasets are still closely controlled by data engineering.
+ **In development:** These datasets are currently being developed. They have not settled into a routine production schedule yet, and may experience major overhauls between versions. 


### [PLUTO: ](/_content/pluto)
**Stability:** <span class="label stable">stable</span> 

**Business-owners:** <span class="label dcp-edm">DCP EDM</span>

**Update-cycle:** Monthly

**GitHub:** [db-pluto](https://github.com/NYCPlanning/db-pluto)

Contains over seventy tax lot, building, and geographic/political/administrative characteristics for NYC lots. MapPLUTO is a combination of these attributes with the DOF Digital Tax Map, and is designed for GIS users. 

### [COLP: City Owned and Leased Properties](/_content/colp) 
**Stability:** <span class="label in-development">in development</span>

**Business-owners:** <span class="label dcp-edm">DCP EDM</span> <span class="label dcas">DCAS</span>

**Update-cycle:** Not determined

**GitHub:** [db-colp](https://github.com/NYCPlanning/db-colp)

Contains property-level information about use, owning/leasing agency, location, and tenent agreements. Built from the DCAS Integrated Property Information System

### [Facilities](/_content/facilities) 
**Stability:** <span class="label enhancing">frequent enhancement</span>

**Business-owners:** <span class="label dcp-edm">DCP EDM</span>

**Update-cycle:** Quarterly

**GitHub:** [db-facilities](https://github.com/NYCPlanning/db-colp)

Location and characteristics and categorization of more than 35,000 public facilities in NYC. This data is a standardized aggregation of other public datasets.


### [Developments](/_content/developments) 
**Stability:** <span class="label enhancing">frequent enhancement</span>

**Business-owners:** <span class="label dcp-hed">DCP HED</span>

**Update-cycle:** Bianually

**GitHub:** [db-developments](https://github.com/NYCPlanning/db-developments)

Contains information about new building, demolitions, and alterations of buildings occuring since the 2010 Census. The purpose of this dataset is to capture development and residential growth over time. The primary input for this dataset is DOB jobs and occupancy data.
