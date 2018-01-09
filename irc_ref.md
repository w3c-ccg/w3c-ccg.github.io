# IRC Commands Reference

People that are participating in the meeting will find these commands useful:

* voip: number? - Get the dial in numbers for the call.
* /me ```TEXT``` - Say something off of the record. Everything else you type is recorded in the official transcript.
* q? - See who is on the speaker queue.
* q+ - Add yourself to the speaker queue.
* q+ to say ```TEXT``` - Add yourself to the speaker queue while including a reminder to yourself on what you want to say.
* q+ ```<alias>``` - Add someone else to the speaker queue.
* q- ```<alias>``` - Remove someone from the speaker queue.
* ack ```<alias>``` - Acknowledge someone to speak from the speaker queue.

People that are running the meeting may find these commands useful:

* agenda: ```<URL>``` - Specify the link for the meeting agenda.
* scribe: ```<alias>``` - Specify the IRC nickcname of the person that is scribing.
* topic: ```TEXT``` - Set the current topic of discussion.
* voip: ```<last 3 digits of SIP/...>``` is ```<alias>``` - Associate a voice channel with an IRC nickname.
* voip: noisy? - See which audio channels are being noisy. Useful for finding distracting audio from participants.
* voip: mute ```<last 3 digits of SIP/...>``` - Mute an audio channel.
* voip: unmute ```<last 3 digits of SIP/...>``` - Unmute an audio channel.
* voip: disconnect ```<last 3 digits of SIP/...>``` - Disconnect an audio channel.
* chair: ```<alias>``` - Specify the person running the meeting.
* meeting: ```<TEXT>``` - Specify the title of the meeting.
* date: ```<YYYY-MM-dd>``` - Specify the date of the meeting. Useful when creating minutes after the fact.

## Associate your phone number with your alias

### Command

```
voip: <last 3 digits of SIP/...> is <alias>
```

### Example

Suppose your alias is `kimhd` and phone number is 555-222-1212. Look for your phone number in the chat window and get the last 3 digits from the adjacent string `[SIP/xx.xx.xx.xxx-xxxxxxxx]`

```
[09:01] <voip-vctf> 15552221212 [SIP/69.77.77.777-00000174] has joined the conference.
```

The last 3 digits are `174`. You would enter command:

```
voip: 174 is kimhd
```

## Speaking off the record

### Command

```
/me <your message>
```

### Example

```
/me can you speak up please?
```

## List connections

### Command

```
voip: connections?
```

## Scribing

### Command

```
<alias>: <what they said>
```

### Example

Suppose ChristopherA is scribing, and kimhd says "The next thing we will discuss is the DID spec"

ChristopherA would type:
```
kimhd: The next thing we will discuss is the DID spec
```

To continue, and avoid repeating the author name, type `...` (on the new line)

## Posting an agenda

### Command

```
Agenda: <agenda link>
```

### Example

```
Agenda: https://lists.w3.org/Archives/Public/public-credentials/2017Jul/0040.html
```

# Publishing the Minutes

This section documents how one can clean up and publish minutes.

## Setup

To publish the minutes, you must have the meetings Github repository checked out. WARNING: This is a very large, multi-gigabyte repository, don't try to download it without a good Internet connection. These instructions should work for Linux and Mac OS X systems.

1. `git clone git@github.com:w3c-ccg/meetings.git w3c-ccg-meetings`
1. `cp publishing.cfg.example publishing.cfg` (setup the text editor and audio editor variables in publishing.cfg)
1. `./download-raw-minutes`
1. `cd <LATEST_MINUTES_DIRECTORY>` (e.g. `cd 2018-01-09`)
1. Edit the WAV file to 1) delete all audio before the Chair starts talking about the Agenda, and 2) delete all audio after the first person hangs up at the end of the call. Basically, clean up the audio to save the content and save the new file as audio.wav.
1. `oggenc -b 32 audio.wav`
1. Go to https://w3c-ccg.github.io/meetings/scribe-tool/ and copy/paste irc.log into the text input box at the bottom. Clean up the IRC log accordingly and overwrite irc.log with the edited file.
1. `cd ../scribe-tool`
1. `./publish ../<LATEST_MINUTES_DIRECTORY>` (e.g. `./publish ../2018-01-09`)

If there are no errors, the latest minutes should now be published.
