---

copyright:
  years: 2017
lastupdated: "2017-07-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Connect to Object Storage using Cyberduck

This guide will help you get Cyberduck connected to your Object Storage account. There are a few reasons to use Cyberduck instead of sFTP, SCP, or the cURL commands, and they will be explained here.

OpenStack limits the size of any individual object to 5 GB. OpenStack supports storage of files larger than this limit via segmentation. Additionally, various clients have their own file size limits, such as:

- iPhone/iOS: 20 MB for upload/download on the carrier network; 5 GB if you're on WiFi though
- SoftLayer Portal: 20 MB for upload/download
- Android: 20 MB for upload/download for the carrier network; 5 GB if you're on WiFi though
- AT&T: 20 MB for upload/download
- API: 5 GB

## Pros and Cons of using Cyberduck 

### Pros:

- Cyberduck supports SLO (Static Large Objects).
- Cyberduck will automatically split files over 5 GB to create them as SLO's (Static Large Objects have each segment defined in a JSON array stored as the content of the manifest file).
- You can simply drag and drop your files rather than type out complex cURL commands.
- You have a GUI to work with.

### Cons:

- There's no SL API functionality for this

Essentially, the file size doesn't matter when it comes to using Cyberduck. Uploading a file over 5 GB won't be a problem because it will automatically split it. If you tried to upload that with sFTP or SCP, your upload would stop at 5GB and fail. This is due to the limitation of the swftp client installed on the OpenStack servers.  

Cyberduck is compatible with Mac OS X and Windows, but there are a couple differences.

## Getting Started:

1. Download Cyberduck from https://cyberduck.io/ - Select the right version for your OS.
2. Run the installer and let it install with defaults.
3. Create a valid Cyberduck profile using Notepad.
     1. Copy this template:
     ```
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" 
     "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
        <dict>
             <key>Protocol</key>
       <string>swift</string>
             <key>Vendor</key>
             <string>softlayer-Par01</string>
             <key>Description</key>
             <string>Softlayer Object Storage (Paris)</string>
             <key>Default Hostname</key>
     <string>par01.objectstorage.softlayer.net</string>
             <key>Default Port</key>
             <string>443</string>
             <key>Hostname Configurable</key>
             <false/>
             <key>Port Configurable</key>
         <false/>
             <key>Context</key>
             <string>/auth/v1.0</string>
             <key>SLOSXXXXXX:username</key>
             <string>Username</string>
             <key>API Key goes here</key>
             <string>API Key:</string>
         </dict>
     </plist>
     ```
     2. Update the template with the following:
        - `<string>softlayer-Par01</string>`- Change "par01" to whatever cluster you are using. (This helps you find it easier)
        - `<string>Softlayer Object Storage (Paris)</string>`- Change "Paris" to whatever the location you're using is. (This helps you find it easier)
        - `<string>par01.objectstorage.softlayer.net</string>` - Change "par01" to the cluster you are using.  (This is important.)
        - `<key>SLOSXXXXXX:username</key>` - Change SLOSXXXXXX:username to your Object Storage username, which you can get from going to your **Object Storage** page in the [Portal](https://control.softlayer.com/) and clicking the **Object Storage** user, then the cluster you wish to use, then View **Credentials**.
       - `<key>API Key goes here</key>` - Change "API Key goes here" to your full API key which you can get by following the step above as well.

4. Save your file by clicking **File > Save As..** and change the **Save As Type** to **All Files**, then save your file with the name of the cluster and add **.cyberduckprofile** to the end as shown in the image below. <br/> ![](/images/cyberduck_fig1.png)

5. Navigate to the profile file you just created and double-click on it. When the application launches, two screens come up, close the one on top.  You should now be at the main screen of the program. Simply click the **bookmark** icon on the taskbar, then double click your **Object Storage** link. <br/> ![](/images/cyberduck_fig2.png)
 
6. A pop-up box comes up asking for the login information. If you check the box for Save Password, it will not pop up again.  Filled out, it should look like the image below. <br/> ![](/images/cyberduck_fig3.png)

7. Click **Login** to see all of your containers. <br/> ![](/images/cyberduck_fig4.png)

8. At this point, Cyberduck is fully connected and you can now drag-and-drop files to and from Object Storage without having to worry about the upload or download timing out due to the 5GB file limit. If you run into any issues, feel free to open a ticket and we will assist you.
