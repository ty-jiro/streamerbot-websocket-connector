
# Streamer.bot WebSocket Connector

This plugin is used to bridge Streamer.bot to Godot to receive data from events, commands, etc..

You can create a StreamerBot node anywhere in your scene and fill out the IP and port of your WebSocket server in the inspector. You should extend the default StreamerBot script in order to customize what you need. There is an included GDScript named 'streamerbot_example.gd' if you need help getting started.



## Authors

- [@tyjiro](https://www.twitter.com/TYJlRO)


## Installation
Extract StreamerbotConnector folder into res://addons/
Enable addon in Project Settings (Project > Project Settings > Plugins)

## Creating a Connection
Add a StreamerBot node to your scene and extend the script, or create a script and make an autoload. Fill out the IP and port of your Streamer.bot WebSocket Server.


## Properties
| Variable | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `eventsub` | `WebSocketPeer` | The WebSocket connection to Streamer.bot. |
| `ip` | `String` | The IP of the Streamer.bot WebSocket server. |
| `port` | `String` | The port of the Streamer.bot WebSocket server. |
| `url` | `String` | The full URL of the Streamer.bot WebSocket server. |
| `auto-reconnect` | `bool` | Automatically attempt to reconnect to the Streamer.bot WebSocket server. |


## Method Descriptions
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

### unsubscribe()
Unsubscribe from any events that are currently subscribed to. 'id' can be any String you want, mostly for organization. 'events' is a Dictionary with the names of events you want to unsubscribe to.
