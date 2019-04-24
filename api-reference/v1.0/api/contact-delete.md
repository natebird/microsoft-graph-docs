---
title: "Delete contact"
description: "Delete a contact."
author: "angelgolfer-ms"
localization_priority: Normal
ms.prod: "outlook"
---

# Delete contact

Delete a contact.
## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Contacts.ReadWrite    |
|Delegated (personal Microsoft account) | Contacts.ReadWrite    |
|Application | Contacts.ReadWrite |

## HTTP request
<!-- { "blockType": "ignored" } -->
A [contact](../resources/contact.md) from a user's default [contactFolder](../resources/contactfolder.md).
```http
DELETE /me/contacts/{id}
DELETE /users/{id | userPrincipalName}/contacts/{id}
```
A [contact](../resources/contact.md) from a user's top level [contactFolder](../resources/contactfolder.md).
```http
DELETE /me/contactFolders/{id}/contacts/{id}
DELETE /users/{id | userPrincipalName}/contactFolders/{id}/contacts/{id}
```
A [contact](../resources/contact.md) contained in a child folder of a [contactFolder](../resources/mailfolder.md). The 
example below shows one level of nesting, but a contact can be located in a child of a child and so on.
```http
DELETE /me/contactFolder/{id}/childFolders/{id}/.../contacts/{id}
DELETE /users/{id | userPrincipalName}/contactFolders/{id}/childFolders/{id}/contacts/{id}
```
## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns `204 No Content` response code. It does not return anything in the response body.

## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "delete_contact"
}-->
```http
DELETE https://graph.microsoft.com/v1.0/me/contacts/{id}
```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```
#### SDK Sample Code
# [C#](#tab/CS)
[!INCLUDE [Sample Code]( ../includes/delete_contact-CS-snippets.md)]

# [Javascript](#tab/Javascript)
[!INCLUDE [Sample Code]( ../includes/delete_contact-Javascript-snippets.md)]

---

Read the [SDK documentation](https://docs.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://docs.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://docs.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/v1.0/api/contact-delete.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/delete_contact-CS-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/v1.0/api/contact-delete.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/delete_contact-Javascript-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}-->
