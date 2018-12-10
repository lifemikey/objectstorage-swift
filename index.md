---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-10"

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


# Getting Started with {{site.data.keyword.objectstorageshort}} OpenStack Swift

{{site.data.keyword.objectstorageshort}} OpenStack Swift is a redundant and expandable cloud storage service. With {{site.data.keyword.objectstorageshort}} users can easily store, search, and retrieve data across the internet, with optional CDN connectivity, or across {{site.data.keyword.BluSoftlayer}}’s global private network. This offering was formerly known as SoftLayer {{site.data.keyword.objectstorageshort}}. {{site.data.keyword.objectstorageshort}} can be accessed through a RESTful API and through [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}. By using the {{site.data.keyword.slportal}} you can complete easy, point-and-click interactions with your account without making direct calls to the API.
{:shortdesc}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**. 
{:deprecated}

The Swift Object Storage service that is provisioned from and managed in the [{{site.data.keyword.BluSoftlayer_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")] (https://www.ibm.com/cloud/infrastructure) are no longer be sold or marketed after **10 December 2018**.

Existing Swift accounts continue to be supported, but no new Swift accounts are created. The service is replaced by the [{{site.data.keyword.cos_full}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/object-storage) which is provisioned from and managed in the unified console alongside our PaaS offerings such as Containers and Watson services. 

{{site.data.keyword.cos_notm}} is available at a lower cost per GB than OpenStack Swift. {{site.data.keyword.cos_notm}} is designed to provide the performance, flexibility, and pricing that fits your workload demands and data access patterns. 

{{site.data.keyword.cos_notm}} benefits:
* Secure to the core
   - Integration with {{site.data.keyword.iamlong}} allows for granular access control at the bucket-level by using role-based policies.
   - All data is encrypted at-rest and in-flight by default.
   - Encryption keys are automatically managed by default but can optionally be self-managed or managed by using {{site.data.keyword.keymanagementservicelong}}.
* Built for all your applications
  - Select the best resiliency to store your data – “Cross Region”, “Regional”, and“Single Location” storage options are available.
  - Flexible data storage classes for Active, Less Active, Cold and Dynamic workloads.
  - No charge for data ingress.
  - Lowest cost archive with lifecycle policies for long-term data retention.
  - Analyze data directly in {{site.data.keyword.cos_notm}} with {{site.data.keyword.sqlquery_full}}.
  
**Recommended Action** 

Migrate to {{site.data.keyword.cos_notm}} to take advantage of the superior cost-performance profile. Please, migrate your workloads to the [{{site.data.keyword.cos_notm}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/cloud-object-storage) at your earliest convenience.

For more information about how to perform the migration, see [Migrating data from OpenStack Swift](https://{DomainName}/docs/services/cloud-object-storage/tutorials/migrate.html#migrating-data-from-openstack-swift)
{:tip}

If you no longer use {{site.data.keyword.objectstorageshort}} OpenStack Swift and no longer need your data stored, please delete your Swift account from the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.

If you have questions, reach out to swift-cos-migration@wwpdl.vnet.ibm.com or raise a support case.


**How {{site.data.keyword.objectstorageshort}} works**

{{site.data.keyword.objectstorageshort}} uses multiple servers and multiple drives. It replicates the data that you provide to the cluster across multiple physical servers. Replication ensures that your data is available exactly when you need it. To provide more reliability, all update requests are handled through proxy servers, which abstract the actual data storage to provide the highest levels of fault tolerance. {{site.data.keyword.objectstorageshort}} is run on a RESTful interface.

The primary use of {{site.data.keyword.objectstorageshort}} is the long-term storage of static data. {{site.data.keyword.BluSoftlayer}} customers use {{site.data.keyword.objectstorageshort}} in various ways, but use the system most commonly for

- Archiving documents and email,
- Archiving system backups,
- Storing photos and videos,
- Storing virtual machine images.

## Introducing Key Features

Although {{site.data.keyword.objectstorageshort}} is based on OpenStack’s Swift, {{site.data.keyword.BluSoftlayer}} offered many unique features. Among them are:

- **Integrated Indexing and Search functions**

Quickly access information through user-defined metadata key-value pairs, file names, or unique identifiers.

- **Worldwide Storage Fabric**

Storage clusters are located in North America, Europe, and Asia. With all the clusters that are connected through {{site.data.keyword.BluSoftlayer}}’s private network, you are guaranteed secure data replication and transfer.

- **Redundant Architecture**

Data is written multiple times per cluster with self-healing capabilities to immediately restore data if a drive fails.

- **Flexible Data Distribution**

Highly expandable read/write access gives users the ability to serve content directly from the storage system or through {{site.data.keyword.cdn_full}}.

- **Powerful Management Toolkit**

Full integration into the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}, mobile applications (iPhone, iPad, Android, and Windows) and a RESTful API provides a full range of human or machine access.

## Explaining Primary {{site.data.keyword.objectstorageshort}} Concepts

If you're new to {{site.data.keyword.BluSoftlayer_full}}'s {{site.data.keyword.objectstorageshort}}, here are a few things that can better acquaint you with how this product functions and what you can expect when you use it.

**Cluster Replication**

{{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} is possible through the functionality of cluster replication. On each client's account, a cluster, or set of servers, exists. When you use {{site.data.keyword.objectstorageshort}}, your data is replicated across the cluster. Your data is still retrievable, even if one of the servers fails.

**Eventual Consistency**

{{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} functions on the principle of eventual consistency. Because your data is replicated to your cluster, it exists on multiple servers. When the time comes for each server to be updated, those updates generally occur independently of one another. However, the changes eventually reach all servers so they mirror each other again. In practice, the upload operation might appear to complete to your client, but the data that you uploaded might not become available for retrieval immediately.

The principle of Eventual Consistency helps {{site.data.keyword.objectstorageshort}} work reliably in a distributed and expandable fashion. For example, if a storage node goes down during an update to a file, when the hardware comes back online, the system checks for consistency. If the node is found to be inconsistent with its partners, the system writes the most recent copy of the file onto the hardware from the copy that was written to one of the online nodes.


**Containers, Folders, and Objects**

Stored within each cluster are containers, folders, and objects (files), which are vital to {{site.data.keyword.objectstorageshort}}. Containers store your data, files help organizing data that is located within the container and an object represents the data that is stored.

**Container**

A container is the basic storage unit for all the data within {{site.data.keyword.objectstorageshort}}. Containers work similar to a folder or directory within many operating systems. However, containers can't be nested.

One container must be associated with each {{site.data.keyword.objectstorageshort}} account. But the number of containers, which a user can create is unlimited. Aside from nesting, containers can be organized by each user to meet individual business needs.

Container names can't contain a forward slash (`/`) and must be less than 256 bytes.

- **Folder**
  Folders are an optional addition to {{site.data.keyword.objectstorageshort}} that allows the user to better organize their metadata.
  After a container is created, both folders and files can be added. Files provide an extra layer to {{site.data.keyword.objectstorageshort}}, allowing the user to organize specific objects in specific folders, at the user’s discretion.
  Although folders are available for use with your container, the use of folders is not required. When a folder is created, files are not required to be organized within it. That being said, a user can view a container’s contents and see both folders and files at the same level.

- **Object (File)**
  Any data or metadata for the files that are stored in the system is considered an object, or file.
  Files that are stored on the system can't exceed 5 GB. Files that are larger than 5 GB must be segmented before they are loaded to storage. However, they can be concatenated together so that the eventual download can be viewed as a single file.
  File names must be shorter than 1024 bytes after URL encoding.

## Accessing the {{site.data.keyword.objectstorageshort}} Screen

The {{site.data.keyword.objectstorageshort}} screen can be accessed through Navigation in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.

- Click the {{site.data.keyword.objectstorageshort}} link from the list of storage nodes to access the {{site.data.keyword.objectstorageshort}} screen. If there are multiple users on an account, select the user whose {{site.data.keyword.objectstorageshort}} account you want to access.

- Select one of the following Clusters based on the city that is of nearest proximity to your users.
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
