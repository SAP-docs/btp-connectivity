<!-- loio9fdad3cad92e4b63b73d5772014b380e -->

# Create and Bind a Destination Service Instance

To use the Destination service in your application, you need an instance of the service.



<a name="loio9fdad3cad92e4b63b73d5772014b380e__section_bzt_wqq_2nb"/>

## Concept

To consume the Destination service, you must provide the appropriate credentials through a service instance and a service binding/service key. The Destination service is publicly visible and cross-consumable from several environments and provides the service plan *lite* to all those environments. Provisioning a service instance and service key is done in the standard way for the respective environment, see:

-   Cloud Foundry: [Using Services in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f22029f0e7404448ab65f71ff5b0804d.html "Learn more about using services in the Cloud Foundry environment, how to create (user-provided) service instances and bind them to applications, and how to create service keys.") :arrow_upper_right:
-   Kyma: [Using SAP BTP Services in the Kyma Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ea4dd81e49254dd482d32e3c20f4477a.html#loioea4dd81e49254dd482d32e3c20f4477a "With the Kyma environment, you can connect SAP BTP services to your cluster and manage them using SAP BTP Service Operator.") :arrow_upper_right:
-   Kubernetes: [Consuming SAP BTP Services in Kubernetes with SAP Service Manager Broker Proxy (Service Catalog)](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Validation/en-US/20195bf3b6e64189966e08f669c275e1.html "") :arrow_upper_right:
-   Other environments: [Consuming Services in Other Environments Using the SAP Service Manager Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Validation/en-US/0714ac254e83492281d95e25548b388c.html "Consume SAP BTP services from any runtime environment by creating service instances and service bindings directly in your subaccount with the Service Manager Control (SMCTL) CLI or APIs.") :arrow_upper_right:

In all environments, the Destination service lets you provide a configuration JSON during instance creation or update.



<a name="loio9fdad3cad92e4b63b73d5772014b380e__procedure_ds"/>

## Using a Configuration JSON

You can pass a configuration JSON during instance creation or update to modify some of the default settings of the instance and/or provide some content to be created during the operation.

The detailed structure of the configuration JSON is described in [Use a Config.JSON to Create or Update a Destination Service Instance](use-a-config-json-to-create-or-update-a-destination-service-instance-6816d3c.md).



<a name="loio9fdad3cad92e4b63b73d5772014b380e__cli_ds"/>

## Troubleshooting

If you get this failure message:

```
Failed to create all provided configurations. Will delete all on instance level, for configurations on subaccount level you can set policies to handle duplicates: "existing_destinations_policy" with value "update|fail|ignore" and "existing_certificates_policy" with value "fail|ignore".

```

the root cause may be:

-   A provided destination or certificate with the same name already exists in this subaccount. Solution: set policies on subaccount level to update or ignore in case of conflicts.

    ```
    "existing_destinations_policy": "update|fail|ignore"
    "existing_certificates_policy: "fail|ignore"
    ```

-   A client input error occurred. Solution: check the input, apply correction and try again.
-   An internal server error occurred. In this case, please try again later or report a support incident.



## X.509 Bindings

> ### Note:  
> Older instances of the service do not support the X.509 credentials binding type and an attempt to create one will result in an error. To overcome this, you just need to update the service instance, so it picks up the X.509 support.

The service supports X.509 bindings as described in [Retrieving Access Tokens with Mutual Transport Layer Security (mTLS)](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f60c8e724bb8496eae10ed29e896766a.html "Mutual Transport Layer Security (mTLS) is considered more secure than the combination of client ID and client secret. Unlike retrieving the access token with client ID and client secret, no secret is shared between calling application and the service instance of SAP Authorization and Trust Management service (XSUAA).") :arrow_upper_right:. This lets you choose if your binding / service key will be with a client secret X.509 certificate generated by SAP or an X.509 certificate provided by you. To do so, add a config JSON when creating your binding:

```
cf bind-service <app-name> <service-name> [-c <config json>]

```

The structure of the config JSON should be like this:

```
{
    "xsuaa":
    {
        <X.509 properties>
    },
    <other config parameters>
}
```

For a list of the supported X.509 properties, see:

-   [Parameters for X.509 Certificates Managed by SAP Authorization and Trust Management Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/436ed684eadc4045881e59bd1048d98d.html "Use the parameters to have the service generate X.509 certificates for you.") :arrow_upper_right:
-   [Parameters for Self-Managed X.509 Certificates](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5168df615064457eafe3e48e10a95665.html "Use these parameters to provide your own certificates for a binding or service key to service instances of the SAP Authorization and Trust Management service (XSUAA).") :arrow_upper_right: 

> ### Note:  
> By default, without providing a config JSON, a binding with client secret will be created.
