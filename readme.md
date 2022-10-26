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

3. 