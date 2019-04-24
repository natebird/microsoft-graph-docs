
```CS

GraphServiceClient graphClient = new GraphServiceClient( authProvider );

var message = await graphClient.Me.Messages
	.Request()
	.Filter("MentionsPreview/IsMentioned eq true,")
	.Select( e => new {
			 e.Subject,
			 e.Sender,
			 e.ReceivedDateTime,
			 e.MentionsPreview 
			 })
	.GetAsync();

```