
```Javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookChart = {
  index: {
  }
};

let res = await client.api('/me/drive/items/{id}/workbook/worksheets/{id|name}/charts/ItemAt')
	.version('beta')
	.post({workbookChart : workbookChart});

```