<!-- loio0097891bffc54edeabe0b0dc1df71e0a -->

# Monitoring

Check operability, scenarios and metrics of the connectivity proxy for Kubernetes.



<a name="loio0097891bffc54edeabe0b0dc1df71e0a__section_ovn_rmm_1qb"/>

## Basic Availability Monitoring

The basic availability check is the minimal verification you can do to make sure the connectivity proxy is alive. This check only shows if the process of the connectivity proxy is running and if it is able to handle requests. This check is also what is configured as the *liveness probe* for the Kubernetes deployment resource.

You can perform this check on-demand by invoking a simple HTTP GET request to the healthcheck endpoint of the connectivity proxy. If the response is ***200 OK***, the check was *successful*. Any other response means the check *failed*. There are two ways to perform this:

-   From **within the cluster**: Call `connectivity-proxy-tunnel:8042/healthcheck` and observe the result
-   From **outside the cluster**: Call `https://healthcheck.<ingress host of the connectivity proxy>/healthcheck` and observe the result. See [External Health Checking](external-health-checking-5c75674.md) for more details.



<a name="loio0097891bffc54edeabe0b0dc1df71e0a__section_az4_rmm_1qb"/>

## Scenario Monitoring

On top of the availability monitoring of the component itself, it is useful to also monitor entire scenarios. This, however, cannot be provided out of the box by the connectivity proxy as it is specific to the way you use the component. Some options you can explore for this are:

-   Monitor the failure rate of requests to the connectivity proxy.
-   Monitor the amount of error logs in the connectivity proxy.
-   Set up a scheduled execution of a full scenario that performs end-to-end verification, including the operations done via the connectivity proxy.



<a name="loio0097891bffc54edeabe0b0dc1df71e0a__section_f1p_rmm_1qb"/>

## Metrics

The connectivity proxy supports the collection and exposure of metrics in *Prometheus* format.

The metrics are exposed through an HTTP endpoint on the port specified in the configuration \(default: 9494\).

To enable the collection and exposure of metrics, set `config.metrics.prometheus.enabled` to true.

```
config:
  metrics:
    prometheus:
      enabled: true
```

To obtain the collected metrics, send an HTTP GET request to the \`/metrics\` endpoint of the connectivity proxy.

```
curl http://connectivity-proxy-prometheus-metrics:9494/metrics
```

The metrics collected in the connectivity proxy without any additional configuration include:

-   **connectivity\_tunnel\_opening\_timeout\_count\_total**: This metric tracks the total number of tunnel openings that have timed out.

    By default, if a tunnel opening takes longer than 10 seconds, it is deemed to have timed out.

    This metric reflects the total count of such timeout occurrences. Additionally, a tunnel ID is included as a label in the metric.

    > ### Sample Code:  
    > ```
    > # HELP connectivity_tunnel_opening_timeout_count_total Total number of tunnel openings that timed out
    > # TYPE connectivity_tunnel_opening_timeout_count_total counter
    > connectivity_tunnel_opening_timeout_count_total{tunnel_id="account:///83039ea2-e213-46e5-9723-fbfa2d0f7ee3"} 1.0
    > ```


-   **connectivity\_business\_data\_tunnels\_count**: This metric tracks the total number of active business data tunnels \(connections between the connectivity proxy and different Cloud Connectors\).

    > ### Sample Code:  
    > ```
    > # HELP connectivity_business_data_tunnels_count Total number of active business data tunnels
    > # TYPE connectivity_business_data_tunnels_count gauge
    > connectivity_business_data_tunnels_count 5.0
    > ```


The connectivity proxy also supports the collection of JVM-related metrics by setting `config.metrics.prometheus.jvmMetrics.enabled` to true:

```
config:
  metrics:
    prometheus:
      enabled: true
      jvmMetrics:
        enabled: true
```

This will expose the following JVM-related metrics:

-   JVM Buffer Pool Metrics
-   JVM Class Loading Metrics
-   JVM Compilation Metrics
-   JVM Garbage Collector Metrics
-   JVM Memory Metrics
-   JVM Memory Pool Allocation Metrics
-   JVM Runtime Info Metric
-   JVM Thread Metrics
-   Process Metrics

The full list of JVM-related and process-related metrics with descriptions can be found in the [Prometheus Java Client documentation](https://prometheus.github.io/client_java/instrumentation/jvm/).

There is also support for collecting metrics from JMX that are exposed by the connectivity proxy.

To enable this, set `config.metrics.prometheus.jmxMetrics.enabled` to true:

```
config:
  metrics:
    prometheus:
      enabled: true
      jmxMetrics:
        enabled: true
```

The JMX metrics collected by the connectivity proxy include:

-   `connectivity_proxy_open_tunnel_call_health_status` - Health status of the open tunnel call.

    This metric indicates the health status of the open tunnel call.

    It reports a value of 1 if the open tunnel call is considered healthy and 0 if it is not.

    A failure may occur for various reasons, such as a network issue or an internal error.

    A call is considered a failure if either the last five open tunnel calls failed or if at least 60% of the last fifteen open tunnel calls failed.


```
# HELP connectivity_proxy_open_tunnel_call_health_status Open tunnel call health status of the connectivity proxy
# TYPE connectivity_proxy_open_tunnel_call_health_status gauge
connectivity_proxy_open_tunnel_call_health_status 1.0
```

> ### Note:  
> The standard Prometheus format allows for integration with various monitoring and alerting tools, such as Grafana, Prometheus, Dynatrace, and others.

