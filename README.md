# sql-vm-dcr


## Deployment with PowerShell
The deployment creates a new resource group, asks the user for the SQL Server admin password, and then creates resources to test custom performance counters of an Azure SQL VM.

``` PowerShell
Connect-AzAccount

$resourceGroupName = "rg-sqlvm"
$location = "westeurope"

New-AzResourceGroup -Name $resourceGroupName -Location $location

$adminPassword = Read-Host "Enter the password for the SQL Server admin account" -AsSecureString
New-AzResourceGroupDeployment -Name sqldeployment -ResourceGroupName $resourceGroupName -TemplateFile ./main.bicep -TemplateParameterFile ./main.parameters.json -location $location -existingVnetResourceGroup $resourceGroupName -adminPassword $adminPassword
```

The bicep script creates the following resources.
![bicepVisualizer](images/bicepVisualizer.png)

## Testing the DCR

![law](images/law.png)