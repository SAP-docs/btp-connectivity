<!-- loio0eb9851c41914d379feb138bf808a18f -->

# Update the Java VM

How to update the Java VM used by the Cloud Connector.

Sometimes you must update the Java VM used by the Cloud Connector, for example, because of expired TLS certificates contained in the JVM trust store, bug fixes, deprecated JVM versions, and so on.

-   If you make a replacement in the same directory, shut down the Cloud Connector, upgrade the JVM, and restart the Cloud Connector when you are done.
-   **If you change the installation directory** of the JVM, **follow the steps below** for your operating system.

Make sure that the JVM has been installed successfully.

> ### Note:  
> A Java Runtime Environment \(JRE\) is not sufficient. You must use a JDK or SAP JVM.



## Microsoft Windows OS

1.  Make sure that the current user has administrative privileges.
2.  Shutdown the Cloud Connector \(for example, by stopping the corresponding Windows service or by double-clicking the *Stop SAP Cloud Connector* shortcut\).
3.  Open the *registry editor* \(regedit32\) and locate the following registry entry: `HKEY_LOCAL_MACHINE\SOFTWARE\SAP\Cloud Connector`.
4.  Change the value `JavaHome` to reflect the installation directory of the new SAP JVM or JDK.

    > ### Note:  
    > The *bin* subdirectory must not be part of the `JavaHome` value.

    If the `JavaHome` value does not yet exist, create it here with a "String Value" \(REG\_SZ\) and specify the full path of the Java installation directory, for example: `C:\Program Files\sapjvm`.

5.  Close the registry editor and restart the Cloud Connector.



## Linux OS

1.  Open a shell command line prompt as root user.
2.  In this shell, set the environment variable `JAVA_HOME`, pointing to the installation directory of the new SAP JVM or JDK, for example:
    -   in csh/tcsh:

        ```
        setenv JAVA_HOME /opt/sap/sapjvm_8
        ```

    -   in sh/bash/dash/zsh:

        ```
        export JAVA_HOME=/opt/sap/sapjvm_8
        ```


3.  Execute the command

    ```
    System V init distributions: service scc_daemon stop
    systemd distributions: systemctl stop scc_daemon
    ```

4.  Execute the command

    ```
    System V init distributions: /opt/sap/scc/daemon.sh reinstall
    systemd distributions: /opt/sap/scc/daemon.sh reinstallSystemd
    ```

5.  Execute the command

    ```
    System V init distributions: service scc_daemon start
    systemd distributions: systemctl start scc_daemon
    ```




## Both Operating Systems

> ### Note:  
> -   If you use your own CA certificates for the e-mail configuration \(see [Alerting](alerting-87bffd9.md)\) or for LDAP \(see [Use LDAP for User Administration](use-ldap-for-user-administration-120ceec.md)\), you must reimport them to the JVM trust store as described there.
> -   Make sure the selected cipher suites are accepted by the JVM you are about to install. If in doubt, revert to the default selection prior to changing the JVM.

> ### Tip:  
> If own CA certificates for e-mail alerting or the LDAP user authorization setup are required, but these certificates are not necessary for other Java processes using the very same JVM installation, consider storing these custom CA certificates in the respective trust stores of the Cloud Connector instead of importing them into the JVM trust store. In this case, you do not need to reimport them into the JVM trust store after a JVM update, and you will benefit from these certificates being stored in Cloud Connector configuration backups.

After executing the above steps, the Cloud Connector should be running again and should have picked up the new Java version during startup. You can verify this by logging in to the Cloud Connector with your favorite browser, opening the *About* dialogue and checking that the field *<Java Details\>* shows the version number and build date of the new Java VM. After you verified that the new JVM is indeed used by the Cloud Connector, delete or uninstall the old JVM.

