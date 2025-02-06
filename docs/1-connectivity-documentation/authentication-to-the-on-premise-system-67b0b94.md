<!-- loio67b0b94f09f2446598787eea0855e56b -->

# Authentication to the On-Premise System

Provide authentication information for the authentication type you use.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.

You can use the Connectivity service in different authentication scenarios:

-   **No authentication** to the on-premise system
-   **Principal propagation** \(user propagation\) to the on-premise system
-   **Basic authentication** to the on-premise system



<a name="loio67b0b94f09f2446598787eea0855e56b__procedure_auth_cs"/>

## Procedure

For each authentication type, you must provide specific information in the request to the virtual host:

-   [The SAP-Connectivity-Authentication Header](authentication-to-the-on-premise-system-67b0b94.md#loio67b0b94f09f2446598787eea0855e56b__header)
-   [Authentication Types](authentication-to-the-on-premise-system-67b0b94.md#loio67b0b94f09f2446598787eea0855e56b__types)



<a name="loio67b0b94f09f2446598787eea0855e56b__header"/>

## The SAP-Connectivity-Authentication Header

> ### Note:  
> For the principal propagation scenario, the `SAP-Connectivity-Authentication` header is only required if you do not use the user exchange token flow, see [Configure Principal Propagation via User Exchange Token](configure-principal-propagation-via-user-exchange-token-39f538a.md).

Applications must propagate the user JWT token \(`userToken`\) using the `SAP-Connectivity-Authentication` header. This is required for the Connectivity service to open a tunnel to the subaccount for which a configuration is made in the Cloud Connector. The following example shows you how to do this using the *Spring* framework:

> ### Sample Code:  
> ```
> 
> Authentication auth = SecurityContextHolder.getContext().getAuthentication();
> 
> if (auth == null) {
> 
>         throw new UserInfoException("User not authenticated");
> 
> }
> 
> OAuth2AuthenticationDetails details = (OAuth2AuthenticationDetails) auth.getDetails();
> 
> String userToken = details.getTokenValue();
> 
> urlConnection.setRequestProperty("SAP-Connectivity-Authentication", "Bearer " + userToken);
> 
> ```

Back to [Procedure](authentication-to-the-on-premise-system-67b0b94.md#loio67b0b94f09f2446598787eea0855e56b__procedure_auth_cs)



<a name="loio67b0b94f09f2446598787eea0855e56b__types"/>

## Authentication Types

The required setup for each of the authentication type is as follows:

**No Authentication**

If the on-premise system does not need to identify the user, you should use this authentication type. It requires no additional information to be passed with the request.

**Principal Propagation**

When you open the application router to access your cloud application, you are prompted to log in. Doing so means that the cloud application now knows your identity. Principal propagation forwards this identity via the Cloud Connector to the on-premise system. This information is then used to grant access without additional input from the user. To achieve this, you do not need to send any additional information from your application, but you must set up the Cloud Connector for principal propagation. See [Configuring Principal Propagation](configuring-principal-propagation-c84d4d0.md).

> ### Note:  
> Do not use the `Authorization` header in *principal propagation* scenarios.

**Technical User Propagation**

As of Cloud Connector version 2.15, consumers of the Connectivity service can propagate technical users from the cloud application towards the on-premise systems. To make use of this feature, provide a JWT \(usually obtained via `client_credentials` OAuth flow\), representing the technical user, via the `SAP-Connectivity-Technical-Authentication` header. This is similar to *principal propagation*, but in this case, a technical user is propagated instead of a business user.

```
urlConnection.setRequestProperty("SAP-Connectivity-Technical-Authentication", "Bearer " + technicalUserToken);
```

For more information, see [Configuring Principal Propagation](configuring-principal-propagation-c84d4d0.md).

> ### Note:  
> Do not use the `Authorization` header in *technical user propagation* scenarios.

**Basic Authentication**

If the on-premise system requires username and password to grant access, the cloud application must provide these data using the *Authorization* header. The following example shows how to do this:

> ### Sample Code:  
> ```
> // Basic authentication to backend system
> String credentials = MessageFormat.format("{0}:{1}", backendUser, backendPassword);
> byte[] encodedBytes = Base64.encodeBase64(credentials.getBytes());
> urlConnection.setRequestProperty("Authorization", "Basic " + new String(encodedBytes));
> ```

Back to [Procedure](authentication-to-the-on-premise-system-67b0b94.md#loio67b0b94f09f2446598787eea0855e56b__procedure_auth_cs)

**Related Information**  


[Configure Principal Propagation via Corporate IdP-Embedded Token](configure-principal-propagation-via-corporate-idp-embedded-token-dfecfb4.md "Configure a corporate IdP-embedded token for principal propagation (user propagation) from your application to an on-premise system.")

[Configure Principal Propagation via User Exchange Token](configure-principal-propagation-via-user-exchange-token-39f538a.md "Configure a user exchange token for principal propagation (user propagation) from your application to an on-premise system.")

[Configure Principal Propagation via IAS Token](configure-principal-propagation-via-ias-token-47a3cff.md "Configure an Identity Authentication service (IAS) token for principal propagation (user propagation) from your application to an on-premise system.")

[Configure Principal Propagation via OIDC Token](configure-principal-propagation-via-oidc-token-000232b.md "Configure an OpenID-Connect (OIDC) token for principal propagation (user propagation) from your application to an on-premise system.")

