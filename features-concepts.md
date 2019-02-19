---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-05"

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

# Key concepts and features of {{site.data.keyword.objectstorageshort}}
{: #concepts}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**. Effective of **31 March 2019**, IBM Cloud no longer supports the Image Templates import/export feature.
{:deprecated}

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

Effective of **31 March 2019**, IBM Cloud will no longer support the Search function with Cloud Object Storage Swift..
{:important}

- **Worldwide Storage Fabric**

Storage clusters are located in North America, Europe, and Asia. With all the clusters that are connected through {{site.data.keyword.BluSoftlayer}}’s private network, you are guaranteed secure data replication and transfer.

- **Redundant Architecture**

Data is written multiple times per cluster with self-healing capabilities to immediately restore data if a drive fails.

- **Flexible Data Distribution**

Highly expandable read/write access gives users the ability to serve content directly from the storage system or through {{site.data.keyword.cdn_full}}.

Effective of **31 March 2019**, IBM Cloud will no longer support the Content Delivery Network (CDN) feature with Cloud Object Storage Swift.
{:important}

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
