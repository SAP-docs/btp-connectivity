<!-- loio6c3eec1350e04d4fab801263e26ad939 -->

# Installation on Apple macOS

Installing the Cloud Connector on an Apple macOS operating system.



## Prerequisites

> ### Note:  
> Apple macOS is not supported for productive scenarios. The developer version described below must not be used as productive version.

> ### Caution:  
> There are two different Cloud Connector portable versions available for running on Apple macOS with native support either for Apple M series CPUs based on the *aarch64* architecture, or with native support for INTEL x86 64-bit CPUs based on the *x64* architecture. Make sure you download and use the Cloud Connector version in combination with a JVM version, which both match your used hardware CPU architecture.

-   You have one of the supported 64-bit operating systems. For more information, see [Product Availability Matrix](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).
-   The supported platforms are *aarch64* and *x64*, represented below by the variable *<platform\>*.
-   You have downloaded the `tar.gz` archive for the developer use case on Apple macOS from [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud).
-   A supported Java version must be installed. For more information, see [JDKs](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__jdk).

    If you are running Apple macOS on an INTEL x86 64-bit CPU and you want to use SAP JVM, you can download it from the [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud) page.

    Alternatively supported SapMachine JDK versions for macOS on aarch64 and x64 processor architectures can be downloaded from the [SapMachine](https://sapmachine.io) homepage.

-   Environment variable *<JAVA\_HOME\>* must be set to the Java installation directory so that the `bin` subdirectory can be found. Alternatively, you can add the Java installation's `bin` subdirectory to the *<PATH\>* variable.



## Procedure

1.  Extract the `tar.gz` file to an arbitrary directory on your local file system using the following command:

    ```
    tar -xzof sapcc-<version>-macosx-<platform>.tar.gz 
    ```

2.  Go to this directory and start Cloud Connector using the `go.sh` script.

3.  Continue with the **Next Steps** section.

    > ### Note:  
    > The Cloud connector is not started as a daemon, and therefore will not automatically start after a reboot of your system. Also, the macOS version of the Cloud Connector does not support the automatic upgrade procedure.




## Next Steps

1.  Open a browser and enter: `https://<hostname>:8443`. *<hostname\>* is the host name of the machine on which you installed the Cloud Connector.

    If you access the Cloud Connector locally from the same machine, you can simply enter `localhost`.

2.  Continue with the initial configuration of the Cloud Connector, see [Initial Configuration](initial-configuration-db9170a.md).

**Related Information**  


[Recommendations for Secure Setup](recommendations-for-secure-setup-e7ea82a.md "For the Connectivity service and the Cloud Connector, you should apply the following guidelines to guarantee the highest level of security for these components.")

