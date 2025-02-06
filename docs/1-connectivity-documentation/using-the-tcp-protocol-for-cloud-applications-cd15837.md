<!-- loiocd1583775afa43f0bb9ec69d9dbcc880 -->

# Using the TCP Protocol for Cloud Applications

Access on-premise systems from an application via TCP-based protocols, using a SOCKS5 Proxy.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loiocd1583775afa43f0bb9ec69d9dbcc880__content"/>

## Content

[Concept](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__concept)

[Restrictions](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__restrictions)

[Example](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__example)

[Troubleshooting](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__errors)



<a name="loiocd1583775afa43f0bb9ec69d9dbcc880__concept"/>

## Concept

SAP BTP Connectivity provides a SOCKS5 proxy that you can use to access on-premise systems via TCP-based protocols. SOCKS5 is the industry standard for proxying TCP-based traffic \(for more information, see IETF [RFC 1928](https://www.ietf.org/rfc/rfc1928.txt)\).

The SOCKS5 proxy host and port are accessible through the environment variables, which are generated after binding an application to a Connectivity service instance. For more information, see [Consuming the Connectivity Service](consuming-the-connectivity-service-313b215.md).

You can access the host under `onpremise_proxy_host`, and the port through `onpremise_socks5_proxy_port`, obtained from the Connectivity service instance.

Authentication to the SOCKS5 proxy is mandatory. It involves the usage of a JWT \(JSON Web token\) access token \(for more information, see IETF [RFC 7519](https://tools.ietf.org/html/rfc7519)\). The JWT can be retrieved through the `client_id` and `client_secret`, obtained from the Connectivity service instance. For more information, see [Set up the HTTP Proxy for On-Premise Connectivity](consuming-the-connectivity-service-313b215.md#loio313b215066a8400db461b311e01bd99b__section_HttpProxy), section **Authorization**.

The value of the SOCKS5 protocol authentication method is defined as **0x80** \(defined as *X'80'* in IETF, refer to the official specification [SOCKS Protocol Version 5](https://www.ietf.org/rfc/rfc1928.txt)\). This value should be sent as part of the authentication method's negotiation request \(known as *Initial Request* in SOCKS5\). The server then confirms with a response containing its decimal representation \(either **128** or **\-128**, depending on the client implementation\).

After a successful SOCKS5 *Initial Request*, the authentication procedure follows the standard SOCKS5 authentication sub-procedure, that is SOCKS5 *Authentication Request*. The request bytes, in sequence, should look like this:


<table>
<tr>
<th valign="top">

Bytes

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

1 byte

</td>
<td valign="top">

Authentication method version - currently `1` 

</td>
</tr>
<tr>
<td valign="top">

4 bytes

</td>
<td valign="top">

Length of the JWT

</td>
</tr>
<tr>
<td valign="top">

X bytes

</td>
<td valign="top">

X - The actual value of the JWT in its encoded form

</td>
</tr>
<tr>
<td valign="top">

1 byte

</td>
<td valign="top">

Length of the Cloud Connector location ID \(`0` if no Cloud Connector location ID is used\)

</td>
</tr>
<tr>
<td valign="top">

Y bytes

</td>
<td valign="top">

Optional. Y - The value of the Cloud Connector location ID in base64-encoded form \(if the the value of the location ID is not `0`\)

</td>
</tr>
</table>

The Cloud Connector location ID identifies Cloud Connector instances that are deployed in various locations of a customer's premises and connected to the same subaccount. Since the location ID is an optional property, you should include it in the request only if it has already been configured in the Cloud Connector. For more information, see [Set up Connection Parameters and HTTPS Proxy](initial-configuration-db9170a.md#loiodb9170a7d97610148537d5a84bf79ba2__configure_proxy) \(Step 4\).

If not set in the Cloud Connector, the byte representing the length of the location ID in the *Authentication Request* should have the value `0`, without including any value for the Cloud Connector location ID \(`sccLocationId`\).

Back to [Content](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__content)



<a name="loiocd1583775afa43f0bb9ec69d9dbcc880__restrictions"/>

## Restrictions

-   You cannot use the provided SOCKS5 proxy as general-purpose proxy.
-   Proxying UDP traffic is not supported.

Back to [Content](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__content)



<a name="loiocd1583775afa43f0bb9ec69d9dbcc880__example"/>

## Example

The following code snippet demonstrates an example based on the `Apache Http Client` library and Java code, which represents a way to replace the standard socket used in the Apache HTTP client with one that is responsible for authenticating with the Connectivity SOCKS5 proxy:

> ### Sample Code:  
> ```
> @Override
> public void connect(SocketAddress endpoint, int timeout) throws IOException {
>     super.connect(getProxyAddress(), timeout);
>  
>     OutputStream outputStream = getOutputStream();
>   
>     executeSOCKS5InitialRequest(outputStream); // 1. Negotiate authentication method, i.e. 0x80 (128)
>   
>     executeSOCKS5AuthenticationRequest(outputStream); // 2. Negotiate authentication sub-version and send the JWT (and optionally the Cloud Connector Location ID)
>   
>     executeSOCKS5ConnectRequest(outputStream, (InetSocketAddress) endpoint); // 3. Initiate connection to target on-premise backend system
> }
> ```

> ### Sample Code:  
> ```
> private byte[] createInitialSOCKS5Request() throws IOException {
>     ByteArrayOutputStream byteArraysStream = new ByteArrayOutputStream();
>     try {
>         byteArraysStream.write(SOCKS5_VERSION);
>         byteArraysStream.write(SOCKS5_AUTHENTICATION_METHODS_COUNT);
>         byteArraysStream.write(SOCKS5_JWT_AUTHENTICATION_METHOD);
>         return byteArraysStream.toByteArray();
>     } finally {
>         byteArraysStream.close();
>     }
> }  
>  
>  
> private void executeSOCKS5InitialRequest(OutputStream outputStream) throws IOException {
>     byte[] initialRequest = createInitialSOCKS5Request();
>     outputStream.write(initialRequest);
>  
>     assertServerInitialResponse();
> }
> ```

> ### Sample Code:  
> ```
> private byte[] createJWTAuthenticationRequest() throws IOException {
>     ByteArrayOutputStream byteArraysStream = new ByteArrayOutputStream();
>     try {
>         byteArraysStream.write(SOCKS5_JWT_AUTHENTICATION_METHOD_VERSION);
>         byteArraysStream.write(ByteBuffer.allocate(4).putInt(jwtToken.getBytes().length).array());
>         byteArraysStream.write(jwtToken.getBytes());
>         byteArraysStream.write(ByteBuffer.allocate(1).put((byte) sccLocationId.getBytes().length).array());
>         byteArraysStream.write(sccLocationId.getBytes());
>         return byteArraysStream.toByteArray();
>     } finally {
>         byteArraysStream.close();
>     }
> }
>      
> private void executeSOCKS5AuthenticationRequest(OutputStream outputStream) throws IOException {
>     byte[] authenticationRequest = createJWTAuthenticationRequest();
>     outputStream.write(authenticationRequest);
>  
>     assertAuthenticationResponse();
> }
> ```

In version 4.2.6 of the Apache HTTP client, the class responsible for connecting the socket is `DefaultClientConnectionOperator`. By extending the class and replacing the standard socket with the complete example code below, which implements a Java Socket, you can handle the SOCKS5 authentication with ID **0x80**. It is based on a JWT and supports the Cloud Connector location ID.

> ### Sample Code:  
> ```
> import java.io.ByteArrayOutputStream;
> import java.io.IOException;
> import java.io.InputStream;
> import java.io.OutputStream;
> import java.net.InetAddress;
> import java.net.InetSocketAddress;
> import java.net.Socket;
> import java.net.SocketAddress;
> import java.net.SocketException;
> import java.nio.ByteBuffer;
>  
> import java.util.Base64; // or any other library for base64 encoding
> import org.json.JSONArray; // or any other library for JSON objects
> import org.json.JSONObject; // or any other library for JSON objects
> import org.json.JSONException; // or any other library for JSON objects
>  
> public class ConnectivitySocks5ProxySocket extends Socket {
>  
>     private static final byte SOCKS5_VERSION = 0x05;
>     private static final byte SOCKS5_JWT_AUTHENTICATION_METHOD = (byte) 0x80;
>     private static final byte SOCKS5_JWT_AUTHENTICATION_METHOD_VERSION = 0x01;
>     private static final byte SOCKS5_COMMAND_CONNECT_BYTE = 0x01;
>     private static final byte SOCKS5_COMMAND_REQUEST_RESERVED_BYTE = 0x00;
>     private static final byte SOCKS5_COMMAND_ADDRESS_TYPE_IPv4_BYTE = 0x01;
>     private static final byte SOCKS5_COMMAND_ADDRESS_TYPE_DOMAIN_BYTE = 0x03;
>     private static final byte SOCKS5_AUTHENTICATION_METHODS_COUNT = 0x01;
>     private static final int SOCKS5_JWT_AUTHENTICATION_METHOD_UNSIGNED_VALUE = 0x80 & 0xFF;
>     private static final byte SOCKS5_AUTHENTICATION_SUCCESS_BYTE = 0x00;
>  
>     private static final String SOCKS5_PROXY_HOST_PROPERTY = "onpremise_proxy_host";
>     private static final String SOCKS5_PROXY_PORT_PROPERTY = "onpremise_socks5_proxy_port";
>  
>     private final String jwtToken;
>     private final String sccLocationId;
>  
>     public ConnectivitySocks5ProxySocket(String jwtToken, String sccLocationId) {
>         this.jwtToken = jwtToken;
>         this.sccLocationId = sccLocationId != null ? Base64.getEncoder().encodeToString(sccLocationId.getBytes()) : "";
>     }
>  
>     protected InetSocketAddress getProxyAddress() {
>         try {
>             JSONObject credentials = extractEnvironmentCredentials();
>             String proxyHost = credentials.getString(SOCKS5_PROXY_HOST_PROPERTY);
>             int proxyPort = Integer.parseInt(credentials.getString(SOCKS5_PROXY_PORT_PROPERTY));
>             return new InetSocketAddress(proxyHost, proxyPort);
>         } catch (JSONException ex) {
>             throw new IllegalStateException("Unable to extract the SOCKS5 proxy host and port", ex);
>         }
>     }
>  
>     private JSONObject extractEnvironmentCredentials() throws JSONException {
>         JSONObject jsonObj = new JSONObject(System.getenv("VCAP_SERVICES"));
>         JSONArray jsonArr = jsonObj.getJSONArray("connectivity");
>         return jsonArr.getJSONObject(0).getJSONObject("credentials");
>     }
>  
>     @Override
>     public void connect(SocketAddress endpoint, int timeout) throws IOException {
>         super.connect(getProxyAddress(), timeout);
>  
>         OutputStream outputStream = getOutputStream();
>  
>         executeSOCKS5InitialRequest(outputStream);
>  
>         executeSOCKS5AuthenticationRequest(outputStream);
>  
>         executeSOCKS5ConnectRequest(outputStream, (InetSocketAddress) endpoint);
>     }
>  
>     private void executeSOCKS5InitialRequest(OutputStream outputStream) throws IOException {
>         byte[] initialRequest = createInitialSOCKS5Request();
>         outputStream.write(initialRequest);
>  
>         assertServerInitialResponse();
>     }
>  
>     private byte[] createInitialSOCKS5Request() throws IOException {
>         ByteArrayOutputStream byteArraysStream = new ByteArrayOutputStream();
>         try {
>             byteArraysStream.write(SOCKS5_VERSION);
>             byteArraysStream.write(SOCKS5_AUTHENTICATION_METHODS_COUNT);
>             byteArraysStream.write(SOCKS5_JWT_AUTHENTICATION_METHOD);
>             return byteArraysStream.toByteArray();
>         } finally {
>             byteArraysStream.close();
>         }
>     }
>  
>     private void assertServerInitialResponse() throws IOException {
>         InputStream inputStream = getInputStream();
>  
>         int versionByte = inputStream.read();
>         if (SOCKS5_VERSION != versionByte) {
>             throw new SocketException(String.format("Unsupported SOCKS version - expected %s, but received %s", SOCKS5_VERSION, versionByte));
>         }
>  
>         int authenticationMethodValue = inputStream.read();
>         if (SOCKS5_JWT_AUTHENTICATION_METHOD_UNSIGNED_VALUE != authenticationMethodValue) {
>             throw new SocketException(String.format("Unsupported authentication method value - expected %s, but received %s",
>                     SOCKS5_JWT_AUTHENTICATION_METHOD_UNSIGNED_VALUE, authenticationMethodValue));
>         }
>     }
>  
>     private void executeSOCKS5AuthenticationRequest(OutputStream outputStream) throws IOException {
>         byte[] authenticationRequest = createJWTAuthenticationRequest();
>         outputStream.write(authenticationRequest);
>  
>         assertAuthenticationResponse();
>     }
>  
>     private byte[] createJWTAuthenticationRequest() throws IOException {
>         ByteArrayOutputStream byteArraysStream = new ByteArrayOutputStream();
>         try {
>             byteArraysStream.write(SOCKS5_JWT_AUTHENTICATION_METHOD_VERSION);
>             byteArraysStream.write(ByteBuffer.allocate(4).putInt(jwtToken.getBytes().length).array());
>             byteArraysStream.write(jwtToken.getBytes());
>             byteArraysStream.write(ByteBuffer.allocate(1).put((byte) sccLocationId.getBytes().length).array());
>             byteArraysStream.write(sccLocationId.getBytes());
>             return byteArraysStream.toByteArray();
>         } finally {
>             byteArraysStream.close();
>         }
>     }
>  
>     private void assertAuthenticationResponse() throws IOException {
>         InputStream inputStream = getInputStream();
>  
>         int authenticationMethodVersion = inputStream.read();
>         if (SOCKS5_JWT_AUTHENTICATION_METHOD_VERSION != authenticationMethodVersion) {
>             throw new SocketException(String.format("Unsupported authentication method version - expected %s, but received %s",
>                     SOCKS5_JWT_AUTHENTICATION_METHOD_VERSION, authenticationMethodVersion));
>         }
>  
>         int authenticationStatus = inputStream.read();
>         if (SOCKS5_AUTHENTICATION_SUCCESS_BYTE != authenticationStatus) {
>             throw new SocketException("Authentication failed!");
>         }
>     }
>  
>     private void executeSOCKS5ConnectRequest(OutputStream outputStream, InetSocketAddress endpoint) throws IOException {
>         byte[] commandRequest = createConnectCommandRequest(endpoint);
>         outputStream.write(commandRequest);
>  
>         assertConnectCommandResponse();
>     }
>  
>     private byte[] createConnectCommandRequest(InetSocketAddress endpoint) throws IOException {
>         String host = endpoint.getHostName();
>         int port = endpoint.getPort();
>         ByteArrayOutputStream byteArraysStream = new ByteArrayOutputStream();
>         try {
>             byteArraysStream.write(SOCKS5_VERSION);
>             byteArraysStream.write(SOCKS5_COMMAND_CONNECT_BYTE);
>             byteArraysStream.write(SOCKS5_COMMAND_REQUEST_RESERVED_BYTE);
>             byte[] hostToIPv4 = parseHostToIPv4(host);
>             if (hostToIPv4 != null) {
>                 byteArraysStream.write(SOCKS5_COMMAND_ADDRESS_TYPE_IPv4_BYTE);
>                 byteArraysStream.write(hostToIPv4);
>             } else {
>                 byteArraysStream.write(SOCKS5_COMMAND_ADDRESS_TYPE_DOMAIN_BYTE);
>                 byteArraysStream.write(ByteBuffer.allocate(1).put((byte) host.getBytes().length).array());
>                 byteArraysStream.write(host.getBytes());
>             }
>             byteArraysStream.write(ByteBuffer.allocate(2).putShort((short) port).array());
>             return byteArraysStream.toByteArray();
>         } finally {
>             byteArraysStream.close();
>         }
>     }
>  
>     private void assertConnectCommandResponse() throws IOException {
>         InputStream inputStream = getInputStream();
>  
>         int versionByte = inputStream.read();
>         if (SOCKS5_VERSION != versionByte) {
>             throw new SocketException(String.format("Unsupported SOCKS version - expected %s, but received %s", SOCKS5_VERSION, versionByte));
>         }
>  
>         int connectStatusByte = inputStream.read();
>         assertConnectStatus(connectStatusByte);
>  
>         readRemainingCommandResponseBytes(inputStream);
>     }
>  
>     private void assertConnectStatus(int commandConnectStatus) throws IOException {
>         if (commandConnectStatus == 0) {
>             return;
>         }
>  
>         String commandConnectStatusTranslation;
>         switch (commandConnectStatus) {
>             case 1:
>                 commandConnectStatusTranslation = "FAILURE";
>                 break;
>             case 2:
>                 commandConnectStatusTranslation = "FORBIDDEN";
>                 break;
>             case 3:
>                 commandConnectStatusTranslation = "NETWORK_UNREACHABLE";
>                 break;
>             case 4:
>                 commandConnectStatusTranslation = "HOST_UNREACHABLE";
>                 break;
>             case 5:
>                 commandConnectStatusTranslation = "CONNECTION_REFUSED";
>                 break;
>             case 6:
>                 commandConnectStatusTranslation = "TTL_EXPIRED";
>                 break;
>             case 7:
>                 commandConnectStatusTranslation = "COMMAND_UNSUPPORTED";
>                 break;
>             case 8:
>                 commandConnectStatusTranslation = "ADDRESS_UNSUPPORTED";
>                 break;
>             default:
>                 commandConnectStatusTranslation = "UNKNOWN";
>                 break;
>         }
>         throw new SocketException("SOCKS5 command failed with status: " + commandConnectStatusTranslation);
>     }
>  
>     private byte[] parseHostToIPv4(String hostName) {
>         byte[] parsedHostName = null;
>         String[] virtualHostOctets = hostName.split("\\.", -1);
>         int octetsCount = virtualHostOctets.length;
>         if (octetsCount == 4) {
>             try {
>                 byte[] ipOctets = new byte[octetsCount];
>                 for (int i = 0; i < octetsCount; i++) {
>                     int currentOctet = Integer.parseInt(virtualHostOctets[i]);
>                     if ((currentOctet < 0) || (currentOctet > 255)) {
>                         throw new IllegalArgumentException(String.format("Provided octet %s is not in the range of [0-255]", currentOctet));
>                     }
>                     ipOctets[i] = (byte) currentOctet;
>                 }
>                 parsedHostName = ipOctets;
>             } catch (IllegalArgumentException ex) {
>                 return null;
>             }
>         }
>  
>         return parsedHostName;
>     }
>  
>     private void readRemainingCommandResponseBytes(InputStream inputStream) throws IOException {
>         inputStream.read(); // skipping over SOCKS5 reserved byte
>         int addressTypeByte = inputStream.read();
>         if (SOCKS5_COMMAND_ADDRESS_TYPE_IPv4_BYTE == addressTypeByte) {
>             for (int i = 0; i < 6; i++) {
>                 inputStream.read();
>             }
>         } else if (SOCKS5_COMMAND_ADDRESS_TYPE_DOMAIN_BYTE == addressTypeByte) {
>             int domainNameLength = inputStream.read();
>             int portBytes = 2;
>             inputStream.read(new byte[domainNameLength + portBytes], 0, domainNameLength + portBytes);
>         }
>     }
> }
> ```

Back to [Example](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__example)

Back to [Content](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__content)



<a name="loiocd1583775afa43f0bb9ec69d9dbcc880__errors"/>

## Troubleshooting

If the handshake with the SOCKS5 proxy server fails, a SOCKS5 protocol error is returned, see IETF [RFC 1928](https://www.ietf.org/rfc/rfc1928.txt). The table below shows the most common errors and their root cause in the scenario you use:


<table>
<tr>
<th valign="top">

SOCSK5 Error Code

</th>
<th valign="top">

Technical Description

</th>
<th valign="top">

Client-Side Error Description

</th>
<th valign="top">

Scenario Error

</th>
</tr>
<tr>
<td valign="top">

0x00

</td>
<td valign="top">

SUCCESS

</td>
<td valign="top">

 

</td>
<td valign="top">

Success

</td>
</tr>
<tr>
<td valign="top">

0x01

</td>
<td valign="top">

FAILURE

</td>
<td valign="top">

 

</td>
<td valign="top">

Connection closed by backend or general scenario failure.

</td>
</tr>
<tr>
<td valign="top">

0x02

</td>
<td valign="top">

FORBIDDEN

</td>
<td valign="top">

***Connection not allowed by ruleset***

</td>
<td valign="top">

No matching host mapping found in Cloud Connector access control settings, see [Configure Access Control \(TCP\)](configure-access-control-tcp-befd437.md).

</td>
</tr>
<tr>
<td valign="top">

0x03

</td>
<td valign="top">

NETWORK\_UNREACHABLE

</td>
<td valign="top">

 

</td>
<td valign="top">

The Cloud Connector is not connected to the subaccount and the Cloud Connector `Location ID` that is used by the cloud application can't be identified. See [Connect and Disconnect a Cloud Subaccount](connect-and-disconnect-a-cloud-subaccount-e8f055e.md) and [Managing Subaccounts](managing-subaccounts-f16df12.md), section *Procedure*.

</td>
</tr>
<tr>
<td valign="top">

0x04

</td>
<td valign="top">

HOST\_UNREACHABLE

</td>
<td valign="top">

 

</td>
<td valign="top">

Cannot open connection to the backend, that is, the host is unreachable.

</td>
</tr>
<tr>
<td valign="top">

0x05

</td>
<td valign="top">

CONNECTION\_REFUSED

</td>
<td valign="top">

 

</td>
<td valign="top">

Authentication failure

</td>
</tr>
<tr>
<td valign="top">

0x06

</td>
<td valign="top">

TTL\_EXPIRED

</td>
<td valign="top">

 

</td>
<td valign="top">

*Not used*

</td>
</tr>
<tr>
<td valign="top">

0x07

</td>
<td valign="top">

COMMAND\_UNSUPPORTED

</td>
<td valign="top">

 

</td>
<td valign="top">

Only the SOCKS5 `CONNECT` command is supported.

</td>
</tr>
<tr>
<td valign="top">

0x08

</td>
<td valign="top">

ADDRESS\_UNSUPPORTED

</td>
<td valign="top">

 

</td>
<td valign="top">

Only the SOCKS5 `DOMAIN` and `IPv4` commands are supported.

</td>
</tr>
</table>

Back to [Content](using-the-tcp-protocol-for-cloud-applications-cd15837.md#loiocd1583775afa43f0bb9ec69d9dbcc880__content)

