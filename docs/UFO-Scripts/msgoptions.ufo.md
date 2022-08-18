This script file allows you to define default settings for message
notifications on game startup. These settings are stored for every
savegame, as it is intended that default settings may be changed during
gameplay (e.g. you are no longer interested in some message categories).

Actually there is only one default msgoptions section, which contains
lines in the following format. Every line describes a positiv (checked)
option - all missing values are considered to be unchecked.

    msgoptions default {
        <notify_type> <pause|notify|sound>
    }

pause
stop game time if event associated with notify_type occurs

notify
create a notification message for notify_type event

sound
play notification sound for message if available

See and for available notification types. **MSO_CheckAddNewMessage**
should be used to add new messages. This method checks whether to add a
message, play sound and whether to stop game time.

See [this howto](Include_new_notify_types "wikilink") to include more
notify types.

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")