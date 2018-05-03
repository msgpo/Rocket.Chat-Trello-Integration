# Rocket.Chat-Trello-Integration
>A Rocket.Chat [Trello](https://trello.com/) integration to send activity notifications to Rocket.Chat channels.

![image](Rocket.Chat-Trello-Integration.png)

## How To
1. Create an incoming webhook in your RocketChat
   1. Go to **RocketChat-> Administration-> Integrations-> New Integration-> Incoming webhook**
   1. Set **"Enabled"** to **"True"**
   1. Give a name for the webhook (i.e "sda.tech-trello")
   1. Select the channel where you will receive the alerts (ex: #sda.tech-events). You may wish to create a dedicated channel for your notifications.
   1. Select an account from which the alerts will be posted (usually rocket.chat bot account is used).
   1. Set **"Script Enabled"** to **"True"**
   1. Paste [Trello.js](https://github.com/GezimSejdiu/Rocket.Chat-Trello-Integration/blob/master/Trello.js) inside the Script field.
   1. Save the integration. This will generate a webhook URL and secret for you.
   1. Use the generated **WebHook URL** to POST messages to Rocket.Chat
1. Go to [Trello's REST API](https://developers.trello.com/v1.0/reference) and enter your [Trello API Key](https://trello.com/app-key) and your Token to get started.
   1. Get a board's idModel by entering the url of the board and appending .json to the end (eg; https://trello.com/b/4N4GSasC/fundraising.json) and copying the id.
   1. Select `"id": "idModel"` of a board which you would like to create POST messages to Rocket.Chat.
   1. Go to **[Create Webhook](https://developers.trello.com/v1.0/reference#webhooks-2)** in the Trello’s REST API and add your WebHook URL (**callbackURL**), Board Id (**idModel**) and other parameters as below:
   ```javascript
   description : ”Trello-YourChannel-Webhook”
   callbackURL:  "WebHook URL"
   idModel: "ID of the model to be monitored (which you obtained above)"
   active: "true"
   ```
   1. Press **Try it** to make it works.
1. The integration is ready to generate notifications for the given board :) Enjoy it!
