---
author: JeremyKelley
ms.author: JeremyKelley
ms.date: 09/10/2017
title: Upload small files
localization_priority: Normal
ms.prod: "sharepoint"
---
# Upload or replace the contents of a DriveItem

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

The simple upload API allows you to provide the contents of a new file or update the contents of an existing file in a single API call. 
This method only supports files up to 4MB in size.

To upload large files see [Upload large files with an upload session](driveitem-createuploadsession.md).

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Files.ReadWrite, Files.ReadWrite.All, Sites.ReadWrite.All    |
|Delegated (personal Microsoft account) | Files.ReadWrite, Files.ReadWrite.All    |
|Application | Files.ReadWrite.All, Sites.ReadWrite.All |

## HTTP request (to replace an existing item)

<!-- { "blockType": "ignored" } -->

```http
PUT /drives/{drive-id}/items/{item-id}/content
PUT /groups/{group-id}/drive/items/{item-id}/content
PUT /me/drive/items/{item-id}/content
PUT /sites/{site-id}/drive/items/{item-id}/content
PUT /users/{user-id}/drive/items/{item-id}/content
```

## HTTP request (to upload a new file)

<!-- { "blockType": "ignored" } -->

```http
PUT /drives/{drive-id}/items/{parent-id}:/{filename}:/content
PUT /groups/{group-id}/drive/items/{parent-id}:/{filename}:/content
PUT /me/drive/items/{parent-id}:/{filename}:/content
PUT /sites/{site-id}/drive/items/{parent-id}:/{filename}:/content
PUT /users/{user-id}/drive/items/{parent-id}:/{filename}:/content
```

## Request body

The contents of the request body should be the binary stream of the file to be uploaded.

## Response

If successful, this method returns a [driveItem](../resources/driveitem.md) object in the response body for the newly created or updated file.

## Example (upload a new file)

This example uploads the string "The contents of the file goes here." to a file in the signed-in user's drive under FolderA named FileB.txt.

<!-- { "blockType": "request", "name": "upload-via-put", "scopes": "files.readwrite" } -->

```http
PUT /me/drive/root:/FolderA/FileB.txt:/content
Content-Type: text/plain

The contents of the file goes here.
```

### Response

If successful, this method returns an [driveItem][item-resource] resource in the response body for the newly created file.

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true } -->

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0123456789abc",
  "name": "FileB.txt",
  "size": 35,
  "file": { }
}
```

## Example (updating an existing file)

This example replaces the contents of a file with a known ID.

<!-- { "blockType": "request", "name": "upload-via-put-id", "scopes": "files.readwrite" } -->

```http
PUT /me/drive/items/{item-id}/content
Content-Type: text/plain

The contents of the file goes here.
```

### Response

If successful, this method returns an [driveItem][item-resource] resource in the response body for the newly created file.

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true } -->

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0123456789abc",
  "name": "FileB.txt",
  "size": 35,
  "file": { }
}
```
#### SDK Sample Code
# [C#](#tab/CS)
[!INCLUDE [Sample Code]( ../includes/upload-via-put-id-CS-snippets.md)]

# [Javascript](#tab/Javascript)
[!INCLUDE [Sample Code]( ../includes/upload-via-put-id-Javascript-snippets.md)]

---

Read the [SDK documentation](https://docs.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://docs.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://docs.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.


## Error responses

See [Error Responses][error-response] for details about
how errors are returned.

[error-response]: /graph/errors
[item-resource]: ../resources/driveitem.md

<!--
{
  "type": "#page.annotation",
  "description": "Create a new file with content or update a file's content.",
  "keywords": "insert,upsert,update,upload",
  "section": "documentation",
  "suppressions": [
    "Error: /api-reference/beta/api/driveitem-put-content.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/upload-via-put-id-CS-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/beta/api/driveitem-put-content.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/upload-via-put-id-Javascript-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/beta/api/driveitem-put-content.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->
