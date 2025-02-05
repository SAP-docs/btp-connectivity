<!-- loio0781bb60003c41a1aadb1586d774449a -->

# Create and Consume a Destination for the Cloud Foundry Application

Create and consume an OAuth2SAMLBearerAssertion destination for your Cloud Foundry application.



<a name="loio0781bb60003c41a1aadb1586d774449a__section_m4v_snm_gjb"/>

## Create the Destination

1.  In the cloud cockpit, navigate to your Cloud Foundry subaccount and from the left-side subaccount menu, choose *Connectivity* \> *Destinations*. Choose *New Destination* and enter a name Then provide the following settings:
    -   *<URL\>*: URL of the SuccessFactors OData API you want to consume.
    -   *<Authentication\>*: `OAuth2SAMLBearerAssertion`
    -   *<Audience\>*: `www.successfactors.com`
    -   *<Client Key\>*: API Key of the OAuth client you created in SuccessFactors.
    -   *<Token Service URL\>*: API endpoint URL for the SuccessFactors instance, followed by`/oauth/token` and the URL parameter `company_id` with the company ID, for example `https://apisalesdemo2.successfactors.eu/oauth/token?company_id=SFPART019820`.

2.  Enter three additional properties:
    -   **`apiKey`**: the API Key of the OAuth client you created in SuccessFactors.

    -   **`authnContextClassRef`**: `urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession`

    -   **`nameIdFormat`**:

        -   `urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified`, if the **user ID** will be propagated to a SuccessFactors application, or
        -   `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress`, if the **user e-mail** will be propagated to SuccessFactors.



![](images/CS_CF_SF_Destination_06ba541.png)



## Consume the Destination and Execute the Scenario

To perform the scenario and execute the request from the source application towards the target application, proceed as follows:

1.  Decide on where the user identity will be located when calling the Destination service. For details, see [User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md). This will determine how exactly you will perform step 2.
2.  Execute a "find destination" request from the source application to the Destination service. For details, see [Consuming the Destination Service](consuming-the-destination-service-7e30625.md) and the [REST API documentation](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource).
3.  From the Destination service response, extract the access token and URL, and construct your request to the target application. See ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md) for details on the structure of the response from the Destination service.

