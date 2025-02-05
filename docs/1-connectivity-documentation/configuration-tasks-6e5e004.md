<!-- loio6e5e004b6553403486a03da53bfcaf4e -->

# Configuration Tasks

Perform these steps to set up user propagation between S/4HANA Cloud and the SAP BTP Cloud Foundry environment.



<a name="loio6e5e004b6553403486a03da53bfcaf4e__steps_s4"/>

## Tasks

1.  [Configure Single Sign-On between S/4HANA Cloud and the Cloud Foundry Organization on SAP BTP](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__sso)
2.  [Configure OAuth Communication](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__oauth)
3.  [Configure Communication Settings in S/4HANA Cloud](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__s4)
4.  [Configure Communication Settings in SAP BTP](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__scp)
5.  [Consume the Destination and Execute the Scenario](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__consume)



<a name="loio6e5e004b6553403486a03da53bfcaf4e__sso"/>

## Configure Single Sign-On between S/4HANA Cloud and the Cloud Foundry Organization on SAP BTP

To configure SSO with S/4HANA you must configure trust between the S/4HANA IAS tenant and theCloud Foundry organization, see [Manually Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7c6aa87459764b179aeccadccd4f91f3.html#loio7c6aa87459764b179aeccadccd4f91f3 "Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. Exchange SAML metadata to establish trust with the SAP Cloud Identity Services tenant and then register your subaccount with the tenant. To complete federation, maintain the federation attributes of the user groups.") :arrow_upper_right:.



<a name="loio6e5e004b6553403486a03da53bfcaf4e__oauth"/>

## Configure OAuth Communication

Download the certificate from your Cloud Foundry subaccount on SAP BTP.

1.  From the SAP BTP cockpit, choose *Cloud Foundry environment* \> *your global account*.
2.  Choose or create a subaccount, and from your left-side subaccount menu, go to *Connectivity* \> *Destinations*.
3.  Press the *Download Trust* button.

![](images/CS_CF_S4C_OAuth_DownloadTrust_da18af4.png)

Back to [Tasks](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__steps_s4) 



<a name="loio6e5e004b6553403486a03da53bfcaf4e__s4"/>

## Configure Communication Settings in S/4HANA Cloud

1.  **Create a Communication User**
    1.  In your S/4HANA Cloud launchpad, choose the application *Maintain Communication Users*.

        ![](images/CS_CF_S4C_Comm_User_1_d11ad71.png)

    2.  From the *User List* view, create a new user.
    3.  Set *<User Name\>*, *<Password\>* and *<Description\>*.
    4.  Copy this password, you will need it in a later step.
    5.  Press the *Save* on the bottom of the screen.

        ![](images/CS_CF_S4C_Comm_User_2_ffd9f8c.png)

    6.  Close the *Communication Users* application.

2.  **Set up a Communication System for OAuth**
    1.  From the launchpad, choose the application *Communication Systems*.

        ![](images/CS_CF_S4C_Comm_System_1_81f4b43.png)

    2.  From the list view, select *New*.
    3.  A popup window appears. Enter the *<System ID\>* and the *<System Name\>*, then choose *Create*.

        ![](images/CS_CF_S4C_Comm_System_2_ebcb49d.png)

    4.  Enter the host name. This is your Cloud Foundry region, for example: `cf.eu10.hana.ondemand.com` for Europe \(Frankfurt\).

        > ### Note:  
        > For the complete list of standard regions, see [Regions](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html "You can deploy applications in different regions. Each region represents a geographical location (for example, Europe, US East) where applications, data, or services are hosted.") :arrow_upper_right:.

        ![](images/CS_CF_S4C_Comm_System_3_09ac1fd.png)

    5.  Enable the OAuth Identity Provider.

        ![](images/CS_CF_S4C_Comm_System_4_cbd4aad.png)

    6.  Upload the subaccount certificate that you have downloaded before from the SAP BTP cockpit.

        ![](images/CS_CF_S4C_Comm_System_5_ec6d60a.png)

    7.  From *<Signing Certificate Subject\>*, copy the ***CN*** value \(for example: ***cfapps.sap.hana.ondemand.com/a352a17b-<...\>***\) and paste it in the field *<Provider Name\>*.
    8.  Add the *Communication User* you have created in the previous step.

        ![](images/CS_CF_S4C_Comm_System_6_ab295aa.png)

    9.  Save your settings and go back to the launchpad.

3.  **Create a Communication Arrangement**
    1.  Start the *Communication Arrangements* application.

        ![](images/CS_CF_S4C_Comm_Arr_1_f533983.png)

    2.  From the list view, select *New*.
    3.  In the popup, choose a scenario. For our example, we use `SAP_COM_0008`. Set the arrangement name, for example `SAP_COM_0008_MY_TEST`.
    4.  In the *Common Data* section of the configuration screen, select the *<Communication System\>* that you have created in the step before. The communication user is added automatically in the *Inbound Communication* section, and the *<Authentication Method\>* is set to ***OAuth 2.0***.

        ![](images/CS_CF_S4C_Comm_Arr_2_736581b.png)

    5.  In the *Outbound Services* section, go to *Launch SAP Web IDE* and uncheck the *Active* checkbox of the field *<Service Status\>*.

        ![](images/CS_CF_S4C_Comm_Arr_3_cd89f3f.png)

    6.  Save your settings and go back to the launchpad.


Back to [Tasks](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__steps_s4) 



<a name="loio6e5e004b6553403486a03da53bfcaf4e__scp"/>

## Configure Communication Settings in SAP BTP

1.  From the SAP BTP cockpit, choose *Cloud Foundry environment* \> *your global account*.
2.  Choose your subaccount, and from the left-side subaccount menu, go to *Connectivity* \> *Destinations*.
3.  Press the *New Destination* button.
4.  Enter the following parameters for your destination:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `Name`
    
    </td>
    <td valign="top">
    
    Enter a meaningful name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Type`
    
    </td>
    <td valign="top">
    
    `HTTP`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Description`
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a meaningful description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    The OData URL, for example `https://my300117-api.s4hana.ondemand.com/sap/opu/odata/IWFND/CATALOGSERVICE;v=2?$format=json`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Proxy Type`
    
    </td>
    <td valign="top">
    
    `Internet`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    `OAuth2SAMLBearerAssertion`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Audience`
    
    </td>
    <td valign="top">
    
    The URL of your SAP S/4HANA Cloud account.

    To get it, log on to your SAP S/4HANA Cloud account. Select the profile picture. Then choose *Settings* and copy the value from the *<Server\>* field. Add `https://` to the beginning of this string, for example, `https://my300117.s4hana.ondemand.com`.

    > ### Note:  
    > This URL does not contain `my300117`*\-api*, but only `my300117`.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Client Key`
    
    </td>
    <td valign="top">
    
    The name of the communication user you have in the SAP S/4HANA ABAP tenant, e.g VIKTOR.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Token Service URL`
    
    </td>
    <td valign="top">
    
    For this field, you need the part of the URL before `/sap/...` that you copied before from *Communications Arrangements* service URL/service interface:

    `https://my300117-api.s4hana.ondemand.com/sap/bc/sec/oauth2/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Token Service User` 
    
    </td>
    <td valign="top">
    
    The same user as for the `Client Key` parameter.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Token Service Password`
    
    </td>
    <td valign="top">
    
    The password for the communication user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `System User`
    
    </td>
    <td valign="top">
    
    This parameter is not used, leave the field empty.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `authnContextClassRef`
    
    </td>
    <td valign="top">
    
    `urn:oasis:names:tc:SAML:2.0:ac:classes:X509` 
    
    </td>
    </tr>
    </table>
    

![](images/CS_CF_S4C_Dest_SCP_787bd1a.png)

Back to [Tasks](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__steps_s4) 



<a name="loio6e5e004b6553403486a03da53bfcaf4e__consume"/>

## Consume the Destination and Execute the Scenario

To perform the scenario and execute the request from the source application towards the target application, proceed as follows:

1.  Decide on where the user identity will be located when calling the Destination service. For details, see [User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md). This will determine how exactly you will perform step 2.
2.  Execute a "find destination" request from the source application to the Destination service. For details, see [Consuming the Destination Service](consuming-the-destination-service-7e30625.md) and the [REST API documentation](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource).
3.  From the Destination service response, extract the access token and URL, and construct your request to the target application. See ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md) for details on the structure of the response from the Destination service.

Back to [Tasks](configuration-tasks-6e5e004.md#loio6e5e004b6553403486a03da53bfcaf4e__steps_s4) 

