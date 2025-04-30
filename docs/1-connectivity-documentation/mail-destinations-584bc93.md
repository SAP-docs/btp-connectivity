<!-- loio584bc93be7b84020868a129c53f8821d -->

# Mail Destinations

Configure Mail destinations for the Transparent Proxy for Kubernetes.

Mail destinations simplify access to target systems which use the SMTP, POP3 or IMAP protocol. The Transparent Proxy handles these communication protocols for on-premise destinations.

The Transparent Proxy performs the SOCKS5 handshake with the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md) to enable the consumption of that \(otherwise complex\) functionality out-of-the-box for the application developer.

For more information about SOCKS5 refer to the [TCP Destinations](tcp-destinations-558b39a.md) section.

In addition, the Transparent Proxy supports *Basic Authentication* for *Mail* destinations. Whether *Basic Authentication* is used or not, the TCP connection remains secure due to the SOCKS5 communication.

**Related Information**  


[IMAP](imap-8eb0ae6.md "Configure IMAP destinations for the Transparent Proxy for Kubernetes.")

[POP3](pop3-387e3e4.md "Configure POP3 destinations for the Transparent Proxy for Kubernetes.")

[SMTP](smtp-426527a.md "Configure SMTP destinations for the Transparent Proxy for Kubernetes.")

