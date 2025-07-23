<!-- loioe23f776e4d594fdbaeeb1196d47bbcc0 -->

# Prerequisites

Prerequisites for successful installation of the Cloud Connector.



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__content"/>

## Content


<table>
<tr>
<th valign="top">

Section

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[Connectivity Restrictions](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__restritctions)

</td>
<td valign="top">

General information about SAP BTP and connectivity restrictions.

</td>
</tr>
<tr>
<td valign="top">

[Hardware](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__hardware)

</td>
<td valign="top">

Hardware prerequisites for a physical or virtual machine.

</td>
</tr>
<tr>
<td valign="top">

[Software](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__software)

</td>
<td valign="top">

Required software download and installation.

</td>
</tr>
<tr>
<td valign="top">

[JDKs](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__jdk)

</td>
<td valign="top">

Java Development Kit \(JDK\) versions that you can use.

</td>
</tr>
<tr>
<td valign="top">

[Product Availability Matrix](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix)

</td>
<td valign="top">

Availability of operating systems/versions for specific Cloud Connector versions.

</td>
</tr>
<tr>
<td valign="top">

[Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

</td>
<td valign="top">

Required Internet connection to SAP BTP hosts per region.

</td>
</tr>
</table>

> ### Note:  
> For additional system requirements, see also [System Requirements](system-requirements-7e8ebc9.md).



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__restritctions"/>

## Connectivity Restrictions

For general information about SAP BTP restrictions, see [Prerequisites and Restrictions](https://help.sap.com/docs/btp/sap-business-technology-platform/prerequisites-and-restrictions?version=Cloud).

For specific information about all Connectivity restrictions, see [Connectivity: Restrictions](what-is-sap-btp-connectivity-e54cc8f.md#loioe54cc8fbbb571014beb5caaf6aa31280__restrictions).

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__hardware"/>

## Hardware

Hardware prerequisites, physical or virtual machine:


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

Minimum

</th>
<th valign="top">

Recommended

</th>
</tr>
<tr>
<td valign="top">

CPU

</td>
<td valign="top">

Single core 3 GHz, x86-64 architecture compatible

</td>
<td valign="top">

Dual core 2 GHz, x86-64 architecture compatible

</td>
</tr>
<tr>
<td valign="top">

Memory \(RAM\)

</td>
<td valign="top">

2 GB

</td>
<td valign="top">

4 GB

</td>
</tr>
<tr>
<td valign="top">

Free disk space

</td>
<td valign="top">

3 GB

</td>
<td valign="top">

20 GB

</td>
</tr>
</table>

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__software"/>

## Software

-   You have downloaded the Cloud Connector installation archive from [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud).
-   A full JDK must be installed. Lightweight JRE installations are not sufficient. You can download a fitting up-to-date SAP JVM from [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud).

> ### Caution:  
> Do not use [Apache Portable Runtime \(APR\)](http://tomcat.apache.org/tomcat-8.5-doc/apr.html) on the system on which you use the Cloud Connector. If you cannot avoid this restriction and want to use APR at your own risk, you must manually adapt the `server.xml` configuration file in directory `<scc_installation_folder>/conf`. To do so, follow the steps in [HTTPS port configuration](http://tomcat.apache.org/tomcat-8.5-doc/config/http.html#SSL_Support_-_Connector_-_APR/Native_(deprecated)) for APR.

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__jdk"/>

## JDKs


<table>
<tr>
<th valign="top">

JDK

</th>
<th valign="top">

Version

</th>
<th valign="top">

Cloud Connector Version

</th>
</tr>
<tr>
<td valign="top">

SAP JVM 64-bit \(recommended\)

</td>
<td valign="top">

8

</td>
<td valign="top">

2.7.2 and higher

</td>
</tr>
<tr>
<td valign="top">

Oracle JDK 64-bit

</td>
<td valign="top">

8

</td>
<td valign="top">

2.7.2 and higher

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

[SAP Machine](https://sapmachine.io/) 64-bit

</td>
<td valign="top">

11 \(EOM\)

</td>
<td valign="top">

2.14.0 and higher

</td>
</tr>
<tr>
<td valign="top">

17

</td>
<td valign="top">

2.15.0 and higher

</td>
</tr>
<tr>
<td valign="top">

21

</td>
<td valign="top">

2.17.0 and higher

</td>
</tr>
</table>

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix"/>

## Product Availability Matrix


<table>
<tr>
<th valign="top">

Operating System Version

</th>
<th valign="top">

Architecture

</th>
<th valign="top">

Cloud Connector Version

</th>
</tr>
<tr>
<td valign="top">

Windows 7, Windows Server 2008 R2

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.1.0 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

SUSE Linux Enterprise Server 11, Red Hat Enterprise Linux 6

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.1.0 up to 2.16.0

</td>
</tr>
<tr>
<td valign="top">

Mac OS X 10.7 \(Lion\), Mac OS X 10.8 \(Mountain Lion\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.1.0 up to 2.12.5

</td>
</tr>
<tr>
<td valign="top">

Windows 8.1, Windows Server 2012, Windows Server 2012 R2

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.5.1 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

SUSE Linux Enterprise Server 12, Red Hat Enterprise Linux 7

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.5.1 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

Mac OS X 10.9 \(Mavericks\), Mac OS X 10.10 \(Yosemite\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.5.1 up to 2.12.5

</td>
</tr>
<tr>
<td valign="top">

Windows 10

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.7.2 and higher

</td>
</tr>
<tr>
<td valign="top">

Mac OS X 10.11 \(El Capitan\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.8.1 up to 2.16.2

</td>
</tr>
<tr>
<td valign="top">

Windows Server 2016

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.9.1 and higher

</td>
</tr>
<tr>
<td valign="top">

Windows Server 2019

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.11.3 and higher

</td>
</tr>
<tr>
<td valign="top">

macOS 10.12 \(Sierra\), macOS 10.13 \(High Sierra\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.11.3 up to 2.16.2

</td>
</tr>
<tr>
<td valign="top">

macOS 10.14 \(Mojave\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.11.3 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

SUSE Linux Enterprise Server 15

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.12.0 and higher

</td>
</tr>
<tr>
<td valign="top">

Red Hat Enterprise Linux 8

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.12.2 and higher

</td>
</tr>
<tr>
<td valign="top">

SUSE Linux Enterprise Server 12, Red Hat Enterprise Linux 7

</td>
<td valign="top">

ppc64le

</td>
<td valign="top">

2.13.0 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

SUSE Linux Enterprise Server 15, Red Hat Enterprise Linux 8

</td>
<td valign="top">

ppc64le

</td>
<td valign="top">

2.13.0 and higher

</td>
</tr>
<tr>
<td valign="top">

Windows Server 2022

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.14.0 and higher

</td>
</tr>
<tr>
<td valign="top">

macOS 10.15 \(Catalina\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.14.0 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

Windows 11

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.15.0 and higher

</td>
</tr>
<tr>
<td valign="top">

Red Hat Enterprise Linux 9

</td>
<td valign="top">

x86\_64, ppc64le

</td>
<td valign="top">

2.15.0 and higher

</td>
</tr>
<tr>
<td valign="top">

Oracle Linux 8

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.15.2 and higher

</td>
</tr>
<tr>
<td valign="top">

macOS 11 \(Big Sur\)

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.16.0 up to 2.17.2

</td>
</tr>
<tr>
<td valign="top">

Oracle Linux 9

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.16.0 and higher

</td>
</tr>
<tr>
<td valign="top">

macOS 12 \(Monterey\), macOS 13 \(Ventura\)

</td>
<td valign="top">

x86\_64, aarch64

</td>
<td valign="top">

2.16.0 and higher

</td>
</tr>
<tr>
<td valign="top">

macOS 14 \(Sonoma\)

</td>
<td valign="top">

x86\_64, aarch64

</td>
<td valign="top">

2.17.0 and higher

</td>
</tr>
<tr>
<td valign="top">

macOS 15 \(Sequoia\)

</td>
<td valign="top">

x86\_64, aarch64

</td>
<td valign="top">

2.18.0 and higher

</td>
</tr>
<tr>
<td valign="top">

Windows Server 2025

</td>
<td valign="top">

x86\_64

</td>
<td valign="top">

2.18.0 and higher

</td>
</tr>
</table>

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__network"/>

## Network

You must have Internet connection at least to the following Connectivity service hosts \(depending on the region\), to which you can connect your Cloud Connector. All connections to the hosts are TLS-based and connect to port 443.

> ### Remember:  
> For some solutions of the BTP portfolio, you must include additional hosts to set up an on-premises connectivity scenario with the Cloud Connector. This applies, for example, to: SAP Data Intelligence, SAP HANA Cloud, Business Appilcation Studio, SAP Cloud Identity Services, and SAP Build Apps. Check the respective solution documentation for details.

> ### Note:  
> To configure the Cloud Connector for SAP Datasphere, see also [Configure Cloud Connector](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/f289920243a34127b0c8b13012a1a4b5.html) \(SAP Datasphere documentation\).

> ### Note:  
> For general information on IP ranges per region, see [Regions](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html) \(Cloud Foundry and ABAP environment\) or [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html). Find detailed information about the region status and planned network updates on [Platform Updates and Notifications](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/99070c7bfc0e4f41842bd7c648b7fca7.html).

[Cloud Foundry Environment](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__cf)

[ABAP Environment](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__abap)

[Neo Environment](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__neo)

[Trial](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__trial)


<table>
<tr>
<th valign="top">

Region \(Region Host\)

</th>
<th valign="top" colspan="2">

Hosts

</th>
<th valign="top">

IP Addresses \(IPv4\)

</th>
<th valign="top">

IP Addresses \(IPv6\)

</th>
</tr>
<tr>
<td valign="top" colspan="5">

**Cloud Foundry Environment**

> ### Note:  
> In the Cloud Foundry environment, IPs are controlled by the respective IaaS provider - Amazon Web Services \(AWS\), Microsoft Azure \(Azure\), or Google Cloud. IPs may change due to network updates on the provider side. Any planned changes will be announced at least 4 weeks before they take effect. See also [Regions](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).



</td>
</tr>
<tr>
<td valign="top" rowspan="7">

Europe \(Frankfurt\) - AWS

\(`cf.eu10.hana.ondemand.com`\)

*Enterprise & Trial*

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`, `18.159.31.22`, `3.69.186.98`, `3.77.195.119`

**Additional IP addresses \(as of January 19, 2025\):**

**3.123.247.156, 18.184.184.134, 3.76.166.75**

</td>
<td valign="top">

2a05:d014:ca2:3702::17, 2a05:d014:ca2:3705::17, 2a05:d014:ca2:3708::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`, `18.159.31.22`, `3.69.186.98`, `3.77.195.119`

**Additional IP addresses \(as of January 19, 2025\):**

**3.123.247.156, 18.184.184.134, 3.76.166.75**

</td>
<td valign="top">

2a05:d014:ca2:3702::17, 2a05:d014:ca2:3705::17, 2a05:d014:ca2:3708::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`, `18.159.31.22`, `3.69.186.98`, `3.77.195.119`

**Additional IP addresses \(as of January 19, 2025\):**

**35.157.237.81, 52.58.116.80, 18.196.77.73**

</td>
<td valign="top">

2a05:d014:e0d:f902::17, 2a05:d014:e0d:f908::17, 2a05:d014:e0d:f905::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-002.hana.ondemand.com

</td>
<td valign="top">

`3.64.227.236`, `3.126.229.22`, `18.193.180.19`, `18.153.123.11`, `3.121.37.195`, `3.73.215.90`

**Additional IP addresses \(as of January 19, 2025\):**

**3.72.125.186, 18.199.43.118, 3.69.159.226**

</td>
<td valign="top">

2a05:d014:173b:8505::17, 2a05:d014:173b:8502::17, 2a05:d014:173b:8508::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-003.hana.ondemand.com

</td>
<td valign="top">

`3.127.77.3`, `3.64.196.58`, `18.156.151.247`, `18.197.252.154`, `3.79.137.29`, `52.58.93.50`

**Additional IP addresses \(as of January 19, 2025\):**

**3.65.23.248, 18.192.224.62, 35.159.136.14**

</td>
<td valign="top">

2a05:d014:1db0:1705::17, 2a05:d014:1db0:1702::17, 2a05:d014:1db0:1708::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-004.hana.ondemand.com

</td>
<td valign="top">

`3.65.185.47`, `3.70.38.218`, `18.196.206.8`, `3.73.109.100`, `3.73.8.210`, `52.59.18.183`

**Additional IP addresses \(as of January 19, 2025\):**

**3.125.225.167, 18.158.49.214, 35.157.19.103**

</td>
<td valign="top">

2a05:d014:1140:c905::17, 2a05:d014:1140:c908::17, 2a05:d014:1140:c902::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-005.hana.ondemand.com

</td>
<td valign="top">

`3.122.31.132`, `18.193.56.244`, `3.78.172.245`

**Additional IP addresses \(as of January 19, 2025\):**

**3.72.138.152, 18.195.38.125, 52.57.99.237**

</td>
<td valign="top">

2a05:d014:1e09:6a02::17, 2a05:d014:1e09:6a05::17, 2a05:d014:1e09:6a08::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Frankfurt\) - AWS

\(`cf.eu11.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

`3.124.207.41`, `18.157.105.117`, `18.156.209.198`, `3.66.26.249`, `3.72.216.204`, `3.74.99.245`

**Additional IP addresses \(as of January 19, 2025\):**

**3.65.41.79, 35.159.179.221, 52.59.124.48**

</td>
<td valign="top">

2a05:d014:1b2c:b502::17, 2a05:d014:1b2c:b508::17, 2a05:d014:1b2c:b505::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

`3.124.207.41`, `18.157.105.117`, `18.156.209.198`, `3.66.26.249`, `3.72.216.204`, `3.74.99.245`

**Additional IP addresses \(as of January 19, 2025\):**

**3.65.41.79, 35.159.179.221, 52.59.124.48**

</td>
<td valign="top">

2a05:d014:1b2c:b502::17, 2a05:d014:1b2c:b508::17, 2a05:d014:1b2c:b505::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

`3.124.207.41`, `18.157.105.117`, `18.156.209.198`, `3.66.26.249`, `3.72.216.204`, `3.74.99.245`

**Additional IP addresses \(as of January 19, 2025\):**

**3.78.138.146, 3.78.214.251, 18.199.183.133**

</td>
<td valign="top">

2a05:d014:62c:7a05::17, 2a05:d014:62c:7a08::17, 2a05:d014:62c:7a02::17

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Europe \(Netherlands\) - Azure

\(`cf.eu20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu20.hana.ondemand.com

</td>
<td valign="top">

`40.119.153.88`

**Additional IP address \(as of January 19, 2025\):**

**57.153.48.23**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu20.hana.ondemand.com

</td>
<td valign="top">

`40.119.153.88`

**Additional IP address \(as of January 19, 2025\):**

**57.153.48.23**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu20.hana.ondemand.com

</td>
<td valign="top">

`40.119.153.88`

**Additional IP address \(as of January 19, 2025\):**

**57.153.52.157**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu20-001.hana.ondemand.com

</td>
<td valign="top">

`20.82.83.59`

**Additional IP address \(as of January 19, 2025\):**

**20.67.69.84**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Frankfurt\) - Google Cloud

\(`cf.eu30.hana.ondemand.com` \)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu30.hana.ondemand.com

</td>
<td valign="top">

`35.198.143.110` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu30.hana.ondemand.com

</td>
<td valign="top">

`35.198.143.110` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu30.hana.ondemand.com

</td>
<td valign="top">

`35.198.143.110` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Netherlands\) - Google Cloud

\(`cf.eu31.hana.ondemand.com` \)

> ### Note:  
> Available as of June 30, 2025



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu31.hana.ondemand.com

</td>
<td valign="top">

`34.90.22.237`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu31.hana.ondemand.com

</td>
<td valign="top">

`34.90.22.237`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu31.hana.ondemand.com

</td>
<td valign="top">

`34.90.22.237`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="5">

US East \(VA\) - AWS

\(`cf.us10.hana.ondemand.com`\)

*Enterprise & Trial*

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`, `18.213.242.208`, `3.214.110.153`, `34.205.56.51`

**Additional IP addresses \(as of January 19, 2025\):**

**98.82.227.152, 107.20.252.91, 34.198.33.88**

</td>
<td valign="top">

2600:1f18:ef:9b05::17, 2600:1f18:ef:9b08::17, 2600:1f18:ef:9b02::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`, `18.213.242.208`, `3.214.110.153`, `34.205.56.51`

**Additional IP addresses \(as of January 19, 2025\):**

**98.82.227.152, 107.20.252.91, 34.198.33.88**

</td>
<td valign="top">

2600:1f18:ef:9b05::17, 2600:1f18:ef:9b08::17, 2600:1f18:ef:9b02::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`, `18.213.242.208`, `3.214.110.153`, `34.205.56.51`

**Additional IP addresses \(as of January 19, 2025\):**

**54.147.47.110, 18.214.162.12, 44.206.11.12**

</td>
<td valign="top">

2600:1f18:12b5:c605::17, 2600:1f18:12b5:c602::17, 2600:1f18:12b5:c608::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10-001.hana.ondemand.com

</td>
<td valign="top">

`3.220.114.17`, `3.227.182.44`, `52.86.131.53`, `44.218.82.203`, `44.219.57.163`, `50.16.106.103` 

**Additional IP addresses \(as of January 19, 2025\):**

**54.157.55.28, 3.234.87.202, 50.17.185.79**

</td>
<td valign="top">

2600:1f18:2d7e:2905::17, 2600:1f18:2d7e:2908::17, 2600:1f18:2d7e:2902::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10-002.hana.ondemand.com

</td>
<td valign="top">

`34.202.68.0`, `54.234.152.59`, `107.20.66.86`, `3.214.116.95`, `54.144.230.36`, `54.226.37.104`

**Additional IP addresses \(as of January 19, 2025\):**

**34.234.117.43, 34.237.168.235, 44.221.148.86**

</td>
<td valign="top">

2600:1f18:264b:5405::17, 2600:1f18:264b:5402::17, 2600:1f18:264b:5408::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

US West \(Oregon\) - AWS

\(`cf.us11.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us11.hana.ondemand.com

</td>
<td valign="top">

`34.211.82.149`, `100.20.19.69`, `35.95.238.236`, `54.69.228.173`, `35.161.174.123`, `44.230.137.133`, `54.201.79.229`, `34.217.172.244`, `44.235.33.61` 

</td>
<td valign="top">

2600:1f14:180c:7205::17, 2600:1f14:180c:7208::17, 2600:1f14:180c:7202::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us11.hana.ondemand.com

</td>
<td valign="top">

`34.211.82.149`, `100.20.19.69`, `35.95.238.236`, `54.69.228.173`, `35.161.174.123`, `44.230.137.133`, `54.201.79.229`, `34.217.172.244`, `44.235.33.61`

</td>
<td valign="top">

2600:1f14:180c:7205::17, 2600:1f14:180c:7208::17, 2600:1f14:180c:7202::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us11.hana.ondemand.com

</td>
<td valign="top">

`34.211.82.149`, `100.20.19.69`, `35.95.238.236`, `54.69.228.173`, `35.161.174.123`, `44.230.137.133`, `54.201.79.229`, `34.217.172.244`, `44.235.33.61`

</td>
<td valign="top">

2600:1f14:2448:f202::17, 2600:1f14:2448:f205::17, 2600:1f14:2448:f208::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

US West \(WA\) - Azure

\(`cf.us20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us20.hana.ondemand.com

</td>
<td valign="top">

`40.91.120.100` 

**Additional IP address \(as of January 19, 2025\):**

**52.137.100.108**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us20.hana.ondemand.com

</td>
<td valign="top">

`40.91.120.100`

**Additional IP address \(as of January 19, 2025\):**

**52.137.100.108**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us20.hana.ondemand.com

</td>
<td valign="top">

`40.91.120.100`

**Additional IP address \(as of January 19, 2025\):**

**52.137.108.200**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

US East \(VA\) - Azure

\(`cf.us21.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us21.hana.ondemand.com

</td>
<td valign="top">

`40.88.52.17`

**Additional IP address \(as of January 19, 2025\):**

**48.216.153.6**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us21.hana.ondemand.com

</td>
<td valign="top">

`40.88.52.17`

**Additional IP address \(as of January 19, 2025\):**

**48.216.153.6**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us21.hana.ondemand.com

</td>
<td valign="top">

`40.88.52.17`

**Additional IP address \(as of January 19, 2025\):**

**48.216.153.226**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

US Central \(IA\) - Google Cloud

\(`cf.us30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us30.hana.ondemand.com

</td>
<td valign="top">

`35.184.169.79` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us30.hana.ondemand.com

</td>
<td valign="top">

`35.184.169.79` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us30.hana.ondemand.com

</td>
<td valign="top">

`35.184.169.79` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Brazil \(São Paulo\) - AWS

\(`cf.br10.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.br10.hana.ondemand.com

</td>
<td valign="top">

`18.229.91.150`, `52.67.135.4`, `54.232.179.204`, `18.228.53.198`, `52.67.149.240`, `54.94.179.209`

**Additional IP addresses \(as of January 19, 2025\):**

**177.71.155.99, 177.71.245.233, 18.231.25.174**

</td>
<td valign="top">

2600:1f1e:c13:1502::17, 2600:1f1e:c13:1508::17, 2600:1f1e:c13:1505::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.br10.hana.ondemand.com

</td>
<td valign="top">

`18.229.91.150`, `52.67.135.4`, `54.232.179.204`, `18.228.53.198`, `52.67.149.240`, `54.94.179.209`

**Additional IP addresses \(as of January 19, 2025\):**

**177.71.155.99, 177.71.245.233, 18.231.25.174**

</td>
<td valign="top">

2600:1f1e:c13:1502::17, 2600:1f1e:c13:1508::17, 2600:1f1e:c13:1505::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.br10.hana.ondemand.com

</td>
<td valign="top">

`18.229.91.150`, `52.67.135.4`, `54.232.179.204`, `18.228.53.198`, `52.67.149.240`, `54.94.179.209`

**Additional IP addresses \(as of January 19, 2025\):**

**18.229.78.152, 54.232.119.169, 18.228.231.243**

</td>
<td valign="top">

2600:1f1e:32e:2c05::17, 2600:1f1e:32e:2c08::17, 2600:1f1e:32e:2c02::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Brazil \(São Paulo\) - Azure

\(`cf.br20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.br20.hana.ondemand.com

</td>
<td valign="top">

`4.228.118.21`

**Additional IP address \(as of January 19, 2025\):**

**20.201.104.57**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.br20.hana.ondemand.com

</td>
<td valign="top">

`4.228.118.21`

**Additional IP address \(as of January 19, 2025\):**

**20.201.104.57**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.br20.hana.ondemand.com

</td>
<td valign="top">

`4.228.118.21`

**Additional IP address \(as of January 19, 2025\):**

**20.201.105.31**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Brazil \(São Paulo\) - Google Cloud

\(`cf.br30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.br30.hana.ondemand.com

</td>
<td valign="top">

`34.95.189.118` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.br30.hana.ondemand.com

</td>
<td valign="top">

`34.95.189.118`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.br30.hana.ondemand.com

</td>
<td valign="top">

`34.95.189.118`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Japan \(Tokyo\) - AWS

\(`cf.jp10.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

`13.114.117.83`, `3.114.248.68`, `3.113.252.15`, `18.178.155.134`, `57.180.140.5`, `57.180.145.179`

**Additional IP addresses \(as of January 19, 2025\):**

**35.74.196.228, 35.75.166.160, 52.198.15.94**

</td>
<td valign="top">

2406:da14:1d30:cb05::17, 2406:da14:1d30:cb08::17, 2406:da14:1d30:cb02::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

`13.114.117.83`, `3.114.248.68`, `3.113.252.15`, `18.178.155.134`, `57.180.140.5`, `57.180.145.179`

**Additional IP addresses \(as of January 19, 2025\):**

**35.74.196.228, 35.75.166.160, 52.198.15.94**

</td>
<td valign="top">

2406:da14:1d30:cb05::17, 2406:da14:1d30:cb08::17, 2406:da14:1d30:cb02::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

`13.114.117.83`, `3.114.248.68`, `3.113.252.15`, `18.178.155.134`, `57.180.140.5`, `57.180.145.179`

**Additional IP addresses \(as of January 19, 2025\):**

**13.114.120.142, 18.176.244.8, 54.92.104.72**

</td>
<td valign="top">

2406:da14:191b:9005::17, 2406:da14:191b:9002::17, 2406:da14:191b:9008::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Japan \(Tokyo\) - Azure

\(`cf.jp20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.jp20.hana.ondemand.com

</td>
<td valign="top">

`20.43.89.91`

**Additional IP address \(as of January 19, 2025\):**

**48.218.89.49**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.jp20.hana.ondemand.com

</td>
<td valign="top">

`20.43.89.91`

**Additional IP address \(as of January 19, 2025\):**

**48.218.89.49**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.jp20.hana.ondemand.com

</td>
<td valign="top">

`20.43.89.91`

**Additional IP address \(as of January 19, 2025\):**

**48.218.90.204**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Japan \(Osaka\) - Google Cloud

\(`cf.jp30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.jp30.hana.ondemand.com

</td>
<td valign="top">

`34.97.168.169` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.jp30.hana.ondemand.com

</td>
<td valign="top">

`34.97.168.169`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.jp30.hana.ondemand.com

</td>
<td valign="top">

`34.97.168.169`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Japan \(Tokyo\) - Google Cloud

\(`cf.jp31.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.jp31.hana.ondemand.com

</td>
<td valign="top">

`34.84.96.118` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.jp31.hana.ondemand.com

</td>
<td valign="top">

`34.84.96.118`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.jp31.hana.ondemand.com

</td>
<td valign="top">

`34.84.96.118`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Australia \(Sydney\) - AWS

\(`cf.ap10.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

`13.236.220.84`, `13.211.73.244`, `3.105.95.184`, `13.55.188.95`, `3.105.212.249`, `3.106.45.106`

**Additional IP addresses \(as of January 19, 2025\):**

**3.107.130.66, 3.104.152.189, 3.105.214.80**

</td>
<td valign="top">

2406:da1c:339:e808::17, 2406:da1c:339:e805::17, 2406:da1c:339:e802::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

`13.236.220.84`, `13.211.73.244`, `3.105.95.184`, `13.55.188.95`, `3.105.212.249`, `3.106.45.106`

**Additional IP addresses \(as of January 19, 2025\):**

**3.107.130.66, 3.104.152.189, 3.105.214.80**

</td>
<td valign="top">

2406:da1c:339:e808::17, 2406:da1c:339:e805::17, 2406:da1c:339:e802::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

`13.236.220.84`, `13.211.73.244`, `3.105.95.184`, `13.55.188.95`, `3.105.212.249`, `3.106.45.106`

**Additional IP addresses \(as of January 19, 2025\):**

**13.54.123.199, 13.55.164.105, 3.106.145.100**

</td>
<td valign="top">

2406:da1c:b6a:b905::17, 2406:da1c:b6a:b908::17, 2406:da1c:b6a:b902::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Asia Pacific \(Singapore\) - AWS

\(`cf.ap11.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

`3.0.9.102`,`18.140.39.70`, `18.139.147.53`, `13.229.158.122`, `18.140.228.217`, `52.74.215.89`

**Additional IP addresses \(as of January 19, 2025\):**

**52.76.177.178, 13.213.177.227, 13.251.142.208**

</td>
<td valign="top">

2406:da18:500:5402::17, 2406:da18:500:5405::17, 2406:da18:500:5408::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

`3.0.9.102`, `18.140.39.70`, `18.139.147.53`, `13.229.158.122`, `18.140.228.217`, `52.74.215.89`

**Additional IP addresses \(as of January 19, 2025\):**

**52.76.177.178, 13.213.177.227, 13.251.142.208**

</td>
<td valign="top">

2406:da18:500:5402::17, 2406:da18:500:5405::17, 2406:da18:500:5408::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

`3.0.9.102`, `18.140.39.70`, `18.139.147.53`, `13.229.158.122`, `18.140.228.217`, `52.74.215.89`

**Additional IP addresses \(as of January 19, 2025\):**

**13.215.4.190, 13.229.41.216, 52.76.219.61**

</td>
<td valign="top">

2406:da18:6d5:c05::17, 2406:da18:6d5:c08::17, 2406:da18:6d5:c02::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Asia Pacific \(Seoul\) - AWS

\(`cf.ap12.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

`3.35.255.45`, `3.35.106.215`, `3.35.215.12`, `13.209.236.215`, `43.201.194.105`, `43.202.204.5`

**Additional IP addresses \(as of January 19, 2025\):**

**3.37.25.26, 43.202.209.5, 54.180.187.39**

</td>
<td valign="top">

2406:da12:ae7:cc02::17, 2406:da12:ae7:cc05::17, 2406:da12:ae7:cc08::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

`3.35.255.45`, `3.35.106.215`, `3.35.215.12`, `13.209.236.215`, `43.201.194.105`, `43.202.204.5`

**Additional IP addresses \(as of January 19, 2025\):**

**3.37.25.26, 43.202.209.5, 54.180.187.39**

</td>
<td valign="top">

2406:da12:ae7:cc02::17, 2406:da12:ae7:cc05::17, 2406:da12:ae7:cc08::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

`3.35.255.45`, `3.35.106.215`, `3.35.215.12`, `13.209.236.215`, `43.201.194.105`, `43.202.204.5`

**Additional IP addresses \(as of January 19, 2025\):**

**3.37.1.194, 13.124.112.64, 54.180.67.191**

</td>
<td valign="top">

2406:da12:21d:9308::17, 2406:da12:21d:9305::17, 2406:da12:21d:9302::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Australia \(Sydney\) - Azure

\(`cf.ap20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap20.hana.ondemand.com

</td>
<td valign="top">

`20.53.99.41`

**Additional IP address \(as of January 19, 2025\):**

**20.227.99.35**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap20.hana.ondemand.com

</td>
<td valign="top">

`20.53.99.41`

**Additional IP address \(as of January 19, 2025\):**

**20.227.99.35**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap20.hana.ondemand.com

</td>
<td valign="top">

`20.53.99.41`

**Additional IP address \(as of January 19, 2025\):**

**20.227.102.91**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Singapore - Azure

\(`cf.ap21.hana.ondemand.com`\)

*Enterprise & Trial*

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

**Additional IP address \(as of January 19, 2025\):**

**57.155.80.35**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

**Additional IP address \(as of January 19, 2025\):**

**57.155.80.35**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

**Additional IP address \(as of January 19, 2025\):**

**57.155.80.232**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Australia \(Sydney\) - Google Cloud

\(`cf.ap30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap30.hana.ondemand.com

</td>
<td valign="top">

`35.244.71.16`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap30.hana.ondemand.com

</td>
<td valign="top">

`35.244.71.16`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap30.hana.ondemand.com

</td>
<td valign="top">

`35.244.71.16`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Singapore - Google Cloud

\(`cf.ap31.hana.ondemand.com`\)

> ### Note:  
> Available as of June 30, 2025



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap31.hana.ondemand.com

</td>
<td valign="top">

`35.198.192.195`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap31.hana.ondemand.com

</td>
<td valign="top">

`35.198.192.195`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap31.hana.ondemand.com

</td>
<td valign="top">

`35.198.192.195`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Canada \(Montreal\) - AWS

\(`cf.ca10.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

`3.98.102.153`, `35.182.75.101`, `35.183.74.34`, `15.157.88.166`, `3.98.202.222`, `52.60.210.33`

**Additional IP addresses \(as of January 19, 2025\):**

**15.157.235.215, 15.222.67.204, 3.96.123.72**

</td>
<td valign="top">

2600:1f11:b90:f908::17, 2600:1f11:b90:f905::17, 2600:1f11:b90:f902::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

`3.98.102.153`, `35.182.75.101`, `35.183.74.34`, `15.157.88.166`, `3.98.202.222`, `52.60.210.33`

**Additional IP addresses \(as of January 19, 2025\):**

**15.157.235.215, 15.222.67.204, 3.96.123.72**

</td>
<td valign="top">

2600:1f11:b90:f908::17, 2600:1f11:b90:f905::17, 2600:1f11:b90:f902::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

`3.98.102.153`, `35.182.75.101`, `35.183.74.34`, `15.157.88.166`, `3.98.202.222`, `52.60.210.33`

**Additional IP addresses \(as of January 19, 2025\):**

**3.97.216.231, 15.156.32.232, 52.60.236.134**

</td>
<td valign="top">

2600:1f11:f08:3302::17, 2600:1f11:f08:3305::17, 2600:1f11:f08:3308::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Canada Central \(Toronto\) - Azure

\(`cf.ca20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ca20.hana.ondemand.com

</td>
<td valign="top">

`4.172.17.29`, `130.107.188.238` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ca20.hana.ondemand.com

</td>
<td valign="top">

`4.172.17.29`, `130.107.189.169` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ca20.hana.ondemand.com

</td>
<td valign="top">

`4.172.17.29`, `130.107.189.169` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Switzerland \(Zurich\) - Azure

\(`cf.ch20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ch20.hana.ondemand.com

</td>
<td valign="top">

`20.208.56.83`

**Additional IP address \(as of January 19, 2025\):**

**74.242.192.152**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ch20.hana.ondemand.com

</td>
<td valign="top">

`20.208.56.83`

**Additional IP address \(as of January 19, 2025\):**

**74.242.192.152**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ch20.hana.ondemand.com

</td>
<td valign="top">

`20.208.56.83`

**Additional IP address \(as of January 19, 2025\):**

**74.242.193.142**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

India \(Mumbai\) - Google Cloud

\(`cf.in30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.in30.hana.ondemand.com

</td>
<td valign="top">

`34.93.125.74`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.in30.hana.ondemand.com

</td>
<td valign="top">

`34.93.125.74`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.in30.hana.ondemand.com

</td>
<td valign="top">

`34.93.125.74`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Israel \(Tel Aviv\) - Google Cloud

\(`cf.il30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.il30.hana.ondemand.com

</td>
<td valign="top">

`34.165.59.26`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.il30.hana.ondemand.com

</td>
<td valign="top">

`34.165.59.26`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.il30.hana.ondemand.com

</td>
<td valign="top">

`34.165.59.26`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

China \(Shanghai\) - Alibaba Cloud

\(`cf.cn40.platform.sapcloud.cn`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.cn40.platform.sapcloud.cn

</td>
<td valign="top">

`139.224.7.71`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.cn40.platform.sapcloud.cn

</td>
<td valign="top">

`139.224.7.71`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.cn40.platform.sapcloud.cn

</td>
<td valign="top">

`139.224.7.71`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

China North - Azure

\(`cf.cn20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.cn20.hana.ondemand.com

</td>
<td valign="top">

`155.56.210.43` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.cn20.hana.ondemand.com

</td>
<td valign="top">

`155.56.210.43`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.cn20.hana.ondemand.com

</td>
<td valign="top">

`155.56.210.43`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

KSA \(Dammam\) - Google Cloud

\(`cf.sa30.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.sa30.hana.ondemand.com

</td>
<td valign="top">

`34.166.32.46` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.sa30.hana.ondemand.com

</td>
<td valign="top">

`34.166.32.46`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.sa30.hana.ondemand.com

</td>
<td valign="top">

`34.166.32.46`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

KSA \(Dammam\) - Google Cloud

\(`cf.sa31.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.sa31.hana.ondemand.com

</td>
<td valign="top">

`34.166.72.122` 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.sa31.hana.ondemand.com

</td>
<td valign="top">

`34.166.72.122`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.sa31.hana.ondemand.com

</td>
<td valign="top">

`34.166.72.122`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="5">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

</td>
</tr>
<tr>
<td valign="top" colspan="5">

 

</td>
</tr>
<tr>
<td valign="top" colspan="5">

**ABAP Environment**

> ### Note:  
> To enable the full scenario for the SAP BTP ABAP environment, the DNS names below are needed *in addition* to the IPs of the Connectivity service mentioned above. If you can only configure allowlists for *IP addresses* in your firewall, please note that these addresses may change at any time and that you need to validate the values with a DNS service of your choice regularly.
> 
> For more information, see [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-for-abap-environment).



</td>
</tr>
<tr>
<td valign="top">

**Region \(Region Host\)**

</td>
<td valign="top" colspan="2">

**Hosts**

</td>
<td valign="top" colspan="2">

**IP Addresses**

</td>
</tr>
<tr>
<td valign="top">

Europe \(Frankfurt\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.eu10.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Europe \(Frankfurt\) EU Access - AWS

</td>
<td valign="top" colspan="2">

\*.abap.eu11.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Europe \(Netherlands\) - Azure

</td>
<td valign="top" colspan="2">

\*.abap.eu20.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

US East \(VA\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.us10.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

US East \(VA\) - Azure

</td>
<td valign="top" colspan="2">

\*.abap.us21.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

US West \(WA\) - Azure

</td>
<td valign="top" colspan="2">

\*.abap.us20.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Brazil \(São Paulo\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.br10.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Japan \(Tokyo\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.jp10.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Japan \(Tokyo\) - Azure

</td>
<td valign="top" colspan="2">

\*.abap.jp20.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Australia \(Sydney\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.ap10.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Australia \(Sydney\) - Azure

</td>
<td valign="top" colspan="2">

\*.abap.ap20.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Asia Pacific \(Singapore\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.ap11.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Asia Pacific \(Seoul\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.ap12.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Singapore - Azure

</td>
<td valign="top" colspan="2">

\*.abap.ap21.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Canada \(Montreal\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.ca10.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top">

Switzerland \(Zurich\) - Azure

</td>
<td valign="top" colspan="2">

\*.abap.ch20.hana.ondemand.com

</td>
<td valign="top" colspan="2">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top" colspan="5">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

</td>
</tr>
<tr>
<td valign="top" colspan="5">

 

</td>
</tr>
<tr>
<td valign="top" colspan="5">

**Neo Environment**

</td>
</tr>
<tr>
<td valign="top">

**Region \(Region Host\)**

</td>
<td valign="top" colspan="2">

**Hosts**

</td>
<td valign="top" colspan="2">

**IP Addresses**

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Rot\)

\(`hana.ondemand.com`\)

\(`eu1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`155.56.210.83`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`155.56.210.43`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`155.56.210.84`

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Frankfurt\)

\(`eu2.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.eu2.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`157.133.206.143` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.eu2.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`157.133.205.174` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.eu2.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`157.133.205.233` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Amsterdam\)

\(`eu3.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.eu3.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.87.72` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.eu3.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.87.76`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.eu3.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.86.212` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

United States East \(Ashburn\)

\(`us1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.us1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.181.204` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.181.48` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.181.134` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

United States West \(Chandler\)

\(`us2.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.us2.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.129.127` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us2.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.129.140` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us2.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.129.88` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

United States East \(Sterling\)

\(`us3.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.us3.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.32.144` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us3.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.33.92` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us3.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.33.119` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

US States West \(Colorado Springs\)

\(`us4.hana.ondemand.com` \)

</td>
<td valign="top" colspan="2">

connectivitynotification.us4.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.183.46` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us4.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.183.14` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us4.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.183.103` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Australia \(Sydney\)

\(`ap1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.ap1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`157.133.97.47`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.ap1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`157.133.97.27` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.ap1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`157.133.97.46` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

China \(Shanghai\)

\(`cn1.platform.sapcloud.cn`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cn1.platform.sapcloud.cn

</td>
<td valign="top" colspan="2">

`121.91.109.81`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cn1.platform.sapcloud.cn

</td>
<td valign="top" colspan="2">

`121.91.109.77`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cn1.platform.sapcloud.cn

</td>
<td valign="top" colspan="2">

`121.91.109.82`

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Japan \(Tokyo\)

\(`jp1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.jp1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.112.168` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.jp1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.112.212` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.jp1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.112.164` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Canada \(Toronto\)

\(`ca1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.ca1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.174.201` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.ca1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.174.220` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.ca1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.174.236` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Brazil \(São Paulo\)

\(`br1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.br1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.96.193` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.br1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.96.195` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.br1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.96.173` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

UAE \(Dubai\)

\(`ae1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.ae1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.80.206` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.ae1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.80.208` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.ae1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.80.182` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

KSA \(Riyadh\)

\(`sa1.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.sa1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.209.241` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.sa1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.209.207` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.sa1.hana.ondemand.com

</td>
<td valign="top" colspan="2">

`130.214.209.191` 

</td>
</tr>
<tr>
<td valign="top" colspan="5">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

</td>
</tr>
<tr>
<td valign="top" colspan="5">

 

</td>
</tr>
<tr>
<td valign="top" colspan="5">

**Trial \(Cloud Foundry Environment\)**



> ### Note:  
> In the Cloud Foundry environment, IPs are controlled by the respective IaaS provider \(AWS, Azure, or Google Cloud\). IPs may change due to network updates on the provider side. Any planned changes will be announced several weeks before they take effect. See also [Regions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html "You can deploy applications in different regions. Each region represents a geographical location (for example, Europe, US East) where applications, data, or services are hosted.") :arrow_upper_right:.



</td>
</tr>
<tr>
<td valign="top">

**Region \(Region Host\)**

</td>
<td valign="top" colspan="2">

**Hosts**

</td>
<td valign="top">

**IP Addresses \(IPv4\)**

</td>
<td valign="top">

**IP Addresses \(IPv6\)**

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Frankfurt\) - AWS

\(`cf.eu10.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`, `18.159.31.22`, `3.69.186.98`, `3.77.195.119`

**Additional IP addresses \(as of January 19, 2025\):**

**3.123.247.156, 18.184.184.134, 3.76.166.75**

</td>
<td valign="top">

2a05:d014:ca2:3702::17, 2a05:d014:ca2:3705::17, 2a05:d014:ca2:3708::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`, `18.159.31.22`, `3.69.186.98`, `3.77.195.119`

**Additional IP addresses \(as of January 19, 2025\):**

**3.123.247.156, 18.184.184.134, 3.76.166.75**

</td>
<td valign="top">

2a05:d014:ca2:3702::17, 2a05:d014:ca2:3705::17, 2a05:d014:ca2:3708::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`, `18.159.31.22`, `3.69.186.98`, `3.77.195.119`

**Additional IP addresses \(as of January 19, 2025\):**

**35.157.237.81, 52.58.116.80, 18.196.77.73**

</td>
<td valign="top">

2a05:d014:e0d:f902::17, 2a05:d014:e0d:f908::17, 2a05:d014:e0d:f905::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

United States East \(VA\) - AWS

\(`cf.us10.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`, `18.213.242.208`, `3.214.110.153`, `34.205.56.51`

**Additional IP addresses \(as of January 19, 2025\):**

**98.82.227.152, 107.20.252.91, 34.198.33.88**

</td>
<td valign="top">

2600:1f18:ef:9b05::17, 2600:1f18:ef:9b08::17, 2600:1f18:ef:9b02::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`, `18.213.242.208`, `3.214.110.153`, `34.205.56.51`

**Additional IP addresses \(as of January 19, 2025\):**

**98.82.227.152, 107.20.252.91, 34.198.33.88**

</td>
<td valign="top">

2600:1f18:ef:9b05::17, 2600:1f18:ef:9b08::17, 2600:1f18:ef:9b02::17

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`, `18.213.242.208`, `3.214.110.153`, `34.205.56.51`

**Additional IP addresses \(as of January 19, 2025\):**

**54.147.47.110, 18.214.162.12, 44.206.11.12**

</td>
<td valign="top">

2600:1f18:12b5:c605::17, 2600:1f18:12b5:c602::17, 2600:1f18:12b5:c608::17

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Singapore - Azure

\(`cf.ap21.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" colspan="5">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

</td>
</tr>
</table>

> ### Note:  
> If you install the Cloud Connector in a network segment that is isolated from the backend systems, make sure the exposed hosts and ports are still reachable and open them in the firewall that protects them:
> 
> -   for HTTP, the ports you chose for the HTTP/S server.
> -   for LDAP, the port of the LDAP server.
> -   for RFC, it depends on whether you use an SAProuter or not and whether load balancing is used:
>     -   if you use an SAProuter, it is typically configured as visible in the network of the Cloud Connector and the corresponding *routtab* is exposing all the systems that should be used.
>     -   without SAProuter, you must open the application server hosts and the corresponding gateway ports \(33\#\#, 48\#\#\). When using load balancing for the connection, you must also open the message server host and port.
> 
> 
> See also [Network Zones](network-zones-7b9d90c.md).

> ### Note:  
> For more information about the used ABAP server ports, see: [Ports of SAP NetWeaver Application Server ABAP](http://help.sap.com/saphelp_nw75/helpdata/en/4e/c26cdc58e968b9e10000000a42189e/frameset.htm).
> 
> For more information about additional IP addresses for SAP Business Application Studio, see [SAP Business Application Studio Inbound IP Addresses](https://help.sap.com/docs/bas/sap-business-application-studio/sap-business-application-studio-availability#inbound-ip-address).

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

**Related Information**  


[Installation on Microsoft Windows OS](installation-on-microsoft-windows-os-204aaad.md "Installing the Cloud Connector on a Microsoft Windows operating system.")

[Installation on Linux OS](installation-on-linux-os-f069840.md "Installing the Cloud Connector on a Linux operating system.")

[Installation on Apple macOS](installation-on-apple-macos-6c3eec1.md "Installing the Cloud Connector on an Apple macOS operating system.")

[Recommendations for Secure Setup](recommendations-for-secure-setup-e7ea82a.md "For the Connectivity service and the Cloud Connector, you should apply the following guidelines to guarantee the highest level of security for these components.")

[Sizing Recommendations](sizing-recommendations-f008494.md "When installing a Cloud Connector, the first thing you need to decide is the sizing of the installation.")

