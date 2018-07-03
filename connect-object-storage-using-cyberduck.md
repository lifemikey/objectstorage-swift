---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-03"

---
{:new_window: target="_blank"}


# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using Cyberduck

OpenStack limits the size of any individual object to 5 GB. OpenStack supports storage of files larger than this limit through segmentation. Additionally, various clients have their own file size limits.

- iPhone/iOS: 20 MB for upload/download on the carrier network; 5 GB if you're on WiFi though
- SoftLayer Portal: 20 MB for upload/download
- Android: 20 MB for upload/download for the carrier network; 5 GB if you're on WiFi though
- AT&T: 20 MB for upload/download
- API: 5 GB

Essentially, the file size doesn't matter when it comes to using Cyberduck. Uploading a file over 5 GB is not a problem because the application automatically splits it. If you tried to upload that with sFTP or SCP, your upload would stop at 5 GB and fail. This is due to the limitation of the swftp client installed on the OpenStack servers.  

Cyberduck is compatible with Mac OS X and Windows, but there are a couple differences.

**Advantages and disadvantages of using Cyberduck**

 - Advantages - Cyberduck supports SLO (Static Large Objects). Cyberduck automatically splits files over 5 GB to create them as SLO's (Static Large Objects have each segment defined in a JSON array stored as the content of the manifest file).  You can simply drag and drop your files rather than type out complex cURL commands. You have a GUI to work with.
 - Disadvantages - there's no {{site.data.keyword.BluSoftlayer}} API functionality for this.
</table>


## Getting Started

1. Download Cyberduck from [https://cyberduck.io/](https://cyberduck.io/){:new_window} 
   - Select the right version for your OS.
2. Run the installer and let it install with defaults.
3. Obtain your user name, cluster information and API key from your **{{site.data.keyword.objectstorageshort}}** page in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Click the **{{site.data.keyword.objectstorageshort}}** user, then the cluster you want to use, then **View Credentials**.
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
     {:pre}
     
     
     2. Update the template with the following:
        - Change the `<string>softlayer-Par01</string>` to include the cluster you are using.
        - Change the `<string>Softlayer Object Storage (Paris)</string>`to the location you're usings.
        - Change the `<string>par01.objectstorage.softlayer.net</string>`to the cluster you're using.
        - Change the `<key>SLOSXXXXXX:username</key>` to your {{site.data.keyword.objectstorageshort}} user name. 
        - Change the `<key>API Key goes here</key>` to your full API key.

5. Save your file by clicking **File > Save As..**, and change the **Save As Type** to **All Files**. Then, save your file with the name of the cluster, and add **.cyberduckprofile** to the end as shown in the image. <br/> ![Cyberduck Profile](/images/cyberduck_fig1.png)

6. Go to the profile file you just created, and double-click on it. When the application launches, two screens come up, close the one on top. You can now see the main screen of the program. Simply click the **bookmark** icon on the taskbar, then double click your **{{site.data.keyword.objectstorageshort}}** link. <br/> ![](/images/cyberduck_fig2.png)
 
7. A pop-up box comes up asking for the login information. If you check the box for Save Password, it will not pop up again.  Filled out, it should look like the image below. <br/> ![](/images/cyberduck_fig3.png)

8. Click **Login** to see all of your containers. <br/> ![](/images/cyberduck_fig4.png)

9. At this point, Cyberduck is fully connected and you can now drag-and-drop files to and from {{site.data.keyword.objectstorageshort}} without having to worry about the upload or download timing out due to the 5 GB file limit. If you run into any issues, feel free to open a ticket and we will assist you.
