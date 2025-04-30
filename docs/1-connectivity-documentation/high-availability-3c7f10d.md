<!-- loio3c7f10d78d6b43c680c2ab99e28f6b19 -->

# High Availability

Run the Connectivity Proxy for Kubernetes in a high-availability setup.



<a name="loio3c7f10d78d6b43c680c2ab99e28f6b19__content"/>

## Content

[Overview](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__overview)

[High-Availability Modes](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__modes)

[Advantages and Drawbacks](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__advantages)

[High-Availability Mode: *Path*](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__path)

[High-Availability Mode: *Subdomain*](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__subdomain)



<a name="loio3c7f10d78d6b43c680c2ab99e28f6b19__overview"/>

## Overview

The Connectivity Proxy can work in an active-active high-availability setup. In this setup, there are at least two Connectivity Proxy instances, both running actively and simultaneously.

The main purpose of an active-active deployment is to provide high availability and allow zero-downtime maintenance as well as horizontal-scaling capabilities.

The Kubernetes service exposing the Connectivity Proxy pods distributes and load-balances the traffic from the workloads across all running Connectivity Proxy pods.

> ### Note:  
> The load balancing strategy for distributing traffic to the Connectivity Proxy pods depends on the *kube-proxy* mode. The strategies used by the different *kube-proxy* modes are described in the [Kubernetes documentation](https://kubernetes.io/docs/concepts/services-networking/service/#virtual-ips-and-service-proxies). This configuration is done on cluster level.

> ### Tip:  
> [MultiAZ with Pod Anti-Affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/) and [PodDisruptionBudget](https://kubernetes.io/docs/tasks/run-application/configure-pdb/) are supported out of the box in the Helm chart.

[Back to Content](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__content)



<a name="loio3c7f10d78d6b43c680c2ab99e28f6b19__modes"/>

## High-Availability Modes

There are two technical options \(modes\) for the active-active deployment:

-   *Path*
-   *Subdomain*

The difference between the two modes is in the way the routing information of the current Connectivity Proxy \(which is being used for the current connection\) is passed to the Cloud Connector.

Depending on the perspective, as well as on the concrete requirements and boundaries you have, both modes may have advantages and drawbacks, so you should carefully choose the one which best suits your needs.

The number of Connectivity Proxy instances that run simultaneously depends on the *replicaCount* configuration in the `values.yml` file.

```
deployment:
  replicaCount: <number_of_replicas>
```

[Back to Content](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__content)



<a name="loio3c7f10d78d6b43c680c2ab99e28f6b19__advantages"/>

## Advantages and Drawbacks


<table>
<tr>
<th valign="top">

High-Availability Mode

</th>
<th valign="top">

Path

</th>
<th valign="top">

Subdomain

</th>
</tr>
<tr>
<td valign="top">

Compatibility with end-to-end mutual TLS without termination

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Compatibility with secure and inexpensive certificates

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
</tr>
</table>

[Back to Content](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__content)



<a name="loio3c7f10d78d6b43c680c2ab99e28f6b19__path"/>

## High-Availability Mode: *Path* 

To configure the Connectivity Proxy for the high-availability mode *Path*, add the following configuration in the `values.yml` file:

```
config:
  highAvailabilityMode: "path"
```

[Back to Content](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__content)



<a name="loio3c7f10d78d6b43c680c2ab99e28f6b19__subdomain"/>

## High-Availability Mode: *Subdomain* 

To configure the Connectivity Proxy for the high-availability mode *Subdomain*, add the following configuration in the `values.yml file`:

```
config:
  highAvailabilityMode: "subdomain"
```

> ### Note:  
> High-Availability mode *Subdomain* uses either wildcard certificates or SAN \(Subject Alternative Name\) certificates. Wildcard certificates cover all possible subdomains. However, they are insecure since when the certificate key that is installed on one subdomain gets compromised, it will be compromised on all of the subdomains it is installed on. A safer option is to use SAN certificates, although they may be expensive and require each subdomain to be specified explicitly.

[Back to Content](high-availability-3c7f10d.md#loio3c7f10d78d6b43c680c2ab99e28f6b19__content)

