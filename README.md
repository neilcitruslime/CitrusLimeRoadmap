# CitrusLime Technical Road Map 
Citrus-Lime High Level Development & Infrastructure Goals

# High Level Strategy

To succeed in our industry the Cloud based tech industry, ultimately the first company to deliver functionality to a specific vertical market wins. Momentum is vital in all things. That said the utterly wild unstructured approach of the past creates software which is difficult to manage and scale. A balance is required. 

We want to create software which is simple, easy to understand and performs well. Performance (speed) should always be analyzed on areas of the system which see high user throughput, this makes the product popular with customers and leads to less infrastructure problems with servers slowing down or applications crashing as they are starved of resource. Code which performs well is essential. This also helps us keep our pricing low by requiring less infrastructure.

DRY (Do Not Repeat Yourself) code is extremely important to us. Single responsibility and dependency inversion should flow thru all our new software. Dependency Inversion (thru dependency injections) forces software to be decoupled which is something which is very important to me. 

Key business logic should be covered by automated tests. For example posting a transaction in Cloud POS should have full test coverage both Unit and Integration, as should creating an e-commerce transaction or calculating pricing. 

# High Level Goals

To move to a Cloud Native approach, with infrastructure deployed as code and managed within the Development Team within Git. 

Work to ensure all applications and migrated to .Net (what was once called Core) this allows applications to be containerized (placed in Docker images) and run on low cost Linux servers, it also encourages/forces the use of DI.

Ensure that all configuration is managed via Git and automatically deployed rather in configuration files stored with the application which are not subject to change control. (This will not apply to customer specific configuration stored within the E-commerce platform). 

To fully automate all software deployments to ensure that the software which is in the Release branch can be guaranteed to be in production. Additional steps maybe required to control release timing/approval for some products. 

Applications will have no local 'state' - e.g. nothing which is part of the web deployments which changes is stored on the local file system. For example Cloud POS stores logo files within the application directory in a sub folder, e-commerce stores images in a folder call /images. This storage should be abstracted away from the application local file system. 

# Cloud POS

The overhaul of Cloud POS business process and data access to .Net and EF is completed. 

##  New User Interface

We wish to implement a new user interface and server side Api layer. We will first migrate the POS, and then migrate the back office platform. 

* Customer Benefits & New Functionality
    * The functionality in Cloud POS is already the best available to a retailer in a Cloud based POS worldwide. The user interface is competitive with other POS products, but we want to create a 'best in class' user experience compared to other web applications outside of the POS space. 
    * The development is being conducted with a 'mobile first' approach, allowing a first class user experience on iPads. 
    * A user interface tasks will be targeted to be four times faster than they are today. This will lead to better user satisfaction and significant staff cost savings for store owners. 

* Citrus-Lime Benefits
    * The user of .Net allow us to deploy the POS and back office as separate containerized applications. This will allow us to cluster our deployments in a more interesting and agile manner. 
    * The move to .Net will allow the use of EF 7 which has significant performance improvements for database access.
    * Faster and more effective training & onboarding

##  Automated Deployment

We need to automate the deployment of of all Cloud POS team owned products.

## API Extensions

Other than this area extending the Cloud POS Api to allow customers to integrate line of business applications will be the only other priority. 

* Customer Benefits & New Functionality
    * Not dependant on Citrus-Lime to extend Cloud POS functionality and reporting so our resources are not a limiting factor on our customers ambitions.

* Citrus-Lime Benefits
    * Not dependant on Citrus-Lime to extend Cloud POS functionality and reporting.

## The Future

Once the user interface overhaul is completed we will extend both the product and API to allow support for multiple bin locations within each stock locations. We are working with a number of third parties on integrating enhanced picking software and scanner systems in the warehouse environment, we will not be implementing such devices/software natively. 

We will improve the despatching processes and workflow at the pack bench. 

We will integrate electronic purchase orders & new courier suppliers aggressively. 

# Roadmap Ecommerce

The core e-commerce product has for many years been neglected and starved of investment. This been a logical and required decision, Customer Rewards, Cloud MT and a SIM product fit for international markets and decoupled from the Citrus-Lime database required resources to be allocated elsewhere and have proved a great success. Cloud MT, Cloud POS and Rewards allowed the company to embraced a move from .Net Framework a legacy product which is rarely updated to a modern platform using .Net a platform with an exciting future. The cost of this however has been that e-commerce functionality has been extended 'hacked in' and this has resulted in an unstructured product which needs overhaul. 

The e-commerce teams focus amongst all the exciting development opportunities which exist must be improving the core product. 

Vision
A fully .Net application which is deployed via Containers (so all content and customer settings are abstracted out of configuration files).

The front end in a mixture of Razor pages and Vue.Js. 
The checkout via Vue.Js & WebApi - with fully test coverage and with each stage decoupled. 
 
 ##  Automated Deployment

All e-commerce team product and microservice releases to be fully automated. 

##  Overhaul F&F Server Side Code

Overhaul F&F to use C# via .Net and EF. From this approach revise the approach recently deployed to generate product pages. 
* Customer Benefits & New Functionality
    * The caching must be transparent to the end user and our customer. For example prices and stock levels most update on F&F pages within minutes. 

    * The want to greatly improve performance this leads to more sales on mobile phones, no slow downs when sites are busy and high Google rankings both thru natural search and Google Adverts.

    * We want to allow per store "instock" filtering.

* Citrus-Lime Benefits & New Functionality
    * Removal of old and duplicated unsupportable and complex code. 
    * Running C# and .Net.
    * We want to separate the core query which shall remain uncached, but pluck properties (e.g. price, stock information and images/descriptions) for cached data. 

NOTE We will use output cache on product and F&F pages with short cache times to prevent 1,000 users running the same DB query simultaneously. 

##  CMS Implementation & Decoupling Content from Site Deployment

We want to allow customers more control over their sites particularly in areas involving commercial promotion. 
We want to abstract customer content out of the deployment of the main application. 

* Customer Benefits & New Functionality
    * Control over stylesheets
    * A library of homepage templates which allow control over the homepage layout and content, this is an area Shopify excels and we should embrace a similar approach
    * Coupons will support options to display on matching product and F&F pages

* Citrus-Lime Benefits
    * Less customer frustration and internal resources used making minor changes to sites
    * The option to move design resource so it is focused on the 'platform' rather than making individual customer changes

## USA Specific or US Driven Developments

Support Quickbooks in our accounts integration. 
Support US Nexus tax on the frontend of the e-commerce site via an API integration (for example Stripe offer one).


## The Future

We want to replace the checkout making it easier to support (for example making it easier to add payment providers), this will be based on Vue.JS and .Net Web API. This will include overhauling the database functionality so they run via EF Services rather than the legacy database layer (for example orders, orderitems etc). This to my mind would largely leave only the Cart and discounting logic left in the .Net Framework project.

We will progress to move to a full Razor/Vue.Js driven approach which is entirely .Net native (No .Net Framework) this will allow the platform to be deployed in Containers. 

## Bits

Customer Rewards Reporting

