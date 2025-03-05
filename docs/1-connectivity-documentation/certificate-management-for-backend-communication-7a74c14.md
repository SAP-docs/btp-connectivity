<!-- loio7a74c144076f4b3aac84df0ff9556081 -->

# Certificate Management for Backend Communication

Manage a CA certificate for principal propagation or a system certificate via API.

> ### Note:  
> The APIs below are available as of Cloud Connector version 2.13.

There are two similar sets of APIs for system certificate and CA certificate for principal propagation.

> ### Note:  
> Some of the APIs list a parameter `subjectAltNames` \(*subject alternative names* or SAN\) for the request or response object. This parameter is an array of objects with the following properties:
> 
> -   `type`: one of the strings *DNS*, *URI*, *IP*, or *RFC822*.
> -   `value`: the value associated with the chosen type.

-   [CA Certificate for Principal Propagation: APIs](ca-certificate-for-principal-propagation-apis-0c4a958.md)
-   [System Certificate: APIs](system-certificate-apis-236c084.md)
-   [Truststore Backend Certificates](truststore-backend-certificates-e8f309f.md)

