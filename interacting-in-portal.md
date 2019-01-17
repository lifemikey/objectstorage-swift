---

copyright:
  years: 2017, 2019
lastupdated: "2019-01-17"

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

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}


## Accessing the {{site.data.keyword.objectstorageshort}} Screen

The {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} can be accessed from the main menu after login.

1. Access the {{site.data.keyword.slportal}} by using your unique credentials.
2. Select **Storage** > **{{site.data.keyword.objectstorageshort}}** from the navigation bar.
3. Click the **{{site.data.keyword.objectstorageshort}}** link from the list of storage nodes to access the {{site.data.keyword.objectstorageshort}} page. If the account has multiple users, select the user whose {{site.data.keyword.objectstorageshort}} account you want to access.
4. Select one of the following **Clusters** based on the city that is of nearest proximity to your users.
   - Amsterdam 1 (AMS01)
   - Dallas 5 (DAL05)
   - Frankfurt 2 (FRA02)
   - Hong Kong 2 (HKG02)
   - London (LON02)
   - Melbourne 1 (MEL01)
   - Paris 1 (PAR01)
   - San Jose 1 (SJC01)
   - Singapore 1 (SNG01)
   - Sydney 1 (SYD01)
   - Toronto 1 (TOR01)
   - Tokyo 2 (TOK02)

  After **31 March, 2019**, the following data center locations are no longer supported:
   - CHE01(Chennai),
   - MEX01 (Mexico City),
   - MON01 (Montreal),
   - SEO01 (Seoul)
   - OSL0 (Oslo)

## Explaining the {{site.data.keyword.objectstorageshort}} User Interface

Upon clicking {{site.data.keyword.objectstorageshort}} in the menu, you are routed directly to the {{site.data.keyword.objectstorageshort}} landing page. From ordering more {{site.data.keyword.objectstorageshort}} on your user account to adding and deleting metadata, all [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} interactions with your {{site.data.keyword.objectstorageshort}} account begin from this screen. The information that is displayed on the landing page is specific to the selected account and is dependent upon how containers, files and metadata are organized on the cluster. Your {{site.data.keyword.objectstorageshort}} account interactions begin on the **Account** Tab.

- **Account Tab**

  The **Account** Tab contains various information about your account, including account and network usage and is the access point to all information stored on your cluster.

- **Account Usage**

  This section of the Account tab contains an overview of the number of containers that are currently active on the cluster and the total amount of storage that is used. Also in this section, you can see the **View Credentials** link. The View Credentials link allows the user to view the credentials that are associated with the selected account, including the Authentication Endpoint, user name and API Key (Password). While this information is not vital for interactions through the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}, the Account Credentials are needed for interacting with {{site.data.keyword.objectstorageshort}} through the API or another client.

- **Bandwidth Usage**

  The various Bandwidth Usage boxes that are located within the Account tab display current details about your public and private network, and CDN bandwidth through the node interface. Because {{site.data.keyword.objectstorageshort}} is set up on a “pay as you go” basis, you only pay for what you use. That being said, this section helps users understand their usage to better manage the amount of money that is spent on {{site.data.keyword.objectstorageshort}} each month.

- **Cluster Contents - Container-Level View**

  The third area on the Account tab displays the contents of the cluster. This view varies based on what information you accessed, but defaults to the container-level view upon initial access of the {{site.data.keyword.objectstorageshort}} account. From this section, the check box can be clicked for high-level details on the container that is displayed in the **Details** window. All views that are available within your cluster are filterable through the **Filter** text box at the top of each view.

  In addition to viewing containers, new containers can be added. Click the **Add Container** link to begin the process of adding a container to your cluster.

  Containers can also be deleted at this level by clicking the **delete** icon and following the prompts.

  The entire contents of the container can be viewed at a folder-level and file-level view (dependent upon how the container is organized) by clicking the container name. Upon clicking the container name, the view populates in a similar format, displaying each folder and file associated with the container.

- **Cluster Contents - Folder/File-Level View**

  When the folder or file-level view of the account is accessed, users can view all folders that are associated with the container and all the files that are associated with the container that weren't yet assigned to folders. If no folders were associated with an account, this is the final level of organization the user can view. Clicking the check box next to the folder or file name provides information about the folder or in the **Details** window. For files present at this level, clicking the **file name** displays the file. For folders present at this level, clicking the **folder name** opens an extra file-level view that displays only those files that are associated with the selected folder.

  The files that are associated with a folder are not viewable in the initial folder-level view, even if files are displayed along with a folder. When you view files that are associated with the folder, the same interactions apply as for files that are not associated with a folder.
  {:note}

  In addition to viewing and expanding contents of the container on this view, both files and folders can be added at this level. Clicking the **Add File** or **Add Folder** link begins the process for adding either item to the selected container. Files and folders can also be deleted at this level by clicking the **delete** icon and following the prompts.

- **Details Pane**

  The Details pane is present throughout the navigation of your container. However, this window displays varied information based on the area in which you are navigating and the boxes, if any, you clicked. Clicking the check box next to a specific line item on the **Account** tab provides high-level details about the item you selected.

  When no items are checked, the **Details** pane displays information about the part of your cluster that you're viewing. For example, in the previous image, the photos container was accessed and the contents of that container are displayed on the folder/file-level view. At this level, the **Details** window displays an overview of the contents of the container and CDN information.

  Clicking the **Actions** list within the **Details Pane** on any view allows various actions to be taken on the cluster, based on what area of the cluster is displayed within the **Details Pane**.

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

  Effective of **31 March 2019**, IBM Cloud no longer supports the CDN feature of Object Storage OpenStack Swift (infrastructure).
  {:note}

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
- [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using the command-line](connect-object-storage-using-command-line.html)
- [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using Cyberduck](connect-object-storage-using-cyberduck.html)
- [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using WinSCP](connect-object-storage-using-winscp.html)

## Accessing an Object in a Folder or Container

After an object is added, it can be accessed at any time from your {{site.data.keyword.objectstorageshort}} account. To access an object, simply click the file or folder name. Files might be downloaded according to browser settings, while folders are opened to show an extra level of objects.


## Viewing and editing file details

After a file was added, details regarding the file can be viewed and edited at any time.

1. Access the **Container** that contains the file you want to edit. <br/>
   **Note**: If the file for edit is located within a folder, click the **Folder Name** to access the folder's contents and locate the file.
2. Click the check box next to the file you want to view. The file details appear in the window to the right of the Object List.
3. Click **Actions**.
4. Select one of the following options and follow the corresponding instructions based on the action to be completed for the file:
<table>
  <caption><Table 1 shows the Actions on the left and the steps that you need to take for each action on the right.>
<tr><th>Action</th><th>Steps to complete</th></tr>
<tr><td>Copy</td><td><li>Select <strong>Copy</strong> from the <strong>Actions</strong> list.</li><li>Select a location to copy the file from the <strong>Browse Locations</strong> window.</li><li>Click <strong>Copy</strong> to copy the file. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Move</td><td><li>Select <strong>Move</strong> from the <strong>Actions</strong> list.</li><li>Select the location to move the file from the <strong>Browse Locations</strong> window.</li><li>Click <strong>Move</strong> to move the file to its new location. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Download</td><td><li>Select <strong>Download</strong> from the <strong>Actions</strong> list. The file is downloaded to your system in accordance with your browser's settings.</li></td></tr>
<tr><td>Rename</td><td><li>Select <strong>Rename</strong> from the <strong>Actions</strong> list.</li><li>Enter the new name for the file in the <strong>Rename</strong> text box.</li><li>Click <strong>OK</strong> to rename the file. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Delete</td><td><li>Select <strong>Delete</strong> from the <strong>Actions<strong> list.</li><li>Click </strong>Yes<strong> to delete the file. Click <strong>No</strong> to cancel the transaction.</li></td></tr>
</table>

The next actions are dependent upon the selections that were made. Generally, the selections dictate the actions that are taken by the system on the file, however, when you delete a file, it can't be retrieved. If a file was downloaded, it generally is available within a location in your browser. More actions can be taken on the same file consecutively, unless the file was not deleted.

## Adding and editing metadata for an Object

After an object is uploaded to the container, metadata can be associated with the object at the object view level. Adding metadata to an object help to identify an object without having to download and open the object. Metadata can be edited at any time.

1. View the object.
2. Click **Add metadata**.
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


## Deleting a Container

At any point in time, a container can be deleted from the cluster, while the container holds no data (files or folders). Before you can delete the container, all files and folders must be deleted or, if they are still needed, they can be copied, moved, or downloaded to another location.

1. Access the {{site.data.keyword.objectstorageshort}} screen on the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
2. Click **Delete**. A **Delete Container** confirmation box appears.
3. Click **Yes** to delete the container. Click **No** to cancel the request.

After a container was deleted, it can't be retrieved. It must be readded and all files or folders that were within the container must also be added back to the cluster.
