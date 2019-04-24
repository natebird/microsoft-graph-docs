
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var receiversList = new List<String>();
receiversList.Add( "550fae72-d251-43ec-868c-373732c2704f" );

var sourcesList = new List<String>();
sourcesList.Add( "632899f8-2ea1-4604-8413-27bd2892079f" );

var AudioRoutingGroup = new AudioRoutingGroup
{
	Id = "oneToOne",
	RoutingMode = RoutingMode.OneToOne,
	Sources = sourcesList,
	Receivers = receiversList,
};

await graphClient.App.Calls["{id}"].AudioRoutingGroups
	.Request()
	.AddAsync(AudioRoutingGroup);

```