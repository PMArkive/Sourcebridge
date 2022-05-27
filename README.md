
![](https://i.imgur.com/IYlbs3T.png)
# Sourcebridge
Powered by Matterbridge, Sourcebridge is a plugin for AMXX that allows simple bridging between your game servers, Mattermost, IRC, XMPP, Gitter, Slack, Discord, Telegram, and more.  
  
![](https://i.imgur.com/3tcvbb8.png)
  
## Description
  
Using Matterbridge API, this plugin allows you to bridge your game server with a Matterbridge installation, relaying messages from/to a growing number of protocols.  
  
You can also bridge multiple servers together so the players can chat between each one.  
  
  
## Protocols natively supported in Matterbridge

- Mattermost
- IRC
- XMPP
- Gitter
- Slack
- Discord
- Telegram
- Rocket.chat
- Matrix
- Steam ([Bugged](https://github.com/42wim/matterbridge/issues/457) [for](https://github.com/Philipp15b/go-steam/issues/94) [now](https://github.com/SteamRE/SteamKit/issues/561))
- Twitch
- Ssh-chat
- WhatsApp
- Zulip
- Keybase

## Dependencies
  
This plugin requires the following to work:

- **[Sourcemod REST In Pawn](https://forums.alliedmods.net/showthread.php?t=298024)**
- **[A working Matterbridge installation](https://github.com/42wim/matterbridge/wiki/How-to-create-your-config)**

  
## Supported Games
This plugin is supposed to be mod agnostic. All official games should work out of the box.
  
## Installation Instructions

- Download all requirements, plus the .sm file.
- Place include files in the /scripting/includes directory.
- Compile the plugin and install the newly generated .smx file. (Remember to install the latest version of REST In Pawn in your server)

  
## Setting up MatterAMXX
  
This quickstart guide assumes you already have a working Matterbridge installation.  
  
Open your `matterbridge.toml` file and add the following lines:  

```
[api.myserver]
BindAddress="0.0.0.0:1337"
Token="verysecrettoken"
Buffer=1000
RemoteNickFormat="{NICK}"
```

Where "myserver" is goes the name of the relay, you can put anything.  
  
Find your gateway where you want to relay the messages.  

```
[[gateway]]  
name="cstrike"  
enable=true  
  
[[gateway.inout]]  
account="discord.mydiscord"  
channel="general"  
  
[[gateway.inout]]  
account="api.myserver"  
channel="api"
```

Where `cstrike` is goes the gateway name. By default is the mod's gamedir (`cstrike` for Counter-Strike, `valve` for Half-Life, etc) but you can change it using cvars, you can add more `gateway.inout` entries depending on how many protocols do you want to relay messages.  
  
  
## Avatar Spoofing

It's possible to set up avatars for each user on protocols that support it. You need to get a [Steam Web API key](https://steamcommunity.com/dev/apikey) and place it in the respective cvar.
  
## Roadmap
  
As this is a port of my previous project, MatterAMXX. The roadmap is to implement most of its features so you can enjoy Sourcebridge at its fullest. The plugin is already in an usable state but lacks most of MatterAMXX features.
  
## Console Variables 

```
// Enable Sourcebridge.
// -
// Default: "1"
sm_sourcebridge_enabled "1"

// Matterbridge gateway on where Sourcebridge should connect to.
// -
// Default: ""
sm_sourcebridge_gateway ""

// Domain of where your Matterbridge instance is hosted.
// -
// Default: "localhost"
sm_sourcebridge_host "localhost"

// Define whether Sourcebridge should print incoming messages.
// -
// Default: "1"
sm_sourcebridge_incoming "1"

// Define whether Sourcebridge should send server chat messages.
// -
// Default: "1"
sm_sourcebridge_outgoing "1"

// Define whether the plugin should add a zero-width space after the @ sign in the messages.
// -
// Default: "1"
sm_sourcebridge_outgoing_chat_zwsp_at "1"

// Define whether the plugin should output the map name at the start of the game.
// -
// Default: "0"
sm_sourcebridge_outgoing_display_map "0"

// Define whether the plugin should output join messages.
// -
// Default: "1"
sm_sourcebridge_outgoing_join "1"

// Define whether the plugin should output leave messages.
// -
// Default: "1"
sm_sourcebridge_outgoing_quit "1"

// URL pointing to the avatar system messages should use. It takes effect after restart.
// -
// Default: ""
sm_sourcebridge_outgoing_system_avatar ""

// The name of system messages whenever they get send to the Matterbridge instance (join/leaves, kills, etc). It takes effect after restart.
// -
// Default: "Server"
sm_sourcebridge_outgoing_system_name "Server"

// Port on where your Matterbridge instance is running.
// -
// Default: "1337"
sm_sourcebridge_port "1337"

// Protocol of your Matterbridge instance. (http/https)
// -
// Default: "http"
sm_sourcebridge_protocol "http"

// Define how much Sourcebridge should wait before querying new incoming messages. It takes effect after restart.
// -
// Default: "3"
sm_sourcebridge_retry_delay "3"

// Token for Steam API queries. Required for player avatars.
// -
// Default: ""
sm_sourcebridge_steam_token ""

// Token of your Matterbridge gateway.
// -
// Default: ""
sm_sourcebridge_token ""
```
  
# Credits

- 42wim  
    _Main developer of Matterbridge._
- Michael Wieland  
    _His MatterBukkit plugin for Minecraft inspired me to create this._