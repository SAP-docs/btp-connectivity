<!-- loio13f633ee2a9645f5b1cbf9eb841784c0 -->

# Sequential User Propagation Chain

Use a predefined destination chain to exchange a user token for another user token, which will then be used to perform a user propagation flow.

This predefined destination chain simplifies the process of transforming and consuming a user token. The chain works in a 2-step process:

1.  The first step uses one destination to generate a user token using the user token provided by the user.
2.  The second step uses the destination specified in the REST API path to consume the generated user token. How this token will be consumed is determined by the configuration properties of the destination specified in the REST API path.



<a name="loio13f633ee2a9645f5b1cbf9eb841784c0__section_xdt_2sn_2gc"/>

## Chain Variable Consumption

To successfully consume the chain, the following headers need to be included in the request to the *Find a Destination* REST API endpoint:


<table>
<tr>
<th valign="top">

Header Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`X-chain-var-tokenTransformationDestinationName`

</td>
<td valign="top">

Specifies the name of the destination that will be retrieved by the Destination service and whose properties will be used to perform the user-token-to-user-token exchange.

</td>
</tr>
<tr>
<td valign="top">

`X-chain-var-userToken`

</td>
<td valign="top">

The user token that will be used to perform the token exchange during the consumption of the destination specified by the `X-chain-var-tokenTransformationDestinationName` header.

</td>
</tr>
</table>



<a name="loio13f633ee2a9645f5b1cbf9eb841784c0__section_bhp_2sn_2gc"/>

## Optional Headers


<table>
<tr>
<th valign="top">

Header Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`X-chain-var-tokenTransformationFragmentName` 

</td>
<td valign="top">

Specifies the name of a destination fragment that will be used to override and/or extend the properties of the destination specified by the `X-chain-var-tokenTransformationDestinationName` header. In case of overlapping properties, the values of the fragment properties take priority over the values of the destination properties.

</td>
</tr>
<tr>
<td valign="top">

`X-chain-var-tokenTransformationFragmentOptional` 

</td>
<td valign="top">

Marks whether the destination fragment provided with the `X-chain-var-tokenTransformationFragmentName` is optional. If the fragment is marked as optional and it does not exist, the destination with its original properties will be consumed. If the fragment is not marked as optional and it does not exist, the request will fail.

This header is only applicable if the `X-chain-var-tokenTransformationFragmentName` header is present. If this header is applicable but not provided, the default value will be *false*.

</td>
</tr>
</table>

