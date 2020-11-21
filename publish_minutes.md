# Generate CCG Minutes

## Step 1: Fetch and clean up the log file

Go to the [scribe tool](https://w3c-ccg.github.io/meetings/scribe-tool/) and enter the date of the meeting (see screenshot)

Things to check:
- Ensure there's a link to the agenda ("Agenda: ...")
- Ensure the topics are labeled ("Topic: ...")
- Ensure the scribe is identified ("Scribe: ...")
- Look for any find/replace suggestions in irc.log and update them ("s/../..")
- Ensure aliases have matches (see people.json file)

## Step 2: Fetch and clean audio (TODO)
- Fetch the audio file 
    - For example: `curl -# "https://w3c-ccg.s3.digitalbazaar.com/minutes/2020-08-04-audio.wav" > audio-raw.wav`
- Open the .wav file in an audio editor (such as audacity) and clean/save the audio:
    - Delete all audio before the Chair starts talking about the Agenda
    - Delete all audio after the first person hangs up at the end of the call.
    - Save the new file as audio.wav or encode to .ogg (file name audio.ogg)
- Add the cleaned up audio file to github under the meeting date
    - For example: https://github.com/w3c-ccg/meetings/2020-08-04/audio.ogg

## Step 3: Commit the files

- Add the log and audio files to github `meetings` repo as follows:
    - log: https://github.com/w3c-ccg/meetings/yyyy-mm-dd/irc.log
    - audio: https://github.com/w3c-ccg/meetings/yyyy-mm-dd/audio.ogg
    - Example: 
        - log: https://github.com/w3c-ccg/meetings/2020-11-17/irc.log
        - audio: https://github.com/w3c-ccg/meetings/2020-11-17/audio.ogg
- On commit, the rest is handled for you; a github action will generate html and publish

You can also update the minutes; changes to irc.log will trigger the github action and refresh the html.

> What it does:
> - Emails summary to ccg email group
> - Tweets with the w3c_ccg account
