<!-- loiod201be05a4aa444898fd20bcecb1ebbb -->

# Installation with Helm

Use the Helm chart to configure and manage the lifecycle of the transparent proxy.

> ### Note:  
> Current version of the transparent proxy is 1.6.0.

The transparent proxy delivery includes a Helm chart that you can use for lifecycle management. The Helm allows full configuration via [the standard Helm method of a "values.yaml" file](https://helm.sh/docs/chart_template_guide/values_files/).

The transparent proxy Helm chart is available via the RBSC \(*repository-based shipment channel*\) Helm repository and DockerHub.



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_frb_w14_vwb"/>

## Latest Helm Chart Version

The latest helm chart version is f for both RBSC and DockerHub.



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_jxx_xbp_y5b"/>

## RBSC Pull information \(Latest Version\)

**Registry:** 73554900100900006891.helmsrv.cdn.repositories.cloud.sap

**Tag:** 1.6.0

**Authorization**: See [RBSC documentation](https://help.sap.com/viewer/0a64be17478d4f5ba45d14ab62b0d74c/Cloud/en-US/7e83dfc309834942b441fc2106c5b7f5.html).

```
helm repo add transparent-proxy-helm https://73554900100900006891.helmsrv.cdn.repositories.cloud.sap --username <user> --password <pass>
helm pull transparent-proxy-helm/transparent-proxy --version=<version of helm chart> 
helm repo update
```



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_ucd_m1g_rtb"/>

## Deploy \(DockerHub\)

To deploy the transparent proxy on a Kubernetes cluster, execute the following steps:

1.  Add the Helm repository and pull the Helm chart from DockerHub.

    You can directly install it with one command:

    ```
    helm install transparent-proxy oci://registry-1.docker.io/sapse/transparent-proxy --version <version of helm chart> --namespace <namespace> -f <path-to-values.yaml>
    ```

    For additional information about using OCI registries with Helm, see [Helm docs](https://helm.sh/docs/topics/registries/).

2.  \(Optional\) Prepare the Docker image configuration for the repository authentication if want to use a registry different from *docker.io*:
    -   Create docker secret:

        ```
        kubectl create secret docker-registry docker-secret --docker-server=73554900100900006891.dockersrv.cdn.repositories.cloud.sap --docker-username=<rbsc-user> --docker-password=<password>
        ```

    -   Place the name of secret it in the `values.yaml` for the `deployment.image.pullSecret` property.

        For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).


3.  Prepare credentials for the Destination service instance :

    -   Option 1: Reuse existing secret
        -   If you already have an existing secret in your Kubernetes cluster you can reference it providing the parameter `config.integration.destinationService.instances[n].serviceCredentials.secretName`.

        -   The secret data format can be either one-key or multi-key \(for example, secrets created by Destination service instance creation in the Kyma dashboard\).

        -   If the secret data key format is one-key you should also provide the value of that key as `config.integration.destinationService.instances[n].serviceCredentials.secretKey`.

        -   If that secret is not in the same namespace as the transparent proxy provide also `config.integration.destinationService.instances[n].serviceCredentials.secretNamespace`.


    -   Option 2: Create secret holding the Destination service key
        -   Get the service key of the Destination service instance.
        -   Base64-encode the service key and place it in the `values.yaml` for `config.integration.destinationService.instances[n].serviceCredentials.secretData`.


    For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).

    > ### Note:  
    > For x.509-based service keys with self-signed certificates, prepare a Kubernetes secret holding the private key for the certificate.
    > 
    > **Example:** 
    > 
    > ```
    > kubectl create secret generic x509-svc-key-private-key --from-file=pk.pem
    > ```
    > 
    > If you are using another secret name or internal key in the secret, provide the required parameters \(`config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretName` and
    > 
    > `config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretInternalKey`\) in the `values.yaml`.
    > 
    > For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).

4.  Fill all other properties in `values.yaml` for your scenario, as described in [Configuration Guide](configuration-guide-2a22cd7.md).

    > ### Caution:  
    > Do not extract the archive and modify the default `values.yml` file included there. Instead, use your own `values.yml` and only include fields that should be overridden.

    1.  > ### Note:  
        > By default, mTLS encryption is enabled using [cert-manager](https://cert-manager.io/). You should check the [Configuration Guide](configuration-guide-2a22cd7.md) to modify the configuration settings according to your setup, for example, referencing your *cert-manager Issuer* or *ClusterIssuer*.

        > ### Tip:  
        > Encryption for the transparent proxy components can also be disabled for test purposes or if you have implemented your own mTLS sidecar solution, for example, Istio.


5.  Use the Helm CLI to deploy the transparent proxy:

    ```
    helm install transparent-proxy transparent-proxy-helm/transparent-proxy --version=<version of helm chart> --namespace <namespace> -f <path-to-values.yaml>
    ```

    > ### Note:  
    > **Installation in a Kyma Cluster**
    > 
    > In case of installation in a Kyma cluster, if you want to enable istio for the transparent proxy workloads, you need to label the namespace where the transparent proxy is installed with:
    > 
    > ```
    > kubectl label namespace <namespace> istio-injection=enabled
    > ```




<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_sps_m1g_rtb"/>

## Update / Upgrade / Downgrade

> ### Caution:  
> Changing any of the `values.yaml` configurations using *helm upgrade* may result in the restart of some or all transparent proxy components.

When you have a transparent proxy deployed on the cluster, you may want to maintain it by changing configurations and/or changing its version. To do so, follow these steps:

1.  Get the transparent proxy Helm chart. It can be the same version as the one currently installed or a different version that you want to upgrade or downgrade.
2.  Prepare the `values.yaml` file for your scenario, as described in [Configuration](configuration-guide-2a22cd7.md#loio2a22cd7872964e6a9ceb5af72920cfd0__config). Here you can just modify the one you used previously by applying the changes you desire.
3.  Use the Helm CLI to upgrade the transparent proxy:

    ```
    helm upgrade transparent-proxy oci://registry-1.docker.io/sapse/transparent-proxy --version <version of helm chart> --namespace <namespace> -f <path-to-new-values.yaml>
    ```




<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_tk4_p1g_rtb"/>

## Undeploy

If you need to remove the transparent proxy from your cluster or from a namespace, you can delete all resources installed by Helm except for the [Custom Resource Definition](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/) \(CRD\) of type `destinations.destination.connectivity.api.sap` using the Helm CLI:

```
helm uninstall transparent-proxy
```

If you need to remove the CRD of type `destinations.destination.connectivity.api.sap`, you can do it manually using [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).

```
kubectl delete crd destinations.destination.connectivity.api.sap
```

This will delete the CRD `destinations.destination.connectivity.api.sap` as well as all custom resources of type `destination.connectivity.api.sap` in the cluster.



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_stj_nlc_zxb"/>

## Deploy/Update/Undeploy using Landscaper

To deploy/update/undeploy the transparent proxy on a Kubernetes cluster via Landscaper, look at the following [Guided Tour with Landscaper](https://github.com/gardener/landscaper/tree/master/docs/guided-tour). You will need an LAAS instance that you can request from the corresponding team, or launch a local one using the Landscaper CLI.

