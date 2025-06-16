<!-- loio558b39a971c74f75835bc29d03199f23 -->

# TCP Destinations

The Transparent Proxy simplifies access to target systems defined as TCP destinations. It handles the TCP protocol for on-premise destinations.

The Connectivity Proxy provides a SOCKS5 proxy interface that you can use to access on-premise systems via TCP-based protocols. SOCKS5 is the industry standard for proxying TCP-based traffic. For more information, see [RFC 1928](https://www.ietf.org/rfc/rfc1928.txt).

The Transparent Proxy performs the SOCKS5 handshake with the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md) to enable the consumption of that \(otherwise complex\) functionality out-of-the-box for the application developer.

**Mandatory Destination Configuration Fields**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

Destination name

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

Destination type. Use TCP.

</td>
</tr>
<tr>
<td valign="top">

Address

</td>
<td valign="top">

<virtual\_host\>:<virtual\_port\> of the on-premise application

</td>
</tr>
<tr>
<td valign="top">

ProxyType

</td>
<td valign="top">

OnPremise

</td>
</tr>
</table>



<a name="loio558b39a971c74f75835bc29d03199f23__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must:

-   Fulfill the on-premise/private cloud connectivity prerequisites
-   Create an SAP BTP Destination

    For more information, see [Managing Destinations](managing-destinations-84e45e0.md).


This destination must have `Type` "TCP" and `ProxyType` "OnPremise".

**Example: TCP Destination**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-tcp",
>         "Type": "TCP",
>         "Address": "tcp://<virtual_host>:<virtual_port>",
>         "ProxyType": "OnPremise"
> }
> ```

To target the destination with the name "example-dest-tcp" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for a TCP destination in Transparent Proxy *dedicated* mode**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec: 
>   destinationRef:
>     name: "example-dest-tcp"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 20004 \(unless another port is specified in the destination CR\).

**Multitenant Usage** 

The Transparent Proxy supports multitenancy for TCP destinations. To consume a target system in a multitenant manner, describe all tenants in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation:

**Destination CR for a TCP destination in Transparent Proxy *shared* mode** 

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
>   annotations:
>     transparent-proxy.connectivity.api.sap/tenant-subdomains: '["tenant-subdomain", "another-tenant-subdomain"]'
>   destinationRef:
>     name: "example-dest-tcp"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for each of the tenants described in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation. The names of the Kubernetes services will be: <destination-cr-name\>-<tenant-subdomain\>.



<a name="loio558b39a971c74f75835bc29d03199f23__section_g4k_bwv_hcc"/>

## Consumption

Once done, the application could start consuming the destination from within the Kubernetes cluster.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**TCP Consumption Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace>
> ```

**TCP Consumption in *Shared* \(Multitenant\) Mode Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace>
> ```

> ### Note:  
> This is just an example, you should choose the right tool based on the system you want to consume.

