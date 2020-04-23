<h1 style="font-size:2rem">Products Overview</h1>

<div id="data-products">
    <div v-for="product in products" :key="product.name" class="product box-shadow">
        <a :href="product.link" class="name">
            <span class="product-name">{{ product.name }}</span>
        </a>
        <a :href="product.repo">
             <i class="fab fa-github fa-lg" style="color:#212326; margin: 0 0 2px 0;"></i>
        </a>
        <div>
            <span 
                v-bind:style="{background: product.stability.color}" class="label"
            >
                {{ product.stability.name }}
            </span>
            <span
                v-for="owner in product.businessowner"
                :key="product.businessowner"
                v-bind:style="{background: owner.color}"
                class="label"
            >
                {{ owner.name }}
            </span>
        </div>
        <p class="description">
            {{ product.description }}
        </p>
    </div>
</div>

> <span class="label" style="background:#00ae00">stable</span>: These products are routinely updated. Code changes and enhancements do not happen with every release, and instead occur in scheduled sprints. Users can expect version-to-version schemas to remain consistent. Updates of these data products are largely automated and transfered to the business owner.  
<span class="label" style="background:#443aff">in development</span>: These datasets are currently being developed. They have not settled into a routine production schedule yet, and may experience major overhauls between versions.  
<span class="label" style="background:#ed1294">frequent enhancement</span>: While these products get produced regularly, few updates occur without hands-on tweaking of the code. The production of these datasets are still closely controlled by data engineering.  

<script>
    var edm = {name:'DCP EDM', color:'#e17e22'}
    var hed = {name:'DCP HED', color:'#3870ff'}
    var dcas = {name:'DCAS', color:'#13ad72'}
    var stable = {name:'stable', color:'#00ae00'}
    var developing = {name:'in development', color:'#443aff'}
    var enhancing = {name:'frequent enhancement', color:'#ed1294'}
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
                link: '#/_content/pluto'
            },
            {
                name: 'COLP',
                description: 'City Owned and Leased Properties: Contains property-level information about use, owning/leasing agency, location, and tenent agreements. Built from the DCAS Integrated Property Information System',
                businessowner: [edm, dcas],
                productcycle: 'NA',
                stability: developing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-colp',
                link: '#/_content/colp'
            },
            {
                name: 'Facilities Database',
                description: 'Location and characteristics and categorization of more than 35,000 public facilities in NYC. This data is a standardized aggregation of other public datasets.',
                businessowner: [edm],
                productcycle: 'NA',
                stability: enhancing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-facilities',
                link: '#/_content/facilities'
            },
            {
                name: 'Developments Database',
                description: 'Contains information about new building, demolitions, and alterations of buildings occuring since the 2010 Census. The purpose of this dataset is to capture development and residential growth over time. The primary input for this dataset is DOB jobs and occupancy data.',
                businessowner: [edm, hed],
                productcycle: 'NA',
                stability: enhancing,
                geometry: 'point',
                repo: 'https://github.com/NYCPlanning/db-facilities',
                link: '#/_content/facilities'
            }
        ]}
    })
</script>
