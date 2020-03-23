# Connecting to a meeting

For the best experience, ensure you are connected through both audio and chat

## Audio
We recommend you connect to our meetings with a SIP client. To do this, you need a SIP client installed on your device. The following examples are SIP clients that members of the community have had success with.

### Linphone

[Linphone](http://www.linphone.org/) is a SIP client that is free and available on many platforms. 

For iOS, Android, Windows and Mac, you can download an installable file from the website. On Ubuntu/Linux, you can install it with `sudo apt install linphone` and launch it from the menu. It should work out of the box, but there are optional configurations you can make.

1. Set your display name, which will be displayed in IRC. 
    - In Linphone it's under Linphone > Preferences > SIP accounts > Default identity
2. Update your settings to use a random SIP port (this will help avoid annoying calls)
    - In Linphone it's under Linphone > Preferences > Network > Network protocol and Ports
3. *Probably* you'll need to disable IPv6
    - In Linphone it's under Linphone > Preferences > Network > Transport -- toggle "allow IPv6"
4. Add the CCG SIP address as a contact so you can dial in with one-click.
    - Click the + under 'Contacts' on the left and add "sip:ccg@96.89.14.196"

If you also want a SIP account (to receive calls), you can use [Linphone's account setup form](https://www.linphone.org/freesip/home).

### Onsip

[Onsip](https://onsip.com) offers a JavaScript-heavy browser-based SIP client that is free. They offer a lot of other services too, so signing up for an account can be confusing. Here's a guide, accurate as of 2020-03:

1. At [onsip.com](https://onsip.com), click 'Start Free' in the top right corner of the homepage ([screenshot](/assets/img/connecting/onsip_1_startfree.png)).
2. Fill in the account creation form with your email address, name, phone number, company name and size, and choose 'Free SIP Services' from the dropdown. All of the input data can be fake except for the email address, as you need to click an account verification link ([screenshot](/assets/img/connecting/onsip_2_create.png)).
3. Once you've verified your account, the next step is 'Create your domain name'. This can be anything, noting that it will be shown when you dial in ([screenshot](/assets/img/connecting/onsip_3_domain.png)).
4. 'Create your profile': set a username (which will be shown when you dial in) and a password (which you need to log into the SIP client) ([screenshot](/assets/img/connecting/onsip_4_profile.png)).
5. Then there are two steps which make no sense for our needs. 
    - 'Configure your display': pick random values, and proceed. (You can delete the preset topics and proceed with none.) ([screenshot](/assets/img/connecting/onsip_5_display.png))
    - 'Which content management system do you use?': you can choose 'skip this step' ([screenshot](/assets/img/connecting/onsip_6_cms.png)).
6. Now log in with the details you set before. Your SIP Address is username@domain.onsip.com ([screenshot](/assets/img/connecting/onsip_7_login.png)).
7. To make a call, visit [app.onsip.com](https://app.onsip.com) and type in the CCG SIP address to the New Call box at the top left ([screenshot](/assets/img/connecting/onsip_8_call.png)). Once you've dialled in once, it will appear in your call history so you can dial in with one click after that. Don't forget to mute yourself! It's not automatic.


### Call

Once your SIP client is set up, connect to the CCG call at:

    sip:ccg@96.89.14.196

If for some reason you're not able to connect via a SIP client, you can dial in by phone: 

US phone: +1.540.274.1034 x6306
EU phone: +33.9.74.59.31.06 x6306

## Chat

During the meeting, we use IRC to share links, keep meeting minutes, ask questions, etc. The CCG IRC channel is:

    irc://irc.w3.org:6665/#ccg

If you're unfamiliar with IRC, note that you can easily connect through a browser: [http://irc.w3.org/?channels=ccg](http://irc.w3.org/?channels=ccg)

Now that you're connected, see the [IRC Command Reference](https://github.com/w3c-ccg/w3c-ccg.github.io/blob/master/irc_ref.md) for help with IRC commands.
