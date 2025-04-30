<!-- loio2b0002b968e741a28765b8245d00ba8d -->

# Operations via Separate YAML Files 

Using separate YAML files to configure and manage the life cycle of the Connectivity Proxy for Kubernetes.

> ### Caution:  
> As operating with separate YAML files that you modify and maintain is considered error prone, we do not recommend this method. Consider using [Operations via Helm](operations-via-helm-23fc110.md) instead. If you do need to use separate YAML files, we recommend that you generate them via Helm template.

[Deploy](operations-via-separate-yaml-files-2b0002b.md#loio2b0002b968e741a28765b8245d00ba8d__deploy)

[Update / Upgrade / Downgrade](operations-via-separate-yaml-files-2b0002b.md#loio2b0002b968e741a28765b8245d00ba8d__update)

[Undeploy](operations-via-separate-yaml-files-2b0002b.md#loio2b0002b968e741a28765b8245d00ba8d__undeploy)



<a name="loio2b0002b968e741a28765b8245d00ba8d__deploy"/>

## Deploy

To deploy the Connectivity Proxy on a cluster that does not have it yet, for example, in a new namespace, follow these steps:

1.  Get the Connectivity Proxy YAML files via Helm template
2.  Download the list of trusted CAs for the SAP BTP region to which you want to pair the Connectivity Proxy. Create a Kubernetes secret from it together with a previously generated public/private TLS key pair \(for the Ingress public endpoint\). For generating the TLS key pair, you can use [Gardener Certificate resources](https://github.com/gardener/cert-management#requesting-a-certificate), *openssl*, or some other tool. Example:

    ```
    # download the list of trusted CAs
    curl https://connectivity.cf.{region_domain}/api/v1/CAs -o connectivity_ca.crt
    # create a Kubernetes secret
    kubectl create secret generic connectivity-tls --from-file=ca.crt=connectivity_ca.crt --from-file=tls.key=private.key --from-file=tls.crt=public.crt --namespace my-namespace
    ```

    Where `private.key` is the private key and `public.crt` is the public key of a TLS certificate, generated for the Ingress public endpoint of the Connectivity Proxy \(the one which the Cloud Connector connects to\).

    > ### Remember:  
    > The content of `/api/v1/CAs` may change over time. Make sure you update it regularly.

3.  Use the `kubectl` CLI to deploy the Connectivity Proxy. Example:

    ```
    kubectl apply -f my_changed_resource.yaml --namespace my-namespace
    ```


[Back to Top](operations-via-separate-yaml-files-2b0002b.md#loio2b0002b968e741a28765b8245d00ba8d__top)



<a name="loio2b0002b968e741a28765b8245d00ba8d__update"/>

## Update / Upgrade / Downgrade

When you have a Connectivity Proxy deployed on the cluster, you may want to maintain it by changing configurations and/or changing it's version. To do so, follow these steps:

1.  Get the YAML files \(or only those you want to modify\) you used to deploy the Connectivity Proxy. You can also export them from the cluster via `kubectl`.
2.  Make the desired changes. For example, you can modify the subaccount ID in the `config` map or the Connectivity Proxy version in the deployment.
3.  Use the `kubectl` CLI to apply your changes. Example:

    ```
    kubectl apply -f my_changed_resource.yaml --namespace my-namespace
    ```


> ### Tip:  
> You can also use `kubectl edit` to directly modify the resources on the cluster.

> ### Note:  
> When updating secrets or config maps, you must restart the pod\(s\) to activate the changes. You can do this by running `kubectl rollout restart statefulset/connectivity-proxy`.

[Back to Top](operations-via-separate-yaml-files-2b0002b.md#loio2b0002b968e741a28765b8245d00ba8d__top)



<a name="loio2b0002b968e741a28765b8245d00ba8d__undeploy"/>

## Undeploy

If you need to remove the Connectivity Proxy from you cluster or from a namespace, follow these steps:

1.  Get the YAML files you used to deploy the Connectivity Proxy. You can also export them from the cluster via `kubectl`.
2.  Use the `kubectl` CLI to undeploy the Connectivity Proxy. Example:

    ```
    kubectl delete -f ./dir_with_yaml_files --namespace my-namespace
    ```

    > ### Tip:  
    > You can also use `kubectl delete <resource type> <resource name>`.

3.  Delete the Kubernetes secret representing the TLS certificate for the Connectivity Proxy public endpoint. Example:

    ```
    kubectl delete secret connectivity-tls --namespace my-namespace
    ```


[Back to Top](operations-via-separate-yaml-files-2b0002b.md#loio2b0002b968e741a28765b8245d00ba8d__top)

