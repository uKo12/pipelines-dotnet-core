# Sample .NET Core app for Endava Azure DevOps Challenge

Simple .NET Core app deployed with Azure DevOps. 

- Project name: uKo-Core

- Pipeline with two stages - DEV -> PROD. PROD is with implemented Pre-deployment approval.

- azure-pipelines.yml:

```
trigger:
- master

pool:
  vmImage: 'Ubuntu-16.04'
 
steps:
- task: DotNetCoreCLI@2
  displayName: Build
  inputs:
    command: build
    projects: '**/*.csproj'
    arguments: '--configuration Release'

- task: DotNetCoreCLI@2
  inputs:
    command: publish
    publishWebProjects: True
    arguments: '--output $(Build.ArtifactStagingDirectory)'
    zipAfterPublish: True

- task: PublishBuildArtifacts@1
  displayName: 'Publish artifacts: drop'
```

- Made some modification in the code (text change).

- Deployed on Azure App services on Windows. PROD and DEV app services.

- Manual test created in the DevOps portal for testing the access to the web page - https://ukowincore.azurewebsites.net.
 
- Created Load test in the Azure DevOps.

- Monitoring (Alert rule) implemented in the Application insights for the PROD WebApp "ukowincore" monitoring for failed HTTP requests.

- App service URL:

  - DEV: https://ukowincore-dev.azurewebsites.net
  - PROD: https://ukowincore.azurewebsites.net

- Credentials for the Azure portal and Azure DevOps portal will be send in the email.

