<!-- loio6c472ff155684c8e9f4c8faa5c66712a -->

# Subject Pattern Rules

Read and edit the Cloud Connector's subject pattern rules via API.



## Get All Subject Pattern Rules


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/subjectPatternRules` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
[{description, condition, subjectPattern}] 
```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response**:

An array of objects with the following properties:

-   `description`: description of the rule \(a string\)
-   `condition`: condition of the rule, described in a human-readable format \(a string\)
-   `subjectPattern`: object containing key-value pairs representing the configured subject pattern fields \(CN, EMAIL, L, OU, O, ST, C\)

> ### Sample Code:  
> ```
> curl -i -k -H 'Accept:application/json' -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules
> ```



## Create a Subject Pattern Rule


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

/api/v1/configuration/connector/onPremises/subjectPatternRules

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
{description, condition, subjectPattern}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

201 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

Bad Request \(400\)

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request**:

An object with the following properties:

-   `description` \(required\): description of the rule \(string\).
-   `condition` \(required\): object specifying when this rule should apply. It must include:
    -   variable \(required, string\): variable name to evaluate \(e.g., "user\_type"\).
    -   operator \(required, string\): operator to use for evaluation. Valid values:
        -   "exist" – Variable must exist.
        -   "exist\_not" – Variable must not exist.
        -   "is" – Variable must exactly match the provided value \(requires value\).
        -   "is\_not" – Variable must not match the provided value \(requires value\).


    -   value \(conditionally required, string\): value to evaluate against. Required if operator is "is" or "is\_not"; otherwise, must not be provided.

-   `subjectPattern` \(required\): object containing key-value pairs representing the configured subject pattern fields \("CN", "EMAIL", "L", "OU", "O", "ST", "C"\). Values may include placeholders in the format "$\{variable\}".

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X POST \
> -H 'Content-Type: application/json' \
> -d '{"description":"<description>","condition":{"variable":"<variable>","operator":"<operator>","value":"<value>"},"subjectPattern":{"<field>":"<value>", ...}}' \
> https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules
> ```



## Change a Subject Pattern Rule


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/subjectPatternRules/{index}` 

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

```
{description, condition, subjectPattern}
```



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

Bad Request \(400\)

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request**:

An object with the following properties:

-   `description` \(required\): description of the rule \(string\).
-   `condition` \(required\): object specifying when this rule should apply. It must include:
    -   variable \(required, string\): variable name to evaluate \(e.g., "user\_type"\).
    -   operator \(required, string\): operator to use for evaluation. Valid values:
        -   "exist" – Variable must exist.
        -   "exist\_not" – Variable must not exist.
        -   "is" – Variable must exactly match the provided value \(requires value\).
        -   "is\_not" – Variable must not match the provided value \(requires value\).


    -   value \(conditionally required, string\): value to evaluate against. Required if operator is "is" or "is\_not"; otherwise, must not be provided.

-   `subjectPattern` \(required\): object containing key-value pairs representing the configured subject pattern fields \("CN", "EMAIL", "L", "OU", "O", "ST", "C"\). Values may include placeholders in the format "$\{variable\}".

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X PUT \
> -H 'Content-Type: application/json' \
> -d '{"description":"<description>","condition":{"variable":"<variable>","operator":"<operator>","value":"<value>"},"subjectPattern":{"<field>":"<value>", ...}}' \
> https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules/<index>
> ```



## Delete a Subject Pattern Rule


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

/api/v1/configuration/connector/onPremises/subjectPatternRules/\{index\}

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

DELETE

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
204 on success
```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

Bad Request \(400\)

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request**:

Path Parameter:

-   `index` \(required, integer\): zero-based index of the subject pattern rule to delete.

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X DELETE \
> https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules/<index>
> ```



## Move a Subject Pattern Rule


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/subjectPatternRules/{id}/move` 

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



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

200 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

Bad Request \(400\)

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request**:

Path Parameter:

-   `id` \(required, integer\): zero-based index of the subject pattern rule to move.

Request Body: A JSON object containing:

-   `position` \(required, integer\): new zero-based index to move the rule to.

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X POST \
> -H 'Content-Type: application/json' \
> -d '{"position": <new_position>}' \
> https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules/<id>/move
> ```



## Generate a Sample Certificate from a Subject Pattern Rule


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

/api/v1/configuration/connector/onPremises/subjectPatternRules/\{index\}/sampleCertificate

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

200 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request**:

Path Parameter:

-   `index` \(required, integer\): zero-based index of the subject pattern rule used to generate the sample certificate.

**Produces**:


<table>
<tr>
<th valign="top">

Format

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

application/pkix-cert

</td>
<td valign="top">

DER-encoded certificate \(binary\)

</td>
</tr>
<tr>
<td valign="top">

application/pkix-cert

</td>
<td valign="top">

PEM-encoded certificate \(Base64 with headers\)

</td>
</tr>
</table>

The response is a downloadable certificate file:

-   **Filename**:
    -   scc\_sample\_cert.der \(for DER\)
    -   scc\_sample\_cert.pem \(for PEM\)


> ### Sample Code:  
> **Curl example for DER format** 
> 
> ```
> curl -i -k -u <user>:<password> -X GET \
> -H 'Accept: application/pkix-cert' \
> "https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules/<index>/sampleCertificate?<placeholder1>=<value1>&<placeholder2>=<value2>"
> ```

> ### Sample Code:  
> **Curl example for PEM format** 
> 
> ```
> curl -i -k -u <user>:<password> -X GET \
> -H 'Accept: application/x-pem-file' \
> "https://<host>:<port>/api/v1/configuration/connector/onPremises/subjectPatternRules/<index>/sampleCertificate?<placeholder1>=<value1>&<placeholder2>=<value2>"
> ```

> ### Caution:  
> -   All required placeholders must be provided. Otherwise, the request fails with *400 Bad Request*.
> -   No extra query parameters are allowed beyond those matching the configured placeholders.
> -   Format \(DER or PEM\) is selected automatically by the `Accept` HTTP header.

