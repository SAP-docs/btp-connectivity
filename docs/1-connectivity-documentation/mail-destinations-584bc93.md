<!-- loio584bc93be7b84020868a129c53f8821d -->

# Mail Destinations

Configure Mail destinations for the Transparent Proxy for Kubernetes.



<a name="loio584bc93be7b84020868a129c53f8821d__section_ivq_v34_sfc"/>

## On-Premise Mail Destinations

The Transparent Proxy handles SMTP, POP3 and IMAP communication protocols for on-premise Mail destinations. The Transparent Proxy performs the SOCKS5 handshake with the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md) to enable the consumption of that \(otherwise complex\) functionality out-of-the-box for the application developer.

For more information about SOCKS5, see [TCP Destinations](tcp-destinations-558b39a.md).

In addition, the Transparent Proxy supports *Basic Authentication* and *OAuth2ClientCredentials* for on-premise Mail destinations. Whether Basic Authentication/OAuth2ClientCredentials is used or not, the TCP connection remains secure due to the SOCKS5 communication.



<a name="loio584bc93be7b84020868a129c53f8821d__section_vmk_v34_sfc"/>

## Internet Mail Destinations

The Transparent Proxy handles SMTP, POP3, IMAP, SMTPS, POP3S and IMAPS communication protocols for Internet Mail destinations. The Transparent Proxy supports *Basic Authentication* and *OAuth2ClientCredentials* for Internet Mail destinations.

**Related Information**  


[IMAP](imap-8eb0ae6.md "Configure IMAP destinations for the Transparent Proxy for Kubernetes.")

[IMAPS](imaps-ceb84cb.md "Configure IMAPS destinations for the Transparent Proxy for Kubernetes.")

[POP3](pop3-387e3e4.md "Configure POP3 destinations for the Transparent Proxy for Kubernetes.")

[POP3S](pop3s-76db66c.md "Configure POP3S destinations for the Transparent Proxy for Kubernetes.")

[SMTP](smtp-426527a.md "Configure SMTP destinations for the Transparent Proxy for Kubernetes.")

[SMTPS](smtps-897df97.md "Configure SMTPS destinations for the Transparent Proxy for Kubernetes.")

[MAIL Destinations](mail-destinations-e3de817.md "Find information about MAIL destinations for Internet or on-premise connections from an SAP BTP subaccount.")

