<!-- loio60267d3a2db04386a99b0d752e123640 -->

# Technical User Access to SuccessFactors

Configure *technical user propagation* for connections from SAP BTP to SuccessFactors.

SuccessFactors supports OIDC \(OpenID Connect\) for authentication. This includes technical users, implemented via *OAuth Client Credentials*. This flow should be used when you do not need to propagate the identity of the logged-in user towards *SuccessFactors*. Instead, all calls will be made on behalf of the same user, represented by an OAuth client.



## Prerequisites

Follow the SuccessFactors guide to complete the OIDC setup: [Register Your Own Application to Communicate with SAP SuccessFactors HCM Suite with OpenID Connect](https://help.sap.com/docs/successfactors-platform/setting-up-sap-successfactors-with-identity-authentication-and-identity-provisioning-services/register-your-own-application-to-communicate-with-sap-successfactors-hcm-suite-with-openid-connect?version=2511). Perform the options for technical user access.



## Configuring the Destination

The interaction is modeled as an *OAuth Client Credentials Authentication* destination.

For more information on details about specific flavors \(like using mTLS instead of a client secret for the token fetching\), see [OAuth Client Credentials Authentication](oauth-client-credentials-authentication-4e1d742.md).

> ### Sample Code:  
> ```
> {
> 	"Name": "sfsftechuser",
> 	"Type": "HTTP",
> 	"Description": "",
> 	"URL": "https://<sfsf url>",
> 	"ProxyType": "Internet",
> 	"Authentication": "OAuth2ClientCredentials",
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

