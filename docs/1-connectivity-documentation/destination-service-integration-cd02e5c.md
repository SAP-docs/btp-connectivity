<!-- loiocd02e5cca9f641e1854107641b41886a -->

# Destination Service Integration

Integrate the Transparent Proxy for Kubernetes with the SAP BTP Destination service.

The Destination service lets you declaratively model a technical connection as a destination configuration, and via its REST APIs find the destination configuration that is required to access a remote service or system from your Kubernetes workload. To integrate the Transparent Proxy with the Destination service, you must:

1.  Create a Destination service instance or reuse an existing one.
2.  Create a service key of the service instance.
3.  Prepare Destination service instance credentials
    -   Option 1. Reference a Kubernetes secret

        -   You can create a Kubernetes secret holding your Destination service instance key by executing this command:

            **Create a Kubernetes Secret** 

            > ### Sample Code:  
            > ```
            > kubectl create secret generic <secret-name> --from-literal=<secret-key>=<destination-service-instance-key> -n <namespace>
            > ```

        -   Reference the Kubernetes secret by providing \`config.integration.destinationService.instances\[n\].serviceCredentials.secretName\`. The secret data format can be either single-key or multi-key \(e.g., secrets created by the BTP Operator for services and bindings inside a Kubernetes cluster\).
            -   If the secret data key format is single-key, you should also provide the value of that key as \`config.integration.destinationService.instances\[n\].serviceCredentials.secretKey\`.

            -   If the secret is not in the same namespace as the Transparent Proxy, also provide \`config.integration.destinationService.instances\[n\].serviceCredentials.secretNamespace\`.


    -   Option 2. Pass a secret holding the Destination service key directly in the Helm values.yaml
        -   Get the service key of the Destination service instance.

        -   Base64 encode the service key and place it in the values.yaml for config.integration.destinationService.instances\[n\].serviceCredentials.secretData. Check the [Configuration Guide](configuration-guide-2a22cd7.md).

            > ### Note:  
            > The base64 encoded value of the service key can only be specified during [Installation with Helm](installation-with-helm-d201be0.md).

            > ### Note:  
            > For x509-based service keys with self-signed certificates prepare a Kubernetes secret holding the private key for the certificate.
            > 
            > Example: *kubectl create secret generic x509-svc-key-private-key --from-file=pk.pem*
            > 
            > If using another secret name or internal key in the secret, provide the required parameters \(`config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretName` and
            > 
            > `config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretInternalKey`\) in the `values.yaml`.



4.  Check the [Configuration Guide](configuration-guide-2a22cd7.md) for the `config.integration.destinationService.instances` property.

**Destination Service Integration**

> ### Sample Code:  
> ```
> config:
>   integration:
>     destinationService:
>       ## Name of the default destination service instance to be used when 'destinationServiceInstanceName' is not provided in the Destination Custom Resource spec.
>       #defaultInstanceName: dest-service-instance
>       connectionTimeoutSeconds: 5
>       readTimeoutSeconds: 10
>       instances:
>           - name: dest-service-instance
>             serviceCredentials:
>               secretKey: <secret-key>
>               secretName: <secret-name>
>               secretNamespace: <secret-namespace>
> ```



## IAS Authorization

The Destination service lets you authorize using IAS as well:

1.  Create a Destination service instance or reuse an existing one.
2.  Create a service key for the Destination service instance.
3.  Create a Cloud Identity service instance or reuse an existing one.
4.  Create a service key for the Cloud Identity service instance.
5.  Prepare instance credentials:
    -   Option 1: Prepare Destination service instance credentials. See step.3 above.
    -   Option 2: Prepare Cloud Identity service instance credentials. See step 3 above.

6.  Check the [Configuration Guide](configuration-guide-2a22cd7.md) for the parameter `config.integration.destinationService.instances`.

> ### Sample Code:  
> ```
> config:
>   integration:
>     destinationService:
>       ## Name of the default destination service instance to be used when 'destinationServiceInstanceName' is not provided in the Destination Custom Resource spec.
>       #defaultInstanceName: dest-service-instance
>       connectionTimeoutSeconds: 5
>       readTimeoutSeconds: 10
>       instances:
>           - name: dest-service-instance
>             serviceCredentials:
>               secretKey: <secret-key>
>               secretName: <secret-name>
>               secretNamespace: <secret-namespace>
> ```

