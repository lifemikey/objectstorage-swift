---

copyright:
  years: 2017
lastupdated: "2017-06-30"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Introduction to Object Storage 

## Overview

Object Storage is a redundant and highly scalable cloud storage service that allows users to easily store, search, and retrieve data across the Internet, with optional CDN connectivity, or across SoftLayer’s global private network. It is based on the OpenStack Swift platform.

Object Storage may be accessed through a RESTful API and through SoftLayer's Web Portal. Using the Web Portal allows for easy, point-and-click interactions with your account without making direct calls to the API. This training module reviews the basic interactions a user will make with Object Storage via SoftLayer's Web Portal.

## How Object Storage Works

Object Storage uses multiple servers and multiple drives, meaning it replicates the data you provide to the cluster across multiple physical servers. Replication ensures that your data will be available exactly when you need it. To provide additional reliability, all update requests are handled through proxy servers, which abstract the actual data storage to provide the highest levels of fault tolerance. Object Storage is run on a RESTful interface.

The primary use of Object Storage is the long-term storage of static data. SoftLayer customers use Object Storage in a variety of ways, but use the system most commonly for:

- Archiving documents and email
- Archiving system backups
- Storing photos and videos
- Storing virtual machine images
    
## Key Features

Although Object Storage is based on OpenStack’s Swift, we offer many value-added features that are unique to Object Storage. Among them are:

### Integrated Indexing and Search Functionality

Quickly access information through user-defined metadata key-value pairs, file names or unique identifiers.

### Wordwide Storage Fabric

Storage clusters located in North America, Europe and Asia. With all clusters connected via SoftLayer’s private network, you are guaranteed secure data replication and transfer.

### Redundant Architecture

Data is written multiple times per cluster with self-healing capabilities to immediately restore data in the event of drive failure.

### Flexible Data Distribution

Highly scalable read/write access gives users the ability to serve content directly from the storage system or via SoftLayer’s Content Delivery Network (CDN).

### Powerful Management Toolkit

Full integration into the [Customer Portal](https://control.softlayer.com/), mobile applications (iPhone, iPad, Android and Windows) and a RESTful API provides a full range of human or machine access.

## Primary Object Storage Concepts

If you're new to IBM Bluemix's Object Storage, here are a few things that will better acquaint you with how this product functions and what you can expect when you use it.

### Cluster Replication

Bluemix Object Storage is possible through the functionality of cluster replication. On each client's account, a cluster, or set of servers, exists. When using Object Storage, your data will be replicated across the cluster, ensuring that in the instance that a single server fails, your data will still be retrievable. Clusters are located in datacenters in Amsterdam, Dallas and Singapore.

### Eventual Consistency

Bluemix Object Storage functions on the principle of eventual consistency. Because your data is replicated to your cluster, it exists on multiple servers. When the time comes for each server to be updated, those updates generally occur independently of another but will eventually hit all servers to allow them to mirror each other once again. In practice, this means that although the upload operation may appear to have completed to your client, the data you upload may not become immediately available for retrieval.

The principle of Eventual Consistency helps Object Storage work reliably in a distributed and scalable fashion. For example, if a storage node goes down during an update to a file, once the hardware comes back online, the system checks for consistency. If the node is found to be inconsistent with its partners, the system writes the latest copy of the file onto the hardware from the copy that was written to one of the online nodes.
Containers, Folders and Objects

Stored within each cluster are containers, folders and objects (files), which are vital to the functionality of Object Storage. Containers store your data, files assist in organizing data located within the container and an object represents the data stored. Let's review each of these a little further.

### Container

As said before, a container is the basic storage unit for all the data within Object Storage. Containers work similar to a folder or directory within many operating systems, however, are unable to be nested. One container must be associated with each Object Storage account; however, the amount of containers which a user may create is unlimited. Aside from nesting, containers may be organized by each user to meet individual business needs.

Container names cannot contain a forward slash (/) and must be less than 256 bytes in length.

#### Folder

Folders are an optional addition to Object Storage that allows the user to better organize their metadata. After creating a container, both folders and files may be added. Files provide an additional layer to Object Storage, allowing the user to organize specific objects in specific folders, at the user’s discretion. Although folders are available for use with your container, the use of folders is not required. After creating a folder, it is important to note that files are not required to be organized within it. That being said, a user can view a container’s contents and see both folders and files at the same level. This concept will be discussed further below.

#### Object (File)

Any data or metadata for the files stored in the system is considered an object, or file. Files stored on the system cannot exceed 5GB; files larger than 5GB must be segmented prior to storage, but may be concatenated together so that the eventual download may be viewed as a single file.

File names must be less than 1024 bytes in length after URL encoding. 

## Accessing the Object Storage Screen

The Object Storage screen can be accessed through Navigation in the [Customer Portal](https://control.softlayer.com/). Follow the steps below to access the Object Storage screen.

![Figure 1: Object Storage in the Customer Portal](/images/objectstorage1.png)

- Click the Object Storage link from the list of storage nodes located at the top of the page to access the Object Storage screen. If there are multiple users on an account, select the user whose Object Storage account you wish to access.

![Figure 2: Choose Object Storage User](/images/objectstorage2.png)

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

## Object Storage Client Overview

Upon clicking Object Storage in the menu, you will be routed directly to the Object Storage landing page. From ordering additional Object Storage on your user account to adding and deleting metadata, all Portal interactions with your Object Storage account begin from this screen. The information displayed on the landing page is specific to the selected account and is dependent upon how containers, files and metadata are organized on the cluster. Your Object Storage account interactions begin on the **Account** Tab.

### Account Tab

The **Account** Tab contains a variety of information regarding your account, including account and network usage and is the access point to all information stored on your cluster. After an Object Storage account has been created and is in use, the Account Tab will appear similar to the image below.

![Figure 3: Account Overview](/images/objectstorage3.png)
 
### Account Usage

This section of the Account tab contains an overview of the number of containers currently active on the cluster and the total amount of storage used. Also present in this section is the View Credentials link. The View Credentials link allows the user to view the credentials associated with the selected account, including the Authentication Endpoint, Username and API Key (Password). While this information is not vital for interactions using the Web Portal, the Account Credentials will be needed for interacting with Object Storage through the API or another client.

### Bandwidth Usage

The various Bandwidth Usage boxes located within the Account tab display current details regarding your public and private network and CDN bandwidth through the node interface. Because Object Storage is currently set up on a “pay as you go” basis, you only pay for what you use. That being said, this section best assists users with understanding their usage to better manage the amount spent on Object Storage each month.

![Figure 4: View Credentials and Bandwidth Overview](/images/objectstorage4.png)

### Cluster Contents: Container-Level View

The third area of interest on the Account tab displays the contents of the cluster. This view varies based on what information you have accessed, but defaults to the container-level view upon initial access of the Object Storage account. From this section, the check box can be clicked for high-level details on the container that will be displayed in the **Details** Pane. All views available within your cluster are filterable through the **Filter** text box at the top of each view.

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

