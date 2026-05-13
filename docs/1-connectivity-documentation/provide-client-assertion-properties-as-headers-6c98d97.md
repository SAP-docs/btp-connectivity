<!-- loio6c98d97155434f94a47597c04ab37737 -->

# Provide Client Assertion Properties as Headers

Provide client assertion properties as headers when using client assertion with OAuth flows for a destination.



## Properties

To configure a destination of this authentication type, you must specify all the required properties.

**Additional Properties**


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`X-client-assertion-type`

</td>
<td valign="top">

Absolute URI

</td>
</tr>
<tr>
<td valign="top">

`X-client-assertion`

</td>
<td valign="top">

Token

</td>
</tr>
</table>

**Example of Client Assertion Properties as Headers**

To use the client assertion mechanism in the *Find Destination* API, you must add two mandatory headers as shown in the following example:

> ### Sample Code:  
> ```
> curl --location --request GET 'https://<destination_service_host>/destination-configuration/v1/destinations/<destination-name>' \
> --header 'X-client-assertion-type: urn:ietf:params:oauth:client-assertion-type:jwt-bearer' \ # mandatory parameter
> --header 'X-client-assertion: eyJraWQiOiJKMWpC...' \ # mandatory parameter
> --header 'Authorization: Bearer <access_token>'
> ```

