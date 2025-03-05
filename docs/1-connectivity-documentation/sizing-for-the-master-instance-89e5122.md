<!-- loio89e51224cc894d67a899be4d10cc54e1 -->

# Sizing for the Master Instance

Learn more about the basic criteria for the sizing of your Cloud Connector master instance.

For the master setup, keep in mind the expected load for communication between the SAP BTP and on-premises systems. The setups listed below differ in a mostly qualitative manner, without hard limits for each of them.

> ### Note:  
> The mentioned sizes are considered as minimal configuration, larger ones are always ok. In general, the more applications, application instances, and subaccounts are connected, the more competition will exist for the limited resources on the machine.


<table>
<tr>
<th valign="top">

Installation Size \(S, M, L\)

</th>
<th valign="top">

CPU \(x86\_64\)

</th>
<th valign="top">

Machine Memory / Heap /Direct Memory

</th>
<th valign="top">

Disk Space

</th>
</tr>
<tr>
<td valign="top">

**S:**

The expected load is small \(up to **1 million requests** per day, request concurrency and size is in average low\) and only a **few subaccounts** with **some applications** are connected.

In addition, only a **few service channels** are used, only **small data amount is replicated** to cloud systems.

Setup can be a done in a virtual or physical machine.

</td>
<td valign="top">

2 cores 2.6 GHz

</td>
<td valign="top">

4GB RAM / 1GB / 2GB

</td>
<td valign="top">

10GB

</td>
</tr>
<tr>
<td valign="top">

**M :**

The expected load is medium \(up to **10 million requests** per day, request concurrency and size is in average medium\) and **multiple subaccounts** with **multiple applications** are connected.

In addition, **many service channels** are used, and a **medium data amount is replicated** to cloud systems.

We recommend that you do the setup in a virtual or physical machine. A virtual machine should be on a host without overcommitted resources.

</td>
<td valign="top">

4 cores 3.0 Ghz

</td>
<td valign="top">

16GB RAM / 4GB / 8GB

</td>
<td valign="top">

20GB

</td>
</tr>
<tr>
<td valign="top">

**L:**

The expected load is large \(**more than 10 million requests** per day, request concurrency and size is in average medium or high\) and multiple subaccounts with multiple applications are connected.

In addition, many service channels are used, and a **large data amount is replicated** to cloud systems concurrently.

We recommend that you do the setup in a virtual or physical machine. A virtual machine should be on a host without overcommitted resources.

</td>
<td valign="top">

8 cores 3.0 Ghz

</td>
<td valign="top">

32GB RAM / 8GB / 16GB

</td>
<td valign="top">

40GB

</td>
</tr>
</table>

Particularly the **heap size** is critical. If you size it too low for the load passing the Cloud Connector, at some point the Java Virtual Machine will execute full GCs \(garbage collections\) more frequently, blocking the processing of the Cloud Connector completely for multiple seconds, which massively slows down overall performance. If you experience such situations regularly, you should increase the heap size in the Cloud Connector UI \(choose *Configuration* \> *Advanced* \> *JVM*\). See also [Configure the Java VM](configure-the-java-vm-09e62bc.md).

> ### Note:  
> You should use the same value for both *<initial heap size\>* and *<maximum heap size\>*.

