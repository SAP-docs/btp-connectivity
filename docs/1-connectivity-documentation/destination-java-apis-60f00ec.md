<!-- loio60f00ec5724e4875b51a2cadfb2364b2 -->

# Destination Java APIs

Use Destination service Java APIs to optimize application development.

> ### Caution:  
> The `ConnectivityConfiguration` and `AuthenticationHeaderProvider` APIs \(the library described in this document\) are not a recommended way of consuming the Destination service. If you, for some reason, have the need to use them, please open a support ticket on component BC-CP-DEST-CF to discuss your use case.
> 
> For the Cloud Foundry environment, these APIs are in support-only mode, which means that no new development is done but bug fixes and security patches. They will not evolve with the service and no feature parity can be expected.
> 
> For Kubernetes, we recommend that you use the Transparent Proxy as an alternative:
> 
> -   In the Kyma environment: [Transparent Proxy in the Kyma Environment](transparent-proxy-in-the-kyma-environment-1700cfe.md)
> -   In any Kubernetes environment: [Transparent Proxy for Kubernetes](transparent-proxy-for-kubernetes-acc64ad.md)
> 
> For the Cloud Foundry environment, the recommendation is to use the [SAP Cloud SDK](https://sap.github.io/cloud-sdk/docs/java/getting-started) instead.

When running your cloud application with *SAP Java Buildpack*, you can use the following Java APIs to optimize the application development:

-   [ConnectivityConfiguration API](connectivityconfiguration-api-d31bdd5.md): Retrieve destination configurations.
-   [AuthenticationHeaderProvider API](authenticationheaderprovider-api-2959ab8.md): Retrieve prepared authentication headers, ready to be used towards the remote target system.

Add the *Connectivity ApiExt* dependency in the `pom.xml` file:

```
<dependency>
    <groupId>com.sap.cloud.connectivity.apiext</groupId>
    <artifactId>com.sap.cloud.connectivity.apiext</artifactId>
    <version>${connectivity-apiext.version}</version>
    <scope>provided</scope>
</dependency>
```

For more information on *SAP Java Buildpack*, see also [Developing Java in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/developing-java-in-cloud-foundry-environment?version=Cloud).

