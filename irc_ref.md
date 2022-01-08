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
* ccgbot: create poll `<POLL>` | `<OPTION 1>` | `<OPTION 2>` ... - Create a poll. [Details](#create-a-poll)
* ccgbot: poll (`<poll>`) - Show a poll. [Details](#show-a-poll)
* ccgbot: polls - List polls. [Details](#list-polls)
* ccgbot: vote `<options>` (on `<poll>`) - Submit a vote on a poll. [Details](#vote-in-a-poll)
* ccgbot: votes (`<poll>`) - Show votes on a poll. [Details](#show-votes-on-a-poll)

## Reference for people running the meeting and scribes

People that are running the meeting may find these commands useful:

* agenda: ```<URL>``` - Specify the link for the meeting agenda. [Details](#posting-an-agenda)
* scribe: ```<alias>``` - Specify the IRC nickcname of the person that is scribing. 
* ```<alias> <TEXT>``` - (For scribe) Record what alias said [Details](#scribing)
* topic: ```TEXT``` - Set the current topic of discussion.
* voip: number? - Get the dial in numbers for the call. (TODO: is this right? I thought it was connections? )
* voip: connections? - Get the dial in numbers for the call. [Details](#list-connections)
* voip: noise? - See which audio channels are being noisy. Useful for finding distracting audio from participants.
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

### Create a poll

This `create poll` command allows chat participants to create Jitsi-bridged
polls. Polls created using this command function the same as polls created from
Jitsi.

#### Command

```
ccgbot: create poll <QUESTION> | <OPTION 1> | <OPTION 2> | ...
```

A poll must have a question and at least two options. The question and options
are passed in the command separated by a pipe character ("|").

#### Examples

##### Creating a poll with three options
```
10:55 <cel> ccgbot: create poll Example Question | One | Two | Three
10:55 <ccgbot> cel created a poll #5 with 3 options.
10:55 <ccgbot> POLL: Example Question
10:55 <ccgbot> ... Option 1: One
10:55 <ccgbot> ... Option 2: Two
10:55 <ccgbot> ... Option 3: Three
```

### Show a poll

ccgbot announces polls in IRC as they are created. To subsequently display the
poll text and options, this `poll` command can be used.

#### Command

```
ccgbot: vote <options>
ccgbot: vote <options> on <poll>
```

If no poll number is referenced, the current (latest) poll is used.

#### Examples

##### Show the current poll
```
10:45 <cel> ccgbot: poll
10:45 <ccgbot> Poll #3 with 2 options.
10:45 <ccgbot> POLL: another poll
10:45 <ccgbot> ... Option 1: asdg
10:45 <ccgbot> ... Option 2: afaasdsad
```

##### Show a specific poll
```
10:45 <cel> ccgbot: poll 2
10:45 <ccgbot> Poll #2 with 2 options.
10:45 <ccgbot> POLL: asdf
10:45 <ccgbot> ... Option 1: A
10:45 <ccgbot> ... Option 2: B
```

### List polls

#### Command

```
ccgbot: polls
```

#### Examples

##### No polls
```
16:07 <cel> ccgbot: polls
16:07 <ccgbot> No polls. Create one in Jitsi or by chatting, "ccgbot: create poll ..."
```

##### One poll
```
16:09 <cel> ccgbot: polls
16:09 <ccgbot> 1 poll.
16:09 <ccgbot> ... Poll #1: as
```

##### Two polls
```
16:10 <cel> ccgbot: polls
16:10 <ccgbot> 2 polls.
16:10 <ccgbot> ... Poll #1: as
16:10 <ccgbot> ... Poll #2: A
```

### Vote in a poll

ccgbot bridges Jitsi polls and their votes to/from IRC. IRC participants can
vote in polls, and their votes will appear in Jitsi.

If you vote in a poll from IRC, you should probably not also vote on it in
Jitsi, or vice-versa, because your vote would be counted twice.

#### Command

```
ccgbot: vote <options>
ccgbot: vote <options> on <poll>
```

Votes are on a poll's options, which are identified by numbers. Multiple
options may be chosen in a vote, by separating the numbers with commas (no
spaces).

Polls are identified by numbers. If you don't specify which poll to vote on,
the most recent poll is assumed.

One can change their vote by using this vote command multiple times.

#### Examples

##### Vote for option 2 on the current poll
```
10:31 <cel> ccgbot: vote 2
10:31 <ccgbot> cel answered poll #3: (2) Option Two
```

##### Vote for option 1 on a specific poll
```
10:30 <cel> ccgbot: vote 1 on 2
10:30 <ccgbot> cel answered poll #2: (1) Option One
```

##### Vote for multiple options (1, 2) on the current poll
```
10:31 <cel> ccgbot: vote 2,1
10:31 <ccgbot> cel answered poll #3: (1) Option One, (2) Option Two
```

### Show votes on a poll

ccgbot announces poll votes in IRC as they are made. To show a summary of votes
made on a poll, similar to how Jitsi shows the details of a poll, this `votes`
command can be used.

#### Command

```
ccgbot: votes
ccgbot: votes on <poll>
```

If no poll number is referenced, the current (latest) poll is used.

#### Examples

##### Show votes on the current poll
```
10:48 <cel> ccgbot: votes
10:48 <ccgbot> Poll #3 with 2 options has 2 votes from 1 voters.
10:48 <ccgbot> POLL: another poll
10:48 <ccgbot> ... Option 1 has 1 votes (100%); voted by: cel
10:48 <ccgbot> ... Option 2 has 1 votes (100%); voted by: cel
```

##### Show votes on a specific poll
```
10:48 <cel> ccgbot: votes 1
10:48 <ccgbot> Poll #1 with 2 options has 1 votes from 1 voters.
10:48 <ccgbot> POLL: A
10:48 <ccgbot> ... Option 1 has 1 votes (100%); voted by: cel
10:48 <ccgbot> ... Option 2 has 0 votes (0%); voted by:
```
