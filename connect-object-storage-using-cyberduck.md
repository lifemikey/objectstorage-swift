---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using Cyberduck

OpenStack limits the size of any individual object to 5 GB. OpenStack supports storage of files larger than this limit via segmentation. Additionally, various clients have their own file size limits, such as:

- iPhone/iOS: 20 MB for upload/download on the carrier network; 5 GB if you're on WiFi though
- SoftLayer Portal: 20 MB for upload/download
- Android: 20 MB for upload/download for the carrier network; 5 GB if you're on WiFi though
- AT&T: 20 MB for upload/download
- API: 5 GB

Essentially, the file size doesn't matter when it comes to using Cyberduck. Uploading a file over 5 GB won't be a problem because it will automatically split it. If you tried to upload that with sFTP or SCP, your upload would stop at 5 GB and fail. This is due to the limitation of the swftp client installed on the OpenStack servers.  

Cyberduck is compatible with Mac OS X and Windows, but there are a couple differences.

<table><tbody>
<tr><td>Advantages:	</td><td><li>Cyberduck supports SLO (Static Large Objects).</li><li>Cyberduck will automatically split files over 5 GB to create them as SLO's (Static Large Objects have each segment defined in a JSON array stored as the content of the manifest file).</li><li>You can simply drag and drop your files rather than type out complex cURL commands.</li><li>You have a GUI to work with.</li></td></tr>
<tr><td>Disadvantages:</td><td>There's no {{site.data.keyword.BluSoftlayer}} API functionality for this.</td></tr>
</tbody></table>


## Getting Started

1. Download Cyberduck from [https://cyberduck.io/](https://cyberduck.io/){:new_window} - Select the right version for your OS.
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
        - `<key>SLOSXXXXXX:username</key>` - Change SLOSXXXXXX:username to your {{site.data.keyword.objectstorageshort}} username, which you can get from going to your **{{site.data.keyword.objectstorageshort}}** page in the [Portal](https://control.softlayer.com/) and clicking the **{{site.data.keyword.objectstorageshort}}** user, then the cluster you wish to use, then View **Credentials**.
       - `<key>API Key goes here</key>` - Change "API Key goes here" to your full API key which you can get by following the step above as well.

4. Save your file by clicking **File > Save As..** and change the **Save As Type** to **All Files**, then save your file with the name of the cluster and add **.cyberduckprofile** to the end as shown in the image below. <br/> ![](/images/cyberduck_fig1.png)

5. Navigate to the profile file you just created and double-click on it. When the application launches, two screens come up, close the one on top.  You should now be at the main screen of the program. Simply click the **bookmark** icon on the taskbar, then double click your **{{site.data.keyword.objectstorageshort}}** link. <br/> ![](/images/cyberduck_fig2.png)
 
6. A pop-up box comes up asking for the login information. If you check the box for Save Password, it will not pop up again.  Filled out, it should look like the image below. <br/> ![](/images/cyberduck_fig3.png)

7. Click **Login** to see all of your containers. <br/> ![](/images/cyberduck_fig4.png)

8. At this point, Cyberduck is fully connected and you can now drag-and-drop files to and from {{site.data.keyword.objectstorageshort}} without having to worry about the upload or download timing out due to the 5 GB file limit. If you run into any issues, feel free to open a ticket and we will assist you.
