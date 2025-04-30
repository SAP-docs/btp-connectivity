<!-- loiodf31094259054c64a2c206166292d2fd -->

# Sizing Recommendations

When installing a transpartent proxy for Kubernetes, the first thing you need to decide is the sizing of the installation.



<a name="loiodf31094259054c64a2c206166292d2fd__section_ds4_4xm_t5b"/>

## Overview

To get the most out of the Transparent Proxy, you must configure it in a suitable way, fitting the scenarios in which it plays a role.



<a name="loiodf31094259054c64a2c206166292d2fd__section_gq3_pxm_t5b"/>

## Sizing Options

The following table gives basic sizing guidance. The values listed in the `CPU` and `Memory` sections correspond to the properties, which should be defined in the configuration. For more information, see [Configuration Guide](configuration-guide-2a22cd7.md):

**HTTP Proxy Sizing**


<table>
<tr>
<th valign="top">

Size

</th>
<th valign="top">

CPU

</th>
<th valign="top">

Memory

</th>
<th valign="top">

Max. Number of Requests per Second \(RPS\)

</th>
<th valign="top">

Concurrent Users

</th>
<th valign="top">

Bytes per Request \(KB\)

</th>
</tr>
<tr>
<td valign="top">

S:

</td>
<td valign="top">

-   `deployment.resources.http.requests.cpu: 0.05`
-   `deployment.resources.http.limits.cpu: 0.05`



</td>
<td valign="top">

-   `deployment.resources.http.requests.memory: 192 M`
-   `deployment.resources.http.limits.memory: 192 M`



</td>
<td valign="top">

10

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

M:

</td>
<td valign="top">

-   `deployment.resources.http.requests.cpu: 0.225`
-   `deployment.resources.http.limits.cpu: 0.225`



</td>
<td valign="top">

-   `deployment.resources.http.requests.memory: 256 M`
-   `deployment.resources.http.limits.memory: 256 M`



</td>
<td valign="top">

100

</td>
<td valign="top">

10

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

L:

</td>
<td valign="top">

-   `deployment.resources.http.requests.cpu: 0.8`
-   `deployment.resources.http.limits.cpu: 0.8`



</td>
<td valign="top">

-   `deployment.resources.http.requests.memory: 320 M`
-   `deployment.resources.http.limits.memory: 320 M`



</td>
<td valign="top">

500

</td>
<td valign="top">

50

</td>
<td valign="top">

5

</td>
</tr>
<tr>
<td valign="top">

XL:

</td>
<td valign="top">

-   `deployment.resources.http.requests.cpu: 1.9`
-   `deployment.resources.http.limits.cpu: 1.9`



</td>
<td valign="top">

-   `deployment.resources.http.requests.memory: 384 M`
-   `deployment.resources.http.limits.memory: 384 M`



</td>
<td valign="top">

1000

</td>
<td valign="top">

100

</td>
<td valign="top">

8

</td>
</tr>
</table>

**TCP Proxy Sizing**


<table>
<tr>
<th valign="top">

Size

</th>
<th valign="top">

CPU

</th>
<th valign="top">

Memory

</th>
<th valign="top">

Max. Number of Requests per Second \(RPS\)

</th>
<th valign="top">

Concurrent Users

</th>
<th valign="top">

Bytes per Request \(KB\)

</th>
</tr>
<tr>
<td valign="top">

S:

</td>
<td valign="top">

-   `deployment.resources.tcp.requests.cpu: 0.01`
-   `deployment.resources.tcp.limits.cpu: 0.01`



</td>
<td valign="top">

-   `deployment.resources.tcp.requests.memory: 64 M`
-   `deployment.resources.tcp.limits.memory: 64 M`



</td>
<td valign="top">

10

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

M:

</td>
<td valign="top">

-   `deployment.resources.tcp.requests.cpu: 0.025`
-   `deployment.resources.tcp.limits.cpu: 0.025`



</td>
<td valign="top">

-   `deployment.resources.tcp.requests.memory: 80 M`
-   `deployment.resources.tcp.limits.memory: 80 M`



</td>
<td valign="top">

100

</td>
<td valign="top">

10

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

L:

</td>
<td valign="top">

-   `deployment.resources.tcp.requests.cpu: 0.08`
-   `deployment.resources.tcp.limits.cpu: 0.08`



</td>
<td valign="top">

-   `deployment.resources.tcp.requests.memory: 96 M`
-   `deployment.resources.tcp.limits.memory: 96 M`



</td>
<td valign="top">

500

</td>
<td valign="top">

50

</td>
<td valign="top">

5

</td>
</tr>
<tr>
<td valign="top">

XL:

</td>
<td valign="top">

-   `deployment.resources.tcp.requests.cpu: 0.2`
-   `deployment.resources.tcp.limits.cpu: 0.2`



</td>
<td valign="top">

-   `deployment.resources.tcp.requests.memory: 128 M`
-   `deployment.resources.tcp.limits.memory: 128 M`



</td>
<td valign="top">

1000

</td>
<td valign="top">

100

</td>
<td valign="top">

8

</td>
</tr>
</table>

> ### Note:  
> **Relation to Connectivity Proxy**
> 
> The above-mentioned sizing recommendations for the TCP proxies are related to the Connectivity Proxy software component, which also acts as a tunnel server to the on-premise systems it connects to. This means that the Connectivity Proxy has to be properly sized as well, see [Sizing Recommendations](sizing-recommendations-204822a.md) \(Connectivity Proxy for Kubernetes\).

> ### Note:  
> **General Note**
> 
> These sizing recommendations are just a direction point. There are many factors that affect the performance offered by the Transparent Proxy, related to the specifics of your concrete scenarios, expected regular and intermittent load, and so on.
> 
> The tests were made with the Transparent Proxy in *dedicated* mode with 50 HTTP or TCP destination custom resources applied respectively.

> ### Note:  
> **General Note**
> 
> These sizing recommendations are aligned with the *Pod Quality* of *Service Classes*, specifically the *Guaranteed* class. The Transparent Proxy components have the strictest resource limits, making them the least likely to face eviction.

