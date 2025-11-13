<!-- loio4f7bb27352e1450bb4b52faff00ac408 -->

# Integration with Zero Trust Identity Service \(ZTIS\)

The Transparent Proxy architecture aligns with *zero trust* principles by enforcing the concept of "never trust, always verify" through its integration with workload identity frameworks.

In a *zero trust* model, all user and service accounts tied to Kubernetes clusters must be authenticated before executing API calls, with no implicit trust granted to any entity. The Transparent Proxy supports this security paradigm by leveraging SPIFFE/SPIRE for workload identity attestation, enabling granular access controls and continuous verification.



<a name="loio4f7bb27352e1450bb4b52faff00ac408__section_sgg_n1n_sfc"/>

## Prerequisites

You have installed and configured the *ZTIS SPIRE* agent in your Kubernetes cluster according to the [ZTIS documentation](https://github.tools.sap/login?return_to=https%3A%2F%2Fpages.github.tools.sap%2Fpse%2Fpse-docs%2Fdocs%2Fidentity-k8s%2Fhow-to-guides%2F).



<a name="loio4f7bb27352e1450bb4b52faff00ac408__section_mjc_n1n_sfc"/>

## Configuration

**Using Workload Attestation:**

1.  Create a *Zero Trust* instance binding

    -   Create 3 zero trust instance service keys for each service account of the Transparent Proxy components.
    -   You can reuse an existing app identifier or reference a new one.

    An example for "sap-transp-proxy-manager-service-account" looks like this:

    > ### Sample Code:  
    > ```
    > {
    >     "app-identifier": "transparent-proxy",
    >     "workload-attestation": {
    >         "k8s": {
    >             "namespace": "<transparent-proxy-installation-namespace>",
    >             "service-account": "sap-transp-proxy-manager-service-account"
    >         }
    >     }
    > }
    > ```

    Execute the same also for "sap-transp-proxy-conn-handler-service-account" and "sap-transp-proxy-tcp-service-account". In total, there should be 3 keys per Transparent Proxy installation.

2.  Create a Destination service key

    > ### Sample Code:  
    > ```
    > {
    >     "xsuaa" :{
    >         "credential-type": "x509_attested",
    >         "x509" :{
    >             "app-identifier": "<app-identifier-from-step-above>",
    >             "api-domain": "<api-domain-of-the-k8s-cluster>"
    >         }
    >     }
    > }
    > ```

    See [Integration with SAP BTP Connectivity](integration-with-sap-btp-connectivity-aa9fc26.md) to find information on how to create a Kubernetes secret holding that Destination service key.

3.  Prepare Helm configuration

    By default, the SVID is retrieved using a UNIX socket defined by `config.ztis.socketPath`.

    For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).


**Using SVID Store:**

1.  Create a *Zero Trust* instance binding:

    Create service key according to this [documentation](https://pages.github.tools.sap/pse/pse-docs/docs/identity-k8s/how-to-guides/service-key-creation/#k8s-secret-svid-store) for using a Kubernetes Secret SVID store.

2.  Create Destination service key

    > ### Sample Code:  
    > ```
    > {
    >     "xsuaa" :{
    >         "credential-type": "x509_attested",
    >         "x509" :{
    >             "app-identifier": "<app-identifier-from-step-above>",
    >             "api-domain": "<api-domain-of-the-k8s-cluster>"
    >         }
    >     }
    > }
    > ```

    See [Integration with SAP BTP Connectivity](integration-with-sap-btp-connectivity-aa9fc26.md) to find information on how to create a Kubernetes secret holding that Destination service key.

3.  Prepare Helm configuration

    The secret created by the *ZTIS SPIRE* agent should be referenced under `config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretName`. If the secret is in an namespace different from the Transparent Proxy namespace, it should be referenced as well under `config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretNamespace`.

    For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).


