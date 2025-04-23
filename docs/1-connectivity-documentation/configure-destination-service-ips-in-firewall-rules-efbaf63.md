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

3.120.127.220

3.123.133.91

18.153.139.6

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

3.127.28.215

18.192.171.62

3.74.96.32

</td>
</tr>
<tr>
<td valign="top">

Europe \(Netherlands\) - Azure

\(cf.eu20.hana.ondemand.com\)

</td>
<td valign="top">

40.115.20.192

108.141.17.178

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

54.243.28.3

35.173.121.86

52.71.181.35

</td>
</tr>
<tr>
<td valign="top">

US West \(Oregon\) - AWS

\(cf.us11.hana.ondemand.com\)

</td>
<td valign="top">

100.21.196.19

44.239.115.54

35.155.159.17

34.215.5.87

44.245.124.5

35.85.25.113

</td>
</tr>
<tr>
<td valign="top">

US West \(WA\) - Azure

\(cf.us20.hana.ondemand.com\)

</td>
<td valign="top">

52.151.19.92

4.149.160.6

</td>
</tr>
<tr>
<td valign="top">

US East \(VA\) - Azure

\(cf.us21.hana.ondemand.com\)

</td>
<td valign="top">

20.163.232.70

135.234.230.67

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

54.232.165.245

54.207.38.48

54.207.88.85

</td>
</tr>
<tr>
<td valign="top">

Brazil \(São Paulo\) - Azure

\(cf.br20.hana.ondemand.com\)

</td>
<td valign="top">

4.201.180.215

4.228.11.82

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

54.249.103.106

18.179.168.29

52.193.24.140

</td>
</tr>
<tr>
<td valign="top">

Japan \(Tokyo\) - Azure

\(cf.jp20.hana.ondemand.com\)

</td>
<td valign="top">

48.210.28.199

74.176.24.90

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

13.54.39.245

13.238.213.186

13.54.25.95

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

47.130.15.124

18.141.62.28

18.138.210.183

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

52.78.218.213

13.209.92.99

3.38.231.134

</td>
</tr>
<tr>
<td valign="top">

Australia \(Sydney\) - Azure

\(cf.ap20.hana.ondemand.com\)

</td>
<td valign="top">

13.75.143.163

4.237.197.40

</td>
</tr>
<tr>
<td valign="top">

Singapore - Azure

\(cf.ap21.hana.ondemand.com\)

</td>
<td valign="top">

23.98.89.110

57.155.52.252

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

15.222.109.206

3.96.0.52

3.97.184.18

</td>
</tr>
<tr>
<td valign="top">

Canada Central \(Toronto\) - Azure

\(cf.ca20.hana.ondemand.com\)

</td>
<td valign="top">

52.138.50.189

130.107.189.173

</td>
</tr>
<tr>
<td valign="top">

Switzerland \(Zurich\) - Azure

\(cf.ch20.hana.ondemand.com\)

</td>
<td valign="top">

51.103.232.173

20.250.185.103

</td>
</tr>
</table>

