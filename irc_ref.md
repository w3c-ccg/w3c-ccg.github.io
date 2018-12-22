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
