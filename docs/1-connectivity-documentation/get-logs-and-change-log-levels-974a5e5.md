<!-- loio974a5e59d44245f2bb29e84dfb31b5d1 -->

# Get Logs and Change Log Levels

Get logs and change log levels for the Transparent Proxy for Kubernetes.



<a name="loio974a5e59d44245f2bb29e84dfb31b5d1__section_ydc_nfn_t5b"/>

## Get Logs of the Transparent Proxy Components

The Transparent Proxy consists of a Transparent Proxy Manager, Transparent HTTP Proxy, Transparent TCP Proxy, Transparent Proxy Health Check, and Transparent Proxy Operator.

1.  To get the logs of the Transparent Proxy Manager, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=manager --tail=-1 -n <installation-namespace> > transparent-proxy-manager.log
    ```

2.  To get the logs of the Transparent HTTP Proxy, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=http-proxy --all-containers --tail=-1 -n <installation-namespace> > transparent-http-proxy.log
    ```

3.  To get the logs of the Transparent TCP Proxy, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=tcp-proxy --tail=-1 -n <installation-namespace> > transparent-tcp-proxy.log
    ```

4.  To get the logs of the Transparent Proxy Health Check, execute:

    ```
    kubectl logs -l transparent-proxy.connectivity.api.sap/component=healthcheck --tail=-1 -n <installation-namespace> > transparent-proxy-health-check.log
    ```

5.  To get the logs of the Transparent Proxy Operator \(not installed when Transparent Proxy is deployed via Helm\) execute:

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

Changing a log level is done without any downtime and requires no restarts. All you need to do is invoke a simple command in the namespace of the Transparent Proxy to gain more insight about a component. Here are some examples:

**Prerequisites:**

-   Kubectl version: Client v1.25+ \(Recommended: v1.28+\).
-   Cluster version: Kubernetes v1.25+ \(ephemeral containers must be enabled\).
-   Version compatibility: The kubectl client version must be within +/- 1 minor version of the Kubernetes server version.
    -   Example: If the server is v1.33, the client must be v1.32, v1.33, or v1.34.

        > ### Note:  
        > Larger version gaps cause API mismatches that break the `--profile` flag.



1.  To change the log level of the Transparent Proxy Manager, execute:

    ```
    kubectl debug -it <pod-name> \
    		--namespace=<installation-namespace> \
    		--image=alpine \
    		--target=sap-transp-proxy-manager \
    		--profile=sysadmin \
    		-- sh -c "printf 'log:\n  level: <log-level>' > /proc/1/root/etc/logging/logger-config.yaml"
    ```

2.  To change the log level of the Transparent HTTP Proxy, execute:

    ```
    kubectl debug -it <pod-name> \
    	    --namespace=<installation-namespace> \
    		--image=alpine \
    		--target=sap-transp-proxy-http \
    		--profile=sysadmin \
    		-- sh -c "printf 'log:\n  level: <log-level>' > /proc/1/root/etc/logging/logger-config.yaml"
    ```

3.  To change the log level of a Transparent TCP Proxy, execute:

    ```
    kubectl debug -it <pod-name> \
    	    --namespace=<installation-namespace> \
    		--image=alpine \
    		--target=sap-transp-proxy-tcp \
    		--profile=sysadmin \
    		-- sh -c "printf 'log:\n  level: <log-level>' > /proc/1/root/etc/logging/logger-config.yaml"
    ```

4.  To change the log level of the Transparent Proxy Health Check, execute:

    ```
    kubectl debug -it <pod-name> \
    	    --namespace=<installation-namespace> \
    		--image=alpine \
    		--target=sap-transp-proxy-healthcheck \
    		--profile=sysadmin \
    		-- sh -c "printf 'log:\n  level: <log-level>' > /proc/1/root/etc/logging/logger-config.yaml"
    ```

5.  To change the log level of the Transparent Proxy Operator \(installed only when [Transparent Proxy is enabled as a Kyma Module in the Kyma environment](transparent-proxy-in-the-kyma-environment-1700cfe.md)\) execute:

    ```
    kubectl debug -it <pod-name> \
    	    --namespace=<installation-namespace> \
    		--image=alpine \
            --target=sap-transp-proxy-operator \
            --profile=sysadmin \
            -- sh -c "printf 'log:\n  level: <log-level>' > /proc/1/root/etc/logging/logger-config.yaml"
    ```


Accepted log levels are: `trace`, `debug`, `info`, `warn`, `error`, `fatal`. The default log level across all Transparent Proxy components is info.

