<!-- loio8aeea65eb9d64267b554f64a3db8a349 -->

# Create Destinations Using the MTA Descriptor

Use the multitarget-application \(MTA\) descriptor to manage destinations for complex deployments.



<a name="loio8aeea65eb9d64267b554f64a3db8a349__content"/>

## Content

-   [Concept](create-destinations-using-the-mta-descriptor-8aeea65.md#loio8aeea65eb9d64267b554f64a3db8a349__concept)
-   [Content Deployment](create-destinations-using-the-mta-descriptor-8aeea65.md#loio8aeea65eb9d64267b554f64a3db8a349__deployment)
-   [Create a Destination on Service Instance Creation](create-destinations-using-the-mta-descriptor-8aeea65.md#loio8aeea65eb9d64267b554f64a3db8a349__json)



<a name="loio8aeea65eb9d64267b554f64a3db8a349__concept"/>

## Concept

When modeling a multitarget application \(MTA\), you can create and update destinations from your MTA descriptor.

For more information on MTA, see [Multitarget Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d04fc0e2ad894545aebfd7126384307c.html "A multitarget application (MTA) is essentially a single application that consists of multiple parts. These parts are created using various technologies and share the same lifecycle.") :arrow_upper_right:.

Back to [Content](create-destinations-using-the-mta-descriptor-8aeea65.md#loio8aeea65eb9d64267b554f64a3db8a349__content)



<a name="loio8aeea65eb9d64267b554f64a3db8a349__deployment"/>

## Content Deployment

When modeling MTAs, you can configure content deployments \(for more information, see [Deploying Content with Generic Application Content Deployment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3e23196166b443db17b3545c912dfc0.html "This approach provides a mechanism for direct content deployment from SAP Cloud Deployment service to the content backend without the need for an intermediate Cloud Foundry application.") :arrow_upper_right:\). The Destinations service supports such content deployments, which lets you create or update destinations by modeling them in the MTA descriptor. Other operations, like deleting a destination, are not supported by this method.



### **Parameters**

The parameters of the content deployment have the following structure:

```
content:
  subaccount:
    existing_destinations_policy: <policy> # optional, default value is "fail". See "Existing destinations policy" for more details
    destinations:
    - <destination descriptor 1> # See "Modeling options" to learn about the structure of this descriptor
    ...
    - <destination descriptor N> # See "Modeling options" to learn about the structure of this descriptor
  instance:
    existing_destinations_policy: <policy> # optional, default value is "fail". See "Existing destinations policy" for more details
    destinations:
    - <destination descriptor 1> # See "Modeling options" to learn about the structure of this descriptor
    ...
    - <destination descriptor N> # See "Modeling options" to learn about the structure of this descriptor
```

> ### Note:  
> Both the `subaccount` and `instance` sections are optional. They can both be present at the same time, or only one of them. They define the level on which the resulting destination is created.

**Existing Destinations Policy**

The `existing_destinations_policy` setting allows you to control what happens if a destination with the same name already exists. The possible values are:

-   `fail`: Treat it as an error situation and fail the deployment. This is the default value of the setting.
-   `ignore`: Keep what is currently saved in the Destination service, and skip deployment for this destination.
-   `update`: Override what is currently saved in the Destination service.

**Modeling Options** 

The `destinations` section represents an array of destination descriptors. Each of these array elements is converted to a destination and saved in the service on the respective level, based on the existing destination policy. The following options are available for modeling a destination descriptor via content deployment. They can be combined:



### **Destination Pointing to a Service Instance**

This option lets you:

-   Reference a service instance and a service key
-   Specify a destination name
-   Enter a description for the resulting destination \(optional\)
-   Add additional properties and override default properties \(optional\)

As a result, a destination is created, based on the properties in the referenced service key.

> ### Note:  
> This function is equivalent to the [Destinations Pointing to Service Instances](destinations-pointing-to-service-instances-685f383.md) template.

> ### Caution:  
> This feature is applicable for a selected set of the most commonly used services \(from a Destination service perspective\). If you would like to use this feature for a service which is not yet supported, let us know by opening a support ticket, see [Connectivity Support](connectivity-support-e5580c5.md).
> 
> In the meantime, you can follow the steps described in [Create Destinations from Scratch](create-destinations-from-scratch-5eba623.md).

The descriptor may have the following structures:

*Without client-provided service credentials:*

```
Name: <name> # name of the destination
Description: <description> # optional, a description for the destination
Authentication: <auth> # optional for some services (the default is service specific). Some services require the Authentication to be specified, like the workflow service. The allowed authentication types are also service-specific
ServiceInstanceName: <instance name> # the name of the service instance to which the destination will be created
ServiceKeyName: <service key name> # the service key of the instance targeted by ServiceInstanceName which will be used as the source for the destination values
AdditionalProp1: <value1> # optional
...
AdditionalPropN: <valueN> # optional
```

Applicable for:

-   Service bindings of type "x509" which contain both a public and private key in the service key credentials
-   Service bindings of type "clientsecret"

*With client-provided service credentials:*

```
Name: <name> # name of the destination
Description: <description> # optional, a description for the destination
Authentication: <auth> # optional for some services (the default is service specific). Some services require the Authentication to be specified, like the workflow service. The allowed authentication types are also service-specific
ServiceInstanceName: <instance name> # the name of the service instance to which the destination will be created
ServiceKeyName: <service key name> # the service key of the instance targeted by ServiceInstanceName which will be used as the source for the destination values
ServiceCredentials: # the credentials of the service key which will be provided by the client
  PrivateKey: <value>
  ...
AdditionalProp1: <value1> # optional
...
AdditionalPropN: <valueN> # optional
```

Applicable for:

-   Service bindings of type "x509" which contain only the public key in the service key credentials



### **Destination Pointing to a Resource Protected by an XSUAA Service Instance**

This option lets you:

-   Reference a service instance and a service key
-   Specify a destination name
-   Enter a description for the resulting destination \(optional\)
-   Specify the URL of the target resource
-   Add additional properties and override default properties \(optional\)

As a result, a destination is created with the token service configuration based on the properties in the referenced service key, while the URL will be the one specified when modeling the destination.

The descriptor may have the following structures:

*Without client-provided service credentials:*

```
Name: <name> # name of the destination
Description: <description> # optional, a description for the destination
Authentication: <auth> # optional for some services (the default is service specific). Some services require the Authentication to be specified, like the workflow service. The allowed authentication types are also service-specific
URL: <url> # the URL of the target resource
TokenServiceInstanceName: <instance name> # the name of the service instance used for protecting the target resource
TokenServiceKeyName: <service key name> # the service key of the instance targeted by ServiceInstanceName which will be used as the source for the token service values in the destination
AdditionalProp1: <value1> # optional
...
AdditionalPropN: <valueN> # optional
```

Applicable for:

-   Service bindings of type "x509" which contain both a public and private key in the service key credentials
-   Service bindings of type "clientsecret"

*With client-provided service credentials:*

```
Name: <name> # name of the destination
Description: <description> # optional, a description for the destination
Authentication: <auth> # optional for some services (the default is service specific). Some services require the Authentication to be specified, like the workflow service. The allowed authentication types are also service-specific
URL: <url> # the URL of the target resource
TokenServiceInstanceName: <instance name> # the name of the service instance used for protecting the target resource
TokenServiceKeyName: <service key name> # the service key of the instance targeted by ServiceInstanceName which will be used as the source for the token service values in the destination
TokenServiceCredentials: # the credentials of the service key which will be provided by the client
  PrivateKey: <value>
AdditionalProp1: value1 # optional
...
AdditionalPropN: valueN # optional
```

Applicable for:

-   Service bindings of type "x509" which contain only the public key in the service key credentials

**Example:**

```
_schema-version: "3.2"
ID: example
version: 0.0.1
modules:
- name: myapp
  path: ./myapp
  type: javascript.nodejs
  requires:
  - name: xsuaa_service
  provides:
  - name: myapp-route
    properties:
      url: ${default-url} #generated during deployment
- name: destination-content
  type: com.sap.application.content
  requires:
  - name: xsuaa_service
    parameters:
      service-key:
        name: xsuaa_service-key
  - name: destination-service
    parameters:
      content-target: true
  - name: myapp-route
  build-parameters:
    no-source: true
  parameters:
    content:
      subaccount:
        existing_destinations_policy: update
        destinations:
        - Name: myappOauth
          URL: ~{myapp-route/url}
          Authentication: OAuth2ClientCredentials
          TokenServiceInstanceName: xsuaa_service
          TokenServiceKeyName: xsuaa_service-key
          myAdditionalProp: myValue
        - Name: workflowOauthJwtBearer
          Authentication: OAuth2JWTBearer
          ServiceInstanceName: workflow_service
          ServiceKeyName: workflow_service-key
      instance:
        existing_destinations_policy: update
        destinations:
        - Name: workflowBasicAuthentication
          Authentication: BasicAuthentication
          ServiceInstanceName: workflow_service
          ServiceKeyName: workflow_service-key
          myAdditionalProp: myValue
resources:
- name: xsuaa_service
  type: org.cloudfoundry.managed-service
  parameters:
    service: xsuaa
    service-name: xsuaa_service
    service-plan: application
    config:
      xsappname: "myApp"
- name: workflow_service
  type: org.cloudfoundry.managed-service
  parameters:
    service: workflow
    service-name: workflow_service
    service-plan: lite
- name: destination-service
  type: org.cloudfoundry.managed-service
  parameters:
    service: destination
    service-name: my-destination-service
    service-plan: lite
```

Back to [Content](create-destinations-using-the-mta-descriptor-8aeea65.md#loio8aeea65eb9d64267b554f64a3db8a349__content)



<a name="loio8aeea65eb9d64267b554f64a3db8a349__json"/>

## Create a Destination on Service Instance Creation

The MTA descriptor lets you create service instances and provide a JSON configuration for this operation. You can use this functionality to create a Destination service instance with a JSON, and include the required data to create or update destinations.

For more details, see [Use a Config.JSON to Create or Update a Destination Service Instance](use-a-config-json-to-create-or-update-a-destination-service-instance-6816d3c.md).

Back to [Content](create-destinations-using-the-mta-descriptor-8aeea65.md#loio8aeea65eb9d64267b554f64a3db8a349__content)

