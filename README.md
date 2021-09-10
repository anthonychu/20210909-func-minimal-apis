
## Run local

1. Create a local.settings.json file which overrides production settings in host.json:

    ```json
    {
        "IsEncrypted": false,
        "Values": {
            "AzureWebJobsStorage": "",
            "FUNCTIONS_WORKER_RUNTIME": "custom",
            "AzureFunctionsJobHost__customHandler__description__defaultExecutablePath": "dotnet",
            "AzureFunctionsJobHost__customHandler__description__workingDirectory": "minimalapp",
            "AzureFunctionsJobHost__customHandler__description__arguments__0": "run --urls=http://localhost:%FUNCTIONS_CUSTOMHANDLER_PORT%"
        }
    }
    ```

2. Run `func start`

## Deploy

1. Build app

    ```
    cd minimalapp
    dotnet publish -c Release -o ../minimalappbin --self-contained -r win-x64 -p:PublishReadyToRun=true -p:PublishSingleFile=true
    ```

1. Deploy to a Windows consumption app (tested from VS Code)