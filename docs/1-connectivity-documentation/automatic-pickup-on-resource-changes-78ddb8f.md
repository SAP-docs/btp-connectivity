<!-- loio78ddb8fba2a94ff98f7152359b8e4875 -->

# Automatic Pickup on Resource Changes

Configure automatic pickup on resource changes for the Connectivity Proxy.

The Connectivity Proxy can automatically pick up changes in secrets and configmaps. This is achieved by performing a rolling restart when a resource is modified.



<a name="loio78ddb8fba2a94ff98f7152359b8e4875__section_p3g_rzt_ysb"/>

## Restart Watcher

The restart watcher is responsible for picking up changes in the above-mentioned resources, and for restarting the Connectivity Proxy if given conditions are met.

It will be informed for changes in a secret or configmap containing the label *connectivityproxy.sap.com/restart*.

To enable the restart watcher, you must configure the following in the `values.yml` file.

```
deployment:
  restartWatcher:
    enabled: true
```

> ### Note:  
> The restart watcher is unique for every Helm installation of the Connectivity Proxy and will be deployed as a part of it.

> ### Caution:  
> If the Connectivity Proxy:
> 
> -   is with initial installation version < 2.5.0
> -   is upgraded via Helm to version 2.5.0 or higher
> -   has the restart watcher enabled
> -   and has replica count 2
> 
> the restart operation which is performed by the restart watcher may not be a ZDM \(zero-downtime migration\).
> 
> To avoid such situation, you should perform a fresh Helm installation. This is inevitable because a change in an immutable field of a Kubernetes resource is required.



<a name="loio78ddb8fba2a94ff98f7152359b8e4875__section_j55_vzt_ysb"/>

## Conditions for Restart

Тhe restart watcher checks for two possible values of the label *connectivityproxy.sap.com/restart*:

-   if the value is an empty string, the restart watcher will perform a rolling update on the Connectivity Proxy, based on respective Helm installation.
-   if the value has the form `<helm_installation_name>.<namespace>`, the restart watcher will perform a rolling restart only if the values of `<helm_Installation_name>` and `<namespace>` match the watcher's installation and namespace.
-   for all other possible values, the restart watcher will not perform a restart.



<a name="loio78ddb8fba2a94ff98f7152359b8e4875__section_wgv_xzt_ysb"/>

## Examples

-   You have a Helm installation in the *default* namespace and a secret with label *connectivityproxy.sap.com/restart: ""* \(with value empty string\) in namespace *test*. In this case, the Connectivity Proxy installation in namespace *default* will be restarted for every change of the secret.
-   You have a Helm installation with name *connectivity-proxy* in namespace *test*, and a configmap with name *test-configmap* and label *connectivityproxy.sap.com/restart* : *connectivity-proxy.test*. In this case, the Connectivity Proxy will be restarted for every change of the configmap. However, if you have another installation in the same namespace *test* but with name *connectivity-proxy2*, restarts will not be triggered on it based on changes of the *configmap test-configmap*.

