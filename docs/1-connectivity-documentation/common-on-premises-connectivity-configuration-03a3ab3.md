<!-- loio03a3ab39cd544e37871b0bf75ad6ca5f -->

# Common On-Premises Connectivity Configuration

Read the Cloud Connector's on-premises connectivity settings via API.



<a name="loio03a3ab39cd544e37871b0bf75ad6ca5f__section_rcp_l1b_vcb"/>

## Get Principal Propagation Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/pp` 

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
{expirationTolerance, certificateValidity, orderedSubjectPatternRules=[orderedSubjectPatternRule]}
where orderedSubjectPatternRule = {order, subjectPattern, condition={condition}, description}
where condition is either {variable, unary operation} or {variable, binary operation, value}
unary operation - EXISTS, NOT_EXISTS, binary operations - IS, IS_NOT
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

Administrator, Subaccount Administrator, Support, Display

</td>
</tr>
</table>

**Response:**

An array of objects, each of which represents a HANA service channel through the following properties:

-   `expirationTolerance`: expiration tolerance in hours
-   `certificateValidity`: certificate validity in minutes
-   `orderedSubjectPatternRules`: array of subject pattern rules
-   `order`: order as number starting with 1
-   `subjectPattern`: port of the HANA service channel \(a number\)
-   `condition`: Boolean flag indicating whether the channel is enabled and therefore should be open.
-   `description`: comment or short description; this property is not supplied if no comment was provided.

> ### Note:  
> `condition` is an object consisting in a condition operation \{variable, condition operation, value\}, where condition operation is one of \{EXIST, EXIST\_NOT, IS, IS\_NOT\}.

