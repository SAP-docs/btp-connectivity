<!-- loioe50acf1d39ec46748bf2609986fdb95f -->

# Using an IAS User Token for Corporate IdP Token Principal Propagation to On-Premise Systems

Using an IAS user token for corporate IdP token principal propagation to on-premise systems allows automatic token exchange to the corporate IdP token.



<a name="loioe50acf1d39ec46748bf2609986fdb95f__section_udd_2p5_bgc"/>

## Prerequisites

-   You have a tenant of SAP Cloud Identity Services.

    For more information, see [Get Your Tenant](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/get-your-tenant?version=Cloud&locale=en-US) \(*SAP Cloud Identity Services* documentation\).

-   You have configured a destination with proxy type *OnPremise* and authentication type *PrincipalPropagation*.



<a name="loioe50acf1d39ec46748bf2609986fdb95f__section_cmz_dp5_bgc"/>

## Scenario

When consuming a destination with principal propagation to an on-premise system using IAS user token that contains the `forward_corp_idp_token` claim, an automatic token exchange will be performed to the corporate IdP token on your behalf.

Depending on the value of the `forward_corp_idp_token` claim, the response in the *Authentication Tokens* section of ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__tokens) will be either an `access_token` or `id_token`. After that, the result may be passed to the Connectivity service.

For more information, see [Configure Principal Propagation via OIDC Token](configure-principal-propagation-via-oidc-token-000232b.md).

For detailed information on how to consume the Destination service using an IAS token, see [Calling the Destination Service REST API via IAS Token](calling-the-destination-service-rest-api-via-ias-token-ce25f2b.md).

> ### Caution:  
> Possible values of the `forward_corp_idp_token` user attribute are: `access_token` or `id_token`, and the IAS tenant must be additionally configured, so that this claim will be part of the IAS user token.
> 
> For more information, see [Configuring User Attributes from a Corporate Identity Provider](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configure-default-attributes-for-subscribed-applications?version=Cloud).

