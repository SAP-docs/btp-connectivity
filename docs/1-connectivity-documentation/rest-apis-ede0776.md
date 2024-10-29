<!-- loioede077617d9d4181b5c755fed15e56c3 -->

# REST APIs

Find general information on the Cloud Connector REST APIs.

The Cloud Connector provides REST APIs to support automation of configuration and monitoring tasks. REST APIs are exposed on the same host and port that you use to access to the Cloud Connector.

[Request and Response Payload Format](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__payload)

[Security and Session](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__sec)

[User Roles](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__roles) 

[Return Codes](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__return)

[Hypertext Application Language](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__hyper)

[Available REST APIs](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__apis)

[Sample Code](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__code) 



<a name="loioede077617d9d4181b5c755fed15e56c3__payload"/>

## Request and Response Payload Format

The payload \(that is, the data transmitted in the body\) of requests and responses is mostly coded in JSON format. The following example shows the request payload *\{description:<value\>\}* coded in JSON:



```
{"description": "very helpful description"}
```

Values that represent a date are provided as a UTC long number, which is the number of milliseconds since 1 January 1970 00:00:00 UT \(GMT+00\).

In case of errors, the HTTP status code is *4xx* or *500*. Error details are supplied in the response body in JSON format:

```
{type: <type>, message: <message>}
```

where *type* can be one of the following strings:

```
INVALID_REQUEST, ILLEGAL_STATE, NOT_FOUND, INVALID_CONFIGURATION, RUNTIME_FAILURE, SHADOW_UPDATE, FORBIDDEN_REQUEST
```

The request JSON is listed in the API descriptions in an abbreviated form, showing only the property names and omitting the values. Details on the values \(data types and restrictions\) are provided separately below the respective API descriptions.

The API documentation also includes possible error types, and details on those errors below the API description. These errors pertain to property values of the payload only. We do not claim this list of errors to be exhaustive. In particular, errors caused by obviously erroneous input, such as missing mandatory or malformed property values, may have been omitted. As a rule of thumb, missing or invalid values result in *INVALID\_REQUEST*. Errors caused elsewhere \(for example, inappropriate header field values\) are not listed.

> ### Note:  
> Request bodies in JSON format require the header field *Content-Type application/json*. The API descriptions do not explicitly mention this fact. Header fields are shown only if they deviate from the default *Content-Type: application/json*.

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)



<a name="loioede077617d9d4181b5c755fed15e56c3__sec"/>

## Security and Session

The Cloud Connector supports the authentication types *basic authentication* and *form-based authentication*. Once authenticated, a client can keep the session and execute subsequent requests in the session. A session avoids the overhead caused by authentication. As usual, the session ID can be obtained from the response header field *Set-cookie* \(as *JSESSIONID=<session Id\>*\), and must be sent in the request header *Cookie: JSESSIONID=<session Id\>*.

The Cloud Connector employs CSRF tokens to counter CSRF \(cross-site request forgery\) attacks. Upon first request, a CSRF token is generated and sent back in the response header in field *X-CSRF-Token*. The client application must retain this token and send it in all subsequent requests as header field *X-CSRF-Token* together with the session cookie as explained above.

> ### Note:  
> No CSRF token is generated if request header field *Connection* has the value *close* \(as opposed to *keep-alive*\). In other words, if you want to make stateful, session-based REST calls, use *Connection: keep-alive*, extract the CSRF token from the first response header and subsequently include it in all request headers. Otherwise, use *Connection: close* and always submit user and password through *basic authentication*.

An inactive session will incur a timeout at some point, and will consequently be removed. A request using an expired session will receive a login page \(*Content-type: text/html*\). The status code of the response is 200 in this case. Hence, the only way to detect an expired session is to pay attention to the content type and status code. Content type*text/html* in a connection with status code 200 indicates an expired session.

For security reasons, a session should be closed or invalidated once it is not needed anymore. You can achieve this by including *Connection: close* in the header of the final call involving the session in question. As a result, the Cloud Connector invalidates the session. Subsequent attempts to send a request in the context of that session respond with a login page as explained above.

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)



<a name="loioede077617d9d4181b5c755fed15e56c3__roles"/>

## User Roles

The REST API supports different user roles. Depending on the role, an API grants or denies access. In default configuration, the Cloud Connector uses local user storage and supports the single user *Administrator* \(administrator role\). Using LDAP user storage, you can use various users:


<table>
<tr>
<th valign="top">

Role

</th>
<th valign="top">

Technical Role Name

</th>
<th valign="top">

Authorization

</th>
</tr>
<tr>
<td valign="top">

Administrator

</td>
<td valign="top">

admin or sccadmin

</td>
<td valign="top">

All operations.

</td>
</tr>
<tr>
<td valign="top">

Support

</td>
<td valign="top">

sccsupport

</td>
<td valign="top">

Edit log and trace configuration.

</td>
</tr>
<tr>
<td valign="top">

Display

</td>
<td valign="top">

sccdisplay

</td>
<td valign="top">

Read configuration.

</td>
</tr>
<tr>
<td valign="top">

Monitoring

</td>
<td valign="top">

sccmonitoring

</td>
<td valign="top">

Read monitoring information.

</td>
</tr>
</table>

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)



<a name="loioede077617d9d4181b5c755fed15e56c3__return"/>

## Return Codes

Successful requests return the code 200, or, if there is no content, 204. POST actions that create new entities return 201, with the location link in the header \(that is, the value of the header field *location* is the full URI of the entity created\).

The following general errors can be returned by each API:

-   400 – Invalid request. For example, if parameters are invalid or the API is not supported anymore, or an unexpected state occurs, as well as in case of other non-critical errors.
-   401 – Authentication is required and has failed or no credentials have been provided.
-   403 – Request is not allowed. Either the user does not have permission to invoke the API or the initial password has not been changed yet.
-   404 – The specified entity does not exist.
-   405 – An entity does not support the requested operation.
-   409 – Current state of the Cloud Connector does not allow a particular request as it conflicts with certain rules or violates certain constraints.
-   415 – Unexpected MIME type.
-   500 – Operation failed.

Most APIs return specific error details depending on the situation. Such errors are addressed by the respective API description.

> ### Remember:  
> The Cloud Connector forbids simultaneous changes on a subaccount from different clients. A subaccount used by the Cloud Connector UI is blocked for changes made from other instances. Even just *selecting* a subaccount in the Cloud Connector dashboard \(displaying the list of all subaccounts\) blocks this subaccount. If you have selected more than one subaccount, the first one in the list is blocked.
> 
> Operations on blocked resources raise an error. In this case, REST APIs return the code *409*.

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)



<a name="loioede077617d9d4181b5c755fed15e56c3__hyper"/>

## Hypertext Application Language

Entities returned by the APIs contain links as suggested by the current draft *JSON Hypertext Application Language* \(see [https://tools.ietf.org/html/draft-kelly-json-hal-08](https://tools.ietf.org/html/draft-kelly-json-hal-08)\).

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)



<a name="loioede077617d9d4181b5c755fed15e56c3__apis"/>

## Available REST APIs

The Cloud Connector provides APIs for:

[Monitoring tasks](monitoring-apis-f6e7a7b.md)

[Configuration tasks](configuration-rest-apis-cfb9d57.md)

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)



<a name="loioede077617d9d4181b5c755fed15e56c3__code"/>

## Sample Code

Some APIs include examples with command line invocations typically involving curl. The use of single and double quotes in those examples depends on the operating system and may have to be adapted.

Back to [Top](rest-apis-ede0776.md#loioede077617d9d4181b5c755fed15e56c3__top)

