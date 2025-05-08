<!-- loio6c88a099a151448282c0b29930adb594 -->

# Resilience Recommendations

Improve resilience of your SAP BTP applications.

While SAP strives to ensure the highest possible availability of the provided services, true resilience actually is a two-way collaboration between client and server. Thus, it is important to implement any applications using the Connectivity and/or Destination services \(or any other services for that matter\) in a resilient way. This page gives suggestions on measures to take in order to endure short disruptions, network issues, slowdowns or other abnormal situations that might arise. By doing this, these application can withstand such disruptions, ensuring business continuity in the face of underlying issues in the platform.

> ### Note:  
> When using client libraries like the [BTP security library](https://github.com/SAP/cloud-security-services-integration-library), the [Cloud SDK](https://sap.github.io/cloud-sdk/), and so on, many of these recommendations may already be included. However, we recommend that you double-check these features, as they might require additional configuration.



<a name="loio6c88a099a151448282c0b29930adb594__section_igw_31s_x5b"/>

## Caching

Caching is an important pillar of resilience. It is the act of storing data \(acquired from an external resource or as a result of a heavy computation\) for future use. Caching operations must be done within a reasonable timespan to avoid the risk of data becoming invalid or outdated. So, caching lets you reduce the number of risky or heavy operations that go over the network towards an external resource. By doing this, the risk of failure is reduced, and caching additionally improves the performance of the application.

> ### Note:  
> Be careful what kind of data you cache and for how long. It is especially important to consider the handling of sensitive data \(personal data, security objects, and so on\).

> ### Caution:  
> Make sure you limit the size of the caches to avoid memory issues. There are different options when the maximum number of entities in the cache is reached. For example, you can drop the oldest entity from the cache in favor of the new one.

**Token Caching**

Caching access tokens to the services is highly recommended for the period of their validity. Access tokens to the service include the timestamp on which the token is no longer valid \(as per JWT specification\). Thus the tokens can be reused at any time before said timestamp. Keep in mind that tokens are issued for the specific clients and in the context of the specific tenant. Thus this should be taken into account when designing the caching mechanism.

**Destination/Certificate Caching**

The entities of the Destination service \(be it destination configurations or certificate configuration\) can also be cached. This includes both responses for single entities, as well as the list of entities responses. The drawback of this is that any changes in the configurations will not become immediately available to the application, thus a reasonable caching time \(3-5 minutes is usually a good choice\) must be set.

If you do not expect time critical changes in the destination configuration, you can set the caching time even higher \(for example, an hour\). Also, we recommend that you refresh the cache on-demand instead of calling the Destination service every 3-5 minutes.

By caching applications, they can withstand temporary issues with the service or the network. We also recommend that in cases where the cache has expired but retrieval of the updated entities does not succeed to still use the cached value as a further resilience measure.



<a name="loio6c88a099a151448282c0b29930adb594__section_qlm_j1s_x5b"/>

## Retry Logic

When requests \(whether it is the token call, the service call or the business call\) fail, it is always a good idea to retry the call over a reasonable time. It also makes sense to have some delay between retries, for example, at least 100 milliseconds. You can even make this delay increase with each subsequent retry. By doing this, you can handle short intermittent issues without having business impact.



<a name="loio6c88a099a151448282c0b29930adb594__section_xjz_j1s_x5b"/>

## Pagination

The APIs of the Destination service that return multiple entities support pagination. We highly recommended that you make use of pagination if you use these APIs and have a high number of entities \(more than 100 entities\). By doing this, you ease the pressure on the service but also make processing lighter on client side as the list can be handled in batches. See more about pagination in the documentation of the [Destination Service REST API](destination-service-rest-api-23ccafb.md).



<a name="loio6c88a099a151448282c0b29930adb594__section_wlk_k1s_x5b"/>

## Timeouts

Connect and read timeouts help you keep your application resources from getting stuck in abnormally long processing. In some cases, one attempt to get data might get stuck, but abandoning it and trying again might immediately succeed.

We recommend you use appropriate *connect* and *read* timeouts when communicating with the services. The *connect* timeout is recommended to be on the low end - a couple of seconds. The *read* timeout would depend on the semantic of the call being made. A call to the Destination service REST API would not require a high read timeout. Around half a minute would be sufficient. The same is true for token retrieval calls. For business calls, including calls to on-premise systems via the Connectivity service, the timeout would be based on the type of the call and is heavily scenario-specific.



<a name="loio6c88a099a151448282c0b29930adb594__section_zrh_v3h_dvb"/>

## Circuit Breaker

The circuit-breaker architecture pattern can be a powerful tool for handling a misbehaving dependency. It reduces the effort done by your application when communicating to a service which is identified as not working or unstable, while waiting for the dependency to come back online.

For more information on this pattern, see [https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker](https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker).



<a name="loio6c88a099a151448282c0b29930adb594__section_vgy_k1s_x5b"/>

## Cloud Connector High Availability

See [High Availability Setup](high-availability-setup-2f9250b.md).

