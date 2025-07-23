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

 <?sap-ot O2O class="- topic/link " href="ceb84cb51ed64008b6aa7782c80c1651.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loiob2927cc326be495da9f4fea0b6bda2b3_en-US/src/content/localization/en-us/584bc93be7b84020868a129c53f8821d.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[POP3](pop3-387e3e4.md "Configure POP3 destinations for the Transparent Proxy for Kubernetes.")

 <?sap-ot O2O class="- topic/link " href="76db66c32d5445ce9c705ea9774c5354.xml" text="" desc="" xtrc="link:4" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loiob2927cc326be495da9f4fea0b6bda2b3_en-US/src/content/localization/en-us/584bc93be7b84020868a129c53f8821d.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[SMTP](smtp-426527a.md "Configure SMTP destinations for the Transparent Proxy for Kubernetes.")

 <?sap-ot O2O class="- topic/link " href="897df9757cd842cfb1cb9fb6c0327911.xml" text="" desc="" xtrc="link:6" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loiob2927cc326be495da9f4fea0b6bda2b3_en-US/src/content/localization/en-us/584bc93be7b84020868a129c53f8821d.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[MAIL Destinations](mail-destinations-e3de817.md "Find information about MAIL destinations for Internet or on-premise connections from an SAP BTP subaccount.")

