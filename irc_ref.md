# IRC Commands Reference

## Reference for call participants
People that are participating in the meeting will find these commands useful:

* voip: ```<last 3 digits of SIP/...>``` is ```<alias>``` - Associate a voice channel with an IRC nickname. [Details](#associate-a-voice-channel-with-an-irc-nickname)
* /me ```TEXT``` - Say something off of the record. Everything else you type is recorded in the official transcript. [Details](#say-something-off-the-record)
* q? - See who is on the speaker queue.
* q+ - Add yourself to the speaker queue.
* q+ to say ```TEXT``` - Add yourself to the speaker queue while including a reminder to yourself on what you want to say.
* q+ ```<alias>``` - Add someone else to the speaker queue.
* q- ```<alias>``` - Remove someone from the speaker queue.
* ack ```<alias>``` - Acknowledge someone to speak from the speaker queue.

## Reference for people running the meeting and scribes

People that are running the meeting may find these commands useful:

* agenda: ```<URL>``` - Specify the link for the meeting agenda. [Details](#posting-an-agenda)
* scribe: ```<alias>``` - Specify the IRC nickcname of the person that is scribing. 
* ```<alias> <TEXT>``` - (For scribe) Record what alias said [Details](#scribing)
* topic: ```TEXT``` - Set the current topic of discussion.
* voip: number? - Get the dial in numbers for the call. (TODO: is this right? I thought it was connections? )
* voip: connections? - Get the dial in numbers for the call. [Details](#list-connections)
* voip: noisy? - See which audio channels are being noisy. Useful for finding distracting audio from participants.
* voip: mute ```<last 3 digits of SIP/...>``` - Mute an audio channel.
* voip: unmute ```<last 3 digits of SIP/...>``` - Unmute an audio channel.
* voip: disconnect ```<last 3 digits of SIP/...>``` - Disconnect an audio channel.
* chair: ```<alias>``` - Specify the person running the meeting.
* meeting: ```<TEXT>``` - Specify the title of the meeting.
* date: ```<YYYY-MM-dd>``` - Specify the date of the meeting. Useful when creating minutes after the fact.
* action: ```<TEXT>``` - Add an action item

## IRC Command Details

### Associate a voice channel with an IRC nickname

#### Command

```
voip: <last 3 digits of SIP/...> is <alias>
```

#### Example

Suppose your alias is `kimhd` and phone number is 555-222-1212. Look for your phone number in the chat window and get the last 3 digits from the adjacent string `[SIP/xx.xx.xx.xxx-xxxxxxxx]`

```
[09:01] <voip-vctf> 15552221212 [SIP/69.77.77.777-00000174] has joined the conference.
```

The last 3 digits are `174`. You would enter command:

```
voip: 174 is kimhd
```

### Say something off the record

#### Command

```
/me <your message>
```

#### Example

```
/me can you speak up please?
```

### Posting an agenda

#### Command

```
Agenda: <agenda link>
```

#### Example

```
Agenda: https://lists.w3.org/Archives/Public/public-credentials/2017Jul/0040.html
```

### List connections

#### Command

```
voip: connections?
```

### Scribing

#### Command

```
<alias>: <what they said>
```

#### Example

Suppose ChristopherA is scribing, and kimhd says "The next thing we will discuss is the DID spec"

ChristopherA would type:
```
kimhd: The next thing we will discuss is the DID spec
```

To continue, and avoid repeating the author name, type `...` (on the new line)

# Scribe and Minutes Publishing Training Video

See a video recording of our training session demonstrating how to scribe (1st half of the video) and how to publish minutes (2nd half). Available [https://youtu.be/0Sn7co2eSCo](https://youtu.be/0Sn7co2eSCo).

# Publishing the Minutes

This section documents how one can clean up and publish minutes.

At the end of every call, the raw IRC log and audio recording are uploaded to:

* https://w3c-ccg.s3.digitalbazaar.com/minutes/YYYY-MM-DD-irc.log
* https://w3c-ccg.s3.digitalbazaar.com/minutes/YYYY-MM-DD-audio.wav

What follows is how you take those raw files and process them to generate the finalized minutes for the meeting.

## Setup

To publish the minutes, you must have the meetings Github repository checked out. WARNING: This is a very large, multi-gigabyte repository, don't try to download it without a good Internet connection. These instructions should work for Linux and Mac OS X systems.

1. `git clone git@github.com:w3c-ccg/meetings.git w3c-ccg-meetings`
1. `cp publishing.cfg.example publishing.cfg`
1. Update the `EDITOR` to your desired editor in publishing.cfg
1. Install an audio editor update the associated variable in publishing.cfg. The default editor used in the config file is [audacity](https://www.audacityteam.org/download/).
1. Enable api access to your Twitter account and update the associated variables in publishing.cfg
    1. Go to https://apps.twitter.com/
    1. Select "Create New App"
    1. You can fill out any details; don't need a callback
    1. Populate the SCRAWL_TWITTER_* variables in publishing.cfg
1. [NOT IMPLEMENTED YET: feel free to skip this step] Enable api access to your LinkedIn account and update associated variables in publishing.cfg
    1. Go to https://www.linkedin.com/developer/apps
    1. Select "Create Application"
    1. After filling in details, generate a client id and secret
    1. Populate the SCRAWL_LINKEDIN_* variables in publishing.cfg 
1. Update publishing.cfg with your SMTP information for sending emails.
    - If you don't have one, you can use Google's free SMTP server https://kinsta.com/knowledgebase/free-smtp-server/
    - Update the SCRAWL_EMAIL_* variables in publishing.cfg 

## Download
Download the raw minutes:

1. Run the `download-raw-minutes` script; flags/options are described below
    - `./download-raw-minutes` downloads the raw minutes and audio for the current date.
    - `./download-raw-minutes -l` downloads the raw minutes and audio for the current date and autolaunches the text and video editors afterward.
    - `./download-raw-minutes -d [YYYY-MM-DD]` downloads the raw minutes and audio for the specified date.
    - `./download-raw-minutes -h` prints help
1. Minutes and audio are placed in a directory formatted as [YYYY-MM-DD], (e.g. `2018-01-09`)

## Edit
Edit the downloaded minutes:

1. Clean up the audio:
    - Open the audio-raw.wav file in an editor (see setup above):
    - Delete all audio before the Chair starts talking about the Agenda
    - Delete all audio after the first person hangs up at the end of the call.
    - Save the new file as audio.wav or encode to .ogg (file name audio.ogg) at 32kbps
        - For example: `oggenc -b 32 audio.wav`
2. Clean up the minutes
    - Go to https://w3c-ccg.github.io/meetings/scribe-tool/ and copy/paste irc.log into the text input box at the bottom. 
    - Clean up the IRC log accordingly and overwrite irc.log with the edited file.
    - Things to check
        - Look for any find/replace suggestions in irc.log and update them (s/../..)
        - Ensure aliases have matches

## Publish
Publish the minutes:

1. `cd ../scribe-tool`
1. `./publish -d ../<LATEST_MINUTES_DIRECTORY>` (e.g. `./publish -d ../2018-01-09`)

If there are no errors, the latest minutes should now be published.

## Debugging issues

If using gmail's SMTP server, you may get an error message (ending like below) the first time; if so, just check your email to enable API access. 

```
   { Error: bad response on command 'cjdHOTJkNGI='
     ...
     code: 2,
     smtp: '534-5.7.14 <https://accounts.google.com/signin/continue?sarp=1&scc=1&plt=AKgnsbvh\n534-5.7.14 IaUhK_-5AOCdpwIXJl2IjOdVTpJv15b1PByBixau67mqEq0Fll-90x-7pW_ffwpwGtNW1T\r\n534-5.7.14 B7nokaCYy9MsgZtK0_VFQsfj8NJks30BNBStBSJCwWQ4q_cih92MPe9UguqixShXYA1S3r\r\n534-5.7.14 6O9N-0wdU-QbrVawNogjL-z_lpAYFeaafanfWWlfBzRdI-tIz8JbNMYmiAbbq0AkyFo2TO\r\n534-5.7.14 QF_I9lGHt5nDzIsmW_5lyHxOC7fLQ> Please log in via your web browser and\r\n534-5.7.14 then try again.\r\n534-5.7.14  Learn more at\r\n534 5.7.14  https://support.google.com/mail/answer/78754 63-v6sm4339204pgi.4 - gsmtp\r\n' },
  smtp: undefined }

```
