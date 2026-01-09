<!-- loio4c4b83b73f0242f8b336dcdc1bc3a02e -->

# Repository Configuration

Configure repository properties for RFC destinations in the SAP BTP cockpit.

Repository properties let you define the behavior of the repository that dynamically retrieves function module metadata.

All properties below are optional. Alternatively, you can create the metadata in the application code, using the metadata factory methods within the `JCo` class, to avoid additional round-trips to the on-premise system.

For convenience, those metadata objects can be stored in a `CustomRepository` when using them in the application.

In the *Destinations* editor in the cockpit, the configuration must be provided in the *Repository Configuration* panel.

> ### Note:  
> **Repository Management: Background**
> 
> The built-in comfortable repository management currently uses the system ID as the identifier of a system, so destinations pointing to the same system can share the data to avoid unnecessary round-trips and memory consumption. However, this approach includes a drawback \(described also in SAP Note [1405466](https://me.sap.com/notes/1405466)\): if you merge multiple networks over multiple Cloud Connectors in a single scenario, the probability of duplicate system IDs increases. As a consequence, collisions of different metadata definitions in those systems may cause issues. If duplicates are likely to be expected, using a `CustomRepository` and an application-managed set of repositories is a recommended workaround for this limitation.


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

Repository Destination

</td>
<td valign="top">

`jco.destination.repository_destination`

</td>
<td valign="top">

Specifies which destination should be used for repository queries. If the destination does not exist, an error occurs when trying to retrieve the repository. Defaults to itself.

> ### Note:  
> The selectbox is visible in the *Destinations* editor only if the selected option for *Repository Configuration Type* is `Repository Destination`.



</td>
</tr>
<tr>
<td valign="top">

Repository User

</td>
<td valign="top">

`jco.destination.repository.user`

</td>
<td valign="top">

Optional property. If this property is set, and the repository destination is not set, it is used as the user for repository queries. This configuration option allows using a different user for repository lookups with a single destination configuration, and restricting this user's permissions accordingly.

See also SAP Note [460089](https://me.sap.com/notes/460089).

> ### Note:  
> The input field is visible in the *Destinations* editor only if the selected option for *Repository Configuration Type* is *Repository Basic Credentials*. When selecting the option *Repository Default Credentials*, the credential settings for repository connections will be the same as for business connections.



</td>
</tr>
<tr>
<td valign="top">

Repository Password

</td>
<td valign="top">

`jco.destination.repository.passwd`

</td>
<td valign="top">

Represents the password for a repository user. If you use such a user, this property is mandatory.

> ### Note:  
> The input field is visible in the *Destinations* editor only, if the selected option for *Repository Configuration Type* is *Repository Basic Credentials*.



</td>
</tr>
<tr>
<td valign="top">

Check Interval

</td>
<td valign="top">

`jco.destination.repository.check_interval`

</td>
<td valign="top">

Time interval in minutes after which the associated repository is regularly checked for outdated metadata in its local cache. If outdated metadata are identified, they will be removed from the cache.

The default value is 0 \(repository checking feature is disabled\).

If multiple repository destination configurations refer to the same repository instance, the smallest configured *non-zero* value of all destinations will be effective for the repository. Therefore, the repository checking feature is only switched off if *all* repository destinations for the repository instance are configured with value 0, or do not specify this property.

> ### Note:  
> The configured value will only be considered when creating a destination from a properties file, if the respective destination can be used for repository metadata queries, and it will be ignored if `jco.destination.repository_destination` has been configured. In the latter case, the property `jco.destination.repository.check_interval` must be configured in the referred repository destination instead in order to activate this checking feature.
> 
> For the same reason, the input field is visible in the *Destinations* editor only if the selected option for *Repository Configuration Type* is not *Repository Destination*.



</td>
</tr>
</table>

**Related Information**  


[Invoking ABAP Function Modules via RFC](invoking-abap-function-modules-via-rfc-fa4adc9.md "Call a remote-enabled function module in an on-premise or cloud ABAP server from your application, using the RFC protocol.")

