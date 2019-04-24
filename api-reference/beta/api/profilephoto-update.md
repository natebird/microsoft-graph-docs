---
title: "Update profilephoto"
description: "Update the photo for any user in the tenant including the signed-in user, or the specified group or contact. Since there"
localization_priority: Normal
---

# Update profilephoto

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the photo for any user in the tenant including the signed-in user, or the specified group or contact. Since there
is currently a limit of 4MB on the total size of each REST request, this limits the size of the photo
you can add to under 4MB.

Use only PUT for this operation in the beta version.

> **Note** The update photo operation in beta supports only the user's work or school mailboxes and not personal mailboxes.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account)     | Profile photo of the signed-in **user**:<br/>User.ReadWrite, User.ReadWrite.All<br /><br />For **group** resource:<br />Group.ReadWrite.All<br /><br />For **contact** resource:<br />Contacts.ReadWrite |
|Delegated (personal Microsoft account) | Not supported. |
|Application                            | For **user** resource:<br/>User.ReadWrite.All<br /><br />For **group** resource:<br />Group.ReadWrite.All<br /><br />For **contact** resource:<br />Contacts.ReadWrite |

> **Note** To update the photo of any user in the organization, your app must have the User.ReadWrite.All application permission and call this API under its own identity, not on behalf of a user. To learn more, see [get access without a signed-in user](/graph/auth-v2-service).

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
PUT /me/photo/$value
PUT /users/{id | userPrincipalName}/photo/$value
PUT /groups/{id}/photo/$value
PUT /me/contacts/{id}/photo/$value
PUT /users/{id | userPrincipalName}/contacts/{id}/photo/$value
PUT /me/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
PUT /users/{id | userPrincipalName}/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
```
## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |
| Content-Type  | image/jpeg. Required.  |

## Request body
In the request body, include the binary data of the photo in the request body.

## Response

If successful, this method returns a `200 OK` response code.
## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "update_profilephoto"
}-->
```http
PUT https://graph.microsoft.com/beta/me/photo/$value
Content-type: image/jpeg

Binary data for the image

```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.profilePhoto"
} -->
```http
HTTP/1.1 200 OK
```
#### SDK Sample Code
# [C#](#tab/CS)
[!INCLUDE [Sample Code]( ../includes/update_profilephoto-CS-snippets.md)]

# [Javascript](#tab/Javascript)
[!INCLUDE [Sample Code]( ../includes/update_profilephoto-Javascript-snippets.md)]

---

Read the [SDK documentation](https://docs.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://docs.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://docs.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Update profilephoto",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/profilephoto-update.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/update_profilephoto-CS-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/beta/api/profilephoto-update.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/update_profilephoto-Javascript-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/beta/api/profilephoto-update.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->
