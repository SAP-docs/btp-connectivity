<!-- loio92224c0b5ea048b3993a0683c5b7b4ae -->

# Sizing for the Shadow Instance

Learn more about the basic criteria for the sizing of your Cloud Connector shadow instance \(high availability mode\).

The shadow installation is typically not used in standard situations and hence does not need the same sizing, assuming that the time span in which it takes over the master role is limited.

> ### Note:  
> The shadow only acts as master, for example, during an upgrade or when an abnormal situation occurs on the master machine, and either the Cloud Connector or the full machine on OS level needs to be restarted.

While being in the shadow state, the resource consumption is very low, especially in productive environments, where typically only few configuration changes are required. Therefore, the machine sizing can usually be smaller than the one for the master. However, if you want to mitigate the risk of a longer outage of the master machine, you should increase the sizing of the shadow up to the master size:


<table>
<tr>
<th valign="top">

Master

</th>
<th valign="top">

Shadow

</th>
</tr>
<tr>
<td valign="top">

**S**

</td>
<td valign="top">

**S** installation as virtual machine

</td>
</tr>
<tr>
<td valign="top">

**M**

</td>
<td valign="top">

**S** installation \(with double memory\) as virtual or physical machine

**M** installation as virtual or physical machine for risk mitigation

</td>
</tr>
<tr>
<td valign="top">

**L**

</td>
<td valign="top">

**M** installation as virtual or physical machine

**L** installation as virtual or physical machine for risk mitigation

</td>
</tr>
<tr>
<td valign="top">

**XL**

</td>
<td valign="top">

**L** installation as virtual or physical machine

**XL** installation as virtual or physical machine for risk mitigation

</td>
</tr>
</table>

