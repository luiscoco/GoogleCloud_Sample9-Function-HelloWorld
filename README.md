# Create and deploy an HTTP Cloud Function with .NET

https://cloud.google.com/functions/docs/create-deploy-http-dotnet?hl=es-419

This example function outputs the greeting "Hello World!". Create a file called Function.cs with the contents below:
```csharp
using Google.Cloud.Functions.Framework;
using Microsoft.AspNetCore.Http;
using System.Threading.Tasks;

namespace HelloWorld;

public class Function : IHttpFunction
{
    public async Task HandleAsync(HttpContext context)
    {
        await context.Response.WriteAsync("Hello World!");
    }
}
```

## Deploying the function
Navigate inside the project path (where the project file is located "HelloWorld.csproj"):

C:\Google Cloud .Net\dotnet-docs-samples-main\functions\helloworld\HelloWorld>gcloud functions deploy my-first-function --entry-point HelloWorld.Function --runtime dotnet6 --trigger-http --allow-unauthenticated --project PROJECT-ID

Run the command:
```
gcloud functions deploy my-first-function --entry-point HelloWorld.Function --runtime dotnet6 --trigger-http --allow-unauthenticated --project PROJECT-ID
```
IMPORTANT! Do not forget to replace the PROJECT-ID for your GoogleCloud projec-id:

## Testing the deployed function

When the function finishes deploying, take note of the httpsTrigger.url property or find it using the following command:
```
gcloud functions describe my-first-function
```

It should look like this:
https://GCP_REGION-PROJECT_ID.cloudfunctions.net/my-first-function

Visit this URL in your browser. You should see a Hello World! message.

### Note: 
You can also find this URL in Google Cloud console. Go to the Cloud Functions Overview page, and click the name of your function to open its Function details page. Open the TRIGGER tab to see your function's URL.

