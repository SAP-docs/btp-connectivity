<!-- loioefbaf636c0394b0b987a666bd13b6046 -->

# Configure Destination Service IPs in Firewall Rules

Include Destination service IP addresses in your target system firewall rules for incoming traffic.

If the Destination service performs a connection check or automatic token retrieval for a configured destination, the recipient of the request \(a system or service configured through the properties `URL`, `tokenServiceUrl`, and so on\), should be reachable for the URLs listed below \(depending on the Destination service region\). If you restrict access to the target system for incoming traffic by allowlisting IPs in firewall rules, make sure you include the relevant IPs accordingly.


<table>
<tr>
<th valign="top">

Region \(Region Host\)

</th>
<th valign="top">

IP Addresses

</th>
</tr>
<tr>
<td valign="top">

Europe \(Frankfurt\) - AWS

\(cf.eu10.hana.ondemand.com\)

</td>
<td valign="top">

3.79.93.46

3.127.4.249

3.68.162.165

</td>
</tr>
<tr>
<td valign="top">

Europe \(Frankfurt\) - AWS

\(cf.eu11.hana.ondemand.com\)

</td>
<td valign="top">

3.77.2.199

3.125.182.25

3.75.8.16

</td>
</tr>
<tr>
<td valign="top">

Europe \(Netherlands\) - Azure

\(cf.eu20.hana.ondemand.com\)

</td>
<td valign="top">

40.115.20.192

</td>
</tr>
<tr>
<td valign="top">

US East \(VA\) - AWS

\(cf.us10.hana.ondemand.com\)

</td>
<td valign="top">

44.196.182.81

52.22.134.17

54.81.172.123

</td>
</tr>
<tr>
<td valign="top">

US West \(WA\) - Azure

\(cf.us20.hana.ondemand.com\)

</td>
<td valign="top">

52.151.19.92

</td>
</tr>
<tr>
<td valign="top">

US East \(VA\) - Azure

\(cf.us21.hana.ondemand.com\)

</td>
<td valign="top">

20.163.232.70

</td>
</tr>
<tr>
<td valign="top">

Brazil \(São Paulo\) - AWS

\(cf.br10.hana.ondemand.com\)

</td>
<td valign="top">

18.228.74.68

18.231.84.86

54.232.114.228

</td>
</tr>
<tr>
<td valign="top">

Brazil \(São Paulo\) - Azure

\(cf.br20.hana.ondemand.com\)

</td>
<td valign="top">

4.201.180.215

</td>
</tr>
<tr>
<td valign="top">

Japan \(Tokyo\) - AWS

\(cf.jp10.hana.ondemand.com\)

</td>
<td valign="top">

18.177.52.4

57.181.89.180

54.150.191.131

</td>
</tr>
<tr>
<td valign="top">

Japan \(Tokyo\) - Azure

\(cf.jp20.hana.ondemand.com\)

</td>
<td valign="top">

48.210.28.199

</td>
</tr>
<tr>
<td valign="top">

Australia \(Sydney\) - AWS

\(cf.ap10.hana.ondemand.com\)

</td>
<td valign="top">

54.206.245.69

52.63.244.160

13.210.143.45

</td>
</tr>
<tr>
<td valign="top">

Asia Pacific \(Singapore\) - AWS

\(cf.ap11.hana.ondemand.com\)

</td>
<td valign="top">

52.220.52.143

13.215.24.185

18.143.71.37

</td>
</tr>
<tr>
<td valign="top">

Asia Pacific \(Seoul\) - AWS

\(cf.ap12.hana.ondemand.com\)

</td>
<td valign="top">

43.202.18.57

13.209.44.214

52.78.55.157

</td>
</tr>
<tr>
<td valign="top">

Australia \(Sydney\) - Azure

\(cf.ap20.hana.ondemand.com\)

</td>
<td valign="top">

13.75.143.163

</td>
</tr>
<tr>
<td valign="top">

Singapore - Azure

\(cf.ap21.hana.ondemand.com\)

</td>
<td valign="top">

23.98.89.110

</td>
</tr>
<tr>
<td valign="top">

Canada \(Montreal\) - AWS

\(cf.ca10.hana.ondemand.com\)

</td>
<td valign="top">

15.222.94.104

15.157.235.95

3.97.147.84

</td>
</tr>
<tr>
<td valign="top">

Switzerland \(Zurich\) - Azure

\(cf.ch20.hana.ondemand.com\)

</td>
<td valign="top">

51.103.232.173

</td>
</tr>
</table>

