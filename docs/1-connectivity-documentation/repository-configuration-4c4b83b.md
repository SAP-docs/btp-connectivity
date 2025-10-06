<!-- loio4c4b83b73f0242f8b336dcdc1bc3a02e -->

# Repository Configuration

JCo properties that allow you to define the behavior of the repository that dynamically retrieves function module metadata.

All properties below are optional. Alternatively, you can create the metadata in the application code, using the metadata factory methods within the `JCo` class, to avoid additional round-trips to the on-premise system.


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

`jco.destination.repository_destination`

</td>
<td valign="top">

Specifies which destination should be used for repository queries. If the destination does not exist, an error occurs when trying to retrieve the repository. Defaults to itself.

</td>
</tr>
<tr>
<td valign="top">

`jco.destination.repository.user`

</td>
<td valign="top">

Optional property. If this property is set, and the repository destination is not set, it is used as the user for repository queries. This configuration option allows using a different user for repository lookups with a single destination configuration, and restricting this user's permissions accordingly. See also SAP Note [460089](https://me.sap.com/notes/460089).

> ### Note:  
> When working with the *Destinations* editor in the cockpit, enter the value in the *<Repository User\>* field. Do not enter it as additional property.



</td>
</tr>
<tr>
<td valign="top">

`jco.destination.repository.passwd`

</td>
<td valign="top">

Represents the password for a repository user. If you use such a user, this property is mandatory.

> ### Note:  
> When working with the *Destinations* editor in the cockpit, enter this password in the *<Repository Password\>* field. Do not enter it as additional property.



</td>
</tr>
<tr>
<td valign="top">

`jco.destination.repository.check_interval`

</td>
<td valign="top">

Time interval in minutes after which the associated repository is regularly checked for outdated metadata in its local cache. If outdated metadata are identified, they will be removed from the cache.

The default value is 0 \(repository checking feature is disabled\).

If multiple repository destination configurations refer to the same repository instance, the smallest configured *non-zero* value of all destinations will be effective for the repository. Therefore, the repository checking feature is only switched off if *all* repository destinations for the repository instance are configured with value 0, or do not specify this property.

> ### Note:  
> The configured value will only be considered if the respective destination can be used for repository metadata queries. It will be ignored if `jco.destination.repository_destination` has been configured. In this case, the property `jco.destination.repository.check_interval` must be configured in the referred repository destination instead to activate this checking feature.



</td>
</tr>
</table>

**Related Information**  


[Invoking ABAP Function Modules via RFC](invoking-abap-function-modules-via-rfc-fa4adc9.md "Call a remote-enabled function module in an on-premise or cloud ABAP server from your application, using the RFC protocol.")

