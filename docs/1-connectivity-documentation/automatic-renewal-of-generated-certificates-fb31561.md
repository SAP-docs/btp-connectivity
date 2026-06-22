<!-- loiofb31561d93b342b5bb90afba6a6faf35 -->

# Automatic Renewal of Generated Certificates

Configure automatic certificate renewal when generating a certificate.

When generating a certificate, you can choose automatic renewal when it gets close to expiration. This will result in a fresh certificate with the same subject and validity duration as the original one. The procedure will continue for the whole lifecycle of the certificate, allowing you to just trust it based on the root CA and the certificate subject on the recipient's side. As soon as configured, there is no more need for manual rotations and trust reestablishment.

> ### Note:  
> The renewal is based on a periodic job that iterates the certificates and decides if they have passed the renewal threshold. Therefore, the exact renewal time may vary slightly, depending on the job schedule.

Find below the thresholds when renewal will be attempted for the first time. They are based on the overall validity of the certificate.

> ### Note:  
> If for any reason the certificate can not be renewed at the time, it will be reattempted on the next job run.

**Renewal Thresholds** 


<table>
<tr>
<th valign="top">

Certificate Validity

</th>
<th valign="top">

Eligible for Renewal

</th>
</tr>
<tr>
<td valign="top">

1 day

</td>
<td valign="top">

12 hours before expiration

</td>
</tr>
<tr>
<td valign="top">

2–14 days

</td>
<td valign="top">

1 day before expiration

</td>
</tr>
<tr>
<td valign="top">

15–31 days

</td>
<td valign="top">

3 days before expiration

</td>
</tr>
<tr>
<td valign="top">

32–154 days

</td>
<td valign="top">

7 days before expiration

</td>
</tr>
<tr>
<td valign="top">

155–365 days

</td>
<td valign="top">

30 days before expiration

</td>
</tr>
<tr>
<td valign="top">

1 month

</td>
<td valign="top">

3 days before expiration

</td>
</tr>
<tr>
<td valign="top">

2–5 months

</td>
<td valign="top">

7 days before expiration

</td>
</tr>
<tr>
<td valign="top">

6–12 months

</td>
<td valign="top">

30 days before expiration

</td>
</tr>
<tr>
<td valign="top">

Any number of years

</td>
<td valign="top">

30 days before expiration

</td>
</tr>
</table>

