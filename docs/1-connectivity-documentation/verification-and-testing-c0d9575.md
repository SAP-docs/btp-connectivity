<!-- loioc0d95757fcd043c7b21b046b3de275ab -->

# Verification and Testing

Check if the Connectivity Proxy for Kubernetes is operational.

Once you have installed the Connectivity Proxy in your cluster, you can perform the following checks to verify it is running successfully.

> ### Note:  
> Before starting the checks, you must wait for a few seconds until all the components are started and can be consumed.

1.  Execute the following command and verify that the status of the pod \(pods\) is **running**.

    ```
    kubectl run verify-connectivity-proxy --image=nginx --restart=Never -it --rm -- curl -v -x "connectivity-proxy:20003" "http://virtual:1234/"
    ```

2.  Call the external health check endpoint of the Connectivity Proxy to verify it is returning a successful response. You can call the endpoint in a web browser or execute the following command from the command line:

    ```
    kubectl run verify-connectivity-proxy --image=nginx --restart=Never -it --rm -- curl -v -x "connectivity-proxy:20003" "http://virtual:1234/" -H "Proxy-Authorization: Bearer <proxy-authorization-jwt-value>"
    ```

    > ### Caution:  
    > If the host of the Ingress in your cluster is configured with a self-signed certificate, add the `-k` flag to curl to disable the SSL certificate verification.

3.  Make sure you have connected a Cloud Connector to your cloud subaccount. For more information, see [Adding and Managing Subaccounts](adding-and-managing-subaccounts-f16df12.md).

    1.  If you have deployed the Connectivity Proxy in a **single-tenant trusted mode** and have **enabled** the HTTP proxy in the `values.yml` file, execute the following command:

        ```
        kubectl run verify-connectivity-proxy --image=nginx --restart=Never -it --rm -- curl -v -x "connectivity-proxy:20003" "http://virtual:1234/"
        ```

    2.  If you have deployed the Connectivity Proxy in a **single-tenant non-trusted** or **multi-tenant non-trusted mode** and have **enabled** the HTTP proxy in the `values.yml` file, execute the following command:

        ```
        kubectl run verify-connectivity-proxy --image=nginx --restart=Never -it --rm -- curl -v -x "connectivity-proxy:20003" "http://virtual:1234/" -H "Proxy-Authorization: Bearer <proxy-authorization-jwt-value>"
        ```

    3.  If you have deployed the Connectivity Proxy in a **single-tenant trusted mode** and have **enabled** the HTTP proxy in the `values.yml` file, execute the following command:

        ```
        kubectl run verify-connectivity-proxy --image=nginx --restart=Never -it --rm -- curl -v -x "connectivity-proxy:20003" "http://virtual:1234/" -H "SAP-CP-Connectivity-Service-Token: <connectivity-service-jwt-value>"
        ```

        For more informaion on the process of fetching a JWT, see [Consuming the Connectivity Service](consuming-the-connectivity-service-313b215.md).

        For more informaion on the different operational modes, see [Operational Modes](operational-modes-148bbad.md).


    If the Connectivity Proxy is working as expected, you get one of these responses:

    -   ***Access denied to system virtual:1234***: If this was a valid request, make sure you expose the system correctly in your Cloud Connector.

        > ### Note:  
        > This response indicates that the business data from the cluster is successfully reaching your Cloud Connector, but the system ***virtual:1234*** is not exposed there.

    -   Response from your backend system if you have exposed it in the Cloud Connector.

        > ### Note:  
        > This response confirms that the business data from the cluster is successfully reaching your backend system exposed in the Cloud Connector.


    If you encounter problems with any of the above steps, please refer to [Troubleshooting](troubleshooting-e7a04d9.md) and [Recommended Actions](recommended-actions-aec9009.md) for further investigation.


