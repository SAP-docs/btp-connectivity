<!-- loio3859e50f652e4a4b9c66a6a572ced7a4 -->

# Configure Named Cloud Connector Users

Set up LDAP-based user management for the Cloud Connector.



<a name="loio3859e50f652e4a4b9c66a6a572ced7a4__section_xkx_wqj_hgb"/>

## LDAP-Based User Management

We recommend that you configure LDAP-based user management for the Cloud Connector to allow only named administrator users to log on to the administration UI.

This guarantees traceability of the Cloud Connector configuration changes via the Cloud Connector audit log. If you use the default and built-in `Administrator` user, you cannot identify the actual person or persons who perform configuration changes. Also, you will not be able to use different types of user groups.



<a name="loio3859e50f652e4a4b9c66a6a572ced7a4__section_xtb_xqj_hgb"/>

## Configuration

If you have an LDAP server in your landscape, you can configure the Cloud Connector to authenticate Cloud Connector users against the LDAP server.

For more information about the supported roles for LDAP, see [Use LDAP for User Administration](use-ldap-for-user-administration-120ceec.md).

Once configured, the default Cloud Connector `Administrator` user becomes inactive and can no longer be used to log on to the Cloud Connector.

**Related Information**  


[Use LDAP for User Administration](use-ldap-for-user-administration-120ceec.md "You can use LDAP (Lightweight Directory Access Protocol) to manage Cloud Connector users and authentication.")

[Logon to the Cloud Connector via Client Certificate](logon-to-the-cloud-connector-via-client-certificate-daa547f.md "Switch from default logon to client certificate logon to access the Cloud Connector.")

