<!-- loioaec9009a8c044101b34d532a5770dffc -->

# Recommended Actions

Find procedures to resolve an outage of the Connectivity Proxy for Kubernetes functionality.

> ### Caution:  
> Before performing any of the steps below, make sure there is really an outage of the Connectivity Proxy and not just a general problem on the entire cluster.

[Pre-Intervention Steps](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__pre)

[Recovery Attempt](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__recovery)

[Request Help from SAP](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__help)

[Request Root Cause Analysis \(RCA\)](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__rca)



<a name="loioaec9009a8c044101b34d532a5770dffc__pre"/>

## Pre-Intervention Steps

Before doing any restarts or modifications, it is important that you collect all relevant information.

1.  Check the status of the Connectivity Proxy pods and collect the outcome. Example via `kubectl`:

    ```
    kubectl get pods | grep 'connectivity-proxy'
    ```

2.  Perform basic availability monitoring from *within* the cluster, as described in [Monitoring](monitoring-0097891.md), and collect the outcome. This can be done from an existing container or by spinning up a container for the check. Example:

    ```
    kubectl run perform-hc --image=curlimages/curl -it --rm --restart=Never -- curl -vvv 'connectivity-proxy-tunnel:8042/healthcheck'
    ```

3.  Perform basic availability monitoring from *outside* the cluster, as described in [Monitoring](monitoring-0097891.md), and collect the outcome. This can be done from your browser or via REST clients like cUrl or Postman. Example:

    ```
    curl -vvv 'https://healthcheck.connectivitytunnel.ingress.mycluster.com/healthcheck'
    ```

4.  Collect the logs of the Connectivity Proxy \(see [Troubleshooting](troubleshooting-e7a04d9.md)\).
5.  Proceed to **Recovery Attempt**.

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)



<a name="loioaec9009a8c044101b34d532a5770dffc__recovery"/>

## Recovery Attempt

The exact action to take here depends on the check result in steps 2 and 3 of section [Pre-Intervention Steps](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__pre). Choose one of the four options below, according to the outcome of your checks.

> ### Tip:  
> Check if the cause of the outage might be insufficient resources. For more information, see [Sizing Recommendations](sizing-recommendations-204822a.md). If this is the possible cause, try scaling the Connectivity Proxy vertically and/or horizontally \(see [Configuration Guide](configuration-guide-eaa8204.md)\).

-   Option 1: [Check *Succeeds* from within the Cluster and *Fails* from outside the Cluster](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__succeed_fail)
-   Option 2: [Check *Fails* from within the Cluster and *Succeeds* from outside the Cluster](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__fail_succeed)
-   Option 3: [Check *Fails* from within the Cluster and *Fails* from outside the Cluster](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__fail_fail)
-   Option 4: [Check *Succeeds* from within the Cluster and *Succeeds* from outside the Cluster](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__succeed_succeed)

**Check *Succeeds* from within the Cluster and *Fails* from outside the Cluster**

This indicates some sort of issue with the Ingress configuration. Some possible reasons:

-   TLS certificate has expired.
-   Something went wrong with the Ingress controller.

Such a situation is likely not an issue with the Connectivity Proxy. Next steps should be to stop following the steps here and shift focus towards the Ingress configuration and Ingress controller.

[Back to Recovery Attempt](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__recovery)

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)

**Check *Fails* from within the Cluster and *Succeeds* from outside the Cluster**

This indicates some sort of issue with the exposure of the Connectivity Proxy to internal pods. Some possible reasons:

-   Some unwanted network policy came into effect, preventing calls to the Connectivity Proxy from where you are executing them.

Such a situation is likely not an issue with the Connectivity Proxy. Next steps should be to stop following the steps here and shift focus towards cluster configurations and the network policies that affect access to the Connectivity Proxy.

[Back to Recovery Attempt](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__recovery)

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)

**Check *Fails* from within the Cluster and *Fails* from outside the Cluster**

This indicates that the Connectivity Proxy itself is indeed having issues. Please perform the following steps:

1.  Restart the Connectivity Proxy deployment. Example via `kubectl`:

    ```
    kubectl rollout restart statefulset/connectivity-proxy
    ```

2.  Collect logs from the Connectivity Proxy after the restart completes.
3.  Check if outage is still ongoing:
    1.  If no, issue is resolved, proceed with [Request Root Cause Analysis \(RCA\)](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__rca).
    2.  If yes, issue is not resolved, proceed with [Request Help from SAP](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__help).


[Back to Recovery Attempt](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__recovery)

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)

**Check *Succeeds* from within the Cluster and *Succeeds* from outside the Cluster**

This indicates that the Connectivity Proxy is currently considered operational, however it might still have trouble when used for real scenarios \(depends on how you detect the outage\).

1.  Check if the outage is still ongoing:
    -   If no, issue is resolved, proceed with [Request Root Cause Analysis \(RCA\)](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__rca).

    -   If yes, issue is not resolved, proceed with the next step.


2.  Restart the Connectivity Proxy deployment. Example via `kubectl`:

    ```
    kubectl rollout restart statefulset/connectivity-proxy
    ```

3.  Collect logs from the Connectivity Proxy after the restart completes.
4.  Check if outage is still ongoing:
    -   If no, issue is resolved, proceed with [Request Root Cause Analysis \(RCA\)](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__rca).
    -   If yes, issue is not resolved, proceed with [Request Help from SAP](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__help).


[Back to Recovery Attempt](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__recovery)

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)



<a name="loioaec9009a8c044101b34d532a5770dffc__help"/>

## Request Help from SAP

If you cannot resolve the issue and require help from SAP, follow this procedure:

1.  Open an incident on the support component \(see [Connectivity Support](connectivity-support-e5580c5.md)\) for the Connectivity Proxy \(with the appropriate priority and impact stated\).
2.  Provide all the collected information in the incident, including all the logs, timestamps of the events that occurred, summary of the taken actions, version of the Connectivity Proxy you are using, and so on.
3.  Engage your SAP contacts to help with this.
4.  Continue working in parallel to identify as much information as possible or to fine a temporary measure to mitigate the outage.

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)



<a name="loioaec9009a8c044101b34d532a5770dffc__rca"/>

## Request Root Cause Analysis \(RCA\)

Once the issue is resolved, the next step is figuring out what exactly caused the issue and if there is something that can be done to prevent it from happening in the future. Follow this procedure for requesting RCA for the issue you experienced:

1.  Open an incident on the support component for the Connectivity Proxy \(see [Connectivity Support](connectivity-support-e5580c5.md)\).
2.  Provide all the collected information in the incident, including all the logs, timestamps of the events that occurred, summary of the taken actions, version of the Connectivity Proxy you are using, and so on.
3.  The incident will be handled according to the SAP incident SLAs.

[Back to Top](recommended-actions-aec9009.md#loioaec9009a8c044101b34d532a5770dffc__top)

