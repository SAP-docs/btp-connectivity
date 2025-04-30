<!-- loio5c756741b38248da8439286621a4e776 -->

# External Health Checking

Perform external health checks for the Connectivity Proxy for Kubernetes.

External health checking lets you check and monitor the health of the Connectivity Proxy using an external application. To achieve this, you must call one of the following URLs:

-   `https://healthcheck.<config.servers.businessDataTunnel.externalHost>/healthcheck`
-   `https://healthcheck.<config.servers.businessDataTunnel.externalHost>`, that will redirect the request to the first URL.

The external health checking configuration depends on the mutual TLS configuration. Currently, the Connectivity Proxy deployment provides three mutual TLS configuration options:

-   [Mutual TLS *only to the Ingress*](external-health-checking-5c75674.md#loio5c756741b38248da8439286621a4e776__with)
-   [End-to-end mutual TLS *with* termination of the TLS connection in the Ingress](external-health-checking-5c75674.md#loio5c756741b38248da8439286621a4e776__with)
-   [End-to-end mutual TLS *without* termination of the TLS connection in the Ingress](external-health-checking-5c75674.md#loio5c756741b38248da8439286621a4e776__without)

For more information, see [Mutual TLS](mutual-tls-7ce7883.md).



<a name="loio5c756741b38248da8439286621a4e776__with"/>

## Mutual TLS *Only to the Ingress* or End-to-End Mutual TLS *with* Termination of the TLS Connection in the Ingress

In these cases, you have two options to configure the external health checking:

-   Reuse the TLS secret that is used for communication with the Cloud Connector. In this case, you don't need to do any extra configuration.

    > ### Note:  
    > The certificate from the TLS secret must be issued for both the external host specified on the configuration path `<config.servers.businessDataTunnel.externalHost>` and the host `healthcheck.<config.servers.businessDataTunnel.externalHost>`. For example, if the external host is "*ingress.mycluster.com*", the certificate CN could be "*ingress.mycluster.com*" and certificate SAN must contain "*healthcheck.ingress.mycluster.com*".

-   Use a specific TLS secret only for the communication with the external health checking application. In this case, there are two options to do this:

    -   If you already have an appropriate secret for this purpose in the cluster, add the following configuration in the `values.yaml` file:

        ```
        ingress:
          healthcheck:
            tls:
              secretName: <secret name>
        ```

        > ### Note:  
        > The Kubernetes secret must contain the following properties, used for authentication to the Ingress resource:
        > 
        > -   `tls.key`: Base 64-encoded private key in PEM format.
        > -   `tls.crt`: Base 64-encoded certificate in PEM format.

    -   If you don't have such a Kubernetes secret, it can be automatically generated. Add the following configuration in the `values.yaml` file:

        ```
        ingress:
          healthcheck:
            tls:
              secretName: <secret name>
              secretData:
                key: <base 64 encoded private key in PEM format>
                certificate: <base 64 encoded certificate in PEM format>
        ```



> ### Note:  
> The certificate from the TLS secret must be issued for the host `healthcheck.<config.servers.businessDataTunnel.externalHost>`. For example, if the external host is "*ingress.mycluster.com*", then the certificate CN or SAN must contain "*healthcheck.ingress.mycluster.com*".

> ### Note:  
> The certificate chain of the CA that issues the certificate from the TLS secret must be imported to the trust store of the external health checking application.

[Back to Top](external-health-checking-5c75674.md#loio5c756741b38248da8439286621a4e776__top)



<a name="loio5c756741b38248da8439286621a4e776__without"/>

## End-to-end Mutual TLS *without* Termination of the TLS Connection in the Ingress

In this case, execute the following steps:

1.  Download the *plugins* archive and unzip it \(for more information, see [Lifecycle Management](lifecycle-management-60c0a45.md)\).
2.  Navigate to the *plugins* folder and install *connectivity-certificate-plugin* by executing the following command:

    ```
    helm plugin install connectivity-certificate-plugin
    
    ```

3.  Generate a TLS secret by executing the following command:

    ```
    helm get-connectivity-certificates <region_domain> <subaccount> <user> <password> <namespace> <secret_name>
    
    ```

    > ### Note:  
    > -   `region_domain`: BTP region to which you are pairing the Connectivity Proxy.
    > -   `subaccount`: BTP subaccount, on whose behalf the Connectivity Proxy is running.
    > -   `user`: BTP subaccount user.
    > -   `password`: Password of the BTP subaccount user.
    > -   `namespace`: Kubernetes namespace to which the secret is created.
    > -   `secret_name`: Name of the Kubernetes secret to be created.

4.  Specify a TLS secret that will be used for the communication with the external health checking application. There are two options to do this:

    -   If you already have an appropriate secret for this purpose in the cluster, add the following configuration in the `values.yaml` file:

        ```
        ingress:
          healthcheck:
            tls:
              secretName: <secret name>
        ```

        > ### Note:  
        > The Kubernetes secret must contain the following properties, used for authentication to the Ingress resource:
        > 
        > -   `tls.key`: Base 64-encoded private key in PEM format.
        > -   `tls.crt`: Base 64-encoded certificate in PEM format.

    -   If you don't have such a Kubernetes secret, it can be automatically generated. Add the following configuration in the `values.yaml` file:

        ```
        ingress:
          healthcheck:
            tls:
              secretName: <secret name>
              secretData:
                key: <base 64 encoded private key in PEM format>
                certificate: <base 64 encoded certificate in PEM format>
        ```


    > ### Note:  
    > The certificate from the TLS secret must be issued for the host `healthcheck.<config.servers.businessDataTunnel.externalHost>`. For example, if the external host is "*ingress.mycluster.com*", then the certificate CN or SAN must contain "*healthcheck.ingress.mycluster.com*".

    > ### Note:  
    > The certificate chain of the CA that issues the certificate from the TLS secret must be imported to the trust store of the external health checking application.

5.  Specify the TLS secret that was generated in step 3, to be used for the communication between the Ingress controller and the Connectivity Proxy. Add the following configuration in the `values.yaml` file:

    ```
    ingress:
      healthcheck:
        tls:
          proxy:
            secretName: <name of the secret generated on step 3>
    ```


[Back to Top](external-health-checking-5c75674.md#loio5c756741b38248da8439286621a4e776__top)

