---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-03"

---
{:new_window: target="_blank"}
{:note: .deprecated} 
{:codeblock: .codeblock} 
{:pre: .pre}

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift with S3QL

S3QL is the Python utility that QuantaStor uses to mount its cloud containers. If you don't have a QuantaStor appliance or want to manage your endpoints manually, then you can install and use the S3QL utility. S3QL supports a wide range of features, such as data-deduplication, compression, encryption, and caching. The following example uses Ubuntu 14.04. Your instructions might vary depending on your distribution.

** Advantages and disadvantages of using S3QL**
- Advantages - Advanced features (encryption, compression, dedup, local caching), highly configurable (cache size, compression method).
- Disadvantages - Object storage containers cannot be shared by multiple hosts, No graphical interface</td></tr>

This solution works great for Integrated solutions, and permanent storage mounts.

## Mounting container with S3QL

1. Open a new terminal and install S3QL (these command are for Ubuntu, your distribution's commands may vary):<br/>
   ```
   apt-get install software-properties-common
   apt-add-repository ppa:nikratio/s3ql
   apt-get update
   apt-get install s3ql
   ```
   {:pre}
   
2. Create a directory to store your credentials:<br/>
   ```
   mkdir ~/.s3ql && touch ~/.s3ql/authinfo2
   chmod 600 ~/.s3ql/authinfo2
   ```
   {:pre}
   
3. Open the newly created file using your favorite editor and add the following information:
   ``` 
   [swift]
   backend-login: 
   backend-password: 
   storage-url: 
   ```
   {:pre}
   
   
   Example:
   ```
   [swift]
   backend-login: IBMOS278685-10:sesson 
   backend-password: #########################
   storage-url: swift://
   ```
   
4. Create a new {{site.data.keyword.objectstorageshort}} container for your S3QL file system.
5. Make your new S3QL file system. <br/>
   ```
   mkfs.s3ql swift://:443/
   ```
   {:pre}
   
   Example
   ```
   mkfs.s3ql swift://tor01.objectstorage.softlayer.net:443/s3qltest
   ```
   
6. Create a new mountpoint for your file system.<br/>
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
