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

# Connecting to {{site.data.keyword.objectstorageshort}} with S3QL
{: #OSSS3QL}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}

S3QL is the Python utility that QuantaStor uses to mount its cloud containers. If you don't have a QuantaStor appliance or want to manage your endpoints manually, then you can install and use the S3QL utility. S3QL supports a wide range of features, such as data-deduplication, compression, encryption, and caching. The following example uses Ubuntu 14.04. Your instructions might vary depending on your distribution.

- Advantages
  - Advanced features (encryption, compression, data deduplication, local caching),
  - Highly configurable (cache size, compression method).
- Disadvantages
  - {{site.data.keyword.objectstorageshort}} containers cannot be shared by multiple hosts
  - No graphical interface

This solution works great for Integrated solutions, and permanent storage mounts.

## Mounting container with S3QL

1. Open a new terminal and install S3QL.<br/>
   ```
   apt-get install software-properties-common
   apt-add-repository ppa:nikratio/s3ql
   apt-get update
   apt-get install s3ql
   ```
   {:pre}

   These commands are for Ubuntu. Your distribution might have different ones. Check your vendor documentation.
   {:tip}

2. Create a directory to store your credentials.<br/>
   ```
   mkdir ~/.s3ql && touch ~/.s3ql/authinfo2
   chmod 600 ~/.s3ql/authinfo2
   ```
   {:pre}

3. Open the newly created file with your favorite editor, and add the following information.
   ```
   [swift]
   backend-login:
   backend-password:
   storage-url:
   ```
   {:pre}


   Example
   ```
   [swift]
   backend-login: IBMOS278685-10:sesson
   backend-password: #########################
   storage-url: swift://
   ```

4. Create an {{site.data.keyword.objectstorageshort}} container for your S3QL file system.
5. Make your new S3QL file system. <br/>
   ```
   mkfs.s3ql swift://:443/
   ```
   {:pre}

   Example
   ```
   mkfs.s3ql swift://tor01.objectstorage.softlayer.net:443/s3qltest
   ```

6. Create a mount point for your file system.<br/>
   ```
   mkdir /mnt/s3ql
   ```
   {:pre}


7. Mount your file system.<br/>
   ```
   mount.s3ql swift://:443/
   ```
   {:pre}

   Example
   ```
   mount.s3ql swift://tor01.objectstorage.softlayer.net:443/s3qltest /mnt/s3qltest
   ```
