<!-- loio1b1c3b791a9c4adb9120266d64b87cf5 -->

# Multiple Destination Service Instances

The Destination service lets you declaratively model a technical connection as a destination configuration, and find via its REST APIs the destination configuration that is required to access a remote service or system from your Kubernetes workload.

To integrate the Transparent Proxy with the Destination Service, you must:

1.  Create a Destination service instance or reuse an existing one.
2.  Create a service key for the service instance.
3.  Follow the instructions in step [Prepare Destination service instance credentials](destination-service-integration-cd02e5c.md) to pair with the Destination service. This involves referencing a secret that contains the base64-encoded service key for the Destination service.
4.  Check the [Configuration Guide](configuration-guide-2a22cd7.md) for *config.integration.destinationService.instances*.

The Transparent Proxy can consume SAP BTP destinations from multiple Destination service instances. They are specified in the Transparent Proxy configuration.

**Integration with Multiple Destination Service Instances**

> ### Sample Code:  
> ```
> config:
>   integration:
>     destinationService:
>        ## Name of the default destination service instance to be used when 'destinationServiceInstanceName' is not provided in the Destination Custom Resource spec.
>        #defaultInstanceName: dest-service-instance
>        instances:
>     ##     Name of the destination service instance that is described. It could be used as config.integration.destinationService.defaultInstanceName or it can be referenced in the Destination Custom Resource spec as destinationServiceInstanceName.
>           - name: dest-service-instance
>             serviceCredentials:
>     ##         The key in the Destination service secret resource, which holds the base64 encoded value of the destination service key. (info) Make sure to provide the right key for an existing secret. Required when Transparent Proxy should create secret and not required when describing an existing secret.
>               secretKey: <secret-key>
>     ##         The name of the existing secret, which holds the credentials for the Destination service or the name of the secret to be created based on "secretName", "secretData", "secretKey" fields.
>               secretName: <secret-name>
>     ##         The base64 encoded value of the service key, obtained from the Destination service instance. Required when Transparent Proxy should create secret and not required when describing an existing secret.
>               secretData: <secret-data>
>     ##         The namespace of the existing secret to be used, which holds the credentials for the Destination service. This field should not be present if there is no existing secret and Transparent Proxy would create one based on "secretName", "secretData", "secretKey" fields
>     #          secretNamespace: <secret-namespace>
>     #          privateKey:
>     ##           The name of K8s secret, which holds the private key to authenticate if using an x509-based service key to the Destination service.
>     #            secretName: <x509-svc-key-secret-name>
>     ##           The name of the internal key inside the K8s secret holding the private key to authenticate if using an x509-based service key to the Destination service.
>     #            secretInternalKey: <key>
>     ##     Name of the destination service instance that is described. It could be used as config.integration.destinationService.defaultInstanceName or it can be referenced in the Destination Custom Resource spec as destinationServiceInstanceName.
>           - name: dest-service-instance-2
>             serviceCredentials:
>     ##         The key in the Destination service secret resource, which holds the base64 encoded value of the destination service key. (info) Make sure to provide the right key for an existing secret. Required when Transparent Proxy should create secret and not required when describing an existing secret.
>               secretKey: <secret-key>
>     ##         The name of the existing secret, which holds the credentials for the Destination service or the name of the secret to be created based on "secretName", "secretData", "secretKey" fields.
>               secretName: <secret-name>
>     ##         The namespace of the existing secret to be used, which holds the credentials for the Destination service. This field should not be present if there is no existing secret and Transparent Proxy would create one based on "secretName", "secretData", "secretKey" fields
>     #          secretNamespace: <secret-namespace>
>     #          privateKey:
>     ##           The name of K8s secret, which holds the private key to authenticate if using an x509-based service key to the Destination service.
>     #            secretName: <x509-svc-key-secret-name>
>     ##           The name of the internal key inside the K8s secret holding the private key to authenticate if using an x509-based service key to the Destination service.
>     #            secretInternalKey: <key>
> ```

A specific instance of the Destination service will be selected by the Transparent Proxy based on the following rules:

If the \`defaultInstanceName\` is provided in the Transparent Proxy configuration, the \`destinationServiceInstanceName\` field in the destination custom resource specification becomes optional.

In cases where two different Destination service instance names are specified, the one in the destination custom resource specification will be prioritized.

**Example with a Default Destination Service Instance** 

> ### Sample Code:  
> ```
> integration:
>   destinationService:
>     ## Local name of the default Destination service instance to be used when 'destinationServiceInstanceName' is not provided in the destination custom resource spec.
>     defaultInstanceName: dest-service-instance
> ```

**Example with a Destination Service Instance Name** 

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: example-dest
> spec: 
>   destinationRef:
>     name: "example-dest-client-cert"
>   destinationServiceInstanceName: dest-service-instance-example // can be ommited if config.integration.destinationService.defaultInstanceName is provided
> ```

> ### Note:  
> For more details about configuring the Transparent Proxy, check the [Configuration Guide](configuration-guide-2a22cd7.md).

