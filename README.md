# azure-resume
Azure Hosted Resume

## First steps

- Frontend folder contains the website.
- main.js contains visitor counter code.
- Added info for static website. 

## CosmoDB Setup

- Configure azure CosmoDB.
- SQL was not an option so I chose NOSQL.
- Issue with EastUS & WestUS availability zones so I picked Central US.
- Issue with using the following code:
```
{
    "id": "1"
    "count" : 0
}
```
- Instead, need to use for NoSQL which is:

```
{
    "id": "1",
    "totalCount": 0
}
```

## Azure Function Setup

- Instal Azure Functions Tools into VSCode
- Create project for Functions
- Selected parameters to connect to api
- Tested successfully 
```
This HTTP triggered function executed successfully. Pass a name in the query string or in the request body for a personalized response.
```
- Reviewed documentation to connect CosmoDB

https://learn.microsoft.com/en-us/azure/azure-functions/functions-bindings-cosmosdb-v2?tabs=isolated-process%2Cextensionv4&pivots=programming-language-csharp

- Need to install the NuGet Functions into the API folder

```
dotnet add package Microsoft.Azure.Functions.Worker.Extensions.CosmosDB --version 4.9.0
```
- Added Key Bindings via Azure CosmoDB.
- Ensure the string is what is being pasted for the Key. 
- Created Counter.cs
    - added Json properties to tie into CosmoDB, ensure they are the same name as in CosmoDB:

    ```
    "id" and "totalCounter"
    ```

- Issue with names in GetResumeCounter:
- Used the following link, ensure you are using new updated parameters
for extension 4.x in in-proccess model. 

https://learn.microsoft.com/en-us/azure/azure-functions/functions-bindings-cosmosdb-v2-trigger?tabs=python-v2%2Cin-process%2Cextensionv4%2Cnodejs-v4&pivots=programming-language-csharp

