<!-- loioba6f417fced446bb8bd47dd265fe22e1 -->

# Monitoring

Check the availability, status, and destination custom resources of the transparent proxy for Kubernetes.



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_dp2_wxf_vwb"/>

## Availability Monitoring

The availability check of the transparent proxy is the minimal verification that can be done to ensure that the transparent proxy is alive and working. This is done by a health check application deployed to the cluster during installation of the transparent proxy.



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_bwf_gfn_t5b"/>

## Status Check

The `/status` check performs the following :

-   If there are HTTP custom resources defined → is the `sap-transp-proxy-http` alive and running?
-   If there are non-HTTP custom resources defined → are all `sap-transp-proxy-tcp` pods alive and running?
-   Is the `sap-transp-proxy-manager` alive and running?

The overall status provided by the `/status` endpoint is formed in the following way:

-   if all used components are in `ok` status→ overall status is `ok`.
-   if some, but not all components are in `critical` status → overall status is `warning`.
-   if all components are in `critical` status → overall status is `critical`.



<a name="loioba6f417fced446bb8bd47dd265fe22e1__section_qzv_bsp_55b"/>

## Destination Custom Resources Check

The `/destinationCRs` check provides information for all destination custom resources in the namespace where the transparent proxy is installed.

To find an example, see [Verification and Testing](verification-and-testing-86dde3e.md).

