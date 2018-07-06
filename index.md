---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-06"

---
{:new_window: target="_blank"}


# Getting Started with {{site.data.keyword.objectstorageshort}} OpenStack Swift

{{site.data.keyword.objectstorageshort}} OpenStack Swift is a redundant and scalable cloud storage service. With {{site.data.keyword.objectstorageshort}} users can easily store, search, and retrieve data across the internet, with optional CDN connectivity, or across {{site.data.keyword.BluSoftlayer}}’s global private network. This offering was formerly known as SoftLayer {{site.data.keyword.objectstorageshort}}.

{{site.data.keyword.objectstorageshort}} can be accessed through a RESTful API and through [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. By using the {{site.data.keyword.slportal}} you can complete easy, point-and-click interactions with your account without making direct calls to the API.

**How {{site.data.keyword.objectstorageshort}} works**

{{site.data.keyword.objectstorageshort}} uses multiple servers and multiple drives. It replicates the data that you provide to the cluster across multiple physical servers. Replication ensures that your data is available exactly when you need it. To provide additional reliability, all update requests are handled through proxy servers, which abstract the actual data storage to provide the highest levels of fault tolerance. {{site.data.keyword.objectstorageshort}} is run on a RESTful interface.

The primary use of {{site.data.keyword.objectstorageshort}} is the long-term storage of static data. {{site.data.keyword.BluSoftlayer}} customers use {{site.data.keyword.objectstorageshort}} in a variety of ways, but use the system most commonly for:

- Archiving documents and email,
- Archiving system backups,
- Storing photos and videos,
- Storing virtual machine images.
    
## Introducing Key Features

Although {{site.data.keyword.objectstorageshort}} is based on OpenStack’s Swift, we offer many value-added features that are unique to {{site.data.keyword.objectstorageshort}}. Among them are:

**Integrated Indexing and Search functions**

Quickly access information through user-defined metadata key-value pairs, file names, or unique identifiers.

**Worldwide Storage Fabric**

Storage clusters that are located in North America, Europe, and Asia. With all clusters connected through {{site.data.keyword.BluSoftlayer}}’s private network, you are guaranteed secure data replication and transfer.

**Redundant Architecture**

Data is written multiple times per cluster with self-healing capabilities to immediately restore data if a drive fails.

**Flexible Data Distribution**

Highly scalable read/write access gives users the ability to serve content directly from the storage system or through {{site.data.keyword.cdn_full}}.

**Powerful Management Toolkit**

Full integration into the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}, mobile applications (iPhone, iPad, Android and Windows) and a RESTful API provides a full range of human or machine access.

## Explaining Primary {{site.data.keyword.objectstorageshort}} Concepts

If you're new to {{site.data.keyword.BluSoftlayer_full}}'s {{site.data.keyword.objectstorageshort}}, here are a few things that can better acquaint you with how this product functions and what you can expect when you use it.

**Cluster Replication**

{{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} is possible through the functionality of cluster replication. On each client's account, a cluster, or set of servers, exists. When using {{site.data.keyword.objectstorageshort}}, your data is replicated across the cluster, ensuring that if a single server fails, your data is still retrievable. Clusters are located in datacenters in Amsterdam, Dallas and Singapore.

**Eventual Consistency**

{{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} functions on the principle of eventual consistency. Because your data is replicated to your cluster, it exists on multiple servers. When the time comes for each server to be updated, those updates generally occur independently of one another but they eventually hit all servers so they mirror each other once again. In practice, the upload operation might appear to have completed to your client, but the data that you upload might not become immediately available for retrieval.

The principle of Eventual Consistency helps {{site.data.keyword.objectstorageshort}} work reliably in a distributed and scalable fashion. For example, if a storage node goes down during an update to a file, when the hardware comes back online, the system checks for consistency. If the node is found to be inconsistent with its partners, the system writes the latest copy of the file onto the hardware from the copy that was written to one of the online nodes.
Containers, Folders and Objects

Stored within each cluster are containers, folders and objects (files), which are vital to the functionality of {{site.data.keyword.objectstorageshort}}. Containers store your data, files assist in organizing data located within the container and an object represents the data stored. Let's review each of these a little further.

**Container**

As said before, a container is the basic storage unit for all the data within {{site.data.keyword.objectstorageshort}}. Containers work similar to a folder or directory within many operating systems, however, are unable to be nested. One container must be associated with each {{site.data.keyword.objectstorageshort}} account; however, the amount of containers which a user may create is unlimited. Aside from nesting, containers may be organized by each user to meet individual business needs.

Container names cannot contain a forward slash (/) and must be less than 256 bytes in length.

- **Folder**
  Folders are an optional addition to {{site.data.keyword.objectstorageshort}} that allows the user to better organize their metadata.
  After creating a container, both folders and files may be added. Files provide an additional layer to {{site.data.keyword.objectstorageshort}}, allowing the user to organize specific objects in specific folders, at the user’s discretion.
  Although folders are available for use with your container, the use of folders is not required. After creating a folder, it is important to note that files are not required to be organized within it. That being said, a user can view a container’s contents and see both folders and files at the same level.

- **Object (File)**
  Any data or metadata for the files stored in the system is considered an object, or file. Files stored on the system can't exceed 5 GB; files larger than 5 GB must be segmented prior to storage, but can be concatenated together so that the eventual download can be viewed as a single file.

File names must be less than 1024 bytes in length after URL encoding. 

## Accessing the {{site.data.keyword.objectstorageshort}} Screen

The {{site.data.keyword.objectstorageshort}} screen can be accessed through Navigation in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Follow the steps below to access the {{site.data.keyword.objectstorageshort}} screen.

![Figure 1: {{site.data.keyword.objectstorageshort}} in the {{site.data.keyword.slportal}}](/images/objectstorage1.png)

- Click the {{site.data.keyword.objectstorageshort}} link from the list of storage nodes located at the top of the page to access the {{site.data.keyword.objectstorageshort}} screen. If there are multiple users on an account, select the user whose {{site.data.keyword.objectstorageshort}} account you wish to access.

![Figure 2: Choose {{site.data.keyword.objectstorageshort}} User](/images/objectstorage2.png)

- Select one of the following Clusters based on the city that is of nearest proximity to your user:
    - Dallas 5 (DAL05)
    - Singapore 1 (SNG01)
    - Amsterdam 1 (AMS01)
    - San Jose 1 (SJC01)
    - Mexico 1 (MEX01)
    - Toronto 1 (TOR01)
    - Melbourne 1 (MEL01)
    - London 2 (LON02)
    - Paris 1 (PAR01)
    - Hong Kong 2 (HKG02)
    - Tokyo 2 (TOK02)
    - Frankfurt 2 (FRA02)

## {{site.data.keyword.objectstorageshort}} Client Overview

Upon clicking {{site.data.keyword.objectstorageshort}} in the menu, you are routed directly to the {{site.data.keyword.objectstorageshort}} landing page. From ordering additional {{site.data.keyword.objectstorageshort}} on your user account to adding and deleting metadata, all [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} interactions with your {{site.data.keyword.objectstorageshort}} account begin from this screen. The information displayed on the landing page is specific to the selected account and is dependent upon how containers, files and metadata are organized on the cluster. Your {{site.data.keyword.objectstorageshort}} account interactions begin on the **Account** Tab.

### Account Tab

The **Account** Tab contains a variety of information regarding your account, including account and network usage and is the access point to all information stored on your cluster. After an {{site.data.keyword.objectstorageshort}} account has been created and is in use, the Account Tab appears similar to the following image.

![Figure 3: Account Overview](/images/objectstorage3.png)
 
### Account Usage

This section of the Account tab contains an overview of the number of containers currently active on the cluster and the total amount of storage used. Also present in this section is the View Credentials link. The View Credentials link allows the user to view the credentials associated with the selected account, including the Authentication Endpoint, Username and API Key (Password). While this information is not vital for interactions using the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}, the Account Credentials will be needed for interacting with {{site.data.keyword.objectstorageshort}} through the API or another client.

### Bandwidth Usage

The various Bandwidth Usage boxes located within the Account tab display current details regarding your public and private network and CDN bandwidth through the node interface. Because {{site.data.keyword.objectstorageshort}} is currently set up on a “pay as you go” basis, you only pay for what you use. That being said, this section best assists users with understanding their usage to better manage the amount spent on {{site.data.keyword.objectstorageshort}} each month.

![Figure 4: View Credentials and Bandwidth Overview](/images/objectstorage4.png)

### Cluster Contents: Container-Level View

The third area of interest on the Account tab displays the contents of the cluster. This view varies based on what information you have accessed, but defaults to the container-level view upon initial access of the {{site.data.keyword.objectstorageshort}} account. From this section, the check box can be clicked for high-level details on the container that will be displayed in the **Details** Pane. All views available within your cluster are filterable through the **Filter** text box at the top of each view.

In addition to viewing containers, new containers may also be added. Click the **Add Container** link at the top of this view to begin the process of adding a new container to your cluster. Containers may also be deleted at this level by clicking the **delete** icon and following the prompts.

The entire contents of the container can be viewed at a folder-level and/or file-level view (dependent upon how the container is organized) by clicking the container name. Upon clicking the container name, the view will re-populate in a similar format, displaying each folder and/or file associated with the container.
![Figure 5: Cluster Contents](/images/objectstorage5.png)

### Cluster Contents: Folder/File-Level View

When the folder and/or file-level view of the account is accessed, users have the ability to view all folders associated with the container and all files associated with the container that have not yet been assigned to folders. If no folders have been associated with an account, this is the final level of organization the user may view. Clicking the check box next to the folder or file name provides information regarding the folder or in the **Details Pane**. For files present at this level, clicking the **File Name** will display the file. For folders present at this level, clicking the **Folder Name** will present an additional file-level view displaying only those files associated with the selected folder. Please note - files associated with a folder are not viewable in the initial folder-level view, even if files are displayed along with a folder. When viewing files associated with the folder, the same interactions apply as for files not associated with a folder.

In addition to viewing and expanding contents of the container on this view, both files and folders may be added at this level. Clicking the **Add File** or **Add Folder** link at the top of this view begins the process for adding either item to the selected container. Files and folders may also be deleted at this level by clicking the **delete** icon and following the prompts.

### Details Pane

The Details Pane is present throughout the navigation of your container, however, displays varied information based on the area in which you are navigating and the boxes, if any, you have clicked. As previously discussed, clicking the check box next to a specific line item located on the **Account** tab will provide high-level details regarding the item you have selected. 

When no items are checked, the **Details Pane** displays information about the part of your cluster being viewed. For example, in the previous image, the photos container has been accessed and the contents of that container are displayed on the folder/file-level view. At this level, the **Details Pane** displays an overview of the contents of the container and CDN information.

Clicking the **Actions** dropdown list within the **Details Pane** on any view allows various actions to be taken on the cluster, based on what area of the cluster is displayed within the **Details Pane**.

![Figure 6: Actions Menu](/images/objectstorage6.png)

