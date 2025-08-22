<!-- loio789acee1faa24e6f8dac6c6ceeed66ec -->

# Using Client Assertion with OAuth Flows

Replace client secrets with client assertions in OAuth flows for destinations.

Client assertion is one of the possible client authentication mechanisms when requesting an access token from an authorization server. When using client assertion, you must provide the `client_assertion` and `client_assertion_type` parameters in the request to an authorization server that supports client assertion for client authentication.

The Destination service supports client assertion as а client authentication mechanism. It sends the client assertion to the authorization server whenever requesting an OAuth token. The assertion can be either generated externally and provided to the Destination service, or it can be retrieved by the Destination service via an additional destination.

For more information, see

-   [RFC 7521](https://www.rfc-editor.org/rfc/rfc7521)
-   [Provide Client Assertion Properties as Headers](provide-client-assertion-properties-as-headers-6c98d97.md).



<a name="loio789acee1faa24e6f8dac6c6ceeed66ec__section_lxn_3gl_cxb"/>

## Prerequisites

You must ensure that the target authorization server supports client assertion as authentication mechanism and accepts the provided client assertions after validation. This might require additional setup in the authorization server and the assertion provider.

