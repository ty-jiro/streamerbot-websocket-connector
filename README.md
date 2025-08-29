

# Streamer.bot Link

This plugin is used to bridge Streamer.bot to Godot to receive data from events, commands, etc..

You can create a StreamerBot node anywhere in your scene and fill out the IP and port of your WebSocket server in the inspector. You should extend the default StreamerBot script in order to customize what you need. There are included examples if you need help getting started.



## Download
Downloads are only available to Patrons at this time! You can check out the Patreon post [here](https://www.patreon.com/posts/116474230).


## Installation
Extract the 'streamerbot_link' folder into res://addons/
Enable the 'Streamer.bot Link' addon in Project Settings (Project > Project Settings > Plugins)

## Creating a Connection
Add a StreamerBot node to your scene and make configurations in the Inspector. You can set the address (ip) and port in order to connect it to your Streamer.bot instance.

## Subscribing to Events
Subcribe to events by configuring them in the Inspector.

You can go to the **'Subscriptions'** section, then **'Subscribe Events'**, and click the box that says **'Array[StreamerBotSubscription]'**. Click the '**Add Element'** box, next click on the **'empty'** box, then select **'New StreamerBotSubscription'**. From there, you can fill out the **'Source'** (e.g. Twitch or Youtube) and add elements into the array for the events you want to subscribe to (e.g. Follow, RewardRedemption, Sub, etc.).

*Example of the Subscribe Events settings:*
![enter image description here](https://media.discordapp.net/attachments/1144044962124681226/1410468131444494428/image.png?ex=68b1204f&is=68afcecf&hm=7de9580393d4cf513024e68554298164fa9ca2b492ad7cfc22dddbe355ec1180&=&format=webp&quality=lossless&width=1383&height=866)

## Tutorials
- [Setting up Streamer bot Link plugin for Godot](https://www.youtube.com/watch?v=rnlj1PB6lF8) (video)

## Properties
| Variable | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `eventsub` | `WebSocketPeer` | The WebSocket connection to Streamer.bot. |
| `ip` | `String` | The IP of the Streamer.bot WebSocket server. |
| `port` | `String` | The port of the Streamer.bot WebSocket server. |
| `url` | `String` | The full URL of the Streamer.bot WebSocket server. |
| `auto-reconnect` | `bool` | Automatically attempt to reconnect to the Streamer.bot WebSocket server. |

## StreamerBot Node - Method Descriptions

### connect_to_event_sub()
Establishes a connection to Streamer.bot's EventSub

### do_action(id: String, guid: String)
Execute an action on the connected Streamer.bot instance. 'id' can be any String you want, mostly for organization. 'guid' is the Streamer.bot action ID that you want to execute.

#### Example:
```py
do_action("Action Name", "SB_ACTION_ID")
```

### subscribe(id: String, events: Dictionary)
Subscribe to a set of events from the connected Streamer.bot instance. 'id' can be any String you want, mostly for organization. 'events' is a Dictionary with the names of events you want to subscribe to.
#### Example:
```py
subscribe("Twitch", {
		"Twitch": [
			"ChatMessage",
			"Follow",
			"RewardRedemption",
			"Sub",
			"ReSub",
			"GiftSub",
			"RewardRedemption",
		]
	})
```

### unsubscribe(id: String, events: Dictionary)
Unsubscribe from any events that are currently subscribed to. 'id' can be any String you want, mostly for organization. 'events' is a Dictionary with the names of events you want to unsubscribe to.

## StreamerBotAlertQueue - Method Descriptions

### add_to_queue(alert: StreamerBotAlertData)
Add an alert to the queue

### play_alert(alert_data: StreamerBotAlertData)
Play an alert, then delete it when it's finished

## StreamerBotEventHandler - Method Descriptions
### handle(type: String, data: Dictionary)
Define a way to handle an alert
