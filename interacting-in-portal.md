---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:shortdesc: .shortdesc}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}

# Interacting with {{site.data.keyword.objectstorageshort}} through the {{site.data.keyword.slportal}}

## Accessing the {{site.data.keyword.objectstorageshort}} Screen

The {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} can be accessed from the main menu after login.

1. Access the {{site.data.keyword.slportal}} by using your unique credentials.
2. Select **Storage** > **{{site.data.keyword.objectstorageshort}}** from the navigation bar.<br/>
   ![{{site.data.keyword.objectstorageshort}} menu option](/images/ObjectStorageMenu.png)
3. Click the **{{site.data.keyword.objectstorageshort}}** link from the list of storage nodes to access the {{site.data.keyword.objectstorageshort}} page. If the account has multiple users, select the user whose {{site.data.keyword.objectstorageshort}} account you want to access.
4. Select one of the following **Clusters** based on the city that is of nearest proximity to your users.
   - Amsterdam 1 (AMS01)
   - Dallas 5 (DAL05)
   - Frankfurt 2 (FRA02)
   - Hong Kong 2 (HKG02)
   - London (LON02)
   - Melbourne 1 (MEL01)
   - Mexico 1 (MEX01)
   - Montreal 1 (MON01)
   - Paris 1 (PAR01)
   - San Jose 1 (SJC01)
   - Singapore 1 (SNG01)
   - Sydney 1 (SYD01)
   - Toronto 1 (TOR01)
   - Tokyo 2 (TOK02)


## Managing {{site.data.keyword.objectstorageshort}} OpenStack Swift User Permissions

User permissions for {{site.data.keyword.objectstorageshort}} accounts require that several individual permissions be granted. By using the Manage Users feature for {{site.data.keyword.objectstorageshort}}, the account administrator can manage users' {{site.data.keyword.objectstorageshort}} permissions by clicking a single check box. Additionally, multiple users can be managed at one time on the same screen. It's important to note the following information.

  - Access to each {{site.data.keyword.objectstorageshort}} Account and Cluster are impacted. If access is removed, the user loses access to all Accounts and Clusters for {{site.data.keyword.objectstorageshort}}.
  - {{site.data.keyword.objectstorageshort}} permissions are derived from a combination of permissions from Storage CDN and StorageLayer. Granting access to {{site.data.keyword.objectstorageshort}} means giving users permissions from those sets. Removing permissions for {{site.data.keyword.objectstorageshort}} results in the removal of permissions for Storage CDN and StorageLayer. For more information, see the [FAQ](https://console.bluemix.net/docs/infrastructure/content-deliver-network/FAQ.html#can-a-user-have-cdn-and-storagelayer-permissions-granted-but-be-prohibited-from-accessing-object-storage-){:new_window}.


### Managing an {{site.data.keyword.objectstorageshort}} User

1. Access the {{site.data.keyword.objectstorageshort}} screen on the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. On the Account tab, click the **Manage Users**.
3. Locate the user by scrolling through the list or typing the user's name in the **Filter** field.
4. Select the **Grant Access** check box to grant the user permission to view and manage the {{site.data.keyword.objectstorageshort}} account. Clear the **Grant Access** check box to remove the user's permission set.
5. Repeat the previous two steps until all permissions are updated.
6. Click **Save** to save the changes. Click **Cancel** to cancel the action.

After you granted or removed permissions for {{site.data.keyword.objectstorageshort}}, the changes are reflected in the following permissions for each user that were changed:

  - Manage Storage CDN
  - Manage Storage CDN File Transfer
  - Manage StorageLayer


## Adding a Container to a Cluster

A container houses data that is associated with an {{site.data.keyword.objectstorageshort}} account and is associated with an {{site.data.keyword.objectstorageshort}} cluster. At least one container must exist per account. However, multiple containers can be made and maintained according to the user's needs.

1. Access the **{{site.data.keyword.objectstorageshort}}** screen in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Click **Add Container**.
3. Enter the name of the container in the **Container Name** field. Container names must be 256 characters or less after URL encoding and cannot contain a forward slash (`/`).
2. Click **OK** to create your container. The new container appears as the first container within the cluster.


## Accessing and Exiting a Container

After a container is created, files and folders can be added and organized within the container. Before you can complete any task within a container, it must be accessed first. To complete a task within another container or directly in the cluster, the user must first exit the container.

1. Access the {{site.data.keyword.objectstorageshort}} screen on the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Click the **Container Name** to access the container.
3. Click the **Cluster Name** to exit the container and return to the cluster.


## Adding a Folder to a Container

Adding a folder in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} allows for organization of files that would ordinarily be placed directly in the container. Folders can be added to the container itself or to another folder to provide extra options for organization. The process for adding a folder directly to a container or adding a folder to another folder (nesting folders) is the same.

1. Access the container.
2. Click **Add Folder**.
3. Enter the name of the new folder in the **Add New Folder** text box.
4. Click **OK** to create the folder. Click **Cancel** to cancel the action.


## Adding an Object (File) through the {{site.data.keyword.slportal}}

Adding an object (file) in the {{site.data.keyword.slportal}} allows the user to upload files into the selected container that is associated with an {{site.data.keyword.objectstorageshort}} account. An unlimited number of files can be uploaded, but each file can't exceed 20 MB.

1. Access the {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Click **Add File**.
3. Click the **Select box** to access the drives on your workstation.
4. Locate the file for upload and select the file.
5. Click **Add** to upload the selected file. Click **Cancel** to cancel the upload.

Due to the {{site.data.keyword.slportal}} upload's size limit of 20 MB, you might consider other means to upload larger files. For more information, see the following instructions.
- [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using the Command Line](connect-object-storage-using-command-line.html)
- [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using Cyberduck](connect-object-storage-using-cyberduck.html)
- [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using WinSCP](connect-object-storage-using-winscp.html)

## Accessing an Object in a Folder or Container

After an object is added, it can be accessed at any time from your {{site.data.keyword.objectstorageshort}} account. To access an object, simply click the file or folder name. Files might be downloaded according to browser settings, while folders are opened to show an extra level of objects.


## Viewing and Editing File Details

After a file was added, details regarding the file can be viewed and edited at any time.

1. Access the **Container** that contains the file you want to edit. <br/>
   **Note**: If the file for edit is located within a folder, click the **Folder Name** to access the folder's contents and locate the file.
2. Click the check box next to the file you want to view. The file details appear in the window to the right of the Object List.
3. Click **Actions**.
4. Select one of the following options and follow the corresponding instructions based on the action to be completed for the file:
<table>
  <caption><Table 1 shows the Actions on the left and the steps that you need to take for each action on the right.>
<tr><th>Action</th><th>Steps to Complete</th></tr>
<tr><td>Copy</td><td><li>Select <strong>Copy</strong> from the <strong>Actions</strong> list.</li><li>Select a location to copy the file from the <strong>Browse Locations</strong> window.</li><li>Click <strong>Copy</strong> to copy the file. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Move</td><td><li>Select <strong>Move</strong> from the <strong>Actions</strong> list.</li><li>Select the location to move the file from the <strong>Browse Locations</strong> window.</li><li>Click <strong>Move</strong> to move the file to its new location. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Download</td><td><li>Select <strong>Download</strong> from the <strong>Actions</strong> list. The file is downloaded to your system in accordance with your browser's settings.</li></td></tr>
<tr><td>Rename</td><td><li>Select <strong>Rename</strong> from the <strong>Actions</strong> list.</li><li>Enter the new name for the file in the <strong>Rename</strong> text box.</li><li>Click <strong>OK</strong> to rename the file. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Delete</td><td><li>Select <strong>Delete</strong> from the <strong>Actions<strong> list.</li><li>Click </strong>Yes<strong> to delete the file. Click <strong>No</strong> to cancel the transaction.</li></td></tr>
</table>

The next actions are dependent upon the selections that were made. Generally, the selections dictate the actions that are taken by the system on the file, however, when you delete a file, it can't be retrieved. If a file was downloaded, it generally is available within a location in your browser. More actions can be taken on the same file consecutively, unless the file was not deleted.

## Adding and Editing Metadata for an Object

After an object is uploaded to the container, metadata can be associated with the object at the object view level. Adding metadata to an object help to identify an object without having to download and open the object. Metadata can be edited at any time.

1. View the object.
2. Click **Add Metadata**.
3. Enter the metadata key in the first text box. The metadata key must indicate the type of metadata you want to enter. Examples for metadata keys are things like `Artist`, `Song` and `Topic`.
4. Enter the metadata value in the second text box. The metadata value corresponds with the key entered.
5. Click **Update** to add the metadata. Click **Cancel** to cancel the action.

After you added metadata to a file, files can be located more easily, and metadata values can also be searched when you're trying to locate a file by using {{site.data.keyword.objectstorageshort}} search function. More than one set of metadata can be added. Repeat these steps to add more metadata to the same file.


## Searching within a Cluster

In addition to cluster, container, and object interactions, you can search across the entire cluster, regardless of what level of data is being viewed.

1. Access the {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Enter the search term or terms in the Search field. <br/>
   **Note**: The Search field for {{site.data.keyword.objectstorageshort}} is on the middle of the screen, to the right of your current location within the cluster hierarchy.
3. Click **Search**.

The system returns all containers and objects that match the search criteria where files and containers are normally viewed.

## Deleting an Object in a Cluster

Similar to containers, users can also delete an object at any time. Like containers, folders must be empty before the deletion. No restrictions are set for files.

1. Access the **{{site.data.keyword.objectstorageshort}}** screen in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Scroll over the **Container Name**.
3. Click **Delete**. A Delete Object confirmation box appears.<br/>
   ![Delete Object](/images/Delete_Object.png)
4. Click **Yes** to delete the object. Click **No** to cancel the request.

Objects can be deleted when they are no longer needed. After an object is deleted, it can't be retrieved.


# Deleting a Container

At any point in time, a container can be deleted from the cluster, while the container holds no data (files or folders). Before you can delete the container, all files and folders must be deleted or, if they are still needed, they can be copied, moved, or downloaded to another location.

1. Access the {{site.data.keyword.objectstorageshort}} screen on the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Click **Delete**. A **Delete Container** confirmation box appears.
3. Click **Yes** to delete the container. Click **No** to cancel the request.

After a container was deleted, it can't be retrieved. It must be readded and all files or folders that were within the container must also be added back to the cluster.
