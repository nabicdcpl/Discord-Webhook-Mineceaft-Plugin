# Discord-Webhook-Mineceaft-Plugin
I'm a newbie, so packaging might feel strange because I'm still learning how to use GitHub. 

📡 Discord Status — Server Online/Restart + Player Count via Webhook
EndStone 0.11+ · Bedrock Dedicated Server · MIT · No bot required
Your server's heartbeat, straight to Discord.
The problem
Players constantly ask "is the server up?" — and you don't want to run and host a whole Discord bot just to tell them. A webhook is all you actually need.
What it does
When your server starts, it posts a clean ONLINE announcement to your Discord channel with the IP/Port and an optional @everyone ping. While the server is up, it keeps the live player count updated on that same message. When the server stops or restarts, that message flips to "Restarting…" automatically. No spam, no bot, no hosting.
Features
🟢 Online announcement on startup — IP, Port, optional @everyone (or role) ping
👥 Live player count refreshed on the same message (edits in place — no channel spam, no re-pinging)
🔄 Restart notice — the message turns red on shutdown, so players always know the current state
🪶 Webhook only — no bot token, no separate process, nothing extra to keep alive
🎨 Fully customizable — title, description, colors, thumbnail, footer, and mention text all editable
🧩 One tidy status message per session instead of an ever-growing wall of posts
How it works (for the curious)
The online announcement is created with ?wait=true so the plugin captures the message ID, then updates run as PATCH edits to that message (embeds only, so @everyone never re-fires). The shutdown notice is sent synchronously inside on_disable because the process is about to exit. All network calls use the Python standard library — no extra packages.
Requirements
EndStone 0.11+
A Discord webhook URL (Channel → Edit Channel → Integrations → Webhooks → New Webhook → Copy URL)
Install
Download the .whl from the release below and drop it in plugins/.
Restart the server.
Set your webhook and test:
Code
If the test message lands in your channel, you're done — every start now announces automatically.
Commands (OP)
Command
Description
/discord setwebhook <url>
Set the webhook URL
/discord test
Send a test message (no ping)
/discord now
Re-post the online announcement (pings @everyone again)
/discord restart
Send the "restarting" message
/discord status
Show current settings
/discord reload
Reload config
Alias: /dc
Config highlights (config.json)
mention_text — use <@&ROLE_ID> to ping a specific role instead of @everyone
max_players — shows X / Y; set 0 to hide the cap
online_title / online_desc / online_color — fully rebrand the announcement
update_interval_sec — how often the player count refreshes (default 60s)
⚠️ The webhook URL contains a secret token. Keep it private; reset it in Discord if it ever leaks.
License
MIT — free to use, modify, and redistribute.
Made by LimitTRACK. Feedback, issues, and PRs welcome!
