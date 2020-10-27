Validate Move Resources - Powershell Azure API Wrapper
======================================================

            

Very powerfull Powershell function which is meant to levearage the Azure API in order to send the query to the backend Azure Resource Manager(ARM) with the specifically constructed JSON body, which contains all resource IDs from the source resource group
 and the target resource group.


ARM will send back format response which will tell you if the resources can be moved, or there are identified dependencies.


Function is based on 'https://docs.microsoft.com/en-us/rest/api/resources/resources/validatemoveresources' 


It's an resolution to the GitHub thread - 'https://github.com/MicrosoftDocs/azure-docs/issues/9349'


There is a helper function at the beginning which will retrieve the token for the service principal.


Prerequsities: Azure Service Principal which has appropriate rights across resource groups.


**EXAMPLE:**


 


$ApplicationId = '1234-1234-1234-1234-1234'


$ApplicationPassword = Convertto-SecureString -String '1234-1234-1234-1234-1234' -AsPlainText -Force
Get-AzResourceMoveValidation -ApplicationId $ApplicationId -ApplicationPassword $ApplicationPassword -SourceResourceGroup nemanjajovic-rg -TargetResourceGroup testrg
StatusCode        : 202
StatusDescription : Accepted
Content           : {}
RawContent        : HTTP/1.1 202 Accepted
                    Pragma: no-cache
                    Retry-After: 15
                    x-ms-ratelimit-remaining-subscription-writes: 1199
                    x-ms-request-id: c50079b7-fc04-4baa-9212-ada40ef20f1a
                    x-ms-correlation-request-id: c50079...
Headers           : {[Pragma, no-cache], [Retry-After, 15], [x-ms-ratelimit-remaining-subscription-writes, 1199], [x-ms-request-id,                    c50079b7-fc04-4baa-9212-ada40ef20f1a]...}

RawContentLength  : 0

Get-AzResourceMoveValidation : {'error':{'code':'ResourceMoveNotSupported','message':'Resource move is not supported for resource types 'Microsoft.Web/hostingEnvironments'.'}}At line:1 char:1+ Get-AzResourceMoveValidation -ApplicationId $spid -ApplicationPasswor
 ...+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException,Get-AzResourceMoveValidation

 





        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
