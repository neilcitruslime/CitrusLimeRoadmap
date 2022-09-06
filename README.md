# CitrusLime Technical Roadmap
Citrus-Lime High Level Development Goals

# High Level Stategy

To succeed in our industry the Cloud based tech industry, ultimately the first company to deliver functionality to a specific vertical market wins. Pace is vital in all things. That said the utterly wild unstructured approach of the past creates software which is unmanagable and does not scale. A balance is required. 

We want to create software which is simple, easy to understand and performs well. Performance (speed) should always be analysed on areas of the system which see high user throughput, this makes the product popular with customers and leads to less infrastructure problems with servers slowing down or crashing. Code which performs well is essential. 

DRY (Do Not Repeat Yourself) code is extremely important to us. Single responsiblity and dependancy inversion should flow thru all our new software. Dependancy Inversion (thru dependancy injections) forces software to be decoupled which is something Citrus-Lime have subscribed to. 

Key business logic should be covered by automated tests. For example posting a transaction in Cloud POS should have full test coverage both Unit and Integration, as should creating an ecommerce transaction or calculating pricing. 

# High Level Goals

To move to a Cloud Native approach, with infrastructure deployed as code and managed within the Development Team. 

Work to ensure all applications and migrated to .Net (what was once called Core) this allows applications to be containerised (placed in Docker images) and run on low cost Linux servers.

Ensure that all configuration is managed via Git rather in configuration files stored with the application which are not subject to change control. 

To fully automate all software deployments to ensure that the software which is in the Release branch can be gareneteed to be in production. Additional steps maybe required to control release timing for some products. 

Applications will have no local 'state' - e.g. nothing which is part of the web deployments which changes is stored on the local file system. For example Cloud POS stores logo files within the application directory in a sub folder, ecommerce stores images in a folder call /images. This storage should be abstracted away from the application local. 

# Roadmap Ecommerce
The core ecommerce product has for many years been neglected and starved of investment. This been a logical and required decision, Customer Rewards, Cloud MT and a SIM product fit for international markets and decoupled from the Citrus-Lime database required resources to be allocated elsewhere and have proved a great success. Cloud MT, Cloud POS and Rewards allowed the company to embraced a move from .Net Framework a legacy product which is rarely updated to a modern platform using .Net (formly Core) a platform with an exciting future. The cost of this however has been that ecommerce functionality has been extended 'hacked in' and this has resulted in an unstructured product which needs overhaul. 

The ecommerce teams focus amongst all the exciting development oppertuntities which exist must be improving the core product. 

Vision
A fully .Net (formly Core) application which is deployed via Containers (so all content and customer settings are abstracted out of configuration files).

The front end in a mixture of Razor pages and Vue.Js. 
The checkout via Vue.Js & WebApi - with fully test coverage and with each stage decoupled. 
 
 # The Tasks
All ecommerce team product and microservice releases to be fully automated. 

Overhaul F&F to use C# via .Net (formly Core) and EF. 
    Customer Benefits & New Functionality
        The caching must be transparent to the end user and our customer. For example prices and stock levels most update on F&F pages within minutes. 

        The want to greatly improve performance this leads to more sales on mobile phones, no slow downs when sites are busy and high Google rankings both thru natural search and Google Adverts.

        We want to allow per store "instock" filtering.

    Citrus-Lime Benfits & New Functionality
        Removal of old and duplicated unsupportable and complex code. 
        Running C# and .Net (formly Core).
        We want to seperate the core query which shall remain uncached, but pluck properties (e.g. price, stock information and images/descriptions) for cached data. 

        NOTE We will use output cache on product and F&F pages with short cache times to prevent 1,000 users running the same DB query simultanously. 



