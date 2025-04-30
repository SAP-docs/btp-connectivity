<!-- loiobbd3040e6c5f4f12b8afdcc17c63502a -->

# Service Channels: On-Premise-to-Cloud Connectivity

Use the Connectivity Proxy to connect to an on-premise network via a Cloud Connector service channel.

If you want to consume a cloud application running in a Kubernetes cluster, and the application is not accessible via Internet, it can be securely exposed by the Connectivity Proxy and consumed from the on-premise network via a Cloud Connector service channel.

For more information on configuring service channels in the Cloud Connector, see [Using Service Channels](using-service-channels-16f6342.md).

Perform the following steps to expose an application through the Connectivity Proxy:

1.  Install the Connectivity Proxy in the cluster where the cloud application is running.
2.  Create a Kubernetes resource of type `ServiceMapping` for every cloud application that you want to expose through the Connectivity Proxy.

    > ### Sample Code:  
    > ```
    > apiVersion: connectivityproxy.sap.com/v1
    > kind: ServiceMapping
    > metadata:
    >   name: <required>
    > spec: 
    >   type: <required>
    >   subaccountId: <required>
    >   serviceId: <required>
    >   tenantId: <optional>
    >   internalAddress: <required>
    >   locationIds: <optional>
    > ```

    -   `name`: Required. Name of the `ServiceMapping` that is created.
    -   `type`: Required. Type of the `ServiceMapping`. The type defines the connection protocol used to expose the cloud application. Currently, the supported types are **RFC** and **TCP**.

        > ### Note:  
        > For Cloud Connectors below version 2.14.2, only **RFC** is supported.

    -   `subaccountId`: Required for multi-tenant modes and optional for single-tenant modes. This is the ID of the tenant on whose behalf the cloud application is exposed. In single-tenant modes, the configured dedicated tenant is used by default.
    -   `serviceId`: Required. This is the virtual host used to expose the cloud application.
    -   `tenantId`: Optional. If the Connectivity Proxy consumer's flow has a tenancy domain model different from the SAP BTP tenancy domain model, you can specify the tenant identifier of the custom domain model here.
    -   `internalAddress`: Required. This field is composed of the host and port for the exposed application. The Connectivity Proxy will use the internal address for opening a connection to the application. This usually is the DNS name of a Kubernetes service and a port.
    -   `locationIds`: Optional. List of location identifiers for which service channels can be opened. By default, if the list of location identifiers is not provided, only the default location identifier is supported. If more identifiers should be supported and the default one is amongst them, you can add them as "" \(empty string\) in the list.

        For more information about location identifiers, see [Set up Connection Parameters and HTTPS Proxy](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-initial-configuration?version=Cloud#loiodb9170a7d97610148537d5a84bf79ba2__configure_proxy) \(step 4\).

        **Example \(Service Mapping\)**:

        > ### Sample Code:  
        > ```
        > spec:
        >   locationIds:
        >     - "locationId1"
        >     - "locationId2"
        >     - ""
        > ```

        > ### Note:  
        > The combination of `type`, `subaccountId` and `serviceId` for a s ervice mapping resource must be unique.


    > ### Note:  
    > The combination of `type`, `subaccountId`, and `serviceId` for a `ServiceMapping` resource should be unique.

3.  Once the `ServiceMapping` resource is successfully created, it is picked up and loaded in the Connectivity Proxy.

    > ### Caution:  
    > The `ServiceMapping` is a cluster-scoped Kubernetes resource. That is, the created `ServiceMapping`s are not bound to a specific namespace. They will be picked up from all namespaces of the Kubernetes cluster and loaded in the Connectivity Proxy.

    > ### Remember:  
    > Picking up and loading a newly created `ServiceMapping` resource in the Connectivity Proxy may take a few seconds, as it is done by Kubernetes-native mechanisms.

4.  After the `ServiceMapping` is loaded in the Connectivity Proxy, the cloud application can be consumed via the Cloud Connector as of version 2.15.0.
5.  To stop exposing the cloud application through the Connectivity Proxy, delete the corresponding `ServiceMapping` resource from the cluster.

