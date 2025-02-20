<!-- loio7437cd6eda804e69b6cca6ae4b49daa8 -->

# Configuration Setup

Choose the right connection configuration options to improve the performance of the Cloud Connector.

This section provides detailed information how you can adjust the configuration to improve overall performance. This is typically relevant for an M or L installation \(see [Hardware Setup](hardware-setup-a84034a.md)\). For S installations, the default configuration will probably be sufficient to handle the traffic.

To change the connection parameters, proceed as follows:

-   You can configure the number of physical connections through the Cloud Connector UI. See also [Configure Advanced Connectivity](configure-advanced-connectivity-3975253.md).
-   In versions prior to 2.11, you have to modify the configuration files with an editor and restart the Cloud Connector to activate the changes.

In general, the Cloud Connector tunnel is multiplexing multiple virtual connections over a single physical connection. Thus, a single connection can handle a considerable amount of traffic. However, increasing the maximum number of physical connections allows you to make use of the full available bandwidth and to minimize latency effects.

If the bandwidth limit of your network is reached, adding additional connections doesn't increase the throughput, but will only consume more resources.

> ### Note:  
> Different network access parameters may impact and limit your configuration options: if the access to an external network is a 1 MB line with an added latency of 50 ms, you will not be able to achieve the same data volumes like with a 10 GB line with an added latency of < 1 ms. However, even if the line is good, for example 10 GB, but with an added latency of 100 ms, the performance might still be bad.

Optimal configuration strongly depends on your actual scenarios. A good approach is to try out different settings, if the current performance does not meet your expectations.

**Related Information**  


[Cloud To On-Premise Connections](cloud-to-on-premise-connections-f9111c8.md "Configure the physical connections for cloud-to-on-premise calls in the Cloud Connector.")

[On-Premise To Cloud Connections \(Service Channels\)](on-premise-to-cloud-connections-service-channels-d404d6f.md "Configure the number of physical connections for a Cloud Connector service channel.")

