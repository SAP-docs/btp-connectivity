<!-- loio3cb7b81115c44cf594e0e3631291af94 -->

# User Propagation via SAML 2.0 Bearer Assertion Flow

Learn about the process for automatic token retrieval, using the `OAuth2SAMLBearerAssertion` authentication type for HTTP destinations.



<a name="loio3cb7b81115c44cf594e0e3631291af94__tasks_up"/>

## Tasks


<table>
<tr>
<th valign="top">

Task Type

</th>
<th valign="top">

Task

</th>
</tr>
<tr>
<td valign="top">

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

Operator and/or Developer

</td>
<td valign="top">

[Prerequisites](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__Prerequisites)

</td>
</tr>
<tr>
<td valign="top">

![](images/CS_TASK_Dev_a4c82d5.png)

Developer

</td>
<td valign="top">

[Automated Access Token Retrieval](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__Token)

-   [Determine the Propagated User ID](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__Options)
-   [Propagate User Attributes](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__attributes)
-   [Scenarios](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__scenarios)



</td>
</tr>
</table>



<a name="loio3cb7b81115c44cf594e0e3631291af94__Prerequisites"/>

## Prerequisites

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

-   You have configured an `OAuth2SAMLBearerAssertion` destination. See [OAuth SAML Bearer Assertion Authentication](oauth-saml-bearer-assertion-authentication-c69ea6a.md).
-   Unless using the destination property `SystemUser`, the user’s identity should be represented by a JSON Web token \(JWT\).

    > ### Caution:  
    > The `SystemUser` property is deprecated and will be removed soon. We recommend that you work on behalf of specific \(named\) users instead of working with a technical user.
    > 
    > As an alternative for technical user communication, we strongly recommend that you use one of these authentication types:
    > 
    > -   Basic Authentication \(see [Client Certificate Authentication](client-certificate-authentication-4e13a04.md)\)
    > 
    > -   Client Certificate Authentication \(see [Client Certificate Authentication](client-certificate-authentication-4e13a04.md)\)
    > -   [OAuth Client Credentials Authentication](oauth-client-credentials-authentication-4e1d742.md)
    > 
    > To extend an OAuth access token's validity, consider using an OAuth refresh token.

    > ### Note:  
    > Though actually not being a strict requirement, it is likely that you need a user JWT to get the relevant information. See [SAP Authorization and Trust Management Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6373bb7a96114d619bfdfdc6f505d1b9.html "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.") :arrow_upper_right:.

-   If you are using custom user attributes to determine the user, the JWT representing the user \(that is passed to the Destination service\) must have the `user_attributes` scope.

Back to [Tasks](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__tasks_up)



<a name="loio3cb7b81115c44cf594e0e3631291af94__Token"/>

## Automated Access Token Retrieval

![](images/CS_TASK_Dev_a4c82d5.png)

For an `OAuth2SAMLBearerAssertion` destination, you can use the automated token retrieval functionality that is available via the "find destination" endpoint. See [Destination Service REST API](destination-service-rest-api-23ccafb.md).

**Determine the Propagated User ID**

There are currently three sources that can provide the propagated user ID. They are prioritized, meaning that the lookup always starts from the top-priority source and goes down the list. If the propagated user ID is not found at a given level, the next level is checked. If not found on any level, the operation would fail.

Find the available sources in the table below, in order of their priority.

**Propagated User ID: Sources**


<table>
<tr>
<th valign="top">

Source

</th>
<th valign="top">

Procedure

</th>
</tr>
<tr>
<td valign="top">

*System User*

</td>
<td valign="top">

The system user is a special user ID that is hardcoded in your destination as value of the `SystemUser` property. If you set this property, its value is used as the propagated user ID.

</td>
</tr>
<tr>
<td valign="top">

*Field in the JWT*

</td>
<td valign="top">

In this case, the Destination service looks for the user ID as a field in the provided JWT. When you make the HTTP call to the Destination service, you must provide the `Authorization` header. The value must be a JWT in its encoded form \(see [RFC 7519](https://tools.ietf.org/html/rfc7519)\). The procedure is as follows:

-   If the `userIdSource` property is configured in the destination, its value is the key of the JWT field that will be the user ID \(if there is no such key in the JWT, the flow proceeds to the next level\). There are 2 options:
    -   plain string: the exact match is searched on the root-level element keys of the JWT.
    -   [JsonPath](https://github.com/json-path/JsonPath/blob/efdab976ad515b42b05d61d8b09a580e6e1a0665/README.md) expression: lets you use non-root-level elements of the JWT.


-   If the `userIdSource` property is missing, the flow falls back to the destination property `nameIdFormat`. It must have one of the following two values \(or not be set at all\), otherwise an exception is thrown:
    -   **urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress**: the `email` element of the JWT is the user ID. If there is no such element in the JWT, an exception is thrown.
    -   **urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified** \(or not set\): the `user_name` element of the JWT is the user ID. If there is no such element in the JWT, an exception is thrown.




</td>
</tr>
<tr>
<td valign="top">

*Custom User Attribute*

</td>
<td valign="top">

Like *Field in the JWT*, this source must use the `Authorization` header. In this case, its value is used to retrieve the custom user attributes from the Identity Provider \(XSUAA\). One of those attributes can be used as the propagated user ID. The access token from the header must be a user JWT with the `user_attributes` scope. Otherwise the custom attributes cannot be retrieved, and the operation results in an error.

-   If the `userIdSource` property is configured in the destination, the same logic applies as for *Field in the JWT*, but this time on the JSON containing the custom user attributes.
-   If `userIdSource` is missing or the desired key is not found in the custom attributes, the operation fails \(***user ID could not be determined***\).



</td>
</tr>
</table>

Back to [Tasks](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__tasks_up)

**Propagate User Attributes**

You can read additional user attributes from the identity provider \(XSUAA\), and propagate them as SAML attributes in the generated SAML bearer assertion.

These attributes are similar to the ones returned by the Cloud Foundry UAA user info endpoint. However, they may differ depending on the XSUAA behavior, and are specific to the identity provider you use.

For more details about these attributes and possible values, see [https://docs.cloudfoundry.org/api/uaa/version/74.15.0/index.html\#user-info](https://docs.cloudfoundry.org/api/uaa/version/74.15.0/index.html#user-info).

> ### Note:  
> When adding the attributes, the following rules apply:
> 
> -   All root elements, except for `user_attributes`, are added "as is", that is, the attribute name and value are displayed as seen in the source \(user info response structure\).
> -   Elements under the `user_attribute` key are parsed and added as attributes prefixed with '`user_attributes.`'. For example, having `{"user_attributes": { "my_param": "my_value" }}` will result in an attribute called '`user_attributes.my_param`' with value '`my_value`' in the SAML assertion. If you want to avoid this `user_attributes.` prefix, you can set the `skipUserAttributesPrefixInSAMLAttributes` additional property of the destination to `true`. If you do so, the above example will result in an attribute called `my_param` with value `my_value` in the SAML assertion.

In addition to identity provider \(XSUAA\) user info attributes, there are some more attributes which are read from the passed JWT. They are located via predefined `JsonPath` expressions and cannot be controlled by the end user:

-   `$.['xs.system.attributes']['xs.saml.groups']`
-   `$.['user_attributes']['xs.saml.groups']`

> ### Note:  
> The `'xs.saml.groups'` attribute, read from the passed JWT, is renamed to `'Groups'` in the resulting SAML assertion. See also [Settings for Default SAML Federation Attributes of Identity Providers for Business Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2ce3938c66d94479848bff3090999027.html#loio6d073332bc5743fdb7f7f06bde499ab7 "This table shows the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a subaccount.") :arrow_upper_right:.

Back to [Tasks](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__tasks_up)

**Scenarios**

Refer to the table below to find the JWT requirements for a specific scenario:


<table>
<tr>
<th valign="top">

Scenario

</th>
<th valign="top">

Authorization Header

</th>
</tr>
<tr>
<td valign="top">

Propagate a **technical user** principal, using the `SystemUser` property of an `OAuth2SAMLBearerAssertion` destination maintained in the **subscriber subaccount**, and used by the **provider application**.

</td>
<td valign="top">

Access token, retrieved

-   via the client credentials of the Destination service instance \(bound to the application\).
-   using the subscriber's tenant-specific `Token Service URL`.



</td>
</tr>
<tr>
<td valign="top">

Propagate a **technical user** principal, using the `SystemUser` property of an `OAuth2SAMLBearerAssertion` destination maintained in the **same subaccount** where the application is deployed.

</td>
<td valign="top">

Access token, retrieved

-   via the client credentials of the Destination service instance \(bound to the application\).
-   using the provider's tenant-specific `Token Service URL`.



</td>
</tr>
<tr>
<td valign="top">

Propagate a **business user** principal, using an `OAuth2SAMLBearerAssertion` destination maintained in the **subscriber subaccount** where the application is deployed.

The business user is represented by a JWT that was **issued by the subscriber**.

</td>
<td valign="top">

The JWT, previously retrieved from the application

-   by exchanging the JWT \(that represents the user\) to another user access token via the client credentials of the Destination service instance \(bound to the application\).
-   using the subscriber's tenant-specific `Token Service URL`.



</td>
</tr>
<tr>
<td valign="top">

Propagate a **business user** principal, using an `OAuth2SAMLBearerAssertion` destination maintained in the **same subaccount** where the application is deployed.

The business user is represented by a JWT that was **issued by the provider**.

</td>
<td valign="top">

The JWT, previously retrieved by the application

-   by exchanging the JWT \(that represents the user\) to another user access token via the client credentials of the Destination service instance \(bound to the application\).
-   using the provider's tenant-specific `Token Service URL`.



</td>
</tr>
</table>

Back to [Tasks](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md#loio3cb7b81115c44cf594e0e3631291af94__tasks_up)

