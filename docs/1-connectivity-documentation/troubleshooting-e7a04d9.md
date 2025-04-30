<!-- loioe7a04d9b30144f40ab0ca3b275ced93f -->

# Troubleshooting

Find procedures to troubleshoot issues with the Connectivity Proxy for Kubernetes.

[Get Logs of the Connectivity Proxy](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__get)

[Changing Log Level\(s\) of the Connectivity Proxy](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__change)

[Viewing Logger\(s\) of the Connectivity Proxy](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__view)

[Troubleshooting the Cloud Connector](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__cc)

[Common Issues and Solutions](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__issues)



<a name="loioe7a04d9b30144f40ab0ca3b275ced93f__get"/>

## Get Logs of the Connectivity Proxy

As the Connectivity Proxy workload is represented as a [standard Kubernetes StatefulSet](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/), fetching the logs is done in the standard Kubernetes way. Example via `kubectl`:

```
kubectl logs statefulset/connectivity-proxy
```

[Back to Top](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__top)



<a name="loioe7a04d9b30144f40ab0ca3b275ced93f__change"/>

## Changing Log Level\(s\) of the Connectivity Proxy

When the default logging level is not sufficient for debugging the issue you are facing, you can change the log level to get more insight about the problem.

> ### Note:  
> Changing a log level to something more verbose will have a negative impact on the performance of the Connectivity Proxy. Thus, we recommend that you do not keep such a log level for a long period of time.

Changing a log level is done without any downtime and requires no restarts. All you need to do is invoke a simple command on a pod of the Connectivity Proxy. Here are some examples:

**Put all loggers on DEBUG \(full command\)**

```
kubectl exec <pod> -it -- connectivity-proxy-operations logging change-log-level DEBUG
```

**Put all loggers on DEBUG \(shortcut\)**

```
kubectl exec <pod> -it -- change-log-level DEBUG
```

**Put only some loggers on DEBUG \(shortcut\)**

```
kubectl exec <pod> -it -- change-log-level com.sap.core.connectivity.tunnel.k8s DEBUG # Will affect all loggers with names, starting with com.sap.core.connectivity.tunnel.k8s
```

**Restore log level to default \(shortcut\)**

```
kubectl exec <pod> -it -- change-log-level INFO
```

For more information, check the help text of the command:

```
kubectl exec <pod> -it -- change-log-level help
```

[Back to Top](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__top)



<a name="loioe7a04d9b30144f40ab0ca3b275ced93f__view"/>

## Viewing Logger\(s\) of the Connectivity Proxy

**List all loggers \(full command\)**

```
kubectl exec <pod> -it -- connectivity-proxy-operations logging list-loggers
```

**List all loggers \(shortcut\)**

```
kubectl exec <pod> -it -- list-loggers
# or
kubectl exec <pod> -it -- get-loggers
```

**List only some specific loggers \(shortcut\)**

```
kubectl exec <pod> -it -- list-loggers com.sap.core.connectivity.tunnel.k8s # Will show all loggers with names, starting with com.sap.core.connectivity.tunnel.k8s
```

For more information, check the help text of the command:

```
kubectl exec <pod> -it -- list-loggers help
```

[Back to Top](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__top)



<a name="loioe7a04d9b30144f40ab0ca3b275ced93f__cc"/>

## Troubleshooting the Cloud Connector

For troubleshooting the Cloud Connector, see [Monitoring, Logging, And Troubleshooting](monitoring-logging-and-troubleshooting-e7df7f1.md) \(Cloud Connector\).

[Back to Top](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__top)



<a name="loioe7a04d9b30144f40ab0ca3b275ced93f__issues"/>

## Common Issues and Solutions


<table>
<tr>
<th valign="top">

Issue

</th>
<th valign="top">

Solution

</th>
</tr>
<tr>
<td valign="top">

You use the HTTP proxy \(port 20003\) and get a 405 response.

</td>
<td valign="top">

Make sure the URL you are calling is `http://<virtual host>:<virtual port>`and not `https://<virtual host>:<virtual port>`.

</td>
</tr>
<tr>
<td valign="top">

You use the HTTP proxy \(port 20003\) and get a 407 response \(in a non-trusted environment / proxy authorization turned on\).

</td>
<td valign="top">

Make sure you set the `Proxy-Authorization` header with a value in the format "`Bearer <valid JWT token>`".

</td>
</tr>
<tr>
<td valign="top">

You use the HTTP proxy \(port 20003\) and get a 503 response stating that there is no Cloud Connector for your subaccount.

</td>
<td valign="top">

-   Make sure the Cloud Connector you are targeting is still connected.
-   Make sure it's location ID matches the one used in the request.
-   Make sure the Cloud Connector is connected to the same subaccount, on whose behalf the token for the request is issued.



</td>
</tr>
<tr>
<td valign="top">

Out of nowhere, the Connectivity Proxy stops working / monitors indicate a failure \(considered an outage if it happens in production\).

</td>
<td valign="top">

See [Recommended Actions](recommended-actions-aec9009.md).

</td>
</tr>
<tr>
<td valign="top">

An SSL error is shown in the Cloud Connector when trying to send a request through the Connectivity Proxy.

</td>
<td valign="top">

Assuming the SSL error occurs during the call from the Cloud Connector to the public endpoint of the Connectivity Proxy, there are two options:

-   Error is due to a connection termination during the SSL handshake. In this case, check you intermediate components \(proxies, firewalls, etc.\).
-   The JVM on which the Cloud Connector is running does not trust the TLS certificate of the public endpoint of the Connectivity Proxy. In this case, import the certificate \(or its CA\) into the trust store of the JVM.



</td>
</tr>
</table>

[Back to Top](troubleshooting-e7a04d9.md#loioe7a04d9b30144f40ab0ca3b275ced93f__top)

**Related Information**  


[Recommended Actions](recommended-actions-aec9009.md "Find procedures to resolve an outage of the Connectivity Proxy for Kubernetes functionality.")

