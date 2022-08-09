## Simple Reports Plugin

This simple plugin allows to report players on the server and store that data in MySQL.
Also there is built in Discord Integration that allows server admins to react faster for the reports.

------------

| SUPPORTED GAMES  |   |
| ------------ | ------------ |
|  CSGO |  ✅ |
|  CS:SOURCE |  ✅ |
|  TEAM FORTRESS 2 | ✅  |
|  LEFT 4 DEAD 2 |  ✅ |

**More games might work as well but their gametype will be marked as unknown in database**
**If you test other games and it will work properly. Let me know so i can add official support for it!**

------------
### FEATURES

- An extensive and eye-catching configuration file.
- MySQL support to store Reports with all the data.
- MultiLang support.
- Admin notification on the server + Sound.
- Reports cooldown in seconds (configurable).
- Full Discord Integration (Embed + Normal Messages). Fully configurable through configuration file + A lot options for discord messages.
------------
### COMMANDS
- !report - Main Report Menu.
- !reloadreports - Reload Configuration File (Reuries: Admin_Root permission).
------------
### CONFIGURATION FILE
```
"Reports"
{
    "Main Configuration"
    {
        // Notify admins on the server when a report is made (1 = yes | 0 = no)
        "admin_notification"        "1"

        // Make a sound when notifying admins (1 = yes | 0 = no)
        "admin_notification_sound"  "1"
        "admin_sound_path"          "reports/admin_notify.mp3"      // Sound file path (relative to the "/sounds" directory).

        // Server name stored in the database (and shown in discord notifications)
        "server_name"               "Only Mirage"

        // Plugin chat tag (should end with a space). Multicolors supported!
        "chat_prefix"               "{lightred}[ Reports ]{yellow} "

        // How long after making a report until players can report again (in seconds).
        "reports_cooldown"          "40"
    }

    "Report Reasons"
    {
        // The list of report reasons on the menu. You can add or remove as many as you want.
        // The left side for each must be "reason".
        "reason"    "Camping"
        "reason"    "Inappropriate Behaviour"
        "reason"    "Cheating"
        "reason"    "Mic Abuse"
        "reason"    "AFK"

        // Allow player to input a custom reason for the report (1 = yes | 0 = no).
        "custom_reason"     "1"
    }

    "Discord Integration" 
    {
        // Enable discord integration? (1 = yes | 0 = no).
        "enabled"               "0"

        // Discord channel WebHook that reports will be sent to.
        "webhook"               ""

        // How should notifications be displayed (0 = Normal Message | 1 = Embed (Recommended)).
        "message_mode"          "1"

        // Set the notification bot's user information
        "bot_name"                  "Reports"
        "bot_picture_url"           ""


        // Report message that will be sent to the discord channel.
        // Message must be less than 1000 characters total.
        //
        // You can add lines of text that use any of the following special values:
        //
        //      {server_name}           -- The server name in "Main Configuration".
        //      {server_ip}             -- The server IP and port.
        //      {client_name}           -- Name of player sending report.
        //      {client_steamid64}      -- SteamID64 of player sending report.
        //      {client_steamid3}       -- SteamID3 of player sending report.
        //      {client_steamid2}       -- SteamID2 of player sending report.
        //      {client_profile}        -- Steam Profile URL of player sending report.
        //      {reported_name}         -- Name of the player being reported.
        //      {reported_steamid64}    -- SteamID64 of the player being reported.
        //      {reported_steamid3}     -- SteamID3 of the player being reported.
        //      {reported_steamid2}     -- SteamID2 of the player being reported.
        //      {reported_profile}      -- Steam Profile URL of the player being reported.
        //      {report_reason}         -- The reason for the report.
        //      {mentions_list}         -- List of role mentions (See "Mention Roles").
        //
        // Discord can display clickable text if you use a URL like this:
        //      [Click Here](https://www.google.com/)
        //
        // For example:
        //      [Reported Player Profile]({client_profile})
        //
        "Message Text"
        {
            "line" "Server: {server_name} (IP: {server_ip})"
            "line" "Player: [{client_name}]({client_profile})"
            "line" "Reported: [{reported_name}]({reported_profile})"
            "line" ""
            "line" "Reason: {report_reason}"
            "line" ""
            "line" ""
            "line" "{mentions_list}"
        }


        // Roles that will be mentioned when a report notification is sent.
        // Left side is the role name (has no effect, it's just for organisation).
        // Right side is the Discord role ID written as <@&ROLEID>.
        // Example: <@&1005717394817286184>
        //
        // You can find these IDs by going to:
        //      Discord Server Settings > Roles > ... > Copy ID
        //
        "Mention Roles"
        {
            "Put role name or whatever"        "<@&ROLEID>"    
        }


        // Embed notification settings (used if "message_mode" is "1")
        "Embed Mode"
        {
            // Report title text.
            "embed_title"               "New Report"

            // Message title text (sub-header).
            "embed_field_name"          "Report Information 👇"

            // Embed colour (in hex).
            // This site might help: https://htmlcolorcodes.com/
            "embed_color"               "#ff2222"

            // Footer message text.
            "embed_footer"              "Simple Reports by Mesharsky"

            // Thumbnail picture URL for the embed message.
            "embed_thumbnail_url"       ""
        }
    }
}
```
### INSTALLATION






