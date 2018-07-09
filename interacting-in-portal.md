---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-09"

---
{:new_window: target="_blank"}

# Interacting with {{site.data.keyword.objectstorageshort}} through the {{site.data.keyword.slportal}}

   
        
        
        delete-object-cluster.md
        delete-container.md
        manage-object-storage-user.md
        search-within-cluster.md


## Accessing the {{site.data.keyword.objectstorageshort}} Screen

The {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} may be accessed through the user navigation after login. Follow the steps below to access the {{site.data.keyword.objectstorageshort}} screen.

1. Access the {{site.data.keyword.slportal}} using your unique credentials.
2. Select **Storage** > **{{site.data.keyword.objectstorageshort}}** from the navigation bar. <br/> ![{{site.data.keyword.objectstorageshort}} menu option](/images/ObjectStorageMenu.png)
3. Click the **{{site.data.keyword.objectstorageshort}}** link from the list of storage nodes located at the top of the page to access the {{site.data.keyword.objectstorageshort}} page. If there are multiple users on an account, select the user whose {{site.data.keyword.objectstorageshort}} account you wish to access.
4. Select one of the following **Clusters** based on the city that is of nearest proximity to your users:
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

## Adding a Container to a Cluster

A container houses data that is associated with an {{site.data.keyword.objectstorageshort}} account and is associated with an {{site.data.keyword.objectstorageshort}} cluster. At least one container must exist per account; however, multiple containers may be made and maintained according to the user's needs. Follow the steps below to add a container to a cluster.

1. Access the **{{site.data.keyword.objectstorageshort}}** screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Refer to [Access the {{site.data.keyword.objectstorageshort}} screen](access-object-storage-screen.html).
2. Click the **Add Container** link. A field will appear prompting the entry of the new container name.
3. Enter the name of the container in the **Container Name** field. Container names must be 256 characters or less after URL encoding and cannot contain a forward slash (/).
2. Click the **OK** button to create your container. Your new container will appear as the first container within the cluster.


## Accessing and Exiting a Container

After a container is created, files and folders can be added and organized within the container. Before you can complete any task within a container, it must be accessed first. To complete a task within another container or directly in the cluster, the user must first exit the container. 

1. Access the {{site.data.keyword.objectstorageshort}} screen on the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}.
2. Click the **Container Name** to access the container.
3. Click the **Cluster Name** to exit the container and return to the cluster.


## Adding a Folder to a Container

Adding a folder in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} allows for organization of files that would ordinarily be placed directly in the container. Folders may be added to the container itself or to another folder to provide additional options for organization. The process for adding a folder directly to a container or adding a folder to another folder (nesting folders) is the same. 

1. Access the container.
2. Click the **Add Folder** link.
3. Enter the name of the new folder in the **Add New Folder** text box.
4. Click the **OK** button to create the folder. Click **Cancel** to cancel the action.


## Adding an Object (File) via the {{site.data.keyword.slportal}}

Adding an object (file) in the {{site.data.keyword.slportal}} allows the user to upload files into the selected container that is associated with an {{site.data.keyword.objectstorageshort}} account. An unlimited number of files can be uploaded, but each file can not exceed 20 MB in size. 

1. Access the {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}.
2. Click the **Add File** link.
3. Click the **Select box** to access the drives on your workstation.
4. Locate the file for upload and select the file.
5. Click **Add** to upload the selected file. Click **Cancel** to cancel the upload.

Due to the {{site.data.keyword.slportal}} upload's size limit of 20 MB, you might consider using other means to upload larger files. See instructions for [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using the Command Line](connect-object-storage-using-command-line.html), [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using Cyberduck](connect-object-storage-using-cyberduck.html) or [Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using WinSCP](connect-object-storage-using-winscp.html) for more information.

## Accessing an Object in a Folder or Container

After adding an object, it can be accessed at any time from your {{site.data.keyword.objectstorageshort}} account. To access an object, simply click on the file or folder name. Files will be downloaded according browser settings, while folders will be opened to show an additional level of objects.

## Viewing and Editing File Details

After a file has been added, details regarding the file may be viewed and edited at any time. 

1. Access the **Container** containing the file requiring edit. <br/>
   **Note**: If the file for edit is located within a folder, click the **Folder Name** to access the folder's contents and locate the file.
2. Click the checkbox next to the file you wish to view. The file details appear in the pane to the right of the Object List. Proceed to the next step to edit the file details.
3. Click the **Actions** drop down list.
4. Select one of the following options and follow the corresponding instructions based on the action to be completed for the file: 
<table><tbody>
<tr><th>Action</th><th>Steps to Complete</th></tr>
<tr><td>Copy</td><td><li>Select <strong>Copy</strong> from the <strong>Actions</strong> drop down list.</li><li>Select a location to copy the file from the <strong>Browse Locations</strong> pop up box.</li><li>Click the <strong>Copy</strong> button to copy the file. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Move</td><td><li>Select <strong>Move</strong> from the <strong>Actions</strong> drop down list.</li><li>Select the location to move the file from the <strong>Browse Locations</strong> pop up box.</li><li>Click the <strong>Move</strong> button to move the file to its new location. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Download</td><td><li>Select <strong>Download</strong> from the Actions drop down list. The file will be downloaded to your system in accordance with your browser's settings.</li></td></tr>
<tr><td>Rename</td><td><li>Select <strong>Rename</strong> from the Actions drop down list.</li><li>Enter the new name for the file in the <strong>Rename</strong> text box.</li><li>Click the <strong>OK</strong> button to rename the file. Click <strong>Cancel</strong> to cancel the action.</li></td></tr>
<tr><td>Delete</td><td><li>Select Delete from the Actions drop down list.</li><li>Click the Yes button to delete the file. Click No to cancel the transaction.</li></td></tr>
</tbody></table>

The next actions are dependent upon the selections made using the previous steps. Generally, the selections will dictate the actions that are taken by the system on the file, however, when deleting a file, it cannot be retrieved. If a file was downloaded, it will generally be available within a location in your browser. Additional actions may be taken on the same file consecutively, so long as the file was not deleted.

## Adding and Editing Metadata for an Object

After an object has been uploaded to the container, metadata may be associated with the object at the object view level. Adding metadata to an object assists the user in identifying an object without having to download and open the object. Metadata may be edited at any time. Follow the steps below to add and edit the metadata associated with an object.

1. View the object.
2. Click the **Add Metadata** icon.
3. Enter the **metadata key** in the first text box. The metadata key should indicate the type of metadata you will enter. Examples for metadata keys are things like Artist, Song and Topic.
4. Enter the **metadata value** in the second text box. The metadata value corresponds with the key entered.
5. Click **Update** to add the metadata. Click **Cancel** to cancel the action.


After adding metadata to a file, files may be located more easily, and metadata values may also be searched when trying to locate a file using [{{site.data.keyword.objectstorageshort}} search functionality](search-within-cluster.html). More than one set of metadata may be added. Repeat the steps above to add additional metadata to the same file.

## Searching within a Cluster

In addition to cluster, container and object interactions, a search may be across the entire cluster, regardless of what level of data is currently being viewed. Follow the steps below to search for information within an {{site.data.keyword.objectstorageshort}} cluster.

1. Access the {{site.data.keyword.objectstorageshort}} screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}.
2. Enter the search term(s) in the Search field. <br/>
   **Note**: The Search field for {{site.data.keyword.objectstorageshort}} will be located on the middle of the screen, to the right of your current location within the cluster hierarchy.
3. Click the Search button.

The system will return all containers and objects that match the search criteria where files and containers are normally viewed. 
