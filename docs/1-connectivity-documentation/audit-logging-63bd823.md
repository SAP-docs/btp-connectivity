<!-- loio63bd823990cb4d26a098869fe3a0a8a7 -->

# Audit Logging

Audit log data can alert Cloud Connector administrators to unusual or suspicious network and system behavior.

Additionally, the audit log data can provide auditors with information required to validate security policy enforcement and proper segregation of duties. IT staff can use the audit log data for root-cause analysis following a security incident.

The Cloud Connector includes an auditor tool for viewing and managing audit log information about access between the cloud and the Cloud Connector, as well as for tracking of configuration changes done in the Cloud Connector. The written audit log files are digitally signed by the Cloud Connector so that their integrity can be checked, see [Manage Audit Logs](manage-audit-logs-2264c70.md).

> ### Note:  
> We recommend that you permanently switch on Cloud Connector audit logging in productive scenarios.
> 
> -   Under normal circumstances, set the logging level to `Security` \(the default configuration value\).
> -   If legal requirements or company policies dictate it, set the logging level to `All`. This lets you use the log files to, for example, detect attacks of a malicious cloud application that tries to access on-premises services without permission, or in a forensic analysis of a security incident.

We also recommend that you regularly copy the audit log files of the Cloud Connector to an external persistent storage according to your local regulations. The audit log files can be found in the Cloud Connector root directory `/log/audit/<subaccount-name>/audit-log_<timestamp>.csv`.

