<!-- loio43b90bc61fa043068cb2bae5ed89f09e -->

# Resilience

Improve resilience of the Transparent Proxy for Kubernetes.

Even though the Transparent Proxy is not a cloud service, it offers options to improve resilience and robustness of the whole system benefiting from the Transparent Proxy functionality.

The software architecture of the Transparent Proxy in terms of HTTP and TCP proxies is loosely decoupled, meaning that if there are failures in one of them it would not affect the other. Thus they are independent of each other and errors regarding for example the Transparent HTTP Proxy should not affect the work of the Transparent TCP Proxy instances.

To achieve additional resilience, see [High Availability](high-availability-fb92ab6.md).

