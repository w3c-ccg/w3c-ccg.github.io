# Connecting to a meeting

For the best experience, ensure you are connected through both audio and chat

## Audio
We recommend you connect to our meetings with an SIP client. To do this, you need a SIP client installed on your device.

If you need help selecting a SIP client, [Linphone](http://www.linphone.org/) is an example SIP client that is free and available on many platforms. 

### Configuration

1. Set your display name, which will be displayed in IRC. 
    - In Linphone it's under Linphone > Preferences > SIP accounts > Default identity
2. Update your settings to use a random SIP port (this will help avoid annoying calls)
    - In Linphone it's under Linphone > Preferences > Network > Network protocol and Ports
3. *Probably* you'll need to disable IPv6
    - In Linphone it's under Linephone > Preferences > Network > Transport -- toggle "allow IPv6"

### Call

Once your SIP client is set up, connect to the CCG call at:

    sip:ccg@96.89.14.196
    
Note: if you also want a SIP account, you can use [Linphone's account setup form](https://www.linphone.org/free-sip-service.html).

If for some reason you're not able to connect via a SIP client, you can dial in by phone: 

    +1.540.961.4469 x6306

## Chat
During the meeting, we use IRC to share links, keep meeting minutes, ask questions, etc. The CCG IRC channel is:

    irc://irc.w3.org:6665/#ccg

If you're unfamiliar with IRC, note that you can easily connect through a browser: [http://irc.w3.org/?channels=ccg](http://irc.w3.org/?channels=ccg)

Now that you're connected, see the [IRC Command Reference](https://github.com/w3c-ccg/w3c-ccg.github.io/blob/master/irc_ref.md) for help with IRC commands.
