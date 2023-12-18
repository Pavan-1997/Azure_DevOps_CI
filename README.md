# Azure DevOps CI

1. Clone the Repo
   
```
git clone https://github.com/piyushsachdeva/Youtube_Clone.git
```

2. Go to Azure DevOps Portal

    Click on Create new project
    
    Give a Project name
    
    Click on Create


3. Now go to Repos in the project created

    Select  the Files -> Copy the "Push an existing repository from command line"
    
    Before doing that remove the origin using - 
```
git remote show origin
```
```
git remote remove origin 
```

4. Now go the portal.azure

    Go to App Services
    
    Click on Create -> Web App
    
    Give a Uniquie name to Name
    
    Publish - Code
    
    Runtime stack - Node 18 LTS
    
    Linus Plan - Create new -> Give name 
    
    Pricing plan - Premium v3 P0V3


4. Click on Next -> Review + create


5. Now go the Resource -> Access the Default domain it shows the default webpage


6. Now go to the dev.azure.com 

    Select Pipelines
    
    Create Pipeline 
    
    Go to Organization Settins -> Pipelines -> Settings -> Turn Off (Disable creation of classic build pipelines & Disable creation of classic release pipelines)
    
    Come back to above step
    
    Click on Use the classic editor 
    
    Go with defaults - once check Repo
    
    Select a template -> Click on Empty job
    
    Agent Specification - ubuntu-latest
    
    Click on Get sources -> Agent job 1 -> Click on + -> Search for npm and click on Add -> Select Command - install 
    
    Click on Get sources -> Agent job 1 -> Click on + -> Search for npm and click on Add -> Select Command - custom -> In Command and arguments - run build -> Chnage Display name - npm build
    
    Click on Get sources -> Agent job 1 -> Click on + -> Search for Publish build artifacts -> Path to publish - build
    
    Click on Get sources -> Agent job 1 -> Click on + -> Search for Azure App Service Settings -> Azure subscription -> Select the subscription -> App Service Type - Web App on Linux -> App Service name - From Step 4. -> Package or folder -       $(System.DefaultWorkingDirectory)/build -> Runtime Stack - 1.0 (STATICSITE|1.0)
    
    Verify and click on Save & queue -> Give a comment -> Click on Save and run


7. Now the Build pipeline executes successfully then go to the portal.azure.com

    Go to App Services -> Configuration -> Click on New applicaiton setting

    Name - `WEBSITE_DYNAMIC_CACHE`
    Value - `0`
    
    
    Go to App Services -> Configuration -> Click on New application setting
    
    Name - `WEBSITE_LOCAL_CACHE_OPTION`
    Value - `never`
    
    Click on Ok
    
    Click on Save -> Continue

    Enable the Deployment slot setting

    Enable the Deployment slot setting -> Click on Ok


8. Re-run the CI Pipeline



zufq6fkeks6pkvr2vx7pfqckhanyswjaynpx3va2jrkkhkgbw55a

Self-Hosted-Pavan

https://dev.azure.com/AzureDevOps-Pavan

./config.sh

./run.sh

tar zxvf
