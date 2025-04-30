<!-- loio974a5e59d44245f2bb29e84dfb31b5d1 -->

# Get Logs and Change Log Levels

Get logs and change log levels for the Transparent Proxy for Kubernetes.



<a name="loio974a5e59d44245f2bb29e84dfb31b5d1__section_ydc_nfn_t5b"/>

## Get Logs of the Transparent Proxy Components

The Transparent Proxy consists of a Transparent Proxy manager, transparent HTTP proxy, transparent TCP proxy, and Transparent Proxy health check.

1.  To get the logs of the Transparent Proxy manager, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=manager --tail=-1 -n <installation-namespace> > transparent-proxy-manager.log
    ```

2.  To get the logs of the transparent HTTP proxy, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=http-proxy --all-containers --tail=-1 -n <installation-namespace> > transparent-http-proxy.log
    ```

3.  To get the logs of the transparent TCP proxy, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=tcp-proxy --tail=-1 -n <installation-namespace> > transparent-tcp-proxy.log
    ```

4.  To get the logs of the Transparent Proxy health check, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=healthcheck --tail=-1 -n <installation-namespace> > transparent-proxy-health-check.log
    ```

5.  To get the logs of the Transparent Proxy Operator \(installed only when [Transparent Proxy is enabled as a Kyma Module in the Kyma environment](transparent-proxy-in-the-kyma-environment-1700cfe.md)\) execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=operator --tail=-1 -n <installation-namespace> > transparent-proxy-operator.log
    ```


Files created by the above commands:

-   `transparent-proxy-manager.log`
-   `transparent-http-proxy.log`
-   `transparent-tcp-proxy.log`
-   `transparent-proxy-health-check.log`
-   `transparent-proxy-operator.log` 

can be used for investigation purposes. For more information, see [Recommended Actions](recommended-actions-20b1a62.md).



<a name="loio974a5e59d44245f2bb29e84dfb31b5d1__section_ng1_4fn_t5b"/>

## Get Status of *destinations.destination.connectivity.api.sap* Custom Resources

```
kubectl describe destinations -n <installation-namespace>
```



<a name="loio974a5e59d44245f2bb29e84dfb31b5d1__section_rjt_4sf_vwb"/>

## Change Log Levels of the Transparent Proxy Components

When the default logging level is not sufficient for debugging the issue you are facing, you can change the log level to get more insight about the problem.

Changing a log level is done without any downtime and requires no restarts. All you need to do is invoke a simple command on the pod of a Transparent Proxy component where you need to gain more insight. Here are some examples:

1.  To change the log level of the Transparent Proxy manager, execute:

    ```
    kubectl exec <transparent proxy manager pod> -n <installation-namespace> -it -- /etc/logging/change-log-level DEBUG
    ```

2.  To change the log level of the transparent HTTP proxy, execute:

    ```
    kubectl exec <transparent http proxy pod> -n <installation-namespace> -it -- /etc/logging/change-log-level DEBUG
    ```

3.  To change the log level of a transparent TCP proxy, execute:

    ```
    kubectl exec <transparent tcp proxy pod> -n <installation-namespace> -it -- /etc/logging/change-log-level DEBUG
    ```

4.  To change the log level of the Transparent Proxy health check, execute:

    ```
    kubectl exec <transparent proxy health check pod> -n <installation-namespace> -it -- /etc/logging/change-log-level DEBUG
    ```

5.  To change the log level of the Transparent Proxy Operator \(installed only when [Transparent Proxy is enabled as a Kyma Module in the Kyma environment](transparent-proxy-in-the-kyma-environment-1700cfe.md)\) execute:

    ```
    kubectl exec <transparent proxy operator pod> -n <installation-namespace> -it -- /etc/logging/change-log-level DEBUG
    ```


Accepted log levels are: `trace`, `debug`, `info`, `warn`, `error`, `fatal`. The default log level across all Transparent Proxy components is info.

