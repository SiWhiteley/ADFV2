# ADFV2
### Dynamic Data Copy Piplines

One of the core demos within this session is the creation of a dynamic data loading pipeline. The json objects in this folder describe the core mechanisms for how it works.

There are five objects contained, two linked services, two datasets and one pipeline. You will need to amend the Linked Services for your own environment

### SandboxADLS
This is the linked service for your data lake - it requires connections to be set up. It is easier to create a new linked service and allow it to automatically acquire parameters from your subscription

### SQLDBAdventureWorks
This is the linked service for the source database in this example. Again, it may be easier to recreate this object

### DynamicDB
This dataset connects to the AdventureWorks copy on our SQLDBAdventureWorks linked service (or any other Azure SQLDB). It has been set to expect a parameter and to use this parameter to determine which table to source it's data from. No schema has been defined, as this is dynamic

### DataLakeStore
The Lake Dataset again expects a parameter, and this time uses it to form part of the path. This means that each different table loaded will automatically go into it's own separate folder. We could enhance this further by including an element of date parsing to separate files by their load date/time.

### DynamicCopy
Finally we have our pipeline, which contains a single activity. The pipeline expects parameters, which it passes to the activity and, in turn, each of the source and sink datasets.
