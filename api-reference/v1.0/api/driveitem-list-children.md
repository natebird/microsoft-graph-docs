---
author: JeremyKelley
ms.author: JeremyKelley
ms.date: 09/10/2017
title: List the contents of a folder
localization_priority: Priority
ms.prod: "sharepoint"
---
# List children of a driveItem

Return a collection of [DriveItems](../resources/driveitem.md) in the **children** relationship of a DriveItem.

DriveItems with a non-null **folder** or **package** facet can have one or more child DriveItems.


## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Files.Read, Files.ReadWrite, Files.Read.All, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All    |
|Delegated (personal Microsoft account) | Files.Read, Files.ReadWrite, Files.Read.All, Files.ReadWrite.All    |
|Application | Files.Read.All, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET /drives/{drive-id}/items/{item-id}/children
GET /groups/{group-id}/drive/items/{item-id}/children
GET /me/drive/items/{item-id}/children
GET /sites/{site-id}/drive/items/{item-id}/children
GET /users/{user-id}/drive/items/{item-id}/children
```

## Optional query parameters

This method supports the `$expand`, `$select`, `$skipToken`, `$top` and `$orderby` [OData query parameters](/graph/query-parameters) to customize the response.

### Optional request headers

| Name     | Value | Description                                                                                                                                              |
|:----------------|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| _if-none-match_ | etag  | If this request header is included and the eTag (or cTag) provided matches the current tag on the file, an `HTTP 304 Not Modified` response is returned. |

## Examples

### List children in the root of the current user's drive

To retrieve files in the root of the drive, use the `root` relationship on the drive, then access the children relationship.

<!-- { "blockType": "request", "name": "list-children-root", "scopes": "files.read", "tags": "service.graph" } -->

```http
GET /me/drive/root/children
```


### List children of a DriveItem with a known ID

To retrieve files in the root of the drive, use the `root` relationship on the drive, then access the children relationship.

<!-- { "blockType": "request", "name": "list-children", "scopes": "files.read" } -->

```http
GET /drives/{drive-id}/items/{item-id}/children
```
#### SDK Sample Code
# [C#](#tab/CS)
[!INCLUDE [Sample Code]( ../includes/list-children-root-CS-snippets.md)]

# [Javascript](#tab/Javascript)
[!INCLUDE [Sample Code]( ../includes/list-children-root-Javascript-snippets.md)]

---

Read the [SDK documentation](https://docs.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://docs.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://docs.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.


### List children of a DriveItem with a known path

<!-- { "blockType": "request", "name": "list-children-from-path", "scopes": "files.read" } -->

```http
GET /drives/{drive-id}/root:/{path-relative-to-root}:/children
```
#### SDK Sample Code
# [C#](#tab/CS)
[!INCLUDE [Sample Code]( ../includes/list-children-CS-snippets.md)]

# [Javascript](#tab/Javascript)
[!INCLUDE [Sample Code]( ../includes/list-children-Javascript-snippets.md)]

---

Read the [SDK documentation](https://docs.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://docs.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://docs.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.


## Response

If successful, this method returns the list of items in the children collection of the target item.
The children collection will be composed of [driveItem][item-resource] resources.

<!-- { "blockType": "response", 
       "@odata.type": "Collection(microsoft.graph.driveItem)", 
       "truncated": true,
       "name": [ "list-children-root", "list-children", "list-children-from-path" ] } -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {"name": "myfile.jpg", "size": 2048, "file": {} },
    {"name": "Documents", "folder": { "childCount": 4} },
    {"name": "Photos", "folder": { "childCount": 203} },
    {"name": "my sheet(1).xlsx", "size": 197 }
  ],
  "@odata.nextLink": "https://..."
}
```

**Note:** If a collection exceeds the default page size (200 items), the **@odata.nextLink** property is returned in the response to indicate more items are available and provide the request URL for the next page of items.

You can control the page size through [optional query string parameters](https://developer.microsoft.com/graph/docs/concepts/query_parameters)

### Error responses

See [Error Responses][error-response] for more info about
how errors are returned.

[error-response]: /graph/errors
[item-resource]: ../resources/driveitem.md

<!-- {
  "type": "#page.annotation",
  "description": "List the children of an item.",
  "keywords": "list,children,collection",
  "section": "documentation",
  "tocPath": "Items/List children",
  "suppressions": [
    "Error: /api-reference/v1.0/api/driveitem-list-children.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/list-children-CS-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/v1.0/api/driveitem-list-children.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/list-children-Javascript-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/v1.0/api/driveitem-list-children.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/list-children-root-CS-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)",
    "Error: /api-reference/v1.0/api/driveitem-list-children.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [Sample Code]( ../includes/list-children-root-Javascript-snippets.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
} -->
