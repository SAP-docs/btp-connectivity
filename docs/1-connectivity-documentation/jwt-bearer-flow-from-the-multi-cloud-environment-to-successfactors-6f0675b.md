<!-- loio6f0675b8151a474d8bbc6b03178537c5 -->

# JWT Bearer Flow from the Multi-Cloud Environment to SuccessFactors

Configure *principal propagation via OAuth JWT Bearer authentication* for connections from SAP BTP to SuccessFactors.

SuccessFactors supports OIDC for authentication. This includes principal propagation, implemented via OAuth JWT Bearer. This flow should be used when you need to propagate the identity of the logged in user towards SuccessFactors.



## Prerequisites

Follow the SuccessFactors guide to complete the OIDC setup: [Register Your Own Application to Communicate with SAP SuccessFactors HCM Suite with OpenID Connect](https://help.sap.com/docs/successfactors-platform/setting-up-sap-successfactors-with-identity-authentication-and-identity-provisioning-services/register-your-own-application-to-communicate-with-sap-successfactors-hcm-suite-with-openid-connect?version=2511). Perform the options for technical user access.



## Configuring the Destination

The interaction is modeled as an *OAuth JWT Bearer Authentication* destination.

For more information on details about specific flavors \(like using mTLS instead of a client secret for the token fetching\), see [OAuth JWT Bearer Authentication](oauth-jwt-bearer-authentication-283cd2d.md).

> ### Sample Code:  
> ```
> {
> 	"Name": "sfsftechuser",
> 	"Type": "HTTP",
> 	"Description": "",
> 	"URL": "https://<sfsf url>",
> 	"ProxyType": "Internet",
> 	"Authentication": "OAuth2JWTBearer",
> 	"clientId": "<oidc client id>",
> 	"clientSecret": "<oidc client secret>",
> 	"tokenServiceURL": "https://<SAP Cloud Identity Services tenant url>/oauth2/token",
> 	"tokenServiceURLType": "Dedicated",
> 	"tokenService.body.resource": "urn:sap:identity:application:provider:name:<sfsf dependency name>"
> }
> ```

Where:

-   `<sfsf url>` is the URL of the SuccessFactors system.
-   `<oidc client id>` is the client ID of the OIDC application, created during the setup.
-   `<oidc client secret>` is the client secret of the OIDC application, created during the setup.
-   `<SAP Cloud Identity Services tenant url>` is the host of the *SAP Cloud Identity services* tenant. The operations are performed in the context of this host.
-   `<sfsf dependency name>` is the name of the dependency created from the OIDC application towards SuccessFactors during the setup phase.



## Consuming the Destination and Executing the Scenario

Use the [Find a Destination REST API](calling-the-destination-service-rest-api-84c5d38.md) or the [Consume REST API](referring-resources-using-the-consume-rest-api-78ba73a.md) to fetch the destination, including the access token that the Destination service will fetch for you.

