# projects
Projects I've either worked on, done research on, or just had fun and would like to share what I've learnt

- Power Virtual Agent (waiting for Import/Export to be fully supported)
Created a Power Virtual Agent to help explain the usage and application of UBL within a company

- Search Frameworks
Some examples and tests performed with different Search frameworks in order to create a solution by crawling data and presenting this in a nice interface. Analyzed: SolR, ElasticSearch, MongoDb Atlas, Azure Search. As the project had no limitation where the data was stored, Microsoft Cognitive Search is the chosen solution. The feature to create a website with search page as a demo from an indexer was very helpfull.

- UI Frameworks
In order to create rapid prototypes, experiments have been done to create a simple user-authorized front-end. The following frameworks have been reviewed: Power Apps Portal, Power Apps Canvas, Blazor, DotNetify.

- IAC
In order to create a re-usable Infrastructure as code multi-cloud, we are for once not starting with ARM, but are starting with alternative frameworks. We are now looking into Pulumi and are trying to create a concept using Automapper to support multi cloud IaC. We found that the functionality provided by TerraForm does have the uniform 'syntax' advantage, but  is still limited to solve the problem to understand/know the specific cloud resources/naming conventions. Although Pulumi has the same disadvantage, as it's code, there are a lot of ways to overcome this.

Lesson #1: In order to prevent the creation of resources with HEX codes (used for versioning), all code required overriding the Name property with arguments;

        // Create an Azure Resource Group
        var azureGroup = new Pulumi.Azure.Core.ResourceGroup("azureGroup", new ResourceGroupArgs
        {
            Name = "azureIAC"
        });

        // Create an Azure Storage Account
        Account account = new Account("storage", new AccountArgs
        {
            ResourceGroupName = azureGroup.Name,
            AccountReplicationType = "LRS",
            AccountTier = "Standard",
            Name = "storageinthezone",
            Location = "westeurope"
        });

