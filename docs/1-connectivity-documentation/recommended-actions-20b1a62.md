<!-- loio20b1a62d6df447daa82fb10962049805 -->

# Recommended Actions

To resolve issues with the Transparent Proxy for Kubernetes, follow the recommendations below.



<a name="loio20b1a62d6df447daa82fb10962049805__pre"/>

## Pre-Intervention Steps

Before doing any restarts or modifications, it is important that you collect all relevant information.

1.  Check the status of the Transparent Proxy pods and collect the outcome. Example via `kubectl`:
    1.  Get the status of the Transparent Proxy manager executions:

        ```
        kubectl get pods -l transparent-proxy.connectivity.api.sap/component=manager –n <installation-namespace>
        ```

    2.  Get the status of the Transparent HTTP Proxy pods:

        ```
        kubectl get pods -l transparent-proxy.connectivity.api.sap/component=http-proxy –n <installation-namespace>
        ```

    3.  Get the status of the Transparent TCP Proxy pods:

        ```
        kubectl get pods -l transparent-proxy.connectivity.api.sap/component=tcp-proxy –n <installation-namespace>
        ```


2.  Perform basic availability monitoring from within the cluster as described in [Monitoring](monitoring-ba6f417.md), and collect the outcome.
3.  Collect the logs of all Transparent Proxy components \(see [Troubleshooting](troubleshooting-fce292a.md)\).
4.  Collect the status of all `destinations.destination.connectivity.api.sap` custom resources \(see [Troubleshooting](troubleshooting-fce292a.md)\).
5.  Proceed with [Recovery Attempt](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__recovery) below.



<a name="loio20b1a62d6df447daa82fb10962049805__recovery"/>

## Recovery Attempt

The exact action to take here depends on the check result in step 2 of section [Pre-Intervention Steps](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__pre). Choose one of the two options below, according to the outcome of your checks.

-   Option 1: [Check Succeeds](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__succeeds)
-   Option 2: [Check Fails](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__fails)



<a name="loio20b1a62d6df447daa82fb10962049805__succeeds"/>

## Check Succeeds

This indicates that the Transparent Proxy is currently considered operational. However, it might still have trouble when used for real scenarios \(depending on how you detect the outage\).

1.  Check if the outage is still ongoing:
    1.  If no, issue is resolved, proceed with [Request Root Cause Analysis\(RCA\)](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__rca).
    2.  If yes, issue is not resolved, proceed with the next step.

2.  Wait for the next Transparent Proxy manager completion.
3.  Check if the outage is still ongoing:
    1.  If no, issue is resolved, proceed with [Request Root Cause Analysis\(RCA\)](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__rca).
    2.  If yes, issue is not resolved, proceed with the next step.

4.  Restart the Transparent HTTP Proxy and Transparent TCP Proxy instances. Example via `kubectl`:

    ```
    k delete po -l transparent-proxy.connectivity.api.sap/component=http-proxy -n <installation-namespace>
    
    ```

    ```
    k delete po -l transparent-proxy.connectivity.api.sap/component=tcp-proxy -n <installation-namespace>
    ```

5.  Collect the logs from the Transparent Proxy components after the restart completes.
6.  Check if outage is still ongoing:
    1.  If no, issue is resolved, proceed with [Request Root Cause Analysis\(RCA\)](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__rca).
    2.  If yes, issue is not resolved, proceed with [Request Help from SAP](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__help).




<a name="loio20b1a62d6df447daa82fb10962049805__fails"/>

## Check Fails

This indicates that the Transparent Proxy itself is indeed having issues. Please perform the following steps:

1.  Wait for the next Transparent Proxy manager completion.
2.  Check if the outage is still ongoing:
    1.  If no, issue is resolved, proceed with [Request Root Cause Analysis\(RCA\)](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__rca).
    2.  If yes, issue is not resolved, proceed with the next step.

3.  Restart the Transparent HTTP Proxy and Transparent TCP Proxy instances. Example via `kubectl`:

    ```
    k delete po -l transparent-proxy.connectivity.api.sap/component=http-proxy -n <installation-namespace>
    
    ```

    ```
    k delete po -l transparent-proxy.connectivity.api.sap/component=tcp-proxy -n <installation-namespace>
    ```

4.  Collect logs from the Transparent Proxy after the restart completes.
5.  Check if outage is still ongoing:
    1.  If no, issue is resolved, proceed with [Request Root Cause Analysis\(RCA\)](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__rca).
    2.  If yes, issue is not resolved, proceed with [Request Help from SAP](recommended-actions-20b1a62.md#loio20b1a62d6df447daa82fb10962049805__help).




<a name="loio20b1a62d6df447daa82fb10962049805__help"/>

## Request Help from SAP

If you cannot resolve the issue and require help from SAP, follow this procedure:

1.  Open an incident on the support component BC-CP-CON-K8S-TP for the Transparent Proxy \(with the appropriate priority and impact stated\).
2.  Provide all the collected information in the incident, including all the logs, timestamps of the events that occurred, a summary of the taken actions, the version of the Transparent Proxy you are using, and so on.
3.  Engage your SAP contacts to help with this.
4.  Continue working in parallel to identify as much information as possible or to find a temporary measure to mitigate the outage.



<a name="loio20b1a62d6df447daa82fb10962049805__rca"/>

## Request Root Cause Analysis \(RCA\)

Once the issue is resolved, the next step is figuring out what exactly caused the issue and if there is something that can be done to prevent it from happening in the future.

Follow this procedure for requesting RCA for the issue you experienced:

1.  Open an incident on the support component for the Transparent Proxy on the support component BC-CP-CON-K8S-TP.
2.  Provide all the collected information in the incident, including all the logs, timestamps of the events that occurred, a summary of the taken actions, the version of the Transparent Proxy you are using, and so on.

The incident will be handled according to the SAP incident SLAs.

