<!-- loiofb92ab615a57408780bfad79e03b4f86 -->

# High Availability

Run the Transparent Proxy for Kubernetes in a high-availability setup.



<a name="loiofb92ab615a57408780bfad79e03b4f86__section_qfq_cdn_t5b"/>

## Overview

The Transparent Proxy can work in an active-active high-availability setup. In this setup, there are at least two Transparent Proxy instances, both running actively and simultaneously.

The main purpose of an active-active deployment is to provide high availability and allow zero-downtime maintenance as well as horizontal-scaling capabilities.



> ### Note:  
> The load balancing strategy for distributing traffic to the Connectivity Proxy pods depends on the kube-proxy mode. The strategies used by the different kube-proxy modes are described in the [Kubernetes documentation](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fkubernetes.io%2Fdocs%2Fconcepts%2Fservices-networking%2Fservice%2F%23virtual-ips-and-service-proxies). This configuration is done on cluster level.



<a name="loiofb92ab615a57408780bfad79e03b4f86__section_qtt_n1g_rtb"/>

## Scaling

If you need to scale your Transparent Proxy, you can do so by updating your Helm chart. Follow these steps:

1.  For horizontal scaling of the TCP and HTTP proxy, update the `values.yaml`, and more concretely `deployment.replicas.tcp` for HTTP and `deployment.replicas.tcp` for TCP, as described in the [Configuration](configuration-guide-2a22cd7.md#loio2a22cd7872964e6a9ceb5af72920cfd0__config) section.
2.  For vertical scaling, update the respective `deployment.resources.limits` and `deployment.resources.requests` properties for *CPU* and *Memory* described in the [Configuration](configuration-guide-2a22cd7.md#loio2a22cd7872964e6a9ceb5af72920cfd0__config) section.
3.  To enable autoscaling of the Transparent Proxy, update the respective `deployment.autoscaling.*` properties.

    > ### Note:  
    > Horizontal and vertical autoscaling cannot be activated simultaneously. You have to choose one or the other.




<a name="loiofb92ab615a57408780bfad79e03b4f86__section_ns4_3xm_t5b"/>

## Multi-AZ

If the Kubernetes cluster is configured with two or more nodes running in different availability zones \(AZ\), the Transparent Proxy automatically deploys and runs in the AZs for the Kubernetes cluster that matches the nodes.

