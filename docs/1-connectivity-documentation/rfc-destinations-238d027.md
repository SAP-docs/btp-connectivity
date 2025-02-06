<!-- loio238d027c154541f597201a0002713c86 -->

# RFC Destinations



RFC destinations provide the configuration required for communication with an on-premise ABAP system via Remote Function Call. The RFC destination data is used by the Java Connector \(JCo\) version that is available within SAP BTP to establish and manage the connection.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loio238d027c154541f597201a0002713c86__section_N10024_N10011_N10001"/>

## RFC Destination Properties

The RFC destination specific configuration in SAP BTP consists of properties arranged in groups, as described below. The supported set of properties is a subset of the standard JCo properties in arbitrary environments. The configuration data is divided into the following groups:

-   [User Logon Properties](user-logon-properties-8b1e1c3.md)
-   [Pooling Configuration](pooling-configuration-7add680.md)
-   [Repository Configuration](repository-configuration-4c4b83b.md)
-   [Target System Configuration](target-system-configuration-ab6eac9.md)
-   [Parameters Influencing Communication Behavior](parameters-influencing-communication-behavior-cce126a.md)

The minimal configuration contains user logon properties and information identifying the target host. This means you must provide at least a set of properties containing this information.



## Example

```ini

Name=SalesSystem
Type=RFC
jco.client.client=000
jco.client.lang=EN
jco.client.user=consultant
jco.client.passwd=<password>
jco.client.ashost=sales-system.cloud
jco.client.sysnr=42
jco.destination.pool_capacity=5
jco.destination.peak_limit=10
```

**Related Information**  


[Invoking ABAP Function Modules via RFC](invoking-abap-function-modules-via-rfc-fa4adc9.md "Call a remote-enabled function module in an on-premise or cloud ABAP server from your application, using the RFC protocol.")

