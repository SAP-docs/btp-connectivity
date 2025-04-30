<!-- loioe7232776e3aa4f0e8d1fe6b6b695f0f5 -->

# Connectivity Entities

Find an overview of the key Destination service entities used to set up connectivity for SAP BTP applications.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loioe7232776e3aa4f0e8d1fe6b6b695f0f5__section_ihh_mm5_x2c"/>

## Destinations

An SAP BTP destination stores your connection configuration data \(including credentials, certificates, URL, etc.\) that is needed to address the corresponding cloud or on-premise target system or service.

For more information, see [Managing Destinations](managing-destinations-84e45e0.md).



<a name="loioe7232776e3aa4f0e8d1fe6b6b695f0f5__section_hm1_mm5_x2c"/>

## Destination Fragments

Destination fragments are objects used to override and extend destination properties through the Destination service REST API.

You can use destination fragments to override and/or extend destination properties as result of the “Find a destination” REST API request. These properties are key-value based objects which contain a name for identification and additional configurable properties.

For more information, see [Manage Destination Fragments](manage-destination-fragments-b085906.md).



<a name="loioe7232776e3aa4f0e8d1fe6b6b695f0f5__section_hhs_lm5_x2c"/>

## Certificates

Certificates are standardized data sets used to authenticate certain properties of a person or object in a cryptographic procedure. Certificates are usually issued by a Certification Authority \(CA\).

A common standard are X.509 public-key certificates, which confirm the identity of the certificate owner as well as other properties of a public cryptographic key.

In the SAP BTP Connectivity context, certificates can be stored in a destination to authenticate users or applications calling a specific target system or service.

For more information, see [Manage Destination Certificates](manage-destination-certificates-df1bb55.md).



<a name="loioe7232776e3aa4f0e8d1fe6b6b695f0f5__section_zrj_lm5_x2c"/>

## Trust

Scenarios involving user propagation from a Multi-Cloud application to other systems, to SAP BTP environments, or to another subaccount in the same SAP BTP environment require a trust configuration between the involved systems \(sender and receiver\).

This includes exchanging public keys and certificates between those systems and configuring trust between them.

For more information, see [Manage Trust](manage-trust-82dbeca.md).

