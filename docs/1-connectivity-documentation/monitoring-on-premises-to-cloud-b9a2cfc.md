<!-- loiob9a2cfc3c73744308b179888d4e35590 -->

# Monitoring \(On-Premises to Cloud\)

Monitor on-premises to cloud connections in the Cloud Connector.



## Connections

This section shows a tabular overview of all currently opened logical connections, aggregated for each local port. You can identify if and how many connections are currently opened through this specific service channel.



## Usage Statistics

Statistical data regarding the traffic handled by each port is shown in tabular form. From the table, you can select a service channel. The respective detail views show a 24 hour overview as a bar chart that aggregates the throughput \(bytes received and bytes sent via a port, respectively\) on an hourly basis.

The collected data comprises the number of bytes received from on-premises applications and the number of bytes sent to cloud applications.

The table listing usage statistics of ports lets you delete unused service channels. Use action *Delete* to delete a service channel.

> ### Caution:  
> Usage statistics are collected at runtime only. They are not stored when stopping the Cloud Connector. These statistics are lost when the Cloud Connector is stopped or restarted. Be mindful of that fact, and use caution when taking the decision to delete a service channel based on its usage statistics.

Using the *Reset* button you can clean up all collected data. This might be helpful when monitoring a specific use case.

The table of service channels provides a filter button to reduce the service channels to those that have never been used \(since the Cloud Connector started\).

