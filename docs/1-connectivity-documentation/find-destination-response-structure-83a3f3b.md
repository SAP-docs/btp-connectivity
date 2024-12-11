<!-- loio83a3f3b9cd314618aba651044ed5b9df -->

# "Find Destination" Response Structure

Overview of data that are returned by the Destination service for the call type "find destination".



<a name="loio83a3f3b9cd314618aba651044ed5b9df__structure"/>

## Response Structure

When you use the "find destination" call \(read a destination by only specifying its name\), the structure of the response includes four parts:

-   The [owner of the destination](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__owner).
-   The actual [destination configuration](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__config).
-   \(Optional\) [Authentication tokens](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__tokens) that are relevant to the destination.
-   \(Optional\) [Certificates](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__cert) that are relevant to the destination.

Each of these parts is represented in the JSON object as a key-value pair and their values are JSON objects, see [Example](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__example).

See also [Call the Destination Service](consuming-the-destination-service-7e30625.md#loio7e306250e08340f89d6c103e28840f30__section_CallDestinationService).



<a name="loio83a3f3b9cd314618aba651044ed5b9df__owner"/>

## Destination Owner

-   **Key:** `owner`

    The JSON object that serves as the value of this property contains two properties itself: `SubaccountId` and `InstanceId`. `SubaccountId` has as its value the ID of the subaccount instance to which the destination belongs. Depending on where the destination was found \(as a subaccount destination or a service instance destination\) `InstanceId` can have the value `null`, or the ID of the service instance to which the destination belongs.

-   **Example:**

    > ### Sample Code:  
    > ```
    > "owner": {
    >         "SubaccountId": "9acf4877-5a3d-43d2-b67d-7516efe15b11",
    >         "InstanceId": null
    >     }
    > ```


Back to [Response Structure](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__structure)



<a name="loio83a3f3b9cd314618aba651044ed5b9df__config"/>

## Destination Configuration

-   **Key:** `destinationConfiguration`

    The JSON object that represents the value of this property contains the actual properties of the destination. To learn more about the available properties, see [HTTP Destinations](http-destinations-42a0e6b.md).

    If a destination fragment was specified in the “Find Destination” call, the value of this property is represented by the JSON object that contains the actual properties of the destination, merged with the JSON object that contains the properties of the destination fragment.

    For more information on how to extend a destination with a destination fragment, see [Extending Destinations with Fragments](extending-destinations-with-fragments-f56600a.md).

-   **Example:**

    > ### Sample Code:  
    > ```
    > "destinationConfiguration": {
    >         "Name": "TestBasic",
    >         "Type": "HTTP",
    >         "URL": "http://sap.com",
    >         "Authentication": "BasicAuthentication",
    >         "ProxyType": "OnPremise",
    >         "User": "test",
    >         "Password": "pass12345"
    >     }
    > ```


Back to [Response Structure](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__structure)



<a name="loio83a3f3b9cd314618aba651044ed5b9df__tokens"/>

## Authentication Tokens

> ### Note:  
> This property is only applicable to destinations that use the following authentication types: *BasicAuthentication*, *OAuth2SAMLBearerAssertion*, *OAuth2ClientCredentials*, *OAuthUserTokenExchange*, *OAuth2JWTBearer*, *OAuth2Password*, *SAMLAssertion*, *OAuth2RefreshToken*, *OAuth2AuthorizationCode*, *OAuth2TechnicalUserPropagation*, *OAuth2TokenExchange*.

> ### Restriction:  
> The section will contain an error if the `tokenServiceUrl` is a private endpoint \(like *localhost*\) and `ProxyType` is `Internet`, as the automation cannot be performed on the server side in this case.

> ### Note:  
> This section will not be present if automatic token retrieval is skipped by setting the query parameter `$skipTokenRetrieval=true`.

-   **Key:** `authTokens`

    The JSON array that represents the value of this property contains tokens that are required for authentication. These tokens are represented by JSON objects with these properties \(expect more new properties to be added in the future\):

    -   `type`: the type of the token.

    -   `value`: the actual token.

    -   `http_header`: JSON object containing the prepared token in the correct format. The *<key\>* field contains the key of the HTTP header. The *<value\>* field contains the value of the header.
    -   `expires_in` \(only in OAuth2 destinations\): The lifetime in seconds of the access token. For example, the value "3600" denotes that the access token will expire in one hour from the time the response was generated.
    -   `error` \(optional\): if the retrieval of the token fails, the value of both `type` and `value` is an empty string and this property shows an error message, explaining the problem.
    -   `scope` \(optional\) \(only in OAuth2 destinations\): The scopes issued with the token. The value of the scope parameter is expressed as a list of space-delimited strings. For example, `read write execute`.
    -   `refresh_token` \(optional\) \(only in OAuth2 destinations\): A refresh token, returned by the OAuth service. It can be used to renew the access token via [OAuth Refresh Token Authentication](oauth-refresh-token-authentication-bff0136.md).
    -   `issued_token_type` \(optional\) \(present and required only in `OAuth2TokenExchange` destinations\): Identifier for the representation of the issued security token \(for example, "urn:ietf:params:oauth:token-type:access\_token"\).

-   **Example:**

    > ### Sample Code:  
    > ```
    > "authTokens": [
    >         {
    >             "type": "Basic",
    >             "value": "dGVzdDpwYXNzMTIzNDU=",
    >             "http_header": {
    >             	"key":"Authorization",
    >             	"value":"Basic dGVzdDpwYXNzMTIzNDU="
    >              }
    >         }
    >     ]
    > ```


Back to [Response Structure](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__structure)



<a name="loio83a3f3b9cd314618aba651044ed5b9df__cert"/>

## Certificates

> ### Note:  
> This property is only applicable to destinations that use mTLS for token retrieval and automatic token retrieval is skipped, or destinations with the following authentication types: *ClientCertificateAuthentication*, *OAuth2SAMLBearerAssertion* \(when default JDK trust store is not used\).

-   **Key:** `certificates`

    The JSON array that represents the value of this property contains the certificates, specified in the destination configuration. These certificates are represented by JSON objects with these properties \(expect more new properties to be added in the future\):

    -   `type`

    -   `content`: the encoded content of the certificate.

    -   `name`: the name of the certificate, as specified in the destination configuration.

-   **Example:**

    > ### Sample Code:  
    > ```
    > "certificates": [
    >         {
    >             "Name": "keystore.jks",
    >             "Content": "<value>"
    >             "Type": "CERTIFICATE"
    >         },
    >         {
    >             "Name": "truststore.jks",
    >             "Content": "<value>"
    >             "Type": "CERTIFICATE"
    >         }
    >     ]
    > ```


Back to [Response Structure](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__structure)



<a name="loio83a3f3b9cd314618aba651044ed5b9df__example"/>

## Example

Example of a full response for a destination using basic authentication:

> ### Sample Code:  
> ```
> {
>     "owner": {
>         "SubaccountId": "9acf4877-5a3d-43d2-b67d-7516efe15b11",
>         "InstanceId": null
>     },
>     "destinationConfiguration": {
>         "Name": "TestBasic",
>         "Type": "HTTP",
>         "URL": "http://sap.com",
>         "Authentication": "BasicAuthentication",
>         "ProxyType": "OnPremise",
>         "User": "test",
>         "Password": "pass12345"
>     },
>     "authTokens": [
>         {
>             "type": "Basic",
>             "value": "dGVzdDpwYXNzMTIzNDU="
>             "http_header": {
>                 "key":"Authorization",
>                 "value":"Basic dGVzdDpwYXNzMTIzNDU="
>             }
>         }
>     ]
> }
> ```

Back to [Response Structure](find-destination-response-structure-83a3f3b.md#loio83a3f3b9cd314618aba651044ed5b9df__structure)

