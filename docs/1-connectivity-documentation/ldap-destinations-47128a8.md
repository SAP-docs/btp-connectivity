<!-- loio47128a845bd3459f80ed8a36ff3518b6 -->

# LDAP Destinations

The Transparent Proxy simplifies access to target systems defined as LDAP destinations. It handles the LDAP protocol for on-premise destinations.

The Transparent Proxy performs the connectivity handshake with the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md) to enable the consumption of that \(otherwise complex\) functionality out-of-the-box for the application developer. If the destination is configured with ldap.authentication "BasicAuthentication", the Transparent Proxy executes LDAP simple authentication bind with the on-premise system using the username and password provided in the destination on behalf of the client.

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

Destination type. Use LDAP.

</td>
</tr>
<tr>
<td valign="top">

ldap.url

</td>
<td valign="top">

<virtual\_host\>:<virtual\_port\> of the on-premise application

</td>
</tr>
<tr>
<td valign="top">

ldap.proxyType

</td>
<td valign="top">

OnPremise

</td>
</tr>
<tr>
<td valign="top">

ldap.authentication

</td>
<td valign="top">

Use "BasicAuthentication" or "NoAuthentication".

</td>
</tr>
<tr>
<td valign="top">

ldap.user

</td>
<td valign="top">

Mandatory when ldap.authentication is "BasicAuthentication"

</td>
</tr>
<tr>
<td valign="top">

ldap.password

</td>
<td valign="top">

Mandatory when ldap.authentication is "BasicAuthentication"

</td>
</tr>
</table>



<a name="loio47128a845bd3459f80ed8a36ff3518b6__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must:

-   Fulfill the on-premise/private cloud connectivity prerequisites
-   Create an SAP BTP Destination

This destination should have `Type` "LDAP" and `ldap.proxyType` "OnPremise", for example:

**LDAP Destination**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-ldap",
>         "Type": "LDAP",
>         "ldap.user": <username>,
>         "ldap.password": <password>,
>         "ldap.authentication": "BasicAuthentication",
>         "ldap.url": "ldap://<virtual_host>:<virtual_port>",
>         "ldap.proxyType": "OnPremise"
> }
> ```

To target the destination with the name "example-dest-ldap" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an LDAP destination in Transparent Proxy *dedicated* mode**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec: 
>   destinationRef:
>     name: "example-dest-ldap"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 389, the default LDAP port \(unless another port is specified in the destination CR\). The Transparent Proxy handles the basic authentication with the LDAP server using the credentials from the respective destination.

**Multitenant Usage** 

The Transparent Proxy supports multitenancy for LDAP destinations. To consume an end-system in a multitenant manner, describe all tenants in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation:

**Destination CR for an LDAP destination in Transparent Proxy *shared* mode** 

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
>   annotations:
>     transparent-proxy.connectivity.api.sap/tenant-subdomains: '["tenant-subdomain", "another-tenant-subdomain"]'
>   destinationRef:
>     name: "example-dest-ldap"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for each of the tenants described in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation. The names of the Kubernetes services will be: <destination-cr-name\>-<tenant-subdomain\>.



<a name="loio47128a845bd3459f80ed8a36ff3518b6__section_g4k_bwv_hcc"/>

## Consumption

Once done, the application ca start consuming the destination from within the Kubernetes cluster.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**LDAP Consumption Bash Snippet**

> ### Sample Code:  
> ```
> ldapsearch -x -H ldap://<destination-cr-name>.<destination-cr-namespace>:389 -b dc=example,dc=org
> ```

**LDAP Consumption in *Shared* \(Multitenant\) Mode Bash Snippet** 

> ### Sample Code:  
> ```
> ldapsearch -x -H ldap://<tenant-subdomain>-<destination-cr-name>.<destination-cr-namespace>:389 -b dc=example,dc=org
> ```

