<!-- loio3ab2b1347bbd46428fb65e4784a75e20 -->

# Deploy the Application

Deploy your Cloud Foundry application to call an ABAP function module via RFC.



<a name="loio3ab2b1347bbd46428fb65e4784a75e20__section_ist_n2r_dgb"/>

## Prerequisites

You have created and bound the required service instances, see [Create and Bind Service Instances](create-and-bind-service-instances-6dd5e26.md).



<a name="loio3ab2b1347bbd46428fb65e4784a75e20__section_d45_1fr_dgb"/>

## Procedure

1.  To deploy your Web application, you can use the following two alternative procedures:
    -   [Deploying from the Eclipse IDE](https://www.eclipse.org/cft/documentation/projectPageLink/CFTProjectPagedocumentation.html)

    -   Deploying from the CLI, see [Developing Java in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a3f90069d6cd41da82f34a6123d82ce6.html "Find selected information for Java development on SAP BTP, Cloud Foundry and references to more detailed sources.") :arrow_upper_right:


2.  In the following, we publish it with the CLI.
3.  To do this, create a `manifest.yml` file. The key parameter is `USE_JCO: true`, which must be set to include JCo into the buildpack during deployment.

    > ### Note:  
    > JCo supports the usage of X.509 secrets for communication with the Destination/Connectivity service. If you want to use it, you must specify the binding accordingly.
    > 
    > For more information, see [Binding Parameters of SAP Authorization and Trust Management Service](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/3240307e513e4bceaa75e4134d337fab.html).

    **manifest.yml**

    > ### Sample Code:  
    > ```
    > 
    > ---
    > applications:
    > 
    > - name: jco-demo-p1234
    >   buildpacks:
    >   - sap_java_buildpack
    >   env:
    >     USE_JCO: true
    >     # This is necessary only if more than one instance is bound
    >     xsuaa_connectivity_instance_name: "xsuaa_jco"
    >     connectivity_instance_name: "connectivity_jco"
    >     destination_instance_name: "destination_jco"
    >   services:
    >     - xsuaa_jco
    >     - connectivity_jco
    >     - destination_jco
    > 
    > ```

    > ### Caution:  
    > The client libraries \(java-security, spring-xsuaa, and container security api for node.js as of version 3.0.6\) have been updated. When using these libraries, setting the parameter `SAP_JWT_TRUST_ACL` has become obsolete. This update comes with a change regarding scopes:
    > 
    > -   For a business application A calling an application B, it is now mandatory that application B grants at least one scope to the calling business application A.
    > -   Business application A must accept these granted scopes or authorities as part of the application security descriptor.
    > 
    > You can grant scopes using the `xs-security.json` file.
    > 
    > For more information, see [Application Security Descriptor Configuration Syntax](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.") :arrow_upper_right:, specifically the sections *Referencing the Application* and *Authorities*.

    > ### Note:  
    > If you have more than one instance of those three services bound to your application, you must specify which one JCo should use with the respective env parameters:
    > 
    > -   `xsuaa_connectivity_instance_name`
    > -   `connectivity_instance_name`
    > -   `destination_instance_name`.

4.  In Eclipse, right-click on the project and navigate to *Export* \> *WAR file*.
5.  Choose a destination by pressing the *Browse...* button next to the `manifest.yml` you created before, for example as `jcodemo.war`.
6.  Leave the other default settings unchanged and choose *Finish* to export the WAR file.
7.  Perform a CLI login via `cf login -a api.cf.eu10.hana.ondemand.com -u <your_email_address>` \(password, org and space are prompted after a successful login\).
8.  Push the application with `cf push -f manifest.yml -p jcodemo.war`.
9.  Now, the application should be deployed successfully.



<a name="loio3ab2b1347bbd46428fb65e4784a75e20__section_mk3_bfr_dgb"/>

## Next Steps

-   [Configure Roles and Trust](configure-roles-and-trust-a6ce7e7.md)
-   [Set Up an Application Router](set-up-an-application-router-f9f8eb2.md)
-   [Configure the RFC Destination](configure-the-rfc-destination-cfd3fea.md)
-   [Monitoring Your Web Application](monitoring-your-web-application-9bd8f7d.md) \(Optional\)

