<!-- loio7e8ebc9554144a26b5a634e2e925bd72 -->

# System Requirements

Additional system requirements for installing and running the Cloud Connector.



## Hardware Requirements

For an up-to-date list of hardware requirements, see [Hardware](prerequisites-e23f776.md#loioe23f776e4d594fdbaeeb1196d47bbcc0__hardware).



## Software Requirements

For an up-to-date list with detailed Cloud Connector version information, see [Prerequisites](prerequisites-e23f776.md).



## Supported Browsers

The browsers that can be used for the Cloud Connector administration UI are the ones supported by SAP UI5. Currently, these are the following:

-   Microsoft Edge \(latest version\)
-   Mozilla Firefox \(latest version and latest Extended Support Release \(ESR\)\)
-   Safari 5.1 and higher \(latest version\)
-   Google Chrome \(latest versions\)

For an up-to-date list of the supported SAP UI5 browsers, see:[Browser and Platform Support](https://sapui5.hana.ondemand.com/#/topic/74b59efa0eef48988d3b716bd0ecc933).



## Minimum Disk Space for Download and Installation

The minimum free disk space required to download and install a new Cloud Connector server is as follows:

-   Size of downloaded Cloud Connector installation file \(ZIP, TAR, MSI files\): 120 MB
-   Newly installed Cloud Connector server: 235 MB
-   Total: 355 MB as a minimum



## Additional Disk Space for Log and Configuration Files

The Cloud Connector writes configuration files, audit log files and trace files at runtime. We recommend that you reserve between 1 and 20 GB of disk space for those files.

Trace and log files are written to `<scc_dir>/log/` within the Cloud Connector `root` directory. The `scc_core.trc` file contains traces in general, communication payload traces are stored in `tunnel_traffic_*.trc` and `snc_traffic_*.trc`. These files may be used by SAP Support to analyze potential issues. The default trace level is `Information`, where the amount of written data is generally only a few KB per day. You can turn off these traces to save disk space. However, we recommend that you don't turn off this trace completely, but that you leave it at the default settings, to allow root cause analysis if an issue occurs. If you set the trace level to `All`, the amount of data can easily reach the range of several GB per day. Use trace level `All` only to analyze a specific issue. *Tunnel Traffic Trace* and *ABAP Cloud SNC Traffic Trace*, however, should normally be turned off, and used only for analysis by SAP Support.

> ### Note:  
> From an operations perspective, we recommend that you back up or delete written trace files regularly in order to clean up the used disk space.

Audit log files are written to `/log/audit/<subaccount-name>/audit-log_<subaccount-name>_<date>.csv` within the Cloud Connector root directory. By default, only security-related events are written in the audit log. You can change the audit log level using the administration UI, as described in [Manage Audit Logs](manage-audit-logs-2264c70.md).

To be compliant with the regulatory requirements of your organization and the regional laws, the audit log files must be persisted for a certain period of time for traceability purposes. Therefore, we recommend that you back up the audit log files regularly from the Cloud Connector file system and keep the backup for the length of time required.

**Related Information**  


[Prerequisites](prerequisites-e23f776.md "Prerequisites for successful installation of the Cloud Connector.")

