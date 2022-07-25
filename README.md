# Eyepatch

Receive mobile notifications when new episodes of your favorite TV series are released.


## How does this work?

It is assumed that new episodes of popular series will be found on The Pirate Bay (TPB). This script, then, looks for episodes on TPB and notifies you if a new episode is found from a TV series that you are tracking. 


## Setting this up

You should follow these few steps to correctly set up `Eyepatch`.

### Requirements

* This script definitely works on Linux, probably works on macOS, and maybe works on Windows (with some tweaks).
* You need to have [jq](https://github.com/stedolan/jq) installed on your computer.
* You need to install the [ntfy app](https://ntfy.sh/docs/subscribe/phone/) on your phone.

### Initial setup

First, you need to define the values of three variables inside `eyepatch.sh`:
1. `ntfy_topic`: The name of the topic you will subscribe to in the ntfy app to receive the notifications. Choose a topic name that is unique to you, as anyone who knows this name can view or send notifications to this topic!
2. `track_file`: The full path of the file containing the list of TV series to track.
3. `log_file`: The full path of the file where the logs will be written.

Second, you need to subscribe to the same topic name as `ntfy_topic`, on the [ntfy app](https://ntfy.sh/docs/subscribe/phone/) on your phone.

Finally, you will want to run this script periodically (ideally once per day), either as a cron job or with a systemd service.

### Contents of `track_file`

The file you have assigned to the variable `track_file` should follow the following format:
* One TV series per line.
* On each line: The name of the series, followed by the season number and the episode number you want to start tracking at.

#### Examples

If you want track [Only Murders in the Building](https://www.imdb.com/title/tt12851524/) **starting with S02E04**, then the matching line in `track_file` for that series should be:

> Only Murders in the Building 2 4

If you want to track [The Rings of Power](https://www.imdb.com/title/tt7631058/), a yet **unreleased** series (at the time of this writing), then the matching line in `track_file` should just be the series name:

> The Rings of Power

Take note that the way torrents are generally named on TPB, you should track `The Rings of Power` rather than `The Lord of the Rings: The Rings of Power`.
