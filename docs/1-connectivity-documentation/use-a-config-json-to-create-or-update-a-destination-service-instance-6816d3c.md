<!-- loio6816d3caeb464f8d8b0d1b5ad0da5869 -->

# Use a Config.JSON to Create or Update a Destination Service Instance

Configure specific parameters in a `config.json` file to create or update a Destination service instance.

> ### Note:  
> By default, creating or updating a Destination service instance does not require passing any configuration settings.

When creating or updating a Destination service instance, you can optionally configure the following settings, which are part of the `config.json` input file \(see [Open Service Broker API](https://www.openservicebrokerapi.org/)\), both via SAP BTP cockpit or Cloud Foundry command line interface \(CLI\):


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`HTML5Runtime_enabled`

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

Optional. Indicates whether the SAP BTP HTML5 runtime should be enabled to work with the service instance on behalf of the HTML5 applications associated with it during deployment.

> ### Note:  
> Check if the SAP BTP HTML5 runtime is available for the region in which the service instance is being created or updated.



</td>
</tr>
<tr>
<td valign="top">

`init_data`

</td>
<td valign="top">

JSON

</td>
<td valign="top">

Optional. Typically, the data for the Destination service instance is managed via BTP cockpit or REST API.

For more information, see [Managing Destinations](managing-destinations-84e45e0.md).

This option allows to add data \(destinations, certificates\) to initialise or update the service instance with. The data can be stored on both *service instance* level and *subaccount* level.

</td>
</tr>
<tr>
<td valign="top">

`subscriber_access` 

</td>
<td valign="top">

JSON

</td>
<td valign="top">

Optional. Typically, the data for the Destination service instance is managed via BTP cockpit or REST API.

For more information, see [Managing Destinations](managing-destinations-84e45e0.md).

This option allows you to define the access level for your subscribers to their configurations stored on subscription level, which are shared with them. By default, subscribers have no access.

You can specify separate scopes for both *read* and *write* operations for each entity type. If multiple scopes are defined for an operation, the subscriber must have all of them to perform the operation.

The provided scopes will either be added during instance creation or used to override the existing scopes during instance update. Each section is optional. If a section is not provided, the existing values will remain unchanged. To delete scopes, you need to provide an empty array.

</td>
</tr>
</table>

Find the `config.json` structure below:

> ### Sample Code:  
> ```
> {
>     "HTML5Runtime_enabled" : true,
>     "init_data" : {
>         "subaccount" : {
>             "existing_destinations_policy": "update|fail|ignore",
>             "existing_certificates_policy": "update|fail|ignore",
>             "destinations" : [
>                 {
>                     ...
>                 }
>             ],
>             "certificates" : [
>                 {
>                     ...
>                 }
>             ]
>         },
>         "instance" : {
>             "existing_destinations_policy": "update|fail|ignore",
>             "existing_certificates_policy": "update|fail|ignore",
>             "destinations" : [
>                 {
>                     ...
>                 }
>             ],
>             "certificates" : [
>                 {
>                     ...
>                 } 
>             ]
>         }
>     }
> }
> ```

**Related Information**  


[HTTP Destinations](http-destinations-42a0e6b.md "Find information about HTTP destinations for Internet and on-premise connections.")

