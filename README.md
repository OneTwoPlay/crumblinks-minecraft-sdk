# Crumblinks Minecraft SDK

Official Minecraft server plugin for sending player events to the Crumblinks attribution platform.

Download latest plugin:

https://github.com/OneTwoPlay/crumblinks-minecraft-sdk/releases/latest/download/crumblinks-plugin.jar

---

# Supported Servers

* Paper
* Spigot
* Purpur

---

# Installation

1. Download the latest plugin `.jar` file from Releases.

2. Put the file into your server:

```text
/plugins
```

3. Start or restart your Minecraft server.

The plugin will automatically generate:

```text
plugins/Crumblinks/config.yml
```

---

# Configuration

Edit:

```text
plugins/Crumblinks/config.yml
```

Example configuration:

```yaml
api_key: "cl_XXXXXXXX"
tracker_id: "YOUR_TRACKER_ID"
base_url: "https://crumblinks.com"
```

Where:

* `api_key` — Crumblinks API key used for authentication.
* `tracker_id` — tracker id from the Crumblinks dashboard.
* `base_url` — Crumblinks API base URL.

The plugin automatically sends the API key as:

```http
Authorization: Bearer cl_XXXXXXXX
```

---

# API Endpoint

```http
POST https://crumblinks.com/api/v1/event
```

Headers:

```http
Authorization: Bearer cl_XXXXXXXX
Content-Type: application/json
Accept: application/json
```

---

# What This Plugin Does

The plugin automatically sends events from your Minecraft server to Crumblinks.

Currently supported events:

| Event        | Description             |
| ------------ | ----------------------- |
| app_start    | Player joins the server |
| app_purchase | Purchase event          |

---

# Example Event

```json
{
  "tracker_id": "rz7sl-oo4z0",
  "event_type": "app_start",
  "user_id": "550e8400-e29b-41d4-a716-446655440000",
  "username": "Steve",
  "timestamp": "2026-03-12 13:16:33"
}
```

Where:

* `user_id` — player's Minecraft UUID.
* `username` — optional player username.

Important:

Minecraft usernames may change over time.
UUID is permanent and should always be used as the primary identifier.

---

# Event Types

## app_start

Sent when a player joins the server.

Example:

```json
{
  "tracker_id": "rz7sl-oo4z0",
  "event_type": "app_start",
  "user_id": "550e8400-e29b-41d4-a716-446655440000",
  "username": "Steve"
}
```

---

## app_purchase

Purchase or monetization event.

Example:

```json
{
  "tracker_id": "rz7sl-oo4z0",
  "event_type": "app_purchase",
  "user_id": "550e8400-e29b-41d4-a716-446655440000",
  "username": "Steve",
  "value": 9.99,
  "currency": "USD"
}
```

---

# Build From Source

Clone repository:

```bash
git clone https://github.com/OneTwoPlay/crumblinks-minecraft-sdk.git
```

Build:

```bash
gradle build
```

Output:

```text
build/libs/crumblinks-plugin.jar
```

---

# Roadmap

Planned features:

* first_join event
* redeem command
* session tracking
* anti-fraud signals
* batched event delivery

---

# License

MIT
