
# Publishing the Minutes

This how to clean up and publish minutes.

## tl;dr

1. Trigger the workflow start by running the following curl command. 
    - Note you need to add the date value (e.g. 2020-01-07) and have a github API token with permissions to this repo.
    - This will download the raw minutes and ping the chairs (or TBD list) to clean it up (with instructions)
```
curl -H "Accept: application/vnd.github.everest-preview+json" \
    -H "Authorization: token <token>" \
    --request POST \
    --data '{"event_type": "download_minutes", "client_payload": { "date": "<date>"}}' \
    https://api.github.com/repos/w3c-ccg/meetings/dispatches
```

2. Clean up the minutes ad check in
    - Go to the [scribe tool](https://w3c-ccg.github.io/meetings/scribe-tool/) and [clean up the minutes](#cleaning-up-the-minutes)
    - Check in the cleaned up file into the same meeting dir irc-raw.log was located in, name it irc.log

3. The rest is handled for you. Checking in a file named irc.log does the following:
    - Creates the html files and checks into github
    - Emails summary to ccg email group
    - Tweets with the w3c_ccg account
    
## Cleaning up the Minutes

- Go to [the online scribe tool](https://w3c-ccg.github.io/meetings/scribe-tool/) and copy/paste irc.log into the text input box at the bottom. 
- Clean up the IRC log accordingly and overwrite irc.log with the edited file.
- Things to check
    - Ensure there's a link to the agenda (Agenda: ...)
    - Ensure the topics are labeled (Topic: ...)
    - Look for any find/replace suggestions in irc.log and update them (s/../..)
    - Ensure aliases have matches (see people.json file)
    
## Details and Implementation Notes    
    
### Comments/Bugs/Future Improvements
- We don't have audio integrated into this process yet. [See details below for what needs to be done]((#cleaning-up-the-minutes))
- Reducing number of steps:
    - This can be reduced to 1 step once we get into better scriibe hygiene habits. The separate cleanup won't be necessary
    - We could also try kicking this off on a schedule or using an s3 file watcher approach
- Bug in meeting minute time (it adds 1 day -- possibly a time zone offset issue)
- Use github caching action because this repo is large
- Make multiple tos not bcc
- Add wait before tweet
- Still confirming bot email gets sent

### How it works
   
At the end of every call, the raw IRC log and audio recording are uploaded to:

* https://w3c-ccg.s3.digitalbazaar.com/minutes/YYYY-MM-DD-irc.log
* https://w3c-ccg.s3.digitalbazaar.com/minutes/YYYY-MM-DD-audio.wav

We use github actions to process the minutes as a pipeline. At the moment there are 2 distinct phases.

1. Download raw minutes for date
    - Trigger: currently a curl command (see below)
    - Actions:
        - Download minutes for <date>
        - Email the chairs to clean up the minutes with helpful links
    - Github Action File: [download_raw_minutes.yml](https://github.com/w3c-ccg/meetings/blob/gh-pages/.github/workflows/download_raw_minutes.yml)

2. Publish the minutes for date
    - Trigger: Kicks off when a chair (or someone with access) checks in cleaned up irc.log file
    - Does the following:
         - Generates html minutes
         - Emails summary to ccg email group
         - Tweets
    - Github Action File: [publish_minutes.yml](https://github.com/w3c-ccg/meetings/blob/gh-pages/.github/workflows/publish_minutes.yml)


### Cleaning up the Audio

- Open the audio-raw.wav file in an editor (see setup above):
- Delete all audio before the Chair starts talking about the Agenda
- Delete all audio after the first person hangs up at the end of the call.
- Save the new file as audio.wav or encode to .ogg (file name audio.ogg) at 32kbps
    - For example: `oggenc -b 32 audio.wav`

