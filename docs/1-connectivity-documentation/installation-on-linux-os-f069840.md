<!-- loiof069840fa34c4196a5858be33a2734ea -->

# Installation on Linux OS

Installing the Cloud Connector on a Linux operating system.



## Context

You can choose between a simple `portable` variant of the Cloud Connector and the RPM-based `installer`. The `installer` is the generally recommended version that you can use for both the developer and the productive scenario. It registers, for example, the Cloud Connector as a daemon service and this way automatically starts it after machine reboot.

> ### Tip:  
> If you are a developer, you might want to use the `portable` variant as you can run the Cloud Connector after a simple "`tar -xzof`" execution. You also might want to use it if you cannot perform a full installation due to missing permissions for the operating system, or if you want to use multiple versions of the Cloud Connector simultaneously on the same machine.



<a name="loiof069840fa34c4196a5858be33a2734ea__section_ukf_cls_ggb"/>

## Prerequisites

-   You have one of the supported 64-bit operating systems. For more information, see [Product Availability Matrix](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).
-   The supported platforms are `x64` and `ppc64le`, represented below by the variable `<platform>`. Variable `<arch>` is `x86_64` or `ppc64le` respectively.
-   You have downloaded either the `portable` variant as `tar.gz` archive for Linux or the RPM `installer` contained in the ZIP for Linux, from [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud).
-   A supported Java version must be installed. For more information, see [JDKs](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__jdk).

    If you want to use SAP JVM, you can download it from the [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud) page.

    Use the following command to install it:

    ```
    rpm -i sapjvm-<version>-linux-<platform>.rpm
    ```

    If you want to check the JVM version installed on your system, use the following command:

    ```
    rpm -qa | grep jvm
    ```

    When installing it using the RPM package, the Cloud Connector will detect it and use it for its runtime.

    Alternatively supported SapMachine JDK versions can be downloaded from the SapMachine homepage \(*https://sapmachine.io*\).

-   When using the `tar.gz` archive, the environment variable *<JAVA\_HOME\>* must be set to the Java installation directory, so that the `bin` subdirectory can be found. Alternatively, you can add the Java installation's `bin` subdirectory to the *<PATH\>* variable.



## Portable Scenario

1.  Extract the *tar.gz* file to an arbitrary directory on your local file system using the following command:

    ```
    tar -xzof sapcc-<version>-linux-<platform>.tar.gz 
    ```

    > ### Note:  
    > If you use the parameter "o", the extracted files are assigned to the user ID and the group ID of the user who has unpacked the archive. This is the default behavior for users other than the `root` user.

2.  Go to this directory and start the Cloud Connector using the `go.sh` script.
3.  Continue with the `Next Steps` section.

> ### Note:  
> In this case, the Cloud Connector is not started as a daemon, and therefore will not automatically start after a reboot of your system. Also, the `portable` version does not support the automatic upgrade procedure.



## Installer Scenario

1.  Extract the *sapcc-<version\>-linux-<platform\>.zip* archive to an arbitrary directory by using the following the command:

    ```
    unzip sapcc-<version>-linux-<platform>.zip
    ```

2.  Go to this directory and install the extracted RPM using the following command. You can perform this step only as a `root` user.

    ```
    rpm -i com.sap.scc-ui-<version>.<arch>.rpm 
    ```

3.  Continue with the `Next Steps` section.

In the productive case, the Cloud Connector is started as a daemon. If you need to manage the daemon process, execute:

```
System V init distributions: service scc_daemon stop|restart|start|status
systemd distributions: systemctl stop|restart|start|status scc_daemon
```

> ### Caution:  
> When adjusting the Cloud Connector installation \(for example, restoring a backup\), make sure the RPM package management is synchronized with such changes. If you simply replace files that do not fit to the information stored in the package management, lifecycle operations \(such as upgrade or uninstallation\) might fail with errors. Also, the Cloud Connector might get into unrecoverable state.
> 
> **Example**: After a file system restore, the system files represent Cloud Connector 2.3.0 but the RPM package management "believes" that version 2.4.3 is installed. In this case, commands like `rpm -U` and `rpm -e` do not work as expected. Furthermore, avoid using the `--force` parameter as it may lead to an unpredictable state with two versions being installed concurrently, which is not supported.

**Extending the Daemon**

When using SNC for encrypting RFC communication, it might be required to provide some settings, for example, environment variables that must be visible for the Cloud Connector process. To achieve this, you must store a file named `scc_daemon_extension.sh` in the installation directory of the Cloud Connector \(`/opt/sap/scc`\), containing all commands needed for initialization without a shebang.

Example \(SAP Cryptographic Library requires SECUDIR to be set\):

> ### Sample Code:  
> ```
> export SECUDIR=/path/to/pse_directory
> ```

To activate it, you must reinstall the daemon.

> ### Note:  
> Make sure JAVA\_HOME is set to the JVM used \(in the shell where the command is executed\).

Execute the following command:

```
System V init distributions: /opt/sap/scc/daemon.sh reinstall
systemd distributions: /opt/sap/scc/daemon.sh reinstallSystemd
```

The daemon extension will survive Cloud Connector version updates.



<a name="loiof069840fa34c4196a5858be33a2734ea__section_lxh_fqj_rfb"/>

## Starting the Cloud Connector

After installation via RPM manager, the Cloud Connector process is started automatically and registered as a daemon process, which ensures the automatic restart of the Cloud Connector after a system reboot.

To start, stop, or restart the process explicitly, open a command shell and use the following commands, which require `root` permissions:

```
System V init distributions: service scc_daemon start|stop|restart
systemd distributions: systemctl start|stop|restart scc_daemon 
```



## Next Steps

1.  Open a browser and enter: `https://<hostname>:8443`. *<hostname\>* is the host name of the machine on which you installed the Cloud Connector.

    If you access the Cloud Connector locally from the same machine, you can simply enter `localhost`.

2.  Continue with the initial configuration of the Cloud Connector, see [Initial Configuration](initial-configuration-db9170a.md).

**Related Information**  


[Recommendations for Secure Setup](recommendations-for-secure-setup-e7ea82a.md "For the Connectivity service and the Cloud Connector, you should apply the following guidelines to guarantee the highest level of security for these components.")

