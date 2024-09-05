<!-- loio6a73ed066c264518abd2b6694c39ee31 -->

# Certificate Manager

Use the certificate manager for secure internal communication of the transparent proxy for Kubernetes.

If you do not integrate the transparent proxy with the Istio service mesh, you must encrypt the traffic between the micro-components. Transparent proxy can use either cert-manager.io, or cert.gardener.cloud to encrypt the communication via mTLS between the transparent proxy components.



<a name="loio6a73ed066c264518abd2b6694c39ee31__section_m1g_4rw_hcc"/>

## Prerequisites

Internal communication between transparent proxy components can be made secure by setting the Helm property `.Values.config.security.communication.internal.encryptionEnabled` to `true`.

> ### Sample Code:  
> ```
> config:
>   security:
>     communication:
>       internal:
>         ## Enables/Disables mTLS communication between the Transparent Proxy components. Make sure to install cert-manager in advance.
>         #It should be disabled only in test environments or if you implement your own mTLS solution like Istio for example.
>         encryptionEnabled: true
> ```

By default, `.Values.config.security.communication.internal.encryptionEnabled` is `true`. This is recommended for all productive scenarios.



<a name="loio6a73ed066c264518abd2b6694c39ee31__section_f2y_nrw_hcc"/>

## Integration

To integrate a certificate manager, follow these steps:

1.  Enable secure communication between internal components by setting `.Values.config.security.communication.internal.encryptionEnabled` to `true`.
2.  Specify`.Values.config.security.communication.internal.certManager.issuerRef.name`. Certificate management types cert-manager.io and cert.gardener.cloud are currently supported.
3.  Depending on the certificate management type \(either cert-manager.io or \`cert.gardener.cloud\), specify the corresponding additional settings:
    1.  When using cert-manager.io, you should specify `.Values.config.security.communication.internal.certManager.issuerRef.kind`.
    2.  When using cert.gardener.cloud, you should specify `.Values.config.security.communication.internal.certManager.issuerRef.namespace`.


**Certificate Manager Integration**

> ### Sample Code:  
> ```
> config: 
>   security:
>     communication:
>       internal:
>         ## Enables/Disables mTLS communication between the Transparent Proxy components. Make sure to install cert-manager in advance.
>         #It should be disabled only in test environments or if you implement your own mTLS solution like Istio for example.
>         encryptionEnabled: true
>         ## Certificate management types cert-manager.io(https://cert-manager.io/docs/) and cert.gardener.cloud(https://github.com/gardener/cert-management) are currently supported
>         certManager:
>           issuerRef:
>             ##  The name of the installed cert-manager issuer.
>             name: <issuer-ref-name>
>             ##  The cert-manager custom k8s resource type of the CA - should be one of (Issuer or ClusterIssuer). Only applicable for cert-manager.io.
>             #   kind: <issues-ref-kind>
>             ##  The namespace of the installed cert-manager issuer(only applicable for cert.gardener.cloud).
>             #   namespace: <issuer-ref-namespace>
>             ## Certificate properties are only applicable for cert-manager.io. If specified when using cert.gardener.cloud - will be ignored.
>             certificate:
>               privateKey:
>                 ## Check cert-manager private key docs - https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey
>                 algorithm: <private-key-algorithm>
>                 ## Check cert-manager private key docs - https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey
>                 encoding: <private-key-encoding>
>                 ## Check cert-manager private key docs - https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey
>                 size: <private-key-duration>
>               ## The duration for which the certificates will be valid. Minimum accepted duration is 1 hour. Value must be in units accepted by Go time.ParseDuration https://golang.org/pkg/time/#ParseDuration
>               duration: <certificate-validity-duration>
>               ## How long before the currently issued certificate’s expiry cert-manager should renew the certificate. Value must be in units accepted by Go time.ParseDuration https://golang.org/pkg/time/#ParseDuration
>               renewBefore: <renew-before-duration>
> ```

> ### Note:  
> For more details about configuring the transparent proxy, check the [Configuration Guide](configuration-guide-2a22cd7.md).

