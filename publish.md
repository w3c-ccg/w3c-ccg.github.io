
# Publishing the Minutes

## Scribe and Minutes Publishing Training Video

See a video recording of our training session demonstrating how to scribe (1st half of the video) and how to publish minutes (2nd half). Available [https://youtu.be/0Sn7co2eSCo](https://youtu.be/0Sn7co2eSCo).

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
    - Go to [the online scribe tool](https://w3c-ccg.github.io/meetings/scribe-tool/) and copy/paste irc.log into the text input box at the bottom. 
    - Clean up the IRC log accordingly and overwrite irc.log with the edited file.
    - Things to check
        - Look for any find/replace suggestions in irc.log and update them (s/../..)
        - Ensure aliases have matches

## Publish
Publish the minutes:

1. `cd ../scribe-tool`
1. `./publish -d ../<LATEST_MINUTES_DIRECTORY>` (e.g. `./publish -d ../2018-01-09`)

If there are no errors, the latest minutes should now be published.

# Debugging issues

If using gmail's SMTP server, you may get an error message (ending like below) the first time; if so, just check your email to enable API access. 

```
   { Error: bad response on command 'cjdHOTJkNGI='
     ...
     code: 2,
     smtp: '534-5.7.14 <https://accounts.google.com/signin/continue?sarp=1&scc=1&plt=AKgnsbvh\n534-5.7.14 IaUhK_-5AOCdpwIXJl2IjOdVTpJv15b1PByBixau67mqEq0Fll-90x-7pW_ffwpwGtNW1T\r\n534-5.7.14 B7nokaCYy9MsgZtK0_VFQsfj8NJks30BNBStBSJCwWQ4q_cih92MPe9UguqixShXYA1S3r\r\n534-5.7.14 6O9N-0wdU-QbrVawNogjL-z_lpAYFeaafanfWWlfBzRdI-tIz8JbNMYmiAbbq0AkyFo2TO\r\n534-5.7.14 QF_I9lGHt5nDzIsmW_5lyHxOC7fLQ> Please log in via your web browser and\r\n534-5.7.14 then try again.\r\n534-5.7.14  Learn more at\r\n534 5.7.14  https://support.google.com/mail/answer/78754 63-v6sm4339204pgi.4 - gsmtp\r\n' },
  smtp: undefined }

```
