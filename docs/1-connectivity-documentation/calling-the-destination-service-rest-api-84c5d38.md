<!-- loio84c5d38ce91a45a495bae7f9fbe5b0ed -->

# Calling the Destination Service REST API

Prerequisites and steps to get access to the Destination service REST API.



<a name="loio84c5d38ce91a45a495bae7f9fbe5b0ed__section_cpq_jyb_zxb"/>

## Prerequisites

To call the Destination service REST API, you must have a Destination service instance inside your subaccount.

If you:

-   **don't have** such instance, follow the next step to get it up and running.
-   **have** such instance, you can skip the next step and go to [Get Credentials](calling-the-destination-service-rest-api-84c5d38.md#loio84c5d38ce91a45a495bae7f9fbe5b0ed__credentials).



<a name="loio84c5d38ce91a45a495bae7f9fbe5b0ed__section_nzm_jyb_zxb"/>

## 1. Set up a Destination Service Instance for your Subaccount

To create a Destination service instance inside your subaccount, see [Creating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-instances?version=Cloud) about creating service instances in the **BTP cockpit**, or from the **Cloud Foundry CLI**.

> ### Note:  
> When creating a Destination service instance, you can refer to the following yaml segment for the basic information of the instance.


<table>
<tr>
<th valign="top">

Basic information for the Destination service instance

</th>
</tr>
<tr>
<td valign="top">

-   *Plan*: lite

    Currently, the Destination service offers only this plan.

-   *Runtime Environment*: Cloud Foundry

    Cloud Foundry must be enabled for your subaccount.

-   *Space*: <space\_name\>

    Choose the space in which the Destination service instance will reside.

-   *Instance Name*: <instance\_name\>

    Enter a name of your choice here for the instance.




</td>
</tr>
</table>

> ### Note:  
> The yaml segment above contains Cloud Foundry-specific information. Other configurations are possible, for instance when running on Kyma. The important part is to deploy your instance in the target runtime and get the service key / binding credentials to access the Destination service.



<a name="loio84c5d38ce91a45a495bae7f9fbe5b0ed__credentials"/>

## 2. Get Credentials

To access the Destination service REST API, you need an **access token**. To generate this token, you need credentials contained in a **service key** of the Destination service instance.

If you don't have any service keys in your Destination service instance, see [Creating Service Keys](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-keys?version=Cloud) about creating a service key for an instance in the **BTP cockpit** or from the **Cloud Foundry CLI**.

Once you have a service key for your Destination service instance, you open it and extract the following information:


<table>
<tr>
<th valign="top">

Information to extract from the service key

</th>
</tr>
<tr>
<td valign="top">

-   *clientid*: "<value\_to\_extract\>"

    The client ID that will be used for authentication in the next step.

-   *clientsecret*: "<value\_to\_extract\>"

    The client secret that will be used for authentication in the next step.

-   *url*: "<value\_to\_extract\>"

    The authentication endpoint from which you get an access token for the Destination service.

-   *uri*: "<value\_to\_extract\>"

    The URL of the Destination service.




</td>
</tr>
</table>

> ### Note:  
> For demonstration purposes, we are using the `clientid` and `clientsecret` for authentication. We recommend that you use mTLS which uses an X.509 client certificate because it is a more secure way of authenticating.



<a name="loio84c5d38ce91a45a495bae7f9fbe5b0ed__section_k2q_3yb_zxb"/>

## 3. Get an AccessToken

In this step, you will get an **access token** from XSUAA which you can then use to authenticate towards the Destination service REST API. For this step, you must use the values you extracted for **clientid**, clientsecret and **url** from the previous step.

Here is an example call using **curl**:

> ### Sample Code:  
> ```
> curl -X POST \
>         "<url>/oauth/token" \
>         -H "Content-Type: application/x-www-form-urlencoded" \
>         -d "grant_type=client_credentials" --data-urlencode 'client_id=<client_id>' --data-urlencode 'client_secret=<client_secret>'
> ```

where:

-   `<url>` is the value of the URL from the previous step.
-   `<client_id>` is the value of *clientid* from the previous step.
-   `<client_secret>` is the value of *clientsecret* from the previous step.

The access token is shown in the **access\_token** key in the response JSON. Make sure you save it because you will need it in the next step.



<a name="loio84c5d38ce91a45a495bae7f9fbe5b0ed__section_umf_3yb_zxb"/>

## 4. Call the Destination Service REST API

Now that you have an access token for the Destination service, you can call one of the Destination service REST API endpoints. To get the full list of available endpoints in the Destination service REST API, see the [Destination Service REST API reference](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/Find_a_Destination) on SAP Business Accelerator Hub.

Here is an example of the call using **curl**:

> ### Sample Code:  
> ```
> curl -X GET \
>         "<uri>/destination-configuration/v1/<endpoint>" \
>         -H "Authorization: Bearer <access_token>"
> ```

where:

-   `<uri>` is the value of *uri* from [Get Credentials](calling-the-destination-service-rest-api-84c5d38.md#loio84c5d38ce91a45a495bae7f9fbe5b0ed__credentials).
-   `<endpoint>` is the endpoint of the Destination service REST API that you want to call.
-   `<access_token>` is the access token you saved from the previous section.

If, for example, you want to make a GET call towards the */subaccountDestinations* endpoint, the call would look like:

> ### Sample Code:  
> ```
> curl -X GET \
>         "<uri>/destination-configuration/v1/subaccountDestinations" \
>         -H "Authorization: Bearer <access_token>"
> ```

**Example: Response from the Destination service**

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

