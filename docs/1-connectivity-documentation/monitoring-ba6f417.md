<!-- loioba6f417fced446bb8bd47dd265fe22e1 -->

# Monitoring

Check the availability, status, and destination custom resources of the Transparent Proxy for Kubernetes.



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_dp2_wxf_vwb"/>

## Availability Monitoring

The availability check of the Transparent Proxy is the minimal verification that can be done to ensure that the Transparent Proxy is alive and working. This is done by a health check application deployed to the cluster during installation of the Transparent Proxy.



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_bwf_gfn_t5b"/>

## Status Check

The `/status` check performs the following :

-   If there are HTTP custom resources defined → is the `sap-transp-proxy-http` alive and running?
-   If there are non-HTTP custom resources defined → is the `sap-transp-proxy-tcp` pod alive and running?
-   Is the `sap-transp-proxy-manager` alive and running?

The overall status provided by the `/status` endpoint is formed in the following way:

-   if all used components are in `ok` status→ overall status is `ok`.
-   if some, but not all components are in `critical` status → overall status is `warning`.
-   if all components are in `critical` status → overall status is `critical`.



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_qzv_bsp_55b"/>

## Destination Custom Resources Check

The `/destinationCRs` check provides information for all destination custom resources in the namespace where the Transparent Proxy is installed.

To find an example, see [Verification and Testing](verification-and-testing-86dde3e.md).



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_zxj_b4n_j2c"/>

## Monitoring

The Transparent Proxy supports the collection and exposure of metrics in *OpenMetrics* format.

The metrics are exposed through an HTTP endpoint on port **9494**.

To enable the collection and exposure of metrics, set `config.metrics.prometheus.enabled` to true.

```
config:
  metrics:
    prometheus:
      enabled: true
```

> ### Note:  
> The Transparent Proxy requires Prometheus version v2.0.0 or higher.

To obtain the collected metrics, send an `HTTP GET` request to the `/metrics` endpoint on any of the Transparent Proxy components.

```
curl http://sap-transp-proxy-manager-metrics.<transparent-proxy-namespace>:9494/metrics // Obtain metrics for sap-transp-proxy-manager
curl http://sap-transp-proxy-healthcheck-metrics.<transparent-proxy-namespace>:9494/metrics // Obtain metrics for sap-transp-proxy-healthcheck
curl http://sap-transp-proxy-tcp-metrics.<transparent-proxy-namespace>:9494/metrics // Obtain metrics for sap-transp-proxy-tcp
curl http://sap-transp-proxy-http-metrics.<transparent-proxy-namespace>:9494/metrics // Obtain metrics for sap-transp-proxy-http
```

Each component exposes metrics for CPU and memory :

> ### Sample Code:  
> ```
> # HELP tp_cpu_percent Process CPU usage percentage
> # TYPE tp_cpu_percent gauge
> tp_cpu_percent{otel_scope_name="system-metrics",otel_scope_version=""} 0.025630845500773086
> # HELP tp_memory_bytes Process memory usage
> # TYPE tp_memory_bytes gauge
> tp_memory_bytes{otel_scope_name="system-metrics",otel_scope_version=""} 4.9000448e+07
> ```

**Custom metrics for sap-transp-proxy-healthcheck:**

-   **tp\_destination\_crs** - This metric tracks the total number of destination custom resources \(CRs\) divided by label *Available* which can be either *True* or *False* depending on the status of the destination CR.


> ### Sample Code:  
> ```
> # HELP tp_destination_crs Total Destination Crs
> # TYPE tp_destination_crs gauge
> tp_destination_crs{Available="False",otel_scope_name="sap-transp-proxy-healthcheck",otel_scope_version=""} 0
> tp_destination_crs{Available="True",otel_scope_name="sap-transp-proxy-healthcheck",otel_scope_version=""} 18
> ```

**Custom metrics for sap-transp-proxy-http:** 

-   **tp\_received\_requests\_total** - This metric tracks the total number of requests that the transparent HTTP proxy has received.

    > ### Sample Code:  
    > ```
    > # HELP tp_received_requests_total Total Received Requests
    > # TYPE tp_received_requests_total counter
    > tp_received_requests_total{otel_scope_name="sap-transp-proxy-conn-handler",otel_scope_version=""} 112
    > ```

-   **tp\_target\_system\_requests\_total** - This metric tracks the total number of requests that have been made through the whole chain to the target system.

    > ### Sample Code:  
    > ```
    > # HELP tp_target_system_requests_total Total Target Systems Requests
    > # TYPE tp_target_system_requests_total counter
    > tp_target_system_requests_total{otel_scope_name="sap-transp-proxy-conn-handler",otel_scope_version=""} 82
    > ```


**Custom metrics for sap-transp-proxy-tcp:** 

-   **tp\_open\_tcp\_connections** - This metric tracks the total number of opened connections at the given time.

    > ### Sample Code:  
    > ```
    > # HELP tp_open_tcp_connections Opened tcp connections
    > # TYPE tp_open_tcp_connections gauge
    > tp_open_tcp_connections{otel_scope_name="sap-transp-proxy-tcp",otel_scope_version=""} 26
    > ```

-   **tp\_tcp\_connections\_total** - This metric tracks the total number of connections to the transparent TCP proxy.

    > ### Sample Code:  
    > ```
    > # HELP tp_tcp_connections_total Total tcp connections
    > # TYPE tp_tcp_connections_total counter
    > tp_tcp_connections_total{otel_scope_name="sap-transp-proxy-tcp",otel_scope_version=""} 15
    > ```


> ### Note:  
> The standard *OpenMetrics* format allows for integration with various monitoring and alerting tools, such as *Prometheus*, *Grafana*, *Dynatrace* and others.

