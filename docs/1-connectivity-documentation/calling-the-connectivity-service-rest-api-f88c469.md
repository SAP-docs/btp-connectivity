<!-- loiof88c4698f46e405a8379918fef03460f -->

# Calling the Connectivity Service REST API

Learn how to call the Connectivity service REST API to read information about Cloud Connectors connected to your SAP BTP subaccount.



## Prerequisites

To enable your application for consuming the Connectivity service REST API, you must create a Connectivity service instance with service plan *api\_access* and bind it to the application.

For more information, see [Create and Bind a Connectivity Service Instance](create-and-bind-a-connectivity-service-instance-a2b88cf.md).



## Get an Access Token

The endpoints of the Connectivity service REST API are protected with OAuth access tokens issued by XSUAA. In order to obtain one, you need to extract the value of `token_service_url` from the binding information and call it using the binding credentials.

**Example: Obtaining an XSUAA access token**

*Request:*

> ### Sample Code:  
> ```
> POST <token_service_url>
> Accept: application/json
> Content-Type: application/x-www-form-urlencoded
>   
> client_id=<clientid>
> client_secret=<clientsecret>
> grant_type=client_credentials
> ```

*Response:*

> ### Sample Code:  
> ```
> {
>     "access_token" : "<JWT>",
>     "token_type" : "Bearer",
>     "expires_in" : 3600
> }
> ```

> ### Caution:  
> For demo purposes, we are using the *clientid* and *clientsecret* for authentication. We recommend that you use mTLS, which includes an X.509 client certificate, as a more secure way of authenticating.



## Call the Connectivity Service REST API

Once you have obtained an access token, you can call one of the Connectivity service's REST API endpoints. The `connectivity_service` object in the binding JSON contains API access properties such as the URL and supported paths.

For more information about the available endpoints, see *Connectivity service REST API reference*.

**Example: Calling the Cloud Connector info REST API endpoint**

*Request:*

> ### Sample Code:  
> ```
> GET <url><scc_info_path>
> Accept: application/json
> Authorization: Bearer <access_token>
> ```

*Response:*

> ### Sample Code:  
> ```
> [
>   {
>     "attributes": {
>       "connected_by": "admin@example.com",
>       "connected_since": "1762174293176",
>       "security_status": "{\"summary\":\"low_risk\",\"cpic_trace\":\"ok\",\"trust_store\":\"ok\",\"ciphers\":\"low_risk\",\"ui_certificate\":\"low_risk\",\"payload_trace\":\"ok\",\"authentication_type\":\"low_risk\",\"application_whitelist\":\"ok\"}",
>       "agent_version": "2.18.0",
>       "agent_type": "master",
>       "client_id": "123456789",
>       "exposed_systems": "[{\"protocol\":\"HTTP\",\"host\":\"virtualhost:1234\",\"description\":\"\",\"type\":\"nonSAPsys\",\"status\":\"exposed\"}]",
>       "jvm_vendor_version": "OpenJDK 64-Bit Server VM (SAP SE, 17.0.14+7-LTS, mixed mode, sharing)",
>       "agent_recent_start_ms": "1762167520212",
>       "java_version": "17.0.14 (SAP SE)"
>     }
>   }
> ]
> ```

