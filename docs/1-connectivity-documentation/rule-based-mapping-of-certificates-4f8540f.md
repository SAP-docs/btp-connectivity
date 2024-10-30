<!-- loio4f8540f4c01f447992ef2f3dff8ab4dd -->

# Rule-Based Mapping of Certificates

Learn how to efficiently map short-lived certificates to users in the ABAP server.

> ### Note:  
> The information in this section applies to both principal propagation and technical user propagation.

To perform rule-based mapping of certificates in the ABAP server, proceed as follows:

1.  Enter a dynamic parameter using transaction RZ10.

    1.  Enter the `login/certificate_mapping_rulebased` parameter.
    2.  Choose the *Change Value* button.
    3.  Enter the value `1`.
    4.  Save the value.

    > ### Note:  
    > If dynamic parameters are disabled, enter the value using transaction RZ10 and restart the whole ABAP system.

2.  Configure rule-based mapping
    1.  Create a sample certificate with the Cloud Connector.
        1.  Log on to the Cloud Connector UI.
        2.  From the main menu, choose *Configuration*, tab *On Premise*.
        3.  Go to the **Principal Propagation** section. In the area **Subject Patterns**, press *Add*.
        4.  Enter a subject pattern and choose *Save*.
        5.  The added item appears in the list of subject patterns. Select the item and choose **Generate a sample certificate**. The certificate will be downloaded to your machine.

    2.  To import the sample certificate into the ABAP server, choose transaction CERTRULE and select *Import certificate*.

        > ### Note:  
        > To access transaction CERTRULE, you need the corresponding authorizations \(see: [Assign Authorization Objects for Rule-based Mapping](assign-authorization-objects-for-rule-based-mapping-0ef22ae.md)\).

    3.  To create explicit rule mappings, choose the *Rule* button.
    4.  Choose *Save*.

        > ### Note:  
        > When you save the changes and return to transaction CERTRULE, the sample certificate which you imported in Step 2b will not be saved. This is just a sample editor view to see the sample certificates and mappings.





## Related Information

[Rule-Based Certificate Mapping](https://help.sap.com/viewer/d528eef3dca14679bcb47b069aa17a9d/7.51.0/en-US/c830fd902dc8473b9e59db1576cc784b.html)

