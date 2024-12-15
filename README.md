# Webex-Email-Bot
A bot that can send email by taking in webex message chat input. 

This email bot is built on Webex-Bot-Starter (https://github.com/WebexSamples/webex-bot-starter). Added one more "send-email" command and you can add this function in to start sending email. If you dont have a webex bot yet, refer to the Webex-Bot-Starter instruction. Use the chat function here to add email feature. 


Release update 
- 16th Dec 2024 - First release of the script 


Pre-requisite:-

* Webex-bot-starter, or a working webex bot - https://github.com/WebexSamples/webex-bot-starter
* NPM - this is needed to run webex bot
* ngrok - we use web hook to get input from that you (or other user) sent to the bot - https://ngrok.com/
* SMTP relay - the bot will call this SMTP using "swaks" command, yes you will need swaks also
* swaks - Swiss army knife for SMTP - http://www.jetmore.org/john/code/swaks/


## Installation (if you have a working webex bot)

You only need "email-function-only.txt", the other file "index.js" is for your reference

Here are the steps to prepare and run the script:-

1. Complete the prerequisites
2. Installation - Clone the repo
```bash
git clone https://github.com/ciscoketcheon/Webex-Email-Bot.git
```
3. Configuration - Edit your existing "index.js" file
   - Copy "email-function-only.txt" content, it is the main code for "send-email" function
   - Paste it anywhere in between function. A function starts with "framework.hears(" and ends with ");"
   - Recommend to paste it before the last catch-all function. Refer to the "index.js" here as reference
4. One more modification needed is to update the x.x.x.x in the "send-email" function with your relay server IP address
```bash
   ...const command = `swaks --server x.x.x.x --from "${sender}...
```
Example update, say relay server IP address is 192.168.25.25. Relay server configuration server is beyond this guide.
```bash
   ...const command = `swaks --server 192.168.25.25 --from "${sender}...
```
5. Save and re-run the bot script
```bash
npm start
```



## Webex-bot Installation (from scratch)

If you never installed a Webex bot before, suggest to follow this full guide -> https://developer.webex.com/blog/from-zero-to-webex-teams-chatbot-in-15-minutes

In summary, here are the steps from scratch:-

1. Complete the prerequisites, e.g. prepare and copy webex bot auth-token, ngrok account sign-up and prep the auth-token, pre-install swaks, prep SMTP relay
2. Clone the Webex bot starter repo
```bash
git clone https://github.com/WebexSamples/webex-bot-starter.git && cd webex-bot-starter
```
3. Start ngrok webhook, find its better with EU region
```bash
ngrok http 7001 --region=eu
```
Optional -- Do explore using a separate screen or terminal for ngrok and npm, try run "screen" from linux to spawn a new one, or do a "screen -r" to show the running screens, and do a "screen -r XXXX" to restore a screen (XXXX is the screen number). If you want to leave current screen session and jump back to main session, do a Ctrl+A+D key combination.
4. Copy ".env.local" to a new file ".env", update the ".env" file with ngrok webhook URL (from #3) and webex bot auth-token (from #1)
5. In another folder, clone this repo 
```bash
git clone https://github.com/ciscoketcheon/Webex-Email-Bot.git
```
6. Configuration - Edit your existing "index.js" file
   - Copy "email-function-only.txt" content, it is the main code for "send-email" function
   - Paste it anywhere in between function. A function starts with "framework.hears(" and ends with ");"
   - Recommend to paste it before the last catch-all function. Refer to the "index.js" here as reference
7. One more modification needed is to update the x.x.x.x in the "send-email" function with your relay server IP address
```bash
   ...const command = `swaks --server x.x.x.x --from "${sender}...
```
Example update, say relay server IP address is 192.168.25.25. Relay server configuration server is beyond this guide.
```bash
   ...const command = `swaks --server 192.168.25.25 --from "${sender}...
```
8. Save and re-run the bot script
```bash
npm start
```


