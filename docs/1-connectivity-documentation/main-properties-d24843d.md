<!-- loiod24843d84f31417ab564cdf181a57cdc -->

# Main Properties

Configure the main properties for RFC destinations in the SAP BTP cockpit.

In the *Destination Details* panel, you configure the general settings for a destination in the section *Main Properties*.


<table>
<tr>
<th valign="top">

Label in Destinations Editor

</th>
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

`Name`

</td>
<td valign="top">

Name of the destination under which it is also accessed in the application code.

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

`Type`

</td>
<td valign="top">

Type of the destination. Must be set to `RFC`.

</td>
</tr>
<tr>
<td valign="top">

Description

</td>
<td valign="top">

`jco.destination.description`

</td>
<td valign="top">

Description that explains the purpose of the concrete destination \(optional\).

</td>
</tr>
<tr>
<td valign="top">

Proxy Type

</td>
<td valign="top">

`jco.destination.proxy_type` 

</td>
<td valign="top">

The select box for the Proxy Type allows to choose between `Internet`, `OnPremise`, and `Local`.

-   When choosing `OnPremise`, the RFC communication is routed over a Cloud Connector that is connected to the subaccount.
-   When choosing `Internet`, the RFC communication is done over a WebSocket connection directly with the partner system.
-   `Local` is used to indicate that the destination is used within an *Edge Integration Cell* context.



</td>
</tr>
<tr>
<td valign="top">

Location ID

</td>
<td valign="top">

`jco.client.cloud_connector_location_id` 

</td>
<td valign="top">

You can connect multiple Cloud Connectors to a subaccount as long as their location ID is different. The value defines the location ID identifying the Cloud Connector over which the connection is opened.

The default value is an empty string identifying the Cloud Connector that is connected without any location ID, which is the default behavior when adding a subaccount in the Cloud Connector.

</td>
</tr>
</table>

