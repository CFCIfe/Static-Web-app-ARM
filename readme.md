# Deploying Azure Static Web App using ARM Templates

[Azure Static web Apps](https://learn.microsoft.com/en-us/azure/static-web-apps/) allows you to build modern web applications that automatically publish to the web as your code changes.

---

The steps were culled from [here](https://learn.microsoft.com/en-us/azure/static-web-apps/publish-azure-resource-manager?tabs=azure-cli)


### Deployment
* These steps use [Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-az-ps)
&nbsp;
1. Clone the repo

```PowerShell
git clone https://github.com/CFCIfe/Static-Web-app-ARM 
```

2. Edit the Parameter Files

Navigate to `azuredeploy/azuredeploy.parameters.json` and change the values of `repositoryUrl` and `repositoryToken`.

3. Sign in to Azure

```PowerShell
Connect-AzAccount
```

4. Create a resource group

```PowerShell
$resourceGroupName = "myfirstswadeployRG"

New-AzResourceGroup `
  -Name $resourceGroupName `
  -Location "Central US"
```

5. Deploy the website.

```PowerShell
$templateFile = Read-Host -Prompt "Enter the template file path and file name"
$templateparameterFile = Read-Host -Prompt "Enter the template parameter file path and file name"

New-AzResourceGroupDeployment `
  -Name DeployLocalTemplate `
  -ResourceGroupName $resourceGroupName `
  -TemplateFile $templateFile `
  -TemplateParameterFile $templateparameterfile `
  -verbose
```

6. Clean up resources after test is done.

---

#### Other Resources related to Static Web App

- [Configure front-end frameworks](https://learn.microsoft.com/en-us/azure/static-web-apps/front-end-frameworks)

- [Enable Monitoring](https://learn.microsoft.com/en-us/azure/static-web-apps/monitor)

- [Troubleshoot Errors](https://learn.microsoft.com/en-us/azure/static-web-apps/troubleshooting)

---