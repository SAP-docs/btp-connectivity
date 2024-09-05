<!-- loio2b3a57282de94843ba26cd2204b96c4b -->

# Error Response Headers

When an error occurs, the transparent proxy returns a response containing one or more of the following error headers:

-   **x-error-message**

    Provides a descriptive message associated with an error that has occurred.


-   **x-error-origin**

    Describes the origin of the error. The value can be one of the following options:

    -   Transparent Proxy
    -   XSUAA
    -   Destination Service
    -   XSUAA/Destination Service


-   **x-internal-error-code**

    It represents a status code generated from an internal call, such as to the Destination Service, XSUAA, or connectivity proxy.


-   **x-request-id**

    The x-request-id header is used by transparent proxy to uniquely identify a request.


-   **x-proxy-server**

    Specifies the proxy server that processes the user's request. The expected value for this header is 'Transparent Proxy'.


You can find a possible solution by examining the response status code along with the values in the x-error-message, x-error-origin, and x-internal-error-code headers using the following table:


<table>
<tr>
<th valign="top">

Status Code

</th>
<th valign="top">

X-Error-Message

</th>
<th valign="top">

X-Error-Origin

</th>
<th valign="top">

X-Internal-Error-Code

</th>
<th valign="top">

Possible Solution

</th>
</tr>
<tr>
<td valign="top">

404 Not Found

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure the URL configured in the destination is valid. Wait for the next Transparent Proxy Manager completion.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

Check your request headers or OAuth Configuration fields in the referenced Destination. Example for 'authorization' header of scheme - 'Authorization: Bearer <base64-encoded-token\>'. Check also 'x-error-message', 'x-error-origin' and 'x-internal-error-code' response headers for more concrete information.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

'x-token-service-tenant' request header is missing. It is required when 'tokenServiceURLType' property in the destination is of type Common.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure you add a valid 'x-token-service-tenant' request header to each destination that has 'tokenServiceURLType' property of type Common.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

Cannot mix header ‘x-client-assertion-destination-name‘ with headers ‘x-client-assertion‘ and ‘x-client-assertion-type

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure you pass either ‘x-client-assertion-destination-name‘ or ‘x-client-assertion‘ and ‘x-client-assertion-type‘ request headers and not the combination of all of them.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

Destination service returned unsuccessful status code. Check your related request headers.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure you pass a valid 'authorization' header value that is appropriate for the referenced destination authentication type.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

In multi-tenant operational mode, either ‘x-tenant-id‘ or ‘x-tenant-subdomain‘ header is mandatory to be provided.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure you pass either x-tenant-id or x-tenant-subdomain header in shared mode.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

Both ‘x-tenant-id‘ and ‘x-tenant-subdomain‘ headers are passed. Only one should be provided.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure you pass either x-tenant-id or x-tenant-subdomain header but not both at the same time in shared mode.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

'x-destination-name' header is missing but required for an endpoint exposing multiple destinations via the same Destination CR.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

In case the spec.destinationRef.name property is "\*" the 'x-destination-name' header is mandatory provide reference to a valid destination.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The value of the header 'x-destination-name' exceeds the maximum allowed length of 200

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The provided header value is wrong since the Destination Service allow maximum length for a destination name to be 200 symbols.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The value of the header 'x-destination-name' contains characters that are not allowed. Check the destination name restrictions in the Destination service documentation.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The provided header value for 'x-destination-name' has invalid characters. Check the name restrictions in the Destination service documentation.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The value of the header 'x-fragment-name' exceeds the maximum allowed length of 200

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The provided header value is wrong since the Destination Service allow maximum length for a fragment name to be 200 symbols.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The value of the header 'x-fragment-name' contains characters that are not allowed. Check the fragment name restrictions in the Destination service documentation.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The provided header value for 'x-destination-name' has invalid characters. Check the name restrictions in the Destination Service documentation.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The requested endpoint is bound to a concrete destination, statically declared in the respective Destination CR. 'x-destination-name' header is not supported for this endpoint. Contact the Transparent Proxy Administrator.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The Destination Custom Resource is bound to a specific destination via spec.destinationRef.name property. Either change the spec.destinationRef.name property in the CR to "\*" or do not pass the 'x-destination-name' header.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The requested endpoint is bound to a concrete destination, statically declared in the respective Destination CR. 'x-fragment-name' header is not supported for this endpoint. Contact the Transparent Proxy Administrator.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The Destination Custom Resource is bound to a specific destination via spec.destinationRef.name property. Either change the spec.destinationRef.name property in the CR to "\*" or set spec.fragmentRef.name to the desired fragment.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Destination '<name\>' referred in Destination CR '<name\>' is not found in tenant '<tenant-subdomain\>'. Inspect the Destination CR or contact the Destination Administrator.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

Check if your referenced destination exists in the specified Destination Service instance or contact the Destination Administrator.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Destination '<name\>' with '<fragmentName\>' referred in Destination CR '<name\>' is not found in tenant '<tenant-subdomain\>'. Inspect the Destination CR or contact the Destination Administrator.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

Check if your referenced destination/fragment exists in the specified Destination Service instance or contact the Destination Administrator.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Received invalid configuration from Destination Service, requested via destination '<destinationName\>'.'

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

There could be an issue with the configuration fields of the destination. Contact the Destination Administrator.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Received invalid configuration from Destination Service, requested via destination '<destinationName\>' and fragment '<fragmentName\>'.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

There could be an issue with the configuration fields of the destination/fragment. Contact the Destination Administrator.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Invalid OAuth configuration in destination '<name\>' referred in Destination CR '<name\>

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

Check Auth Configuration fields or your request headers in the referenced destination.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Invalid OAuth configuration in destination '<name\>' with fragment '<fragmentName\>' referred in Destination CR '<name\>

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

 

</td>
<td valign="top">

Check Auth Configuration fields or your request headers in the referenced destination/fragment.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

On-Premise technical connectivity is not configured. There is no value provided for connectivity proxy service name.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

Make sure you provide correct Connectivity proxy serviceName in Helm Configurations.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Tenant subdomain '<tenantSubdomain\>' could not be determined as valid tenant for Destination service instance with name '<destinationServiceInstanceName\>' as provided in the Transparent Proxy deployment configuration. Contact the Tenant administrator.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

Check if you pass a valid Destination Service instance in Destination CR or contact the Kubernetes cluster administrator to check the Helm configuration.

</td>
</tr>
<tr>
<td valign="top">

500 Internal Server Error

</td>
<td valign="top">

Tenant id '<tenantId\>' could not be determined as valid tenant for Destination service instance with name '<destinationServiceInstanceName\>' as provided in the Transparent Proxy deployment configuration. Contact the Tenant administrator.

</td>
<td valign="top">

XSUAA

</td>
<td valign="top">

404 Not Found

</td>
<td valign="top">

The passed tenant in x-tenant-id is not found. Make sure you pass existing tenant in x-tenant-id.

</td>
</tr>
<tr>
<td valign="top">

500 Internal Server Error

</td>
<td valign="top">

Tenant subdomain '<tenantSubdomain\>' is not subscribed to respective provider application using Destination service instance with name '<destinationServiceInstanceName\>', as provided in the Transparent Proxy deployment configuration, under provider tenant subdomain '<providerTenantSubdomain\>'. Contact the Destination Administrator.

</td>
<td valign="top">

XSUAA

</td>
<td valign="top">

401 Unauthorized

</td>
<td valign="top">

The passed tenant in x-tenant-subdomain is not subscribed to the provider. Make sure you pass subscribed to the provider tenant in x-tenant-subdomain.

</td>
</tr>
<tr>
<td valign="top">

500 Internal Server Error

</td>
<td valign="top">

Tenant id '<tenantId\>' is not subscribed to respective provider application using Destination service instance with name '<destinationServiceInstanceName\>', as provided in the Transparent Proxy deployment configuration, under provider tenant subdomain '<providerTenantSubdomain\>'. Contact the Destination Administrator.

</td>
<td valign="top">

XSUAA

</td>
<td valign="top">

401 Unauthorized

</td>
<td valign="top">

The passed tenant in x-tenant-id is not subscribed to the provider. Make sure you pass subscribed to the provider tenant in x-tenant-id.

</td>
</tr>
<tr>
<td valign="top">

500 Internal Server Error

</td>
<td valign="top">

 

</td>
<td valign="top">

XSUAA

</td>
<td valign="top">

 

</td>
<td valign="top">

The referenced destination is not found in the Destination Service for the given tenant.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Destination '<destinationName\>' referred in Destination CR '<crName'\> is not found in tenant '<tenantName\>'. Inspect the Destination CR or contact the Destination Administrator.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

404 Not Found

</td>
<td valign="top">

The referenced destination is not found in the Destination Service for the given tenant.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Destination '<destinationName\>' with fragment '<fragmentName\>' referred in Destination CR'<crName'\> is not found in tenant '<tenantName\>'. Inspect the Destination CR or contact the Destination Administrator.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

404 Not Found

</td>
<td valign="top">

The referenced destination or fragment is not found in the Destination Service for the given tenant.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Destination '<destinationName\>' not found in tenant '<tenantName\>'. Contact the Destination Administrator.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

404 Not Found

</td>
<td valign="top">

The referenced destination is not found in the Destination Service for the given tenant.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Destination '<destinationName\>' with fragment '<fragmentName\>' not found in tenant '<tenantName\>'. Contact the Destination Administrator.

</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

404 Not Found

</td>
<td valign="top">

The referenced destination or fragment is not found in the Destination Service for the given tenant.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

The following headers: \[<headerKey1\>, ...\] should be passed only once. Check your request parameters.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The provided headers should be passed only once.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Region with ID <regionId\> is not found in the Connectivity Proxy configuration.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The region id <regionId\> passed as SAP-Connectivity-Region-Configuration-Id header or statically configured for the given Destination Service instance in the transparent proxy configurations is not found in the connectivity proxy multi region configurations. Make sure that the used region id is existing in the connectivity proxy multi region configurations.

</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

Connectivity Proxy region ID is not specified. Either pass it as a 'SAP-Connectivity-Region-Configuration-Id' or set it in the Transparent Proxy configuration.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

You should either pass SAP-Connectivity-Region-Configuration-Id header or statically configure the region for the given Destination Service instance in the transparent proxy configurations.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Invalid Connectivity proxy instance configuration. Contact the local Kubernetes cluster administrator to inspect the Connectivity Proxy deployment configuration.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The connectivity proxy multi region config map does not exist.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

The referenced Connectivity Proxy instance configuration for region named '<regionName\>' is not found or is invalid.

</td>
<td valign="top">

Transparent Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

The secret referenced by the connectivity proxy region configuration named <regionName\> does not exist or is invalid.

</td>
</tr>
<tr>
<td valign="top">

502 Bad Gateway

</td>
<td valign="top">

Failed to establish connection to the Connectivity Proxy. Check the configuration and the Connectivity Proxy status.

</td>
<td valign="top">

Connectivity Proxy

</td>
<td valign="top">

 

</td>
<td valign="top">

Check if the Connectivity Proxy service name provided through integration.connectivityProxy.serviceName exists. Additionaly check if "connectivity-proxy" config map exists in the namespace where the connectivity-proxy is installed.

</td>
</tr>
</table>

