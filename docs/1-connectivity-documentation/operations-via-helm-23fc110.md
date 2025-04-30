<!-- loio23fc1100c60b45c58f09694b7f9c7700 -->

# Operations via Helm

Use the Helm chart to configure and manage the life cycle of the Connectivity Proxy for Kubernetes.

> ### Note:  
> Out of the box, the Helm chart only supports the [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/) \(default\) and the [Istio Ingress Gateway](https://istio.io/latest/docs/tasks/traffic-management/ingress/ingress-control/) \(for more information, see [Installing the Connectivity Proxy in Clusters with Istio](installing-the-connectivity-proxy-in-clusters-with-istio-0772710.md)\).

[Deploy](operations-via-helm-23fc110.md#loio23fc1100c60b45c58f09694b7f9c7700__deploy)

[Update / Upgrade / Downgrade](operations-via-helm-23fc110.md#loio23fc1100c60b45c58f09694b7f9c7700__update)

[Undeploy](operations-via-helm-23fc110.md#loio23fc1100c60b45c58f09694b7f9c7700__undeploy)



<a name="loio23fc1100c60b45c58f09694b7f9c7700__deploy"/>

## Deploy

> ### Note:  
> For this procedure, you must have a generated public/private TLS key pair as a prerequisite. For generating the TLS key pair, you can use [Gardener Certificate resources](https://github.com/gardener/cert-management#requesting-a-certificate), *openssl*.

To deploy the Connectivity Proxy on a cluster that does not have the Helm chart yet, for example, in a new namespace, follow these steps:

1.  Get the Connectivity Proxy Helm chart, as described in [Lifecycle Management](lifecycle-management-60c0a45.md).
2.  Create a Kubernetes secret from the generated public/private TLS key pair \(for the Ingress public endpoint\). Depending on the Connectivity Proxy release version, the secret might require additional fields:
    1.  Connectivity Proxy release < 2.4.1:

        Download the list of trusted CAs for the BTP region to which you are pairing the Connectivity Proxy.

        Example:

        ```
        # download the list of trusted CAs
        curl https://connectivity.cf.{region_domain}/api/v1/CAs -o connectivity_ca.crt
        # create a k8s secret
        kubectl create secret generic connectivity-tls --from-file=ca.crt=connectivity_ca.crt --from-file=tls.key=private.key --from-file=tls.crt=public.crt --namespace my-namespace
        ```

        Where `private.key` is the private key and `public.crt` is the public key of a TLS certificate, generated for the Ingress public endpoint of the Connectivity Proxy \(the one which the Cloud Connector connects to\).

        > ### Remember:  
        > The content of `/api/v1/CAs` may change over time. Make sure you update it regularly.

    2.  Connectivity Proxy release \>= 2.4.1:

        Download of the trusted CAs is automated. They are saved in a secret in the respective name space. The secret's name is formed in the following way: *connectivity-ca-<helm\_installation\_name\>*. For example, if the helm installation name is *connectivity-proxy*, the generated secret name is *connectivity-ca-connectivity-proxy*.

        > ### Note:  
        > If a secret with the same name pattern, as mentioned above, is present whenever the Connectivity Proxy is installed/upgraded, its content is overridden.

        Example:

        ```
        # create a k8s secret
        kubectl create secret generic connectivity-tls --from-file=tls.key=private.key --from-file=tls.crt=public.crt --namespace my-namespace
        ```

        Where `private.key` is the private key and `public.crt` is the public key of a TLS certificate, generated for the Ingress public endpoint of the Connectivity Proxy \(the one which the Cloud Connector connects to\).


3.  Prepare the `values.yaml` file for your your scenario, as described in [Configuration Guide](configuration-guide-eaa8204.md).
4.  Use the Helm CLI to deploy the Connectivity Proxy. Example:

    ```
    helm install connectivity-proxy ./connectivity-proxy-<version>.tgz -f values.yaml --namespace my-namespace
    ```


[Back to Top](operations-via-helm-23fc110.md#loio23fc1100c60b45c58f09694b7f9c7700__top)



<a name="loio23fc1100c60b45c58f09694b7f9c7700__update"/>

## Update / Upgrade / Downgrade

When you have a Connectivity Proxy deployed on the cluster, you may want to maintain it by changing configurations and/or changing it's version. To do so, follow these steps:

1.  Get the Connectivity Proxy Helm chart, as described in [Lifecycle Management](lifecycle-management-60c0a45.md). It can be the same version as the one currently installed or a different version, when you want to upgrade or downgrade.
2.  Prepare the `values.yaml` file for your your scenario, as described in [Configuration Guide](configuration-guide-eaa8204.md). Here you can just modify the one you used previously by applying the changes you desire.
3.  Use the Helm CLI to upgrade the Connectivity Proxy. Example:

    ```
    helm upgrade connectivity-proxy ./connectivity-proxy-<version>.tgz -f values.yaml --namespace my-namespace
    ```


> ### Note:  
> Each Helm upgrade will result in a restart of the Connectivity Proxy pod\(s\). This is done to ensure that configuration changes are picked up immediately.

[Back to Top](operations-via-helm-23fc110.md#loio23fc1100c60b45c58f09694b7f9c7700__top)



<a name="loio23fc1100c60b45c58f09694b7f9c7700__undeploy"/>

## Undeploy

If you need to remove the Connectivity Proxy from you cluster or from a namespace, you can do it almost completely via normal Helm tools. However, there are some additional actions required. Please follow these steps:

1.  Use the Helm CLI to undeploy the Connectivity Proxy. Example:

    ```
    helm uninstall connectivity-proxy --namespace my-namespace
    ```

2.  Delete the Kubernetes secret representing the TLS certificate for the Connectivity Proxy public endpoint. Example:

    ```
    kubectl delete secret connectivity-tls --namespace my-namespace
    
    ```


> ### Note:  
> For Connectivity Proxy releases \>= 2.4.1, the secret containing the trusted CAs is removed automatically when `helm uninstall` is executed.

> ### Caution:  
> As of Connectivity Proxy release 2.8, trying to execute `helm uninstall`, while there are still resources of type *ServiceMapping*, would result in an error \(*job failed: BackoffLimitExceeded.* Detailed error message can be obtained after looking into the logs of the newly created pod `servicemapping-cleanup-verifier-job`\), and the proxy would not be uninstalled. Also, `helm upgrade` operations would no longer be available.
> 
> To proceed, remove all resources of type *ServiceMapping* and retry the uninstallation .

[Back to Top](operations-via-helm-23fc110.md#loio23fc1100c60b45c58f09694b7f9c7700__top)

