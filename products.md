<h1 style="font-size:3rem; margin:0 0 2rem 0; font-weight:900; color:#212326;">
Products Overview
</h1>
<div id="data-products" class="card-deck">
    <div v-for="product in products" 
        :key="product.name"
        class="card mb-3" style="min-width: 16rem;">
        <div class="card-header">
            <a :href="product.link">
                    <span class="product-name">
                        {{ product.name }}
                    </span>
                </a>
            <a :href="product.repo">
                <i class="fab fa-github fa-lg" style="color:#212326; margin: 0 0 2px 0;"></i>
            </a>
        </div>
        <div class="card-body">
            <div>
                <div>
                    <p class='product-labelname'>Status:</p>
                    <span 
                        v-bind:style="{background: product.stability.color}" 
                        class="label"
                    >
                        {{ product.stability.name }}
                    </span>
                </div>
                <div>
                    <p class="product-labelname">Business owners:</p>
                    <span
                        v-for="owner in product.businessowner"
                        v-bind:style="{background: owner.color}"
                        class="label"
                    >
                        {{ owner.name }}
                    </span>
                </div>
                <div>
                    <p class="product-labelname">update cycle:</p>
                    <span class="label">{{  product.productcycle }}</span>
                </div>
            </div>
            <p class="description">
                {{ product.description }}
            </p>
        </div>
    </div>
</div>

!> <span class="label" style="background:#00ae00">stable</span>: These products are routinely updated. Code changes and enhancements do not happen with every release, and instead occur in scheduled sprints. Users can expect version-to-version schemas to remain consistent. Updates of these data products are largely automated and transfered to the business owner.  
<span class="label" style="background:#edb700">frequent enhancement</span>: While these products get produced regularly, few updates occur without hands-on tweaking of the code. The production of these datasets are still closely controlled by data engineering.  
<span class="label" style="background:#d73a49">in development</span>: These datasets are currently being developed. They have not settled into a routine production schedule yet, and may experience major overhauls between versions.

<script>
    var edm = {name:'DCP EDM', color:'#0366d6'}
    var hed = {name:'DCP HED', color:'#ff006a'}
    var cp = {name:'DCP CP', color:'#170cf0'}
    var dcas = {name:'DCAS', color:'#c300ff'}
    var pop = {name:'DCP Population', color:'#4a8207'}
    var plancoord = {name:'DCP Planning Coordination', color:'#ed6802'}
    var stable = {name:'stable', color:'#00ae00'}
    var developing = {name:'in development', color:'#d73a49'}
    var enhancing = {name:'frequent enhancement', color:'#edb700'}
    var dataProducts = new Vue({
        el: '#data-products',
        data: {
            products: [
            {
                name: 'PLUTO',
                description: 'Contains over seventy tax lot, building, and geographic/political/administrative characteristics for NYC lots. \
                MapPLUTO is a combination of these attributes with the DOF Digital Tax Map, and is designed for GIS users.',
                businessowner: [edm],
                productcycle: 'Monthly',
                stability: stable,
                geometry: 'polygon',
                repo: 'https://github.com/NYCPlanning/db-pluto',
                link: '#/products/pluto'
            },
            {
                name: 'COLP',
                description: 'City Owned and Leased Properties: Contains property-level information about use, owning/leasing agency, location, and tenent agreements. Built from the DCAS Integrated Property Information System',
                businessowner: [edm, dcas],
                productcycle: 'NA',
                stability: developing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-colp',
                link: '#/products/colp'
            },
            {
                name: 'Facilities Database',
                description: 'Location and characteristics and categorization of more than 35,000 public facilities in NYC. This data is a standardized aggregation of other public datasets.',
                businessowner: [edm, cp],
                productcycle: 'Quarterly',
                stability: enhancing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-facilities',
                link: '#/products/facilities'
            },
            {
                name: 'Developments Database',
                description: 'Contains information about new building, demolitions, and alterations of buildings occuring since the 2010 Census. The purpose of this dataset is to capture development and residential growth over time. The primary input for this dataset is DOB jobs and occupancy data.',
                businessowner: [edm, hed, cp],
                productcycle: 'Bianually',
                stability: enhancing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-developments',
                link: '#/products/developments'
            },
            {
                name: 'Zoning Tax Lot Database',
                description: 'The database includes the zoning designations and zoning map associated with a specific tax block and lot.',
                businessowner: [edm],
                productcycle: 'Monthly',
                stability: stable,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-zoningtaxlots',
                link: '#/products/ztl'
            },
            {
                name: 'Capital Projects Database',
                description: 'The database captures key data points on potential, planned, and ongoing capital projects sponsored or managed by a capital agency in and around NYC',
                businessowner: [edm, cp],
                productcycle: 'Monthly',
                stability: stable,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-cpdb',
                link: '#/products/cpdb'
            },
            {
                name: 'Community Board Budget Requests',
                description: 'It is based on requests for future capital or expense projects submitted by each of NYC\'s 59 Community Boards. We \
                adds value to the submitted budget requests by creating geometries where possible for requested projects, \
                in the effort to map as many budget requests as possible.',
                businessowner: [edm, plancoord],
                productcycle: 'Bianually',
                stability: stable,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-cbbt',
                link: '#/products/cbbr'
            },
            {
                name: 'Population Fact Finder',
                description: 'Population FactFinder allows you to easily define study areas within New York City and examine detailed population profiles showing critical demographic, social, economic, and housing statistics, and how these statistics have changed over time.',
                businessowner: [edm, pop],
                productcycle: 'Yearly',
                stability: stable,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-acs',
                link: '#/products/acs'
            },
            {
                name: 'Geographic Research Quality Checks',
                description: 'This is a test suite we developed using Geosupport to help the Geographic research team to conduct data QAQC',
                businessowner: [edm],
                productcycle: 'Quaterly',
                stability: developing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-gru-qaqc',
                link: '#/products/gru-qaqc'
            }
        ]}
    })
</script>
