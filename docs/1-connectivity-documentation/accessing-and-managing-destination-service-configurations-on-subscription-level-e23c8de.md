<!-- loioe23c8deb86954639ac2d30b05dbc69c2 -->

# Accessing and Managing Destination Service Configurations on Subscription Level

Allow subscriber subaccount administrators of your SaaS application to manage Destination service configurations on subscription level.

By default, only the SaaS application itself can manage Destination service configurations \(destinations, certificates, and so on\) on any of the subscription levels that are associated with its service instance. This is done by fetching an access token using the instance credentials in the context of the desired subscriber account and calling the [Destination Service REST API](destination-service-rest-api-23ccafb.md).

However, every SaaS application provider can decide to allow users with specific roles in the context of the consumer subaccount to manage configurations on subscription level. This makes it easy for SaaS application consumers to share configurations with the application.



## Enablement Process for the SaaS Application

The enablement is done via properties of the Destination service instance that the SaaS application configures as a dependency. During creation or update, using a config JSON, a specification for each configuration type can be provided. Within this specification, for each operation a list of scopes needed to perform the operation can be provided.

For more information, see [Use a Config.JSON to Create or Update a Destination Service Instance](use-a-config-json-to-create-or-update-a-destination-service-instance-6816d3c.md).

To perform these operations, we recommended that you use dedicated scopes in the `xs-app.json` of the SaaS application, assigned to dedicated roles, but you can associate pre-existing scopes with the operations as well.



## Subscription Level Zones

The subscription level is divided into two virtual zones: one that is shared with the consumer subaccount and one that is strictly private to the SaaS application.

Only the shared zone is shown to the consumer subaccount and anything managed by the consumer is located in this zone.

When an SaaS application manages configurations via the REST API, by default the created configuration will be placed in the private zone. However, there is also an option to create it in the shared zone, allowing for the consumer to read and/or modify it. This is done via the `$metadata.shared_with_subscriber` property in the request body of the POST/PUT API. If set to `true`, the configuration will be available via the subscription level of the UIs.

When the SaaS application fetches configurations, the lookup is done in both zones.

> ### Restriction:  
> It is not allowed to have configurations with the same name in both zones.



## Subscription Level Access for Consumer Subaccount Users

The application will become visible to all consumer subaccounts as an available subscription level. Users will see what operations they can perform \(*read*, *read & write*, or *no access*\). This is based on their assigned roles and whether they match the scopes defined during enablement.

For more information, see [Access the Destinations Editor](access-the-destinations-editor-82ca377.md).

> ### Note:  
> It may take some time after enablement for the consumer subaccounts to see the changes taking effect. This is due to caching on the Destination service side.

