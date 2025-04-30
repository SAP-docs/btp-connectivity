<!-- loio47a3cff4f33a4a0f9af1b0d6677a9e6e -->

# Configure Principal Propagation via IAS Token

Configure an Identity Authentication service \(IAS\) token for principal propagation \(user propagation\) from your application to an on-premise system.

> ### Note:  
> For more information on identity authentication, see [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/landing-page?version=Cloud).

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



## Scenario

For a Cloud Foundry application that uses the Connectivity service, you want the currently logged-in user to be propagated via the Cloud Connector to an on-premise system. This user is represented in the cloud application by an IAS token.

For more information, see [Principal Propagation](principal-propagation-e2cbb48.md) and [Getting Started with the Identity Service of SAP BTP](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/066bda825cb148629aa1934b770eb4ed.html).



## Prerequisites

-   Cloud Connector 2.13 \(or newer\) must be used.
-   The Cloud Connector must be connected to a subaccount that is configured with the IAS tenant issuing the tokens.

    For more information, see [Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/161f8f0cfac64c4fa2d973bc5f08a894.html "Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using OpenID Connect (OIDC) to establish trust.") :arrow_upper_right:.




## Solution

The application sends two headers to the Connectivity Proxy:


<table>
<tr>
<td valign="top">

Header: `"SAP-Connectivity-Authentication" : "Bearer <IAS-Token>"`

Header: `"Proxy-Authorization" : "Bearer <accessToken>"`

</td>
</tr>
</table>



## More Information

[Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html)

