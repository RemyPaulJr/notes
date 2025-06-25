### Low level Architecture:

![[Azure-Databricks-Earthquake.png]]
### Step 1: Create Azure account and setup Azure Databricks Workspace

First, we create a free account in Microsoft Azure.

Then, we go to the Azure Databricks service and create a new Azure Databricks workspace.

![[Pasted image 20250615130106.png]]

We have to use the Azure subscription for this service.
And we will add this to a Resource Group, by creating a new resource group.
- This is a grouping of resources or services/subscriptions, this will make it easy to delete an entire group to not incur costs.
But this also allows us to use RBAC (Role based access Control) through IAM (Identity and Access Management).
- This allows us to assign specific access to not only our Storage Account in Azure that we will use, but to our Databricks Service as well.
- This is an industry best practice because you can have a group of users say Developers, who have read and write access to the Services that are needed for their team. Allowing a central place to manage this access and who has this access.

We will use the premium pricing tier to take advantage of RBAC.

Now we run the deployment and we will see a resource get spun up.

Databricks using distributed computing.

This is important for processing large amounts of data. As databricks will distribute the load of tasks to many different computers, to complete a given task more efficiently in parallel with each other. To help visualize this:

![[Pasted image 20250615132150.png]]

Databricks uses it's own resource group made up of resources to handle this compute in the background.

Let's move on to Step 2 while this is being deployed.

### Step 2: Create Storage Account

Search for the Storage Account Service.

Choose the same subscription and resource group.

For the storage account name this has to be globally unique, so I used a password generate to give me lowercase characters, and numbers to use.

For the primary service choose Azure Blob Storage or Azure Data Lake Storage, this will aide in the creation process of this account since we are using Azure Data Lake Storage, but does not limit this account to only these services.

For redundancy we will use Locally-redundant storage (LRS). Since this is a personal project there's no need for higher level redundancies but it's still important to understand the other options as they are used in enterprise environments.

Locally-redundant storage (LRS) - Data is stored in one datacenter in one geo location, in one zone, with mutiple copies in a single datacenter. Lowest level of redundancy as if the datacenter fails we have no failover options.

Geo-redundant storage (GRS) - used in multiple regions, with multiple copies in the same data center. This means if the physical hardware holding our data is damaged then there are backups in that datacenter but if the data center itself is damaged we will have to failover to the next region.

Zone-redundant storage (ZRS) - used in one region, but in multiple availability zones. This means if a datacenter is compromised then we can failover to another zone in that region. but if there's a catostrophe in this geo location then we could possibly lose all our data.

Geo-Zone-Redundant Storage (GZRS) - this is a combination of the previous two. So we have our data in multiple geo locations and multiple zones. this is the highest level of redundancy and used for critical data.

![[Pasted image 20250615135420.png]]

Click next, and check the box for enabling Hierarchel namespace.
This will allow us to use this for a Data Lake Storage, a Data Lake Storage being a place where we can store unstructured, structured, or any structure of data in a single place.

Then create. 

Once done we can go to Data Storage on the left pane, and go to containers.
Here we can create our 3 containers based off the architecture we are going with (Mediallion Architecture).
Create 3 containers: bronze, silver, gold

