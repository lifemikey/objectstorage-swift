---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-03"

---
{:new_window: target="_blank"}


# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using Cyberduck

OpenStack limits the size of any individual object to 5 GB. OpenStack supports storage of files larger than this limit through segmentation. Additionally, various clients have their own file size limits.

- iPhone/iOS - 20 MB for upload/download on the carrier network; 5 GB if you're on Wi-Fi
- Android - 20 MB for upload/download for the carrier network; 5 GB if you're on Wi-Fi
- AT&T - 20 MB for upload/download
- API - 5 GB
- {{site.data.keyword.slportal}} - 20 MB for upload/download

However, the file size doesn't matter when it comes to using Cyberduck. Uploading a file over 5 GB is not a problem because the application automatically splits it. If you try to upload that with sFTP or SCP, your upload stops at 5 GB and fails. This failure is due to the limitation of the swftp client that is installed on the OpenStack servers.  

Cyberduck is compatible with Mac OS X and Windows, but there are a couple differences.

**Advantages and disadvantages of using Cyberduck**

 - Advantages - Cyberduck supports SLO (Static Large Objects). Cyberduck automatically splits files over 5 GB to create them as SLO's (Static Large Objects define each segment in a JSON array that is stored as the content of the manifest file).  You can simply drag and drop your files rather than type out complex cURL commands. You have a GUI to work with.
 - Disadvantages - {{site.data.keyword.BluSoftlayer}} offers no API functions for this application.
</table>


## Setting up Cyberduck

1. Download Cyberduck from [https://cyberduck.io/](https://cyberduck.io/){:new_window}
   - Select the right version for your OS.
2. Run the installer and let is complete with the defaults.
3. Obtain your user name, cluster information and API key from your **{{site.data.keyword.objectstorageshort}}** page in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}. Click the **{{site.data.keyword.objectstorageshort}}** user, then the cluster you want to use, then **View Credentials**.
4. Create a valid Cyberduck profile using Notepad.
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
             <string>IBM Cloud Object Storage (Paris)</string>
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
     {:pre}


     2. Update the template with the following information.
        - Change the `<string>softlayer-Par01</string>` to include the cluster that you're using.
        - Change the `<string>IBM Cloud Object Storage (Paris)</string>` to the location that you're usings.
        - Change the `<string>par01.objectstorage.softlayer.net</string>` to the cluster that you're using.
        - Change the `<key>SLOSXXXXXX:username</key>` to your {{site.data.keyword.objectstorageshort}} user name.
        - Change the `<key>API Key goes here</key>` to your full API key.

5. Click **File** > **Save As..**, and change the **Save As Type** to **All Files**. Then, save your file with the name of the cluster, and add `.cyberduckprofile` to the end. <br/> ![Cyberduck Profile](/images/cyberduck_fig1.png)

6. Go to the profile file you created, and double-click it. When the application launches, two screens come up. Close the one on top. You can now see the main screen of the program.

7. Click the **bookmark** icon on the taskbar. Then, double-click your **{{site.data.keyword.objectstorageshort}}** link.<br/>
   ![Bookmark icon on the login screen](/images/cyberduck_fig2.png)

8. A window comes up asking for the login information. If you check the **Save Password** box, it doesn't open again.<br/>
   ![Login screen](/images/cyberduck_fig3.png)

9. Click **Login** to see all of your containers. <br/> ![Container list](/images/cyberduck_fig4.png)

10. At this point, Cyberduck is fully connected and you can now drag-and-drop files to and from {{site.data.keyword.objectstorageshort}}. You don't have to worry about the upload or download timing out due to the 5 GB file limit. If you run into any issues, open a support ticket.
