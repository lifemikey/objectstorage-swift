---

copyright:
  years: 2017
lastupdated: "2018-07-09"

---
{:new_window: target="_blank"}

# Adding an Object (File) via the {{site.data.keyword.slportal}}

Adding an object (file) in the {{site.data.keyword.slportal}} allows the user to upload files into the selected container associated with an {{site.data.keyword.objectstorageshort}} account. An unlimited number of files may be uploaded, but each file may not exceed 20 MB in size. Follow the steps below to add an object (file) to an {{site.data.keyword.objectstorageshort}} account.

## Add an Object

1. Access the {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Refer to [Access the {{site.data.keyword.objectstorageshort}} screen](access-object-storage-screen.html).
2. Click the **Add File** link.
3. Click the **Select box** in the pop-up to access the drives on your workstation.
4. Locate the file for upload and select the file.
5. Click the **Add** button to upload the selected file. Click **Cancel** to cancel the upload.

## What Happens Next

After uploading the file, it may be [accessed](access-object-folder-or-container.html) at any time. Additionally, it may be [edited](view-and-edit-object-storage-file-details.html) or [deleted](delete-object-cluster.html). To add additional details about the file within the {{site.data.keyword.objectstorageshort}} cluster without editing the file itself, [add meta data](add-and-edit-metadata-object.html) to the object.

Due to the {{site.data.keyword.slportal}} upload's size limit of 20 MB, consider using other means to upload larger files. See instructions for [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using the Command Line](connect-object-storage-using-command-line.html), [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using Cyberduck](connect-object-storage-using-cyberduck.html) or [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using WinSCP](connect-object-storage-using-winscp.html) for more information.
