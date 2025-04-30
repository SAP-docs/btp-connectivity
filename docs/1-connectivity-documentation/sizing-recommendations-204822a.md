<!-- loio204822a72a6646389d4016b985345bd6 -->

# Sizing Recommendations

Find basic sizing guidance for the Connectivity Proxy for Kubernetes.



<a name="loio204822a72a6646389d4016b985345bd6__section_av1_rkm_1qb"/>

## Sizing Options

The following table gives basic sizing guidance for different usage scenarios. The values listed in the **CPU** and **Memory**, and **Thread Pools** columns correspond to the properties you should define in the `values.yaml` file \(for more information, see [Configuration Guide](configuration-guide-eaa8204.md)\):


<table>
<tr>
<th valign="top">

Size \(S/M/L\)

</th>
<th valign="top">

CPU

</th>
<th valign="top">

Memory

</th>
<th valign="top">

Thread Pools

</th>
</tr>
<tr>
<td valign="top">

S:

The expected load is small - request concurrency and size is low

</td>
<td valign="top">

-   deployment.resources.requests.cpu: 0.1
-   deployment.resources.limits.cpu: 1



</td>
<td valign="top">

-   deployment.resources.requests.memory: 256 M
-   deployment.resources.limits.memory: 1024 M



</td>
<td valign="top">

-   config.servers.businessDataTunnel.threadPoolSize: 20
-   config.servers.proxy.threadPoolSize: 20



</td>
</tr>
<tr>
<td valign="top">

M:

The expected load is medium - request concurrency and size is medium

</td>
<td valign="top">

-   deployment.resources.requests.cpu: 1
-   deployment.resources.limits.cpu: 2



</td>
<td valign="top">

-   deployment.resources.requests.memory: 512 M
-   deployment.resources.limits.memory: 2048 M



</td>
<td valign="top">

-   config.servers.businessDataTunnel.threadPoolSize: 20
-   config.servers.proxy.threadPoolSize: 20



</td>
</tr>
<tr>
<td valign="top">

L:

The expected load is large - request concurrency and size is medium or high

</td>
<td valign="top">

-   deployment.resources.requests.cpu: 2
-   deployment.resources.limits.cpu: 4



</td>
<td valign="top">

-   deployment.resources.requests.memory: 1024 M
-   deployment.resources.limits.memory: 4096 M



</td>
<td valign="top">

-   config.servers.businessDataTunnel.threadPoolSize: 20
-   config.servers.proxy.threadPoolSize: 20



</td>
</tr>
</table>



<a name="loio204822a72a6646389d4016b985345bd6__section_kw5_pkm_1qb"/>

## Relation to Operational Modes

The Connectivity Proxy can operate in multiple [Operational Modes](operational-modes-148bbad.md).

A major criteria is the type of tenancy used: single or multi-tenant. If multiple tenants are served, we recommend that you choose a slightly bigger size to make sure each tenant is served without precedence to any other tenant at the same time. Based on the chosen tenancy mode, the following general recommendations apply:


<table>
<tr>
<th valign="top">

Tenancy Mode

</th>
<th valign="top">

Sizes to Consider

</th>
</tr>
<tr>
<td valign="top">

Single-Tenant

</td>
<td valign="top">

S, M

</td>
</tr>
<tr>
<td valign="top">

Multi-Tenant

</td>
<td valign="top">

M, L

</td>
</tr>
</table>

> ### Note:  
> The above-mentioned sizing recommendations are related to the Connectivity Proxy software component, also acting as a tunnel server to which Cloud Connector instances connect. This means the Cloud Connector must be sized properly as well, see [Sizing Recommendations](sizing-recommendations-f008494.md) \(Cloud Connector\).

> ### Remember:  
> These sizing recommendation are just a direction point. There are many factors that affect the performance of the tunneling between Cloud Connector and Connectivity Proxy. They are closely related to the specifics of your scenario, expected regular and intermittent load, and so on.

