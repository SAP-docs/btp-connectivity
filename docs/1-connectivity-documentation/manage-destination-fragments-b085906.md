<!-- loiob08590694eac43a7ad21e33b391f13cf -->

# Manage Destination Fragments

Destination fragments are objects used to override and extend destination properties through the Destination service REST API.

You can use destination fragments to override and/or extend destination properties as result of the [“Find a Destination” REST API request](calling-the-destination-service-rest-api-84c5d38.md). These properties are key-value based objects which contain a name for identification and additional configurable properties.

The structure of the destination fragment is the following:


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

FragmentName

</td>
<td valign="top">

Mandatory. Name of the destination fragment. It must be unique for the level on which it is stored/maintained.

</td>
</tr>
<tr>
<td valign="top">

key1

</td>
<td valign="top">

Optional. Holds the respective value for key1.

</td>
</tr>
<tr>
<td valign="top">

key2

</td>
<td valign="top">

Optional. Holds the respective value for key2.

</td>
</tr>
<tr>
<td valign="top">

keyN

</td>
<td valign="top">

Optional. Holds the respective value for keyN.

</td>
</tr>
</table>

> ### Restriction:  
> The destination fragment must not contain the properties `Name` or `Type`.

> ### Caution:  
> Only a single destination fragment can be used when requesting a destination via the “Find a Destination” REST API.

> ### Caution:  
> Destination fragments can be used only at runtime by the client of the Destination service when executing the request to the “Find a Destination” REST API.

Managing destination fragments for your application is supported only by the Destination service REST API. This API is documented in the [SAP Business Accelerator Hub](https://api.sap.com/package/scpconnectivity/rest).

**Related Information**  


[Extending Destinations with Fragments](extending-destinations-with-fragments-f56600a.md "Use the “Find a Destination” API to extend your destination with a destination fragment.")

[Calling the Destination Service REST API](calling-the-destination-service-rest-api-84c5d38.md "Prerequisites and steps to get access to the Destination service REST API.")

