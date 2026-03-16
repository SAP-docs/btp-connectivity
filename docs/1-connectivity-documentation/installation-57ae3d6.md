<!-- loio57ae3d62f63440f7952e57bfcef948d3 -->

# Installation

Choose a procedure to install the Cloud Connector on your operating system.



<a name="loio57ae3d62f63440f7952e57bfcef948d3__versions"/>

## Portable Version vs. Installer Version

On **Microsoft Windows** and **Linux**, two installation variants are available: a `portable` version and an `installer` version. On **Apple macOS**, only the `portable` version is available.

-   `Portable` version: can be installed easily, by extracting a compressed archive into an empty directory. It does not require administrator or root privileges for the installation, and you can run multiple instances on the same host.

    Restrictions:

    -   You cannot run it in the background as a Windows Service or Linux daemon \(with automatic start capabilities at boot time\).
    -   The portable version does not support an automatic upgrade procedure. To update a portable installation, you must delete the current one, extract the new version, and then re-do the configuration.
    -   Portable versions are meant for non-productive scenarios only.
    -   The environment variable `JAVA_HOME` is relevant when starting the instance, and therefore must be set properly.

-   `Installer` version: requires administrator or root permissions for the installation and can be set up to run as a Windows service or Linux daemon in the background. You can upgrade it easily, retaining all the configuration and customizing.

    > ### Note:  
    > We strongly recommend that you use this variant for a productive setup.


> ### Caution:  
> Cloud Connector is based on Tomcat.
> 
> Tomcat is a well-known and well-documented server, whose configuration can be adapted to one's own needs. However, we strongly recommend that you **do not modify** its configuration files like `conf\server.xml` with a text editor, because the Cloud Connector is making assumptions about the content of those files.
> 
> If you still want to do custom modifications, you do so at your own risk. In this case, we can no longer guarantee that the Cloud Connector keeps working as expected. For any issues that can be traced back to such changes, we cannot provide support, in particular, if such changes cause trouble during upgrade to a newer version.



<a name="loio57ae3d62f63440f7952e57bfcef948d3__prereq"/>

## Prerequisites

-   There are some general prerequisites you must fulfill to successfully install the Cloud Connector, see [Prerequisites](prerequisites-e23f776.md).
-   For OS-specific requirements and procedures, see section **Tasks** below.



<a name="loio57ae3d62f63440f7952e57bfcef948d3__tasks"/>

## Tasks

-   [Installation on Microsoft Windows OS](installation-on-microsoft-windows-os-204aaad.md)
-   [Installation on Linux OS](installation-on-linux-os-f069840.md)
-   [Installation on Apple macOS](installation-on-apple-macos-6c3eec1.md)

**Related Information**  


[Sizing Recommendations](sizing-recommendations-f008494.md "When installing a Cloud Connector, the first thing you need to decide is the sizing of the installation.")

[Recommendations for Secure Setup](recommendations-for-secure-setup-e7ea82a.md "For the Connectivity service and the Cloud Connector, you should apply the following guidelines to guarantee the highest level of security for these components.")

[Uninstallation](uninstallation-d53395c.md "Uninstall an installer version or portable version of the Cloud Connector.")

