# Azure Functions
## Text Summarization using AI Cognitive Language Service

This sample shows how to take text documents as a input via BlobTrigger, does Text Summarization processing using the AI Congnitive Language service, and then outputs to another text document using BlobOutput binding.  

## Run on your local environment

### Pre-reqs
1) .NET 7 SDK
2) Functions Core Tools
3) Install and run Azurite, the easiest way is using a Docker container or the support built into Visual Studio:
`docker run -d -p 10000:10000 -p 10001:10001 -p 10002:10002 mcr.microsoft.com/azure-storage/azurite`
4) Once you have your Azure subscription, [create a Language resource](https://portal.azure.com/#create/Microsoft.CognitiveServicesTextAnalytics) in the Azure portal to get your key and endpoint. After it deploys, click Go to resource.
You will need the key and endpoint from the resource you create to connect your application to the API. You'll need to store the key and endpoint into the Env Vars or User Secrets code in a next step the quickstart.
You can use the free pricing tier (Free F0) to try the service, and upgrade later to a paid tier for production.
5) Export these secrets as Env Vars using values from Step 3.

Mac/Linux
```bash
export AI_URL= *Paste from step 3*
export AI_SECRET= *Paste from step 3*
```

Windows

Search for Environment Variables in Settings, create new System Variables similarly to [these instructions](https://docs.oracle.com/en/database/oracle/machine-learning/oml4r/1.5.1/oread/creating-and-modifying-environment-variables-on-windows.html#GUID-DD6F9982-60D5-48F6-8270-A27EC53807D0):

| Variable | Value |
| -------- | ----- |
| AI_URL | *Paste from step 3* |
| AI_SECRET | *Paste from step 3* |

Close all Visual Studio 2022 instances.  You may need to log out and log back into Windows for these to take after closing Visual Studio.  

### Using Visual Studio
1) Open `text_summarization.sln` using Visual Studio 2022 or later.
2) Press Run/F5 to run in the debugger
3) Open Storage Explorer, Storage Accounts -> Emulator -> Blob Containers -> and create a container `test-samples-trigger` if it does not already exists
4) Copy any .txt document file with text into the `test-samples-trigger` container

You will see AI analysis happen in the Terminal standard out.  The analysis will be saved in a .txt file in the `` blob container.

### Using Functions CLI
1) Open a new terminal and do the following:

```bash
cd text_summarize
dotnet build
func start
```
2) Open Storage Explorer, Storage Accounts -> Emulator -> Blob Containers -> and create a container `test-samples-trigger` if it does not already exists
3) Copy any .txt document file with text into the `test-samples-trigger` container

You will see AI analysis happen in the Terminal standard out.  The analysis will be saved in a .txt file in the `test-samples-output` blob container.