# Slacky Dark
Dark mode theme for Slack desktop clients

## Post 4.0 Install Info
https://old.reddit.com/r/Slack/comments/cexjol/slack_version_400_css_modifications_dark_theme/


# Installing into Slack client
```javascript
*For quick/easy install on Windows, check the **Automated Install** section at the bottom.
```

1. Find the Slack application directory as follows:
* Windows: `%homepath%\AppData\Local\slack\`
* Mac: `/Applications/Slack.app/Contents/`
* Linux: `/usr/lib/slack/`

**NOTE**: You can do this to the Windows Store UWP Slack app as well, but it's recommended to use the Desktop version. If you want to go the UWP route, give yourself access to the following hidden folder `C:\Program Files\WindowsApps\`. The instructions below can be followed in this folder pretty much the same as the ones above.

2. Open the most recent version folder (Ex. app-3.1.0).

3. Navigate to: `\resources\app.asar.unpacked\src\static` and edit the file `ssb-interop.js`.

4. At the very bottom of the file, add the following code:

```javascript
document.addEventListener('DOMContentLoaded', function() {
 $.ajax({
   url: 'https://raw.githubusercontent.com/RheingoldRiver/slacky-dark/master/dark.css',
   success: function(css) {
     $("<style></style>").appendTo('body').html(css);
   }
 });
});
```

5. After save, restart Slack. If any issues are seen with the sidebar colors not showing correct, set your custom theme like this:

![image](https://user-images.githubusercontent.com/6263626/45648214-08737080-ba85-11e8-97a9-9a6b9aa8f5cb.png)

```javascript
*Note: This will have to be done after each Slack app update as the file is overwritten.*
```

# Automated Install (Windows)

1. Open powershell and run the following to allow unsigned scripts ```set-executionpolicy unrestricted```

2. Download SlackInstall.ps1 and run it with powershell. This will automatically add all the code to the correct file.

3. Open Slack and set your color pallete like above and you're all done.

# Enabling Developer Tools in Slack

* Windows: Create a shortcut to Slack and change the target to 

`C:\Windows\System32\cmd.exe /c "SET SLACK_DEVELOPER_MENU=TRUE && start %homepath%\AppData\Local\slack\slack.exe"`

Run Dev Tools with Ctrl+Alt+I or from Menu > View > Developer.

* Mac: Set up as an Automator program with the "program" being Run Shell Script that has the following code:

```
export SLACK_DEVELOPER_MENU=true

open -a /Applications/Slack.app
```

Run Dev Tools with Command+Option+I or from Menu > View > Developer.

**Credits**

###### [Slack Night Mode](https://github.com/laCour/slack-night-mode) ######

###### [Slack Black Theme](https://github.com/widget-/slack-black-theme) ######
