
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var device = new Device
{
	AccountEnabled = false,
};

await graphClient.Devices["{id}"]
	.Request()
	.UpdateAsync(device);

```