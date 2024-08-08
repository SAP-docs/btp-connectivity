<!-- loiob08590694eac43a7ad21e33b391f13cf -->

# Destination Fragments

Destination fragments are objects used to override and extend destination properties through the Destination service REST API.

You can use destination fragments to override and/or extend destination properties as result of the “Find a destination” REST API request. Destination fragments are key-value based objects which contain a name for identification and additional configurable properties.


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

Name of the destination fragment. Must be unique for the level on which it is stored/maintained.

</td>
</tr>
</table>

> ### Restriction:  
> The destination fragment must not contain the properties `Name` or `Type`.

> ### Caution:  
> Only one destination fragment can be configured in a destination.

Managing destination fragments for your application is supported only by the Destination service REST API. This API is documented in the [SAP Business Accelerator Hub](https://api.sap.com/package/scpconnectivity/rest).

**Related Information**  


[Extending Destinations with Fragments](extending-destinations-with-fragments-f56600a.md "Use the “Find Destination” API to extend your destination with a destination fragment.")

[Calling the Destination Service REST API](calling-the-destination-service-rest-api-84c5d38.md "Prerequisites and steps to get access to the Destination service REST API.")

