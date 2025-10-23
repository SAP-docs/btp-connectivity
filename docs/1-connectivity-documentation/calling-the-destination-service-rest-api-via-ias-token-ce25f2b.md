<!-- loioce25f2be9c3640ca832d73e31e7917fc -->

# Calling the Destination Service REST API via IAS Token

Find a step-by-step procedure to use an IAS token for calling available Destination service REST API endpoints.



## Prerequisites

To call the Destination service REST API using an IAS token, you must have the following set up:

-   [Configured Trust](https://help.sap.com/docs/btp/sap-business-technology-platform/establish-trust-and-federation-between-uaa-and-identity-authentication?version=Cloud) between *SAP Authorization and Trust Management service* and *SAP Cloud Identity Services*
-   A Destination service instance inside your subaccount
-   An Identity service instance inside your subaccount



<a name="loioce25f2be9c3640ca832d73e31e7917fc__instance"/>

## Set Up a Destination Service Instance for your Subaccount

To create a Destination service instance inside your subaccount, follow this documentation about creating service instances through the BTP cockpit or from the CF CLI: [Creating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-instances?version=Cloud).

> ### Note:  
> When creating a Destination service instance, you can refer to the following *yaml* segment for the basic information of the instance.


<table>
<tr>
<th valign="top">

Basic Information for the Destination Service instance

</th>
</tr>
<tr>
<td valign="top">

-   Plan: *lite* 

    \# Currently, the Destination service offers only this plan.

-   Runtime Environment: *Cloud Foundry* 

    \# You will need to have enabled Cloud Foundry for your subaccount.

-   Space: *<space\_name\>* 

    \# Choose the space in which the Destination service instance will reside in.

-   Instance Name: *<instance\_name\>* 

    \# Enter whatever name you want here for the instance.




</td>
</tr>
</table>



## Retrieving the Destination Service REST API Endpoint

The Destination service REST API endpoint can be retrieved from the credentials contained in a service key of the Destination Service instance. If you don't have any service keys in your Destination service instance, follow this BTP documentation about creating a service key for an instance from the BTP cockpit or through the CF CLI: [Creating Service Keys](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-keys?version=Cloud).

Once you have a service key for your Destination service instance, you need to open it and extract the following information:


<table>
<tr>
<th valign="top">

Information to Extract from the Service Key

</th>
</tr>
<tr>
<td valign="top">

-   uri: *"<value\_to\_extract\>"* 

    \# The URL of the Destination service




</td>
</tr>
</table>



## Set up a Cloud Identity Service Instance for your Subaccount

To create a Cloud Identity service instance inside your subaccount, follow this documentation about creating service instances through the BTP cockpit or from the CF CLI: [Creating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-instances?version=Cloud).

> ### Note:  
> When creating a Cloud Identity service instance, you must provide the following basic information as well as the parameters in the *config.json* input file.


<table>
<tr>
<th valign="top">

Basic Information for the Cloud Identity Service

</th>
</tr>
<tr>
<td valign="top">

-   Plan: *application* 

    \# Currently, the Cloud Identity service offers only this plan.

-   Runtime Environment: *Cloud Foundry* 

    \# You must have enabled Cloud Foundry for your subaccount.

-   Space: *<space\_name\>* 

    \# Choose the space in which the Cloud Identity service instance will reside in.

-   Instance Name: *<instance\_name\>* 

    \# Enter any name for the instance.




</td>
</tr>
</table>

**config.json \(Example\)**

> ### Sample Code:  
> ```
> {
>     "consumed-services":
>     [
>         {
>             "service-instance-name": "<destination-service-instance-name>"
>         }
>     ]
> }
> ```

where:

*<destination-service-instance-name\>* is the value of `instance_name` from step [Set Up a Destination Service Instance for your Subaccount](calling-the-destination-service-rest-api-via-ias-token-ce25f2b.md#loioce25f2be9c3640ca832d73e31e7917fc__instance).



## Getting the Credentials to Call the Destination Service REST API

To access the Destination service REST API, you need an access token. To generate such, you must get the credentials contained in a service key of the Cloud Identity service instance. If you don't have any service keys in your Cloud Identity service instance, follow this BTP documentation about creating a service key for an instance from the BTP cockpit or through the CF CLI: [Creating Service Keys](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-keys?version=Cloud).

> ### Note:  
> The IAS access token is issued through mTLS, so when you are creating the service key in your Cloud Identity service, you must provide the following *config.json*:
> 
> **X.509 Credential Type \(Example\)**
> 
> > ### Sample Code:  
> > ```
> > {
> >     "credential-type": "X509_GENERATED"
> > }
> > ```

Once you have a service key for your Cloud Identity service instance, you need to open it and extract the following information:


<table>
<tr>
<th valign="top">

Information to Extract from the Service Key

</th>
</tr>
<tr>
<td valign="top">

-   clientid: *"<value\_to\_extract\>"* 

    \# The client id which will be used for the authentication in the next step

-   certificate: *"<value\_to\_extract\>"* 

    \# The certificate which will be used for the authentication in the next step

-   key: *"<value\_to\_extract\>"* 

    \# The key which will be used for the authentication in the next step

-   url: *"<value\_to\_extract\>"* 

    \# The authentication endpoint from where an access token for the Cloud Identity service will be acquired




</td>
</tr>
</table>



<a name="loioce25f2be9c3640ca832d73e31e7917fc__acquire"/>

## Acquire an Access Token from IAS to Access the Destination Service REST API

In this step, we will acquire an access token from IAS which we can then use to successfully authenticate towards the Destination service REST API. For this step, you must use the values you extracted for `clientid`, `certificate`, `key`, and `url` from the previous step.

Here is an example call using curl:

**CURL Command to Acquire an Access Token for the Destination service** 

> ### Sample Code:  
> ```
> curl -X POST \
>         "<url>/oauth2/token" \
>         -H "Content-Type: application/x-www-form-urlencoded" \
>         -d "grant_type=client_credentials" --data-urlencode "client_id=<client_id>" --cert <certificate> --key <key>
> ```

where:

-   <url\> is the value of `url` from the previous step
-   <client\_id\> is the value of `clientid` from the previous step
-   <certificate\> is the value of `certificate` from the previous step
-   <key\> is the value of the `key` from the previous step

The token which you will be using for the next step is provided under the `access_token` key in the response JSON. Make sure you save it because we will need it in the next step.



<a name="loioce25f2be9c3640ca832d73e31e7917fc__section_i1p_qt5_bgc"/>

## Call the Destination Service REST API

Now that you have an access token for the Destination service, you can finally call one of the Destination service REST API endpoints. To see the full list of available endpoints in the Destination service REST API and their responses, see [Destination Service REST API reference](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/Find_a_Destination).

> ### Caution:  
> Authentication to the Destination service via IAS token requires in addition mTLS for accessing instance level [destinations](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/Destinations_on_Service_Instance_Subscription_Level), [destination fragments](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/Destination_Fragments_on_Service_Instance_Subscription_Level), and [certificates](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/Certificates_on_Service_Instance_Subscription_Level).
> 
> > ### Sample Code:  
> > ```
> > curl --cert <IAS service instance certificate> --key --cert <IAS service instance private key> -X GET \
> >         "<uri>/destination-configuration/v1/<endpoint>" \
> >         -H "Authorization: Bearer <access_token>"
> > ```

Here is an example of the call using curl:

**CURL Command for Calling the Destination Service** 

> ### Sample Code:  
> ```
> curl -X GET \
>         "<uri>/destination-configuration/v1/<endpoint>" \
>         -H "Authorization: Bearer <access_token>"
> ```

where:

-   <uri\> is the value of `uri` from [Getting the Credentials to Call the Destination Service](calling-the-destination-service-rest-api-via-ias-token-ce25f2b.md#loioce25f2be9c3640ca832d73e31e7917fc__credentials) 
-   <endpoint\> is the endpoint of the Destination service REST API which you want to call
-   <access\_token\> is the access token you saved from [Acquire an Access Token from IAS to Access the Destination Service REST API](calling-the-destination-service-rest-api-via-ias-token-ce25f2b.md#loioce25f2be9c3640ca832d73e31e7917fc__acquire) 

For a more concrete example, if you want to make a GET call towards the */subaccountDestinations* endpoint, the call would look like this:

**CURL Command for Calling the Destination Service** 

> ### Sample Code:  
> ```
> curl -X GET \
>         "<uri>/destination-configuration/v1/subaccountDestinations" \
>         -H "Authorization: Bearer <access_token>"
> ```

An example response from the Destination service would be:

> ### Sample Code:  
> ```
> [
>     {
>         "Name": "no-authentication-destination",
>         "Type": "HTTP",
>         "URL": "https://sap.com",
>         "Authentication": "NoAuthentication",
>         "ProxyType": "Internet"
>     },
>     {
>         "Name": "basic-authentication-destination",
>         "Type": "HTTP",
>         "URL": "https://sap.com",
>         "Authentication": "BasicAuthentication",
>         "ProxyType": "Internet",
>         "User": "my-user",
>         "Password": "my-password"
>     }
> ]
> ```

