<!-- loiod94b9db4320c4392bcb15accef64d369 -->

# Backup

Manage the Cloud Connector's configuration backup via API.



<a name="loiod94b9db4320c4392bcb15accef64d369__section_rcp_l1b_vcb"/>

## Create Backup Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/backup` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*POST* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{password}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

ZIP archive \(content type `application/zip`\)

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

INVALID\_REQUEST, FORBIDDEN

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>

**Request Properties**:

-   `password`: password used to encrypt sensitive data.

**Errors:**

-   `INVALID_REQUEST` \(400\): if no password was provided.
-   `FORBIDDEN` \(403\): if the instance role is *shadow*.

> ### Note:  
> Only sensitive data in the backup are encrypted with an arbitrary password of your choice. The password is required for the restore operation. The returned ZIP archive itself is not password-protected.

> ### Sample Code:  
> ```
> curl -k -u Administrator:<password> https://<host>:<port>/api/v1/configuration/backup -X POST -H 'Content-Type: application/json' -d "{\"password\":\"<password>\"}" -o <backupfile>.zip
> 
> ```



<a name="loiod94b9db4320c4392bcb15accef64d369__section_lys_l1b_vcb"/>

## Restore Backup Configuration

> ### Caution:  
> A successful request triggers a restart of the Cloud Connector.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/backup` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*PUT* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

multipart/form-data with the following form parameters: `backup`, `password`.

</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

INVALID\_REQUEST, FORBIDDEN, INTERNAL\_SERVER\_ERROR

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>

**Request Properties**:

-   `backup`: a backup file \(produced through POST request\).
-   `password`: password chosen when creating the backup.

**Errors**:

-   `INVALID_REQUEST` \(400\): if invalid or no backup file, or incorrect or missing password was provided.
-   `FORBIDDEN` \(403\): if the instance role is *shadow*.
-   `INTERNAL_SERVER_ERROR` \(500\): if an error happened during restore.

> ### Note:  
> Since this API uses a multipart request, it requires a multipart request header.

> ### Sample Code:  
> ```
> curl -k -u Administrator:<password> https://<host>:<port>/api/v1/configuration/backup -X PUT -F 'password=<password>' -F backup=@<backupfile>.zip
> 
> ```

