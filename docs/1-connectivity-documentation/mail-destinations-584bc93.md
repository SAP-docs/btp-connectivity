<!-- loio584bc93be7b84020868a129c53f8821d -->

# Mail Destinations

Configure Mail destinations for the Transparent Proxy for Kubernetes.



<a name="loio584bc93be7b84020868a129c53f8821d__section_ivq_v34_sfc"/>

## On-Premise Mail Destinations

The Transparent Proxy handles SMTP, POP3 and IMAP communication protocols for on-premise Mail destinations. The Transparent Proxy performs the SOCKS5 handshake with the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md) to enable the consumption of that \(otherwise complex\) functionality out-of-the-box for the application developer.

For more information about SOCKS5, see [TCP Destinations](tcp-destinations-558b39a.md).

In addition, the Transparent Proxy supports *Basic Authentication*, *OAuth2ClientCredentials*, *OAuth2RefreshToken* and *OAuth2AuthorizationCode* for on-premise Mail destinations. Whether Basic Authentication/OAuth2ClientCredentials/OAuth2AuthorizationCode/OAuth2RefreshToken is used or not, the TCP connection remains secure due to the SOCKS5 communication.



<a name="loio584bc93be7b84020868a129c53f8821d__section_vmk_v34_sfc"/>

## Internet Mail Destinations

The Transparent Proxy handles SMTP, POP3, IMAP, SMTPS, POP3S and IMAPS communication protocols for Internet Mail destinations. The Transparent Proxy supports *Basic Authentication*, *OAuth2ClientCredentials*, *OAuth2RefreshToken* and *OAuth2AuthorizationCode* for Internet Mail destinations.

**Related Information**  


[IMAP](imap-8eb0ae6.md "Consume an IMAP system through the Transparent Proxy for Kubernetes and the Destination service.")

[IMAPS](imaps-ceb84cb.md "Consume an IMAPS system through the Transparent Proxy for Kubernetes and the Destination service.")

[POP3](pop3-387e3e4.md "Consume a POP3 system through the Transparent Proxy for Kubernetes and the Destination service.")

[POP3S](pop3s-76db66c.md "Consume a POP3S system through the Transparent Proxy for Kubernetes and the Destination service.")

[SMTP](smtp-426527a.md "Consume an SMTP system through the Transparent Proxy for Kubernetes and the Destination service.")

[SMTPS](smtps-897df97.md "Consume an SMTPS system through the Transparent Proxy for Kubernetes and the Destination service.")

[MAIL Destinations](mail-destinations-e3de817.md "Find information about MAIL destinations for Internet or on-premise connections from an SAP BTP subaccount.")

