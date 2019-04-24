
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var workbookRange = await graphClient.Me.Drive.Items["{id}"].Workbook.Names["name"].Range().UsedRange()
	.Request()
	.GetAsync();

```