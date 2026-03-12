
# Crumblinks Minecraft SDK

Official **Minecraft server plugin** for sending player events to **Crumblinks attribution platform**.

Supported servers:

- Paper
- Spigot
- Purpur

---

# What this plugin does

The plugin automatically sends events from your Minecraft server to Crumblinks.

Currently supported events:

| Event | Description |
|------|-------------|
| app_start | Player joins the server |
| app_purchase | Purchase event (manual or integration) |

---

# API Endpoint

POST https://crumblinks.com/api/v1/event

Authorization header:

Authorization: Bearer cl_XXXXXXXX

---

# Installation

1. Download the plugin `.jar` file from Releases.

2. Put the file into your server:

/plugins

3. Start or restart your Minecraft server.

The plugin will generate:

plugins/Crumblinks/config.yml

---

# Configuration

Edit:

plugins/Crumblinks/config.yml

Example configuration:

api_key: "cl_XXXXXXXX"
tracker_id: "YOUR_TRACKER_ID"
base_url: "https://crumblinks.com"

Where:

api_key – Crumblinks API key  
tracker_id – tracker id from dashboard  
base_url – Crumblinks API base URL

---

# Example Event

{
 "tracker_id": "rz7sl-oo4z0",
 "event_type": "app_start",
 "user_id": "player_username",
 "timestamp": "2026-03-12 13:16:33"
}

---

# Event Types

app_start – sent when player joins the server

app_purchase – purchase event

Example:

{
 "tracker_id": "rz7sl-oo4z0",
 "event_type": "app_purchase",
 "user_id": "player_username",
 "value": 9.99,
 "currency": "USD"
}

---

# Build From Source

git clone https://github.com/OneTwoPlay/crumblinks-minecraft-sdk.git

gradle build

Output:

build/libs/crumblinks-1.0.jar

---

License: MIT
