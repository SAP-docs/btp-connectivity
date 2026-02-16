<!-- loio058785a93cfd4708be6d0a571e6f22da -->

# Manage Certificates Issued by the SAP Cloud Root CA

Generate SAP Cloud Root CA certificates via the Destination service REST API, based on a locally generated and signed CSR \(certificate signing request\). In this scenario, the private key is not transferred over the Internet, and stored in the service.



## Prerequisites

You have an SAP BTP subaccount. There are no specific requirements for the subaccount region.



## Steps

**Getting Access to the API**

1.  First, you need a service instance of the Destination service with service plan lite. You can do this in a Cloud Foundry space \(using the cockpit or the Cloud Foundry CLI\), or directly in the subaccount \(the so called "Other Environment", using the cockpit or the BTP CLI\), or in Kubernetes/Kyma \(using the SAP BTP service operator\).
2.  Create a binding and service key for the instance. We recommend that you use x509 bindings, but for quick tests you can also take client secrets \(which is the default\).
3.  In the binding, you will see the base Destination service URL \(field `uri`\), the subaccount's token retrieval base URL \(field `url`\), the client ID \(field `clientid`\), and either the client secret \(field `clientsecret`\) or the mTLS properties.
4.  Use the credentials to fetch a token which will then be used to call the REST API \(the example uses `clientid` and `clientsecret`\):

    > ### Sample Code:  
    > ```
    > curl -X POST \
    >         "<url>/oauth/token" \
    >         -H "Content-Type: application/x-www-form-urlencoded" \
    >         -d "grant_type=client_credentials" \
    >         --data-urlencode "client_id=<clientid>" \
    >         --data-urlencode "client_secret=<clientsecret>"
    > ```

5.  We will use the `uri` from the binding and the `access_token` from the response of the token request later.

For more information, see also [Calling the Destination Service REST API](calling-the-destination-service-rest-api-84c5d38.md).

**Generating a Private Key and a CSR**

1.  We will use *openssl* for the purposes of the example to get the CSR, signed by a newly generated private key.
2.  Execute:

    > ### Sample Code:  
    > ```
    > openssl req -utf8 -nodes -sha256 -newkey rsa:3072 -keyout genExample.key -out genExample.csr
    > ```

    > ### Note:  
    > All the attributes of the CSR will get overridden during generation, so don't spend too much time on them.

3.  The private key will result in a `genExample.key`. You will need it when you make use of the certificate. It will not be needed for the next steps of the certificate generation.
4.  Get the CSR in base64-encoded form:

    > ### Note:  
    > `-w0` is used to avoid line breaks, but some flavors of base64 don't offer this option.

    > ### Sample Code:  
    > ```
    > base64 -w0 genExample.csr
    > ```

5.  We will use the output of this command later.

**Call the Destination Service REST API to Generate the Certificate**

1.  Execute:

    > ### Sample Code:  
    > ```
    >     curl --request POST \
    >     --url "${uri}/destination-configuration/v1/subaccountCertificates" \
    >     --header "Authorization: Bearer ${token}" \
    >     --header 'content-type: application/json' \
    >     --data """
    >     {
    >         \"Name\": \"example.pem\",
    >         \"Attributes\": {
    >             \"CN\": \"myExampleCertCn\",
    >             \"Validity\": {
    >                 \"TimeUnit\": \"DAYS\",
    >                 \"Value\": 30
    >             },
    >             \"AutomaticRenew\": true,
    >             \"CSR\": \"${csr}\"
    >         }
    >     }
    >     """
    > ```

2.  Note that the `${...}` values are the data collected in the previous steps.
3.  You can specify the `Validity` of the certificate.
4.  You can set an `AutomaticRenew` flag for the certificate. If your subaccount does not offer the auto-renew function, you may want to get notified about the certificate expiration.

    For more information, see [Destination Service Notifications](destination-service-notifications-552e8fd.md).


For more information, see also [SAP Business Accelerator Hub](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/post_v1_subaccountCertificates).

**Fetch your Newly Generated Certificate**

We will show here the corresponding REST API method.

1.  Execute:

    > ### Sample Code:  
    > ```
    > curl --request GET \
    >     --url "${uri}/destination-configuration/v1/subaccountCertificates/example.pem" \
    >     --header "Authorization: Bearer ${token}"
    > ```

2.  You will find the needed value in the `Content` field of the response JSON.
3.  Base64-decode the value of this field and you will get the certificate chain.

For more information, see also:

[SAP Business Accelerator Hub](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/get_v1_subaccountCertificates__certificate_name_) \(REST API\)

[Manage Destination Certificates](manage-destination-certificates-df1bb55.md) \(cockpit\)

