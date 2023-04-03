## Get subscription Resource Details

This collections lets you use the Azure Rest API to pull details about all the resources in a subscription.

You need to create a Service Principal to authenticate the requests, log into the cloud powershell in the azure portal and run:

``` powershell
$subscription_id=$(Get-AzSubscription).id
az ad sp create-for-rbac --name "Postman" --scopes "/subscriptions/$subscription_id" --role reader --sdk-auth

```

You should get:

``` json
{
  "clientId": "66c8037f-7d78-4fce-ba46-1d2cfbf63ced",
  "clientSecret": "0Ok8Q~ylQy5tfhMgAwQMpFixIv5fyGkwKMCOAc8T",
  "subscriptionId": "e3f3c71a-d5bc-4f5a-a2c2-c9bec9b7d4e1",
  "tenantId": "e3ea8c52-835b-4fde-9643-33dbb44c294c",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}

```

You can then set the enviorment variables for clientId, clientSecret, subscriptionId and tenantId with these values.

You should be able to now run the Postman Collection. It stores the resource details to the env variable resourceDetails