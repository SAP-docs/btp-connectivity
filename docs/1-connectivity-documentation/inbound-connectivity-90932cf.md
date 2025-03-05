<!-- loio90932cf45c924956a5106472286f74a2 -->

# Inbound Connectivity

For inbound connections into the on-premises network, the Cloud Connector acts as a reverse invoke proxy between SAP BTP and the internal systems.



<a name="loio90932cf45c924956a5106472286f74a2__section_c5n_vbt_3gb"/>

## Exposing Resources

Once installed, none of the internal systems are accessible by default through the Cloud Connector: you must configure explicitly each system and each service and resource on every system to be exposed to SAP BTP in the Cloud Connector.

You can also specify a virtual host name and port for a configured on-premises system, which is then used in the cloud. Doing this, you can avoid that information on physical hosts is exposed to the cloud.



<a name="loio90932cf45c924956a5106472286f74a2__section_bvl_222_l1b"/>

## TLS Tunnel

The TLS \(Transport Layer Security\) tunnel is established from the Cloud Connector to SAP BTP via a so-called **reverse invoke** approach. This lets an administrator have full control of the tunnel, since it can’t be established from the cloud or from somewhere else outside the company network. The Cloud Connector administrator is the one who decides when the tunnel is established or closed.

The tunnel itself is using TLS with strong encryption of the communication, and mutual authentication of both communication sides, the client side \(Cloud Connector\) and the server side \(SAP BTP\).

The X.509 certificates which are used to authenticate the Cloud Connector and the SAP BTP subaccount are issued and controlled by SAP BTP. They are kept in secure storages in the Cloud Connector and in the cloud. Having encrypted and authenticated the tunnel, confidentiality and authenticity of the communication between the SAP BTP applications and the Cloud Connector is guaranteed.



<a name="loio90932cf45c924956a5106472286f74a2__section_y1y_222_l1b"/>

## Restricting Allowed Applications

As an additional level of control, the Cloud Connector optionally allows restricting the list of SAP BTP applications which are able to use the tunnel. This is useful in situations where multiple applications are deployed in a single SAP BTP subaccount while only particular applications require connectivity to on-premises systems.



<a name="loio90932cf45c924956a5106472286f74a2__section_wpz_222_l1b"/>

## Isolation on Subaccount Level

SAP BTP guarantees strict isolation on subaccount level provided by its infrastructure and platform layer. An application of one subaccount is not able to access and use resources of another subaccount.



<a name="loio90932cf45c924956a5106472286f74a2__section_dx1_f22_l1b"/>

## Supported Protocols

The Cloud Connector supports inbound connectivity for HTTP and RFC, any other protocol is not supported.

-   The payload sent via these protocols is encrypted on TLS/tunnel-level.
-   For the route from the Cloud Connector to the on-premises systems, Cloud Connector administrators have the choice for each configured on-premises system whether to use HTTP, HTTPS, RFC or RFC over SNC.
-   For HTTPS, you can configure a so-called system certificate in the Cloud Connector which is used for the trust relationship between the Cloud Connector and the connected on-premises systems.
-   For RFC over SNC, you can configure an SNC PSE in the Cloud Connector respectively.



<a name="loio90932cf45c924956a5106472286f74a2__section_tdc_f22_l1b"/>

## Principal Propagation

The Cloud Connector also supports principal propagation of the cloud user identity to connected on-premises systems \(single sign-on\). For this, the system certificate \(in case of HTTPS\) or the SNC PSE \(in case of RFC\) is mandatory to be configured and trust with the respective on-premises system must be established. Trust configuration, in particular for principal propagation, is the only reason to configure and touch an on-premises system when using it with the Cloud Connector.

**Related Information**  


[Configuring Principal Propagation](configuring-principal-propagation-c84d4d0.md "Use principal propagation to simplify the access of SAP BTP users to on-premises systems.")

