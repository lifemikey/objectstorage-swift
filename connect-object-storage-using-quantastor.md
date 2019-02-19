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

# Connecting to {{site.data.keyword.objectstorageshort}} with QuantaStor
{: #OSSQuanta}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}

The QuantaStor appliance available from {{site.data.keyword.BluSoftlayer_full}} offers a more permanent solution for accessing your {{site.data.keyword.objectstorageshort}} account. The appliance acts as a storage gateway so you can create NFS/CIFS endpoints from your {{site.data.keyword.objectstorageshort}} clusters. The endpoints can then be mounted and accessed like any other NFS/CIFS  share. The appliance uses the S3QL Python library to access your {{site.data.keyword.objectstorageshort}} account and shares many of the same features, such as data-deduplication, encryption, and compression. With the QuantaStor appliance, you can also schedule backups and push them to your {{site.data.keyword.objectstorageshort}} account.

- Advantages
  - GUI
  - Advanced features (encryption, compression, deduplication, local caching)
  - Scheduled backup of volumes to {{site.data.keyword.objectstorageshort}}
- Disadvantages
  - {{site.data.keyword.objectstorageshort}} containers cannot be shared by multiple hosts
  - Configuration options are lacking (defaults are assumed by QuantaStor)

QuantaStor works great for integrated solutions, automated backups to the cloud, and permanent storage mounts.

## Setting up QuantaStor storage gateway

1. Access your QuantaStor console.
2. Click **Cloud Containers**.
3. Click **Add Credentials**.
4. Select **SoftLayer Object Storage** as your cloud provider, and [enter your {{site.data.keyword.objectstorageshort}} credentials](/docs/infrastructure/objectstorage-swift?topic=objectstorage-swift-OSSSLPortal) and click **OK**.
       ![Add Cloud Provider Credentials](/images/AddCloudProviderCredentials.png)
5. Click **Create** in the **Cloud Container** section.
6. Complete the form with the required information, and click **OK**.
   - **Name** - Enter a name for the container, for example `CloudStorage`.
   - **Cloud Provider** - Select the `SoftLayer` {{site.data.keyword.objectstorageshort}} value that has the credentials that you entered./li>
   - **Location** - Select the data center where your new store is to be created.
   - **Enable NFS/CIFS Access** - Click the check box if it isn't already checked.
   - **Encryption Key** - Enter a password for your storage encryption key. Repeat it in the **Confirm Encryption Key** field.
7. To use the new container, mount it from a Linux server. Open a new terminal and create a directory to be used as the mount point.
   ```
   mkdir /mnt/quanta
   ```

8. Mount the cloud storage container.<br/>
   ```
   mount.nfs4 :/
   ```

   ```
   mount.nfs4 10.114.94.142:/CloudStorage /mnt/quanta
   ```

9. Access the directory like any other local directory. The only difference is that it is backed by {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.
