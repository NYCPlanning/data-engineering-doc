## Products Overview {docsify-ignore}

Data Engineering builds and maintains a variety of data products. Many of these products support the work of other teams within DCP and serve as inputs to public-facing applications. Products are in various phases of development, so version-to-version stability differs.

+ **Stable:** These products are routinely updated. Code changes and enhancements do not happen with every release, and instead occur in scheduled sprints. Users can expect version-to-version schemas to remain consistent. Updates of these data products are largely automated and transfered to the business owner.
+ **Frequent enhancements:** While these products get produced regularly, few updates occur without hands-on tweaking of the code. The production of these datasets are still closely controlled by data engineering.
+ **In development:** These datasets are currently being developed. They have not settled into a routine production schedule yet, and may experience major overhauls between versions. 


| Dataset | Description | Business Owner | Production Cycle | Stability | Geometry | GitHub |
| -------- | ----------- | ----------------- | ----------------- | -------- | ----- | ----- |
| [PLUTO and MapPLUTO](/_content/pluto) | Contains over seventy tax lot, building, and geographic/political/administrative characteristics for NYC lots. MapPLUTO is a combination of these attributes with the DOF Digital Tax Map, and is designed for GIS users. | DCP Enterprise Data Management | Monthly | Stable | Polygons (MapPLUTO) | [db-pluto](https://github.com/NYCPlanning/db-pluto) |
| [COLP](/_content/colp) | City Owned and Leased Properties: Contains property-level information about use, owning/leasing agency, location, and tenent agreements. Built from the DCAS Integrated Property Information System | DCP Enterprise Data Management & DCAS |  | In development | Points | [db-colp](https://github.com/NYCPlanning/db-colp) |
| [Facilities](/_content/facilities) | Location and characteristics and categorization of more than 35,000 public facilities in NYC. This data is a standardized aggregation of other public datasets. | DCP Enterprise Data Management | Quarterly | Frequent enhancements | Points | [db-facilities](https://github.com/NYCPlanning/db-facilities) |
| [Developments](/_content/developments) | Contains information about new building, demolitions, and alterations of buildings occuring since the 2010 Census. The purpose of this dataset is to capture development and residential growth over time. The primary input for this dataset is DOB jobs and occupancy data. | DCP Housing and Economic Development | Bianually | Frequent enhancements | Points | [db-developments](https://github.com/NYCPlanning/db-developments) |

<span class="label dcp-edm">DCP EDM</span>
<span class="label dcas">DCAS</span>
<span class="label dcp-hed">DCP HED</span>

<span class="label stable">stable</span>
<span class="label in-development">in development</span>
<span class="label enhancing">frequent enhancement</span>