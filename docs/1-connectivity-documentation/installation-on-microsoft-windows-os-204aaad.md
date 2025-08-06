<!-- loio204aaad4270245f3baa0c57c8ab1dd60 -->

# Installation on Microsoft Windows OS

Installing the Cloud Connector on a Microsoft Windows operating system.



<a name="loio204aaad4270245f3baa0c57c8ab1dd60__section_ivf_xb4_ggb"/>

## Context

You can choose between a simple `portable` variant of the Cloud Connector and the MSI-based `installer`. The `installer` is the generally recommended version that you can use for both developer and productive scenarios. It lets you, for example, register the Cloud Connector as a Windows service and this way automatically start it after machine reboot.

> ### Tip:  
> If you are a developer, you might want to use the `portable` variant as you can run the Cloud Connector after a simple unzip \(archive extraction\). You might want to use it also if you cannot perform a full installation due to lack of permissions, or if you want to use multiple versions of the Cloud Connector simultaneously on the same machine.



<a name="loio204aaad4270245f3baa0c57c8ab1dd60__section_lg3_xb4_ggb"/>

## Prerequisites

-   You have one of the supported 64-bit operating systems. For more information, see [Product Availability Matrix](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).
-   You have downloaded either the `portable` variant as ZIP archive for Windows, or the MSI `installer` from the [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud) page.
-   You must install Microsoft Visual Studio C++ 2019 runtime libraries \(download `vc_redist.x64.exe`\).

    For more information, see [Microsoft Visual C++ Redistributable latest supported downloads](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170).

-   A supported Java version must be installed. For more information, see [JDKs](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__jdk).

    If you want to use SAP JVM, you can download it from the [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud) page.

    Alternatively supported SapMachine JDK versions can be downloaded from the SapMachine homepage \(*https://sapmachine.io*\).

-   When using the `portable` variant, the environment variable *<JAVA\_HOME\>* must be set to the Java installation directory, so that the `bin` subdirectory can be found. Alternatively, you can add the relevant `bin` subdirectory to the *<PATH\>* variable.



## Portable Scenario

1.  Extract the *<sapcc-<version\>-windows-x64.zip\>* ZIP file to an arbitrary directory on your local file system.
2.  Set the environment variable JAVA\_HOME to the installation directory of the JDK that you want to use to run the Cloud Connector. Alternatively, you can add the `bin` subdirectory of the JDK installation directory to the PATH﻿ environment variable.
3.  Go to the Cloud Connector installation directory and start it using the `go.bat` batch file.
4.  Continue with the `Next Steps` section.

> ### Note:  
> The Cloud Connector is not started as a service when using the portable variant, and hence will not automatically start after a reboot of your system. Also, the portable version does not support the automatic upgrade procedure.sapcc-<version\>-windows-x64.msi



## Installer Scenario

1.  Start the *<\>*sapcc- installer by double-clicking it.
2.  The installer informs you that you are now guided through the installation process. Choose *Next\>*.
3.  Navigate to the desired installation directory for your Cloud Connector and choose *Next\>*. When doing the installation in the context of an upgrade, make sure you choose the previous installation directory again.
4.  You can choose the port on which the administration UI is reachable. Either leave the default `8443` or choose a different port if needed. Then, choose *Next\>*.
5.  Select the JDK to be used for running the Cloud Connector. The installer displays a list of all usable JDKs that are installed on your machine. If the needed JDK is not listed in the drop-down box \(for example, if it's an SAP JVM that is not registered in the Windows registry upon installation\), you can browse to its installation directory and select it. We recommend that you use an up-to-date Java **8** installation to run the Cloud Connector.
6.  Decide whether the Cloud Connector should be started immediately after finishing the setup. Then, choose *Next\>*.
7.  To start the installation, press the *Next\>* button again.
8.  After successful installation, choose *Close*.
9.  Continue with the `Next Steps` section.

> ### Note:  
> The Cloud Connector is started as a Windows service in the productive use case. Therefore, installation requires administration permissions. After installation, manage this service under *Control Panel* \> *Administrative Tools* \> *Services*. The service name is `Cloud Connector` \(formerly named `Cloud Connector 2.0`\). Make sure the service is executed with a user that has limited privileges. Typically, privileges allowed for service users are defined by your company policy. Adjust the folder and file permissions to be manageable by only this user and system administrators.

> ### Note:  
> Using the SAP Cryptographic Library requires the environment variable SECUDIR to be set.

On Windows, the file `scc_service.log` is created and used by the Microsoft MSI installer \(during Cloud Connector installation\), and by the `scchost.exe` executable, which registers and runs the Windows service if you install the Cloud Connector as a Windows background job.

This log file is only needed if a problem occurs during Cloud Connector installation, or during creation and start of the Windows service, in which the Cloud Connector is running. You can find the file in the ***log*** folder of your Cloud Connector installation directory.



<a name="loio204aaad4270245f3baa0c57c8ab1dd60__section_e5n_tpj_rfb"/>

## Starting the Cloud Connector

After installation, the Cloud Connector is registered as a Windows service that is configured to be started automatically after a system reboot. You can start and stop the service via shortcuts on the desktop \("Start Cloud Connector" and "Stop Cloud Connector"\), or by using the `Windows Services` manager and look for the service `SAP Cloud Connector`.

Access the Cloud Connector administration UI at *https://localhost:<port\>*, where the default port is `8443` \(but this port might have been modified during the installation\).



## Next Steps

1.  Open a browser and enter: `https://<hostname>:8443`. *<hostname\>* is the host name of the machine on which you have installed the Cloud Connector. If you access the Cloud Connector locally from the same machine, you can simply enter `localhost`.
2.  Continue with the initial configuration of the Cloud Connector, see [Initial Configuration](initial-configuration-db9170a.md).



## Related Information

[Recommendations for Secure Setup](recommendations-for-secure-setup-e7ea82a.md)

