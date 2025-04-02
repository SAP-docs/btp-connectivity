<!-- loio60f00ec5724e4875b51a2cadfb2364b2 -->

# Destination Java APIs

Use Destination service Java APIs to optimize application development.

> ### Caution:  
> *Connectivity ApiExt* is NOT a recommended way of consuming the Destination service. If you, for some reason, have the need to use *Connectivity ApiExt*, please open a support ticket on component BC-CP-DEST-CF to discuss your use case.
> 
> *Connectivity ApiExt* for the Cloud Foundry environment is in support-only mode, which means that no new development is done but bug fixes and security patches. It will NOT evolve with the service and NO feature parity can be expected.
> 
> We recommend using the SAP Cloud SDK as an alternative.

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

