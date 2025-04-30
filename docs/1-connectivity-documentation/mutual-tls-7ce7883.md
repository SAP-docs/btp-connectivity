<!-- loio7ce7883d1a054634ba18ea5004f253b0 -->

# Mutual TLS

Use Transport Layer Security \(TLS\) for the Connectivity Proxy for Kubernetes.

[TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security) encrypts the connection between client and server, following the TLS specification. When using mutual TLS, both the TLS client and the TLS server authenticate each other through X.509 certificates.

In an on-premise network, the TLS client is represented by the Cloud Connector. On the cloud side, the direct TLS server may be:

-   The Kubernetes Ingress: In this case, the Ingress terminates the TLS connection and establishes a new TLS connection to the Connectivity Proxy.
-   The Connectivity Proxy: In this case, the Ingress does not terminate the TLS, but transparently forwards the TLS traffic to the Connectivity Proxy.

Connectivity proxy deployment provides two options to configure end-to-end mutual TLS, that is, the TLS communication between Cloud Connector and Connectivity Proxy:

-   [*With* TLS termination in the Ingress](mutual-tls-7ce7883.md#loio7ce7883d1a054634ba18ea5004f253b0__with): TLS configuration has to be made on both the Ingress controller \(TLS client\) and Connectivity Proxy \(TLS server\).
-   [*Without* TLS termination in the Ingress](mutual-tls-7ce7883.md#loio7ce7883d1a054634ba18ea5004f253b0__without): TLS configuration has to be made only on the Connectivity Proxy side \(TLS server\).



<a name="loio7ce7883d1a054634ba18ea5004f253b0__with"/>

## End-to-End Mutual TLS *with* Termination of the TLS Connection in the Ingress

Perform the following steps:

1.  Enable the TLS communication on the Connectivity Proxy \(TLS server\) side, adding the following configuration in the `values.yaml` file:

    ```
    config:
      servers:
        businessDataTunnel:
          enableTls: true
    ```

2.  Add the required TLS configuration for the Connectivity Proxy \(TLS server\). There are two options to do this:
    -   If you already have an appropriate secret for this purpose in the cluster, add the following configuration in the `values.yaml` file:

        ```
        secretConfig:
          servers:
            businessDataTunnel:
              secretName: <secret name>
        ```

        > ### Note:  
        > The Kubernetes secret must contain the following properties, used for authentication to the Ingress resource:
        > 
        > -   `tls.key`: Base 64-encoded private key in PEM format.
        > -   `tls.crt`: Base 64-encoded certificate in PEM format.
        > -   `ca.crt`: Base 64-encoded full certificate authority \(CA\) chain in PEM format.

    -   If you don't have such a Kubernetes secret, it can be automatically generated. Add the following configuration in the `values.yaml` file:

        ```
        secretConfig:
          servers:
            businessDataTunnel:
              secretName: <secret name>
              secretData:
                key: <base 64-encoded private key in PEM format>
                certificate: <base 64-encoded certificate in PEM format>
                caCertificate: <base 64-encoded full Certificate Authority chain in PEM format>
        ```

        > ### Note:  
        > The certificate must be issued for the external host specified on the configuration path `config.servers.businessDataTunnel.externalHost` or for the domain to which the external host belongs. For example, if the external host is "*ingress.mycluster.com*", the certificate CN or SAN must contain "*ingress.mycluster.com*" or "*\*.mycluster.com*".


3.  Add the required TLS configuration for the Ingress. There are three options to do this:

    -   If you already have an appropriate Kubernetes secret for this purpose in the cluster, add the following configuration in the `values.yaml` file:

        ```
        ingress:
          tls:
            proxy:
              secretName: <secret name>
        ```

        > ### Note:  
        > The Kubernetes secret must contain the following properties, used for authentication to the Ingress resource:
        > 
        > -   `tls.key`: Base 64-encoded private key in PEM format.
        > -   `tls.crt`: Base 64-encoded certificate in PEM format.
        > -   `ca.crt`: Base 64-encoded full certificate authority \(CA\) chain in PEM format.

    -   If you don't have such a secret, it can be automatically generated. Add the following configuration in the `values.yaml` file:

        ```
        ingress:
          tls:
            proxy:
              secretName: <secret name>
              secretData:
                key: <base 64-encoded private key in PEM format>
                certificate: <base 64-encoded certificate in PEM format>
                caCertificate: <base 64-encoded full Certificate Authority chain in PEM format>
        ```

    -   If you didn't add any TLS configuration for the Ingress, the TLS configuration of the Connectivity Proxy is reused for the Ingress, that is, the Connectivity Proxy and the Ingress will use the same TLS configuration to communicate to each other.

        > ### Note:  
        > In this case, the specified certificate must be issued by the specified certificate authority.


    > ### Note:  
    > The certificate must be issued for the external host specified on the configuration path `config.servers.businessDataTunnel.externalHost` or for the domain to which the external host belongs. For example, if the external host is "*ingress.mycluster.com*", the certificate CN or SAN must contain "*ingress.mycluster.com*" or "*\*.mycluster.com*".


> ### Note:  
> In this case, the **minimum required version** for the NGINX ingress controller is 0.31.0.

[Back to Top](mutual-tls-7ce7883.md#loio7ce7883d1a054634ba18ea5004f253b0__top)



<a name="loio7ce7883d1a054634ba18ea5004f253b0__without"/>

## End-to-End Mutual TLS *without* Termination of the TLS Connection in the Ingress

Perform the following steps:

1.  Enable the TLS communication on the Connectivity Proxy \(TLS server\) side, adding the following configuration in the `values.yaml` file:

    ```
    config:
      servers:
        businessDataTunnel:
          enableTls: true
    ```

2.  Add the required TLS configuration for the Connectivity Proxy \(TLS server\). There are two options to do this:
    -   If you already have an appropriate secret for this purpose in the cluster, add the following configuration in the `values.yaml` file:

        ```
        secretConfig:
          servers:
            businessDataTunnel:
              secretName: <secret name>
        ```

        > ### Note:  
        > The Kubernetes secret must contain the following properties, used for authentication to the Ingress resource:
        > 
        > -   `tls.key`: Base 64-encoded private key in PEM format.
        > -   `tls.crt`: Base 64-encoded certificate in PEM format.
        > 
        > For Connectivity proxy release < 2.4.0, an additional field is required:
        > 
        > -   `ca.crt`: Base 64-encoded full **Connectivity** certificate authority \(CA\) chain in PEM format.

    -   If you don't have such a secret, it can be automatically generated. Add the following configuration in the `values.yaml` file:

        ```
        secretConfig:
          servers:
            businessDataTunnel:
              secretName: <secret name>
              secretData:
                key: <base 64-encoded private key in PEM format>
                certificate: <base 64-encoded certificate in PEM format>
        ```

        > ### Note:  
        > For Connectivity proxy release < 2.4.0 an additional field is required:
        > 
        > ```
        > secretConfig:
        >   servers:
        >     businessDataTunnel:
        >       ...
        >       secretData:
        >         ...
        >         caCertificate: <base 64-encoded full Connectivity Certificate Authority chain in PEM format>
        > ```

        > ### Note:  
        > The certificate must be issued for the external host specified on the configuration path `config.servers.businessDataTunnel.externalHost` or for the domain to which the external host belongs. For example, if the external host is "*ingress.mycluster.com*", the certificate CN or SAN must contain "*ingress.mycluster.com*" or "*\*.mycluster.com*".


3.  Skip the TLS configuration on the Ingress resource, that is, skip the configuration path `ingress.tls` in the `values.yaml` file.

    > ### Note:  
    > In this case, you must set the configuration parameter `config.servers.businessDataTunnel.strictSniEnabled` to `false`, because this strict SNI configuration is relevant for a TLS termination in the Ingress. In case of direct TLS connection, strict SNI is supported by default.


> ### Note:  
> By default, the NGINX ingress controller does not support communication without termination of the TLS connection. To support such communication, the *<--enable-ssl-passthrough\>* flag must be part of the configuration with which the ingress controller is started. For more information, see [Command line arguments](https://kubernetes.github.io/ingress-nginx/user-guide/cli-arguments/) \(Kubernetes documentation on github\).

[Back to Top](mutual-tls-7ce7883.md#loio7ce7883d1a054634ba18ea5004f253b0__top)

