
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var values = new SettingValue
{
	Name = "name-value",
	Value = "value-value",
};

var valuesList = new List<SettingValue>();
valuesList.Add( values );

var directorySetting = new DirectorySetting
{
	Values = valuesList,
};

await graphClient.Settings["{id}"]
	.Request()
	.UpdateAsync(directorySetting);

```