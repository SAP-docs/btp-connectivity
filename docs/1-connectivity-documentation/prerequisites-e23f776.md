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

For specific information about all Connectivity restrictions, see [Connectivity: Restrictions](connectivity-e54cc8f.md#loioe54cc8fbbb571014beb5caaf6aa31280__restrictions).

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
<td valign="top" rowspan="2">

SAP JVM 64-bit \(recommended\)

</td>
<td valign="top">

7

</td>
<td valign="top">

2.x up to 2.12.2

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

2.7.2 and higher

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Oracle JDK 64-bit

</td>
<td valign="top">

7

</td>
<td valign="top">

2.x up to 2.12.2

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

2.7.2 and higher

</td>
</tr>
<tr>
<td valign="top">

[SAP Machine](https://sap.github.io/SapMachine/) 64-bit

</td>
<td valign="top">

11

</td>
<td valign="top">

2.14.0 and higher

</td>
</tr>
<tr>
<td valign="top">

[SAP Machine](https://sap.github.io/SapMachine/) 64-bit

</td>
<td valign="top">

17

</td>
<td valign="top">

2.15.0 and higher

</td>
</tr>
<tr>
<td valign="top">

[SAP Machine](https://sap.github.io/SapMachine/) 64-bit

</td>
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

2.x

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

2.x

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

2.x

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

2.5.1 and higher

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

2.5.1 and higher

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

2.5.1 and higher

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

2.8.1 and higher

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

Windows Server 2019, Mac OS X 10.12 \(Sierra\), Mac OS X 10.13 \(High Sierra\), Mac OS X 10.14 \(Mojave\)

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

SUSE Linux Enterprise Server 12, SUSE Linux Enterprise Server 15, Red Hat Enterprise Linux 7, Red Hat Enterprise Linux 8

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

Windows Server 2022, macOS 10.15 \(Catalina\)

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

Windows 11, Red Hat Enterprise Linux 9

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

ppc64le

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

Oracle Linux 9, macOS 11 \(Big Sur\), macOS 12 \(Monterey\), macOS 13 \(Ventura\)

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

macOS 11 \(Big Sur\), macOS 12 \(Monterey\), macOS 13 \(Ventura\)

</td>
<td valign="top">

aarch64

</td>
<td valign="top">

2.16.0 and higher

</td>
</tr>
</table>

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)



<a name="loioe23f776e4d594fdbaeeb1196d47bbcc0__network"/>

## Network

You must have Internet connection at least to the following Connectivity service hosts \(depending on the region\), to which you can connect your Cloud Connector. All connections to the hosts are TLS-based and connect to port 443.

> ### Remember:  
> For some solutions of the BTP portfolio, you must include additional hosts to set up an on-premise connectivity scenario with the Cloud Connector. This applies, for example, to: SAP Data Intelligence, SAP HANA Cloud, Business Appilcation Studio, and SAP Build Apps. Check the respective solution documentation for details.

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

IP Address

</th>
</tr>
<tr>
<td valign="top" colspan="4">

**Cloud Foundry Environment**

> ### Note:  
> In the Cloud Foundry environment, IPs are controlled by the respective IaaS provider - Amazon Web Services \(AWS\), Microsoft Azure \(Azure\), or Google Cloud. IPs may change due to network updates on the provider side. Any planned changes will be announced at least 4 weeks before they take effect. See also [Regions](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html).



</td>
</tr>
<tr>
<td valign="top" rowspan="6">

Europe \(Frankfurt\) - AWS

\(`cf.eu10.hana.ondemand.com`\)

*Enterprise & Trial*

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`

**Additonal IP addresses:**

**18.159.31.22, 3.69.186.98, 3.77.195.119**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`

**Additonal IP addresses:**

**18.159.31.22, 3.69.186.98, 3.77.195.119**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`

**Additonal IP addresses:**

**18.159.31.22, 3.69.186.98, 3.77.195.119**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-002.hana.ondemand.com

</td>
<td valign="top">

`3.64.227.236`, `3.126.229.22`, `18.193.180.19`

**Additonal IP addresses:**

**18.153.123.11, 3.121.37.195, 3.73.215.90**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-003.hana.ondemand.com

</td>
<td valign="top">

`3.127.77.3`, `3.64.196.58`, `18.156.151.247`

**Additonal IP addresses:**

**18.197.252.154, 3.79.137.29, 52.58.93.50**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10-004.hana.ondemand.com

</td>
<td valign="top">

`3.65.185.47`, `3.70.38.218`, `18.196.206.8`

**Additonal IP addresses:**

**3.73.109.100, 3.73.8.210, 52.59.18.183**

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Europe \(Frankfurt\) - AWS

\(`cf.eu11.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

`3.124.207.41`, `18.157.105.117`, `18.156.209.198`

**Additonal IP addresses:**

**3.66.26.249, 3.72.216.204, 3.74.99.245**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

`3.124.207.41`, `18.157.105.117`, `18.156.209.198`

**Additonal IP addresses:**

**3.66.26.249, 3.72.216.204, 3.74.99.245**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

`3.124.207.41`, `18.157.105.117`, `18.156.209.198`

**Additonal IP addresses:**

**3.66.26.249, 3.72.216.204, 3.74.99.245**

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Europe \(Netherleands\) - Azure

\(`cf.eu20.hana.ondemand.com`\)

</td>
<td valign="top" colspan="2">

connectivitynotification.cf.eu20.hana.ondemand.com

</td>
<td valign="top">

`40.119.153.88`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu20.hana.ondemand.com

</td>
<td valign="top">

`40.119.153.88`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu20.hana.ondemand.com

</td>
<td valign="top">

`40.119.153.88`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu20-001.hana.ondemand.com

</td>
<td valign="top">

`20.82.83.59`

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
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu30.hana.ondemand.com

</td>
<td valign="top">

`35.198.143.110` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu30.hana.ondemand.com

</td>
<td valign="top">

`35.198.143.110` 

</td>
</tr>
<tr>
<td valign="top" rowspan="5">

US East \(VA\) - AWS

\(`cf.us10.hana.ondemand.com`\)

*Enterprise & Trial*

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`

**Additonal IP addresses:**

**18.213.242.208, 3.214.110.153, 34.205.56.51**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211` 

**Additonal IP addresses:**

**18.213.242.208, 3.214.110.153, 34.205.56.51**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`

**Additonal IP addresses:**

**18.213.242.208, 3.214.110.153, 34.205.56.51**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10-001.hana.ondemand.com

</td>
<td valign="top">

`3.220.114.17`, `3.227.182.44`, `52.86.131.53` 

**Additonal IP addresses:**

**44.218.82.203, 44.219.57.163, 50.16.106.103**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10-002.hana.ondemand.com

</td>
<td valign="top">

`34.202.68.0`, `54.234.152.59`, `107.20.66.86`

**Additonal IP addresses:**

**3.214.116.95, 54.144.230.36, 54.226.37.104**

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

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us20.hana.ondemand.com

</td>
<td valign="top">

`40.91.120.100`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us20.hana.ondemand.com

</td>
<td valign="top">

`40.91.120.100`

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

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us21.hana.ondemand.com

</td>
<td valign="top">

`40.88.52.17`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us21.hana.ondemand.com

</td>
<td valign="top">

`40.88.52.17`

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
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us30.hana.ondemand.com

</td>
<td valign="top">

`35.184.169.79` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us30.hana.ondemand.com

</td>
<td valign="top">

`35.184.169.79` 

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Brazil \(São Paulo\) - AWS

\(`cf.br10.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.br10.hana.ondemand.com

</td>
<td valign="top">

`18.229.91.150`, `52.67.135.4`, `54.232.179.204` 

**Additonal IP addresses:**

**18.228.53.198, 52.67.149.240, 54.94.179.209**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.br10.hana.ondemand.com

</td>
<td valign="top">

`18.229.91.150`, `52.67.135.4`, `54.232.179.204`

**Additonal IP addresses:**

**18.228.53.198, 52.67.149.240, 54.94.179.209**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.br10.hana.ondemand.com

</td>
<td valign="top">

`18.229.91.150`, `52.67.135.4`, `54.232.179.204` 

**Additonal IP addresses:**

**18.228.53.198, 52.67.149.240, 54.94.179.209**

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Japan \(Tokyo\) - AWS

\(`cf.jp10.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

`13.114.117.83`, `3.114.248.68`, `3.113.252.15`

**Additonal IP addresses:**

**18.178.155.134, 57.180.140.5, 57.180.145.179**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

`13.114.117.83`, `3.114.248.68`, `3.113.252.15`

**Additonal IP addresses:**

**18.178.155.134, 57.180.140.5, 57.180.145.179**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

`13.114.117.83`, `3.114.248.68`, `3.113.252.15`

**Additonal IP addresses:**

**18.178.155.134, 57.180.140.5, 57.180.145.179**

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

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.jp20.hana.ondemand.com

</td>
<td valign="top">

`20.43.89.91`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.jp20.hana.ondemand.com

</td>
<td valign="top">

`20.43.89.91`

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Australia \(Sydney\) - AWS

\(`cf.ap10.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

`13.236.220.84`, `13.211.73.244`, `3.105.95.184`

**Additonal IP addresses:**

**13.55.188.95, 3.105.212.249, 3.106.45.106**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

`13.236.220.84`, `13.211.73.244`, `3.105.95.184`

**Additonal IP addresses:**

**13.55.188.95, 3.105.212.249, 3.106.45.106**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

`13.236.220.84`, `13.211.73.244`, `3.105.95.184`

**Additonal IP addresses:**

**13.55.188.95, 3.105.212.249, 3.106.45.106**

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Asia Pacific \(Singapore\) - AWS

\(`cf.ap11.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

`3.0.9.102`,`18.140.39.70`, `18.139.147.53`

**Additonal IP addresses:**

**13.229.158.122, 18.140.228.217, 52.74.215.89**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

`3.0.9.102`, `18.140.39.70`, `18.139.147.53`

**Additonal IP addresses:**

**13.229.158.122, 18.140.228.217, 52.74.215.89**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

`3.0.9.102`, `18.140.39.70`, `18.139.147.53`

**Additonal IP addresses:**

**13.229.158.122, 18.140.228.217, 52.74.215.89**

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Asia Pacific \(Seoul\) - AWS

\(`cf.ap12.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

`3.35.255.45`, `3.35.106.215`, `3.35.215.12`

**Additonal IP addresses:**

**13.209.236.215, 43.201.194.105, 43.202.204.5**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

`3.35.255.45`, `3.35.106.215`, `3.35.215.12`

**Additonal IP addresses:**

**13.209.236.215, 43.201.194.105, 43.202.204.5**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

`3.35.255.45`, `3.35.106.215`, `3.35.215.12`

**Additonal IP addresses:**

**13.209.236.215, 43.201.194.105, 43.202.204.5**

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

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap20.hana.ondemand.com

</td>
<td valign="top">

`20.53.99.41`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap20.hana.ondemand.com

</td>
<td valign="top">

`20.53.99.41`

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

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Canada \(Montreal\) - AWS

\(`cf.ca10.hana.ondemand.com`\)

> ### Caution:  
> Additional IP addresses were added to this region.
> 
> **Action:**
> 
> If you restrict system access by *allowlisting IPs* in firewall rules, make sure you update your configuration as soon as possible.



</td>
<td valign="top" colspan="2">

connectivitynotification.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

`3.98.102.153`, `35.182.75.101`, `35.183.74.34`

**Additonal IP addresses:**

**15.157.88.166, 3.98.202.222, 52.60.210.33**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

`3.98.102.153`, `35.182.75.101`, `35.183.74.34`

**Additonal IP addresses:**

**15.157.88.166, 3.98.202.222, 52.60.210.33**

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

`3.98.102.153`, `35.182.75.101`, `35.183.74.34`

**Additonal IP addresses:**

**15.157.88.166, 3.98.202.222, 52.60.210.33**

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

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ch20.hana.ondemand.com

</td>
<td valign="top">

`20.208.56.83`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ch20.hana.ondemand.com

</td>
<td valign="top">

`20.208.56.83`

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
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.in30.hana.ondemand.com

</td>
<td valign="top">

`34.93.125.74`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.in30.hana.ondemand.com

</td>
<td valign="top">

`34.93.125.74`

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
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.cn40.platform.sapcloud.cn

</td>
<td valign="top">

`139.224.7.71`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.cn40.platform.sapcloud.cn

</td>
<td valign="top">

`139.224.7.71`

</td>
</tr>
<tr>
<td valign="top" colspan="4">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

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

**IP Address**

</td>
</tr>
<tr>
<td valign="top" colspan="4">

**ABAP Environment**

> ### Note:  
> To enable the full scenario for the SAP BTP ABAP environment, the DNS names below are needed *in addition* to the IPs of the Connectivity service mentioned above. If you can only configure allowlists for *IP addresses* in your firewall, please note that these addresses may change at any time and that you need to validate the values with a DNS service of your choice regularly.
> 
> For more information, see [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-for-abap-environment).



</td>
</tr>
<tr>
<td valign="top">

Europe \(Frankfurt\) - AWS

</td>
<td valign="top" colspan="2">

\*.abap.eu10.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

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
<td valign="top">

<dynamic\>

</td>
</tr>
<tr>
<td valign="top" colspan="4">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

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

**IP Address**

</td>
</tr>
<tr>
<td valign="top" colspan="4">

**Neo Environment**

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
<td valign="top">

`155.56.210.83`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.hana.ondemand.com

</td>
<td valign="top">

`155.56.210.43`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`157.133.206.143` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.eu2.hana.ondemand.com

</td>
<td valign="top">

`157.133.205.174` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.eu2.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.87.72` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.eu3.hana.ondemand.com

</td>
<td valign="top">

`130.214.87.76`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.eu3.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.181.204` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us1.hana.ondemand.com

</td>
<td valign="top">

`130.214.181.48` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us1.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.129.127` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us2.hana.ondemand.com

</td>
<td valign="top">

`130.214.129.140` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us2.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.32.144` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us3.hana.ondemand.com

</td>
<td valign="top">

`130.214.33.92` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us3.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.183.46` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.us4.hana.ondemand.com

</td>
<td valign="top">

`130.214.183.14` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.us4.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`157.133.97.47`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.ap1.hana.ondemand.com

</td>
<td valign="top">

`157.133.97.27` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.ap1.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`121.91.109.81`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cn1.platform.sapcloud.cn

</td>
<td valign="top">

`121.91.109.77`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cn1.platform.sapcloud.cn

</td>
<td valign="top">

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
<td valign="top">

`130.214.112.168` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.jp1.hana.ondemand.com

</td>
<td valign="top">

`130.214.112.212` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.jp1.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.174.201` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.ca1.hana.ondemand.com

</td>
<td valign="top">

`130.214.174.220` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.ca1.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.96.193` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.br1.hana.ondemand.com

</td>
<td valign="top">

`130.214.96.195` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.br1.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.80.206` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.ae1.hana.ondemand.com

</td>
<td valign="top">

`130.214.80.208` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.ae1.hana.ondemand.com

</td>
<td valign="top">

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
<td valign="top">

`130.214.209.241` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.sa1.hana.ondemand.com

</td>
<td valign="top">

`130.214.209.207` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.sa1.hana.ondemand.com

</td>
<td valign="top">

`130.214.209.191` 

</td>
</tr>
<tr>
<td valign="top" colspan="4">

Back to [Network](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__network)

Back to [Content](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__content)

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

**IP Address**

</td>
</tr>
<tr>
<td valign="top" colspan="4">

**Trial \(Cloud Foundry Environment\)**

> ### Note:  
> In the Cloud Foundry environment, IPs are controlled by the respective IaaS provider \(AWS, Azure, or Google Cloud\). IPs may change due to network updates on the provider side. Any planned changes will be announced several weeks before they take effect. See also [Regions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html "You can deploy applications in different regions. Each region represents a geographical location (for example, Europe, US East) where applications, data, or services are hosted.") :arrow_upper_right:.



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

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.eu10.hana.ondemand.com

</td>
<td valign="top">

`3.124.222.77`, `3.122.209.241`, `3.124.208.223`

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

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211` 

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.us10.hana.ondemand.com

</td>
<td valign="top">

`52.23.189.23`, `52.4.101.240`, `52.23.1.211`

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
</tr>
<tr>
<td valign="top" colspan="2">

connectivitycertsigning.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

connectivitytunnel.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

`20.184.61.122`

</td>
</tr>
<tr>
<td valign="top" colspan="4">

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

