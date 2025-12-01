<!-- loio69130a77dd12431ca5e0c41c2d5fbecb -->

# Create an OAuth Client in SAP SuccessFactors

Create an OAuth client in SuccessFactors for user propagation from the SAP BTP Cloud Foundry environment.

1.  Export the X.509 certificate \(trust certificate\) from your Cloud Foundry subaccount.

    For more information, see [Manage Trust](manage-trust-82dbeca.md).

2.  Create a SuccessFactors OAuth Client:

    In SuccessFactors, go to the *Admin Center* and search for `OAuth`. Choose `Manage OAuth2 Client Applications`.

    ![](images/CS_CF_SF_OAuth_2_4de241a.png)

    ![](images/CS_CF_SF_OAuth_3_ef04530.png)

3.  Press the *Register Client Application* button on the right. In the *<Application Name\>* field, provide some arbitrary descriptive name for the client. For *<Application URL\>*, enter the Cloud Foundry API endpoint of the client SAP BTP subaccount, followed by the subaccount GUID, for example `https://api.cf.stagingaws.hanavlab.ondemand.com/17d146c3-bc6c-4424-8360-7d56ee73bd32`. This information is available in the cloud cockpit under subaccount details:

    ![](images/CS_CF_SF_OAuth_4_9385dc5.png)

4.  In the field *<X.509 Certificate\>*, paste the certificate that you downloaded in step 1.
5.  Choose *Register* to save the OAuth client.
6.  Now, locate your client in the list by its application name, choose *View* in the *Actions* column and take note of the *<API Key\>* that has been generated for it. You will use this key later in the OAuth2SAMLBearer destination in the Cloud Foundry environment.

    ![](images/CS_CF_SF_OAuth_5_b89dcbf.png)




<a name="loio69130a77dd12431ca5e0c41c2d5fbecb__section_xd1_x1y_cgb"/>

## Next Step

-   [Create and Consume a Destination for the Cloud Foundry Application](create-and-consume-a-destination-for-the-cloud-foundry-application-0781bb6.md)

