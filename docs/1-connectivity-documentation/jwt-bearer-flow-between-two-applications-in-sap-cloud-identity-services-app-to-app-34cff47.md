<!-- loio34cff47cd0c3458b824327d8398fa9a6 -->

# JWT Bearer Flow between Two Applications in SAP Cloud Identity Services \(App to App\)

Configure principal propagation between two applications in *SAP Cloud Identity Services*.



## Scenario

You have an application protected with *SAP Cloud Identity Services*. You perform user-based login flows \(for example, authorization code grant\) to have a named user authenticated in the application, and the application then works on behalf of that user. You want to call another application, protected with *SAP Cloud Identity Services* as well, maintaining the logged-in user context \(principal propagation\). The called application will then perform its work on behalf of the same user without requiring a separate login.

This guide shows how to model and delegate to the Destination service the operation described in [Consume an API from a Provider Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/consume-api-from-another-application#procedure) \(example *Principal Propagation* in section *Procedure*\).



## Prerequisites

The integration between applications is established and relevant parameters are known, see [Consume an API from a Provider Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/consume-api-from-another-application#prerequisites) \(section *Prerequisites*\).



## Concept Overview

The concept is described in [Consuming APIs from Other Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/consume-apis-from-other-applications?version=Cloud).



## Configuring the Destination

The interaction is modeled as an *OAuth JWT Bearer Authentication* destination.

For detailed information on specific flavors \(like using mTLS instead of a client secret for the token fetching\), see [OAuth JWT Bearer Authentication](oauth-jwt-bearer-authentication-283cd2d.md).

> ### Sample Code:  
> ```
> {
> 	"Name": "app2app",
> 	"Type": "HTTP",
> 	"Description": "",
> 	"URL": "https://<app2 url>",
> 	"ProxyType": "Internet",
> 	"Authentication": "OAuth2JWTBearer",
> 	"clientId": "<app1 client id>",
> 	"clientSecret": "<app1 client secret>",
> 	"tokenServiceURL": "https://<SAP Cloud Identity Services tenant url>/oauth2/token",
> 	"tokenServiceURLType": "Dedicated",
> 	"tokenService.body.resource": "<app2 reference>"
> }
> ```

Where:

-   `<app2 url>` is the URL of the target application \(the provider application\). This is what the first application will call with the resulting token from the exchange to perform its request on behalf of the user.
-   `<app1 client id>` is the client ID of the first application \(the one making the call / the consumer application\).
-   `<app1 client secret>` is the client secret of the first application \(the one making the call / the consumer application\).
-   `<SAP Cloud Identity Services tenant url>` is the host of the *SAP Cloud Identity Services* tenant. The operations are performed in the context of this host.
-   `<app2 reference>` is used to identify the dependency \(the target application / the provider application\) consumed by the first application \(the one making the call / the consumer application\). It can be:
    -   `urn:sap:identity:application:provider:name:<Dependency_name>`, where `<Dependency name>` is the name that the tenant administrator configures for the dependency between the consumer application and the provider application.
    -   `urn:sap:identity:application:provider:clientid:<client_id>`, where `<client_id>` is client ID of the provider application.




## Consuming the Destination and Executing the Scenario

To consume the created destination, use the procedure described in [Exchanging User JWTs via OAuth2JWTBearer Destinations](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md).

