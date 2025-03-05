<!-- loiof0084943389a4112bd441c0e014efd04 -->

# Sizing Recommendations

When installing a Cloud Connector, the first thing you need to decide is the sizing of the installation.

This section gives some basic guidance what to consider for this decision. The provided information includes the shadow instance, which should always be added in productive setups. See also [Install a Failover Instance for High Availability](install-a-failover-instance-for-high-availability-c697705.md).

> ### Note:  
> The following recommendations are based on current experiences. However, they are only a rule of thumb since the actual performance strongly depends on the specific environment. The overall performance of a Cloud Connector is impacted by many factors \(number of hosted subaccounts, bandwidth, latency to the attached regions, network routers in the corporate network, used JVM, and others\).



<a name="loiof0084943389a4112bd441c0e014efd04__section_mhb_pwr_rdb"/>

## Restrictions

The sizing data refer to a single Cloud Connector installation.

> ### Note:  
> Up until now, you cannot perform horizontal scaling directly. However, you can distribute the load statically by operating multiple Cloud Connector installations with different location IDs for all involved subaccounts. In this scenario, you can use multiple destinations with virtually the same configuration, except for the location ID. See also [Adding and Managing Subaccounts](adding-and-managing-subaccounts-f16df12.md), step 4. Alternatively, each of the Cloud Connector instances can host its own list of subaccounts without any overlap in the respective lists. Thus, you can handle more load, if a single installation risks to be overloaded.

**Related Information**  


[Hardware Setup](hardware-setup-a84034a.md "How to choose the right sizing for your Cloud Connector installation.")

[Configuration Setup](configuration-setup-7437cd6.md "Choose the right connection configuration options to improve the performance of the Cloud Connector.")

