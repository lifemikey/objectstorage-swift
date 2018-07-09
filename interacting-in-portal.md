---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-09"

---
{:new_window: target="_blank"}

# Interacting with {{site.data.keyword.objectstorageshort}} through the {{site.data.keyword.slportal}}

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


        access-object-storage-screen.md
        access-and-exit-container.md
        access-object-folder-or-container.md
        add-container-cluster.md
        add-folder-container.md
        add-object-file.md
        add-and-edit-metadata-object.md
        delete-object-cluster.md
        delete-container.md
        manage-object-storage-user.md
        search-within-cluster.md
        view-and-edit-object-storage-file-details.md
        view-object-details.md

## Accessing an Object in a Folder or Container

After adding an object, it can be accessed at any time from your {{site.data.keyword.objectstorageshort}} account. To access an object, simply click on the file or folder name. Files will be downloaded according browser settings, while folders will be opened to show an additional level of objects.
