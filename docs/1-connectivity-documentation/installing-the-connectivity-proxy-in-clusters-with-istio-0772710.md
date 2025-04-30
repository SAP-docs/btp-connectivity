<!-- loio07727103f8974d5288a666e56416db7a -->

# Installing the Connectivity Proxy in Clusters with Istio

Install the Connectivity Proxy in a Kubernetes cluster that is configured for Istio.

> ### Restriction:  
> Currently, in clusters with Istio configured, only the high availability mode "path" is supported. Also, you cannot configure end-to-end mutual TLS \(mTLS\).
> 
> By default, the traffic between Cloud Connector and the ingress gateway is secured by mTLS. The traffic between the ingress gateway pod and the Connectivity Proxy pod is also encrypted by Istio by default.



<a name="loio07727103f8974d5288a666e56416db7a__section_unj_qzy_g5b"/>

## Required Configuration

1.  The ingress `className` must be changed to "istio". You can specify this in the `values.yaml` file:

    > ### Sample Code:  
    > ```
    > ingress:
    >   className: "istio"
    > ```

    > ### Caution:  
    > The default value of `ingress.className` is "nginx". It is mandatory to change it if you have Istio configured.

2.  By default, Istio is usually installed in the namespace "istio-system". However, you can install it in a different namespace. The Connectivity Proxy needs to know Istio's installation namespace because it creates secrets used by the Istio ingress gateway when performing the TLS handshake with the Cloud Connector.

    The Connectivity Proxy will create those secrets in the default namespace "istio-system". However, if you have installed Istio in a different namespace, you can specify this in the `values.yaml` file:

    > ### Sample Code:  
    > ```
    > ingress:
    >   istio:
    >     namespace: <istio-installation-namespace>
    > ```

    > ### Caution:  
    > The secret that will be used for TLS configuration of the ingress-gateway should be created in the installation namespace of Istio. This secret is specified with the field `ingress.tls.secretName` in the `values.yaml`. For more information, see [Configuration Guide](configuration-guide-eaa8204.md).

3.  The Connectivity Proxy uses the selector which is configured in the Istio ingress gateway to apply a gateway configuration on the gateway pods. When installing Istio with default configurations, it uses "istio: ingressgateway" as default value for the selector.

    The Connectivity Proxy also has this value configured as default one. If Istio was installed with different configurations and you need to change the selector, you can specfify this in the `values.yaml` file:

    > ### Sample Code:  
    > ```
    > ingress:
    >   istio:
    >     gateway:
    >       selector:
    >         "key1" : "value1"
    >         "key2" : "value2"
    > ```


> ### Caution:  
> **Istio AuthorizationPolicy**
> 
> If you have configured an Istio authorization policy that could affect traffic to the Connectivity Proxy, you may need to add the following rules \(or the whole authorization policy\):
> 
> > ### Sample Code:  
> > ```
> > apiVersion: security.istio.io/v1beta1
> > kind: AuthorizationPolicy
> > metadata:
> >   name: <authorization-policy-name>
> >   namespace: <istio-installation-namespace>
> > spec:
> >   selector:
> >     matchLabels:
> >       app: connectivity-proxy
> >   action: ALLOW
> >   rules:
> >   - to:
> >     - operation:
> >         ports: ["8042", "20001", "20003", "20004"]
> > ```

