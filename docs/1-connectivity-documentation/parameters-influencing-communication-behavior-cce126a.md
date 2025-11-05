<!-- loiocce126a22e7b462fac6d4de58551e238 -->

# Parameters Influencing Communication Behavior

Configure ABAP communication properties for RFC destinations in the SAP BTP cockpit.

This group of JCo properties allows you to control the connection to an ABAP system. All properties are optional.

In the *Destinations* editor in the cockpit, the configuration must be provided in the *Communication Behavior Configuration* panel.


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

Enable protocol traces

</td>
<td valign="top">

`jco.client.trace`

</td>
<td valign="top">

Defines whether protocol traces are created.

-   If the checkbox is checked or the value in a property file is `1`, protocol traces are turned on.
-   If the checkbox is unchecked or the value in a property file is `0`, protocol traces are turned off.

The default behavior is that protocol traces are turned off.

</td>
</tr>
<tr>
<td valign="top">

SAP codepage

</td>
<td valign="top">

`jco.client.codepage`

</td>
<td valign="top">

Declares the 4-digit SAP codepage that is used when initiating the connection to the backend. The default value is `1100` \(comparable to iso-8859-1\). It is important to provide this property if the password that is used contains characters that cannot be represented in `1100`.

</td>
</tr>
<tr>
<td valign="top">

Enable table parameter delta management

</td>
<td valign="top">

`jco.client.delta`

</td>
<td valign="top">

Enables or disables table parameter delta management.

If the checkbox is checked or the value in a property file is `1`, delta management is enabled, and disabled if the checkbox is unchecked or the value in a property file is `0`.

The default behavior is that delta management is *enabled*.

</td>
</tr>
<tr>
<td valign="top">

Serialization Format

</td>
<td valign="top">

`jco.client.serialization_format`

</td>
<td valign="top">

Defines the serialization format that is used when transferring function module data to the partner system. The property impacts the serialization behavior of function module data.

Valid values are `columnBased` and `rowBased`. If you choose `columnBased`, the *fast RFC serialization* is used, as long as the partner system supports it, see SAP Note [2372888](https://me.sap.com/notes/2372888).

When choosing the `rowBased` option, *classic* or *basXML* serialization are used.

The default value is `rowBased`.

</td>
</tr>
<tr>
<td valign="top">

Network Type

</td>
<td valign="top">

`jco.client.network`

</td>
<td valign="top">

Defines which network type is expected to be used for the destination.

The property impacts the serialization behavior of function module data, see SAP Note [2372888](https://me.sap.com/notes/2372888).

Valid values are `WAN` and `LAN`. The default value is `LAN`.

</td>
</tr>
</table>

