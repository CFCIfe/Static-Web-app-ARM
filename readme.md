# Deploying Azure Static Web App using ARM Templates

[Azure Static web Apps](https://learn.microsoft.com/en-us/azure/static-web-apps/) allows you to build modern web applications that automatically publish to the web as your code changes.

---
&nbsp;

The steps were culled from [Here](https://learn.microsoft.com/en-us/azure/static-web-apps/publish-azure-resource-manager?tabs=azure-cli)

&nbsp;

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