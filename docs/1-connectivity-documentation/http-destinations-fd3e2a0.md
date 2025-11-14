<!-- loiofd3e2a0871f0425a95e8b079708d18b6 -->

# HTTP Destinations

Configure HTTP destinations for the Transparent Proxy for Kubernetes.

The Transparent Proxy simplifies access to target systems which use HTTP protocol. It efficiently handles HTTP traffic for both Internet-based and on-premise destinations.



<a name="loiofd3e2a0871f0425a95e8b079708d18b6__section_lj4_3tv_hcc"/>

## HTTP Authentication

The Transparent Proxy enriches your request by adding credentials configured in the destination configuration. Depending on the authentication of the destination configuration, the Transparent Proxy propagates them via `Authorization` or `SAP-Connectivity-Authentication` header. For more information, see [Configuring Authentication](http-destinations-42a0e6b.md#loio42a0e6b966924f2e902090bdf435e1b2__config).

**Mandatory Destination Configuration Fields**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

Destination name

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

Destination type. Use HTTP for all HTTP\(S\) destinations.

</td>
</tr>
<tr>
<td valign="top">

URL

</td>
<td valign="top">

URL of the application. For on-premise destinations, use the virtual URL of the protected on-premise application.

</td>
</tr>
<tr>
<td valign="top">

Authentication

</td>
<td valign="top">

One of the listed Authentication types here.

</td>
</tr>
<tr>
<td valign="top">

ProxyType

</td>
<td valign="top">

Internet or OnPremise

</td>
</tr>
</table>

**Additional Destination Configuration Fields**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

URL.connectionTimeoutInSeconds

</td>
<td valign="top">

The period of time in which the HTTP client expects a confirmation after it initiated a new TCP connection. It must be in the range of 1 second to 5 minutes \(300 seconds\). If you do not use it, its default is 5 seconds. If you decide to use it, the total timeout of the initial request could be the sum of the timeout configured and the time needed to obtain the destination configuration data from the Destination service. You could set custom timeouts for calls to Destination service and Connectivity Proxy as Helm properties. See the [Configuration Guide](configuration-guide-2a22cd7.md).

</td>
</tr>
<tr>
<td valign="top">

URL.socketReadTimeoutInSeconds

</td>
<td valign="top">

The period of time the HTTP client will wait for receiving a response \(data\) from the server. It must be in the range of 1 second to 12 hours \(43200 seconds\). If you do not use it, its default is 30 seconds. If you decide to use it, the total timeout of the initial request could be the sum of the timeout configured and the time needed to obtain the destination configuration data from the Destination service. You could set custom timeouts for calls to Destination service and Connectivity Proxy as Helm properties. See the [Configuration Guide](configuration-guide-2a22cd7.md).

</td>
</tr>
<tr>
<td valign="top">

URL.headers.<header-key\>

</td>
<td valign="top">

A static key prefix is used as a namespace grouping of URL's HTTP headers which values to be sent to the target endpoint. For each HTTP header's key must be added a ' URL.headers' prefix separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "URL.headers.<header-key-1>" : "<header-value-1>",
>     ...
>     "URL.headers.<header-key-N>": "<header-value-N>",
> }
> ```

> ### Caution:  
> If there are duplicate header keys passed from the request and contained in the destination, they are both added to the request against the target system.
> 
> Example:
> 
> > ### Sample Code:  
> > ```
> > {
> > /// other destination properties
> >   "URL.headers.foo": "bar"
> > }
> > ```
> 
> > ### Sample Code:  
> > ```
> > curl -H "foo: bar2" targetsystem -vvv
> > *   Trying <some ip>...
> > * Connected to targetsystem (<some ip>) port 80 (#0)
> > > GET / HTTP/1.1
> > > Host: targetsystem
> > > User-Agent: curl/7.84.0
> > > foo: bar2
> > > foo: bar
> > ```



</td>
</tr>
<tr>
<td valign="top">

URL.queries.<query-key\>

</td>
<td valign="top">

A static key prefix is used as a namespace grouping of URL's query parameters which values to be sent to the target endpoint. For each query parameter's key must be added to a 'URL.queries' prefix separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "URL.queries.<query-key-1>" : "<query-value-1>",
>     ...
>     "URL.queries.<query-key-N>": "<query-value-N>",
> }
> ```

> ### Caution:  
> If there are duplicate query parameter keys passed from the request and contained in the destination, they are appended to the request against the target system.
> 
> Example:
> 
> > ### Sample Code:  
> > ```
> > {
> > /// other destination properties
> >   "URL.queries.foo": "bar"
> > }
> > ```
> 
> > ### Sample Code:  
> > ```
> > curl targetsystem?foo=bar2 // will result to the following final URL : targetsystem?foo=bar2&foo=bar
> > ```



</td>
</tr>
</table>

**Related Information**  


[Basic Authentication](basic-authentication-427b91d.md "The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with Basic Authentication.")

[Client Certificate Authentication](client-certificate-authentication-cd876f8.md "The Transparent Proxy handles HTTP communication protocol for both Internet and on-premise destinations protected with Client Certificate Authentication.")

[No Authentication](no-authentication-5ef40e3.md "The Transparent Proxy handles HTTP and TCP communication protocols for both Internet and on-premise destinations without authentication.")

[OAuth](oauth-cb36b39.md "Use OAuth authentication for the Transparent Proxy for Kubernetes.")

[User Propagation](user-propagation-23f166f.md "Configure user propagation for the Transparent Proxy for Kubernetes.")

[SAML Assertion Authentication](saml-assertion-authentication-23db6d9.md "The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the SAML Assertion flow.")

