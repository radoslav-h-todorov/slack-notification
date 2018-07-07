![Visual Studio Team Services](https://kasunkodagoda.visualstudio.com/_apis/public/build/definitions/a6819d70-02f9-4711-8ff6-ae44bb52a8d1/28/badge)
# Slack Notification Task for Visual Studio Team Services

Slack Notification task with advanced slack message customization for Visual Studio Team Services. The task includes the ability to send optional attachments with the standard slack messages.
[Visual Studio Marketplace: Slack Notification](https://marketplace.visualstudio.com/items?itemName=kasunkodagoda.slack-notification)

# Using Slack Notification Task
Follow the instructions below to configure the Slack Notification task to send messages to a slack channel or a user.

## Getting the Slack API Token
You will need to generate an API token and include it as a secure variable in Visual Studio Team Services build/release definition. You can generate the API token using the [Slack Token Generator](https://api.slack.com/custom-integrations/legacy-tokens).


### Add the Slack Notification Task
Install the Slack Notification task in to your Visual Studio Team Services account and Search for the task and add it to your build/release definition.

![Add Slack Notification Task](https://raw.githubusercontent.com/kasunkv/slack-notification/master/screenshots/screenshot-add-slack-notification-task.png)

## Slack Configuration
Send Slack Notification section contains some required configuration options.


![Required Configuration](https://raw.githubusercontent.com/kasunkv/slack-notification/master/screenshots/screenshot-required-options.png)

### Required Configuration
 
 * **Message Author**: Text shown as the author of the message in Slack.
 * **Destination**: Select the Destination for the Slack Message. To send a message/upload file to a *Channel*, select _Slack Channel_. To send a direct message/upload file to a *User*, select _Slack User_.
 * **User Identifier Type**: Select the User Identifier Type you will use as to identify the Slack User. Currently supports **Name**, **Real Name** _(not profile.real_name in the slack API)_ and **Display Name**. For more details about why this change was made,  read [A Lingering Farewell to the Slack Username](https://api.slack.com/changelog/2017-09-the-one-about-usernames).
 * **Channel or User**: Channel/User where the message is sent to. This value is tied to the *Destination* input option. If you selected _Slack Channel_ as the Destination, you can enter the slack channel name here. You can either add the channel name with *#* prefix or without the prefix. _(E.g. #general, general)_. If you selected _Slack User_ as the Destination, You need to enter the *Real Name* of the Slack User without any prefix. _(E.g. John Smith, Halc Lewis)_. The real name is *Case Sensitive* so make sure to type it correctly. _If the Channel Name or User's Real Name is invalid, the task will finish without sending any notifications_.
 * **Slack API Token**: Slack API Token generated from the [Slack Token Generator](https://api.slack.com/custom-integrations/legacy-tokens). Save the token in a secure build variable.
 * **Icon URL**: _(Optional)_ The icon that will be shown along side the message.

## Notification Options
Slack Notification task provides support for sending attachments along with the message. Sending attachments is optional. There are several configuration options provided, as described below. 
 
 * **Notification Type**: Select the type of notification. Use _Send Chat Message_ to send a message to a slack Channel. Use _Upload File_ to upload a file to a slack channel

 #### Notification Type: Send Chat Message

 * **Message**: _(Optional)_ Text shown as the author of the message in Slack. Messages can be formatted similar to the markup formats used in Markdown
 * **Author Name**: _(Optional)_ Small text used to display the author's name.
 * **Author Link**: _(Optional)_ A valid URL that will hyperlink the _Author Name_ text mentioned above. Will only work if _Author Name_ is present.
 * **Title**: _(Optional)_ The _Title_ is displayed as larger, bold text near the top of a message attachment.
 * **Title Link**: _(Optional)_ A valid URL will hyperlink the _Text_ mentioned above.
 * **Attachment Pre-Text**: _(Optional)_ This is optional text that appears above the message attachment block.
 * **Attachment Text**: _(Optional)_ This is the main text in a message attachment, and can contain [Standard Slack Message Markup](https://api.slack.com/docs/message-formatting).
 * **Border Color**: _(Optional)_ Color of the border along the left side of the message attachment. Value that can either be one of _good_, _warning_, _danger_, or any _hex color code_ (eg. #439FE0)
 * **Image URL**: _(Optional)_ A valid URL to an image file that will be displayed inside a message attachment. Supports _gif_, _jpeg_, _png_, & _bmp_ formats.
 * **Footer Text**: _(Optional)_ Contextualize footer text for the attachment. Limited to 300 characters.
 * **Footer Icon**: _(Optional)_ Publicly accessible URL string that render a small icon beside your footer text.

 ![Sending Chat Message](https://raw.githubusercontent.com/kasunkv/slack-notification/master/screenshots/screenshot-send-chat-message.PNG)


 #### Notification Type: Upload File

* **File to Upload**: Set the path to the file to upload. Use the file selector dialog to select the file or use VSTS built in variables to set the path.
 * **File Title**: _(Optional)_ Set the title of the file.
 * **Comment**: _(Optional)_ Set the initial comment for the uploaded file.

 ![Uploading a File](https://raw.githubusercontent.com/kasunkv/slack-notification/master/screenshots/screenshot-upload-file.PNG)


 ## Sample Slack Message
The following is a sample slack message sent to the _#general_ slack channel.

### Chat Message
![Sample Message](https://raw.githubusercontent.com/kasunkv/slack-notification/master/screenshots/screenshot-slack-message.PNG)

### File Upload
![File Upload](https://raw.githubusercontent.com/kasunkv/slack-notification/master/screenshots/screenshot-uploaded-to-slack.PNG)


# Contributing
All contributions from the GitHub community are welcome.

* Fork the repository
* Create a feature branch: `git checkout -b new-feature`
* Commit your changes
* Push to the branch: `git push origin new-feature`
* Submit a Pull Request


## Installing Dependencies
Navigate to the `\buildtask\SlackNotification` folder which contains the `package.json`

```sh
# install dependencies listed in package.json
$ npm install
```

## Compile TypeScript Task
A npm script is configured to compile the TypeScript code to JavaScript (ES201)
```sh
# compile the TypeScript code
$ npm run build
```


# License
MIT © [Kasun Kodagoda](http://kasunkodagoda.k2vsoftware.com)


