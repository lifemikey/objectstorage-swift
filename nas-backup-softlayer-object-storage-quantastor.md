---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

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


# Setting up NAS backup to {{site.data.keyword.objectstorageshort}} With QuantaStor

The {{site.data.keyword.BluSoftlayer_full}} QuantaStor platform includes the ability to back up NAS network shares to various cloud storage platforms, including {{site.data.keyword.objectstoragefull}}. The QuantaStor NAS backup capability can be used to back up NAS network shares external to the QuantaStor platform. The backup function operates by using a “server-pull” mechanism, retrieving files through the NAS interface, caching them on the QuantaStor appliance and uploading the files into {{site.data.keyword.objectstorageshort}}. Backed up files are uploaded to the configured cloud storage container.


## Adding Cloud Credential to QuantaStor

1. In the QuantStor Web Administration, select the Cloud Container Tab. Then, right-click in the Cloud Storage Provider window, and select **Add Credentials**.<br/>![Add Credentials](/images/add_credentials.png)
2. Select `Softlayer Object Storage`in the **Cloud Provider** list, Then, enter the account credentials into the appropriate fields.
3. The {{site.data.keyword.objectstorageshort}} account information that is needed for the configuration can be obtained from the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
    1. Select **{{site.data.keyword.objectstorageshort}}** from the Storage menu.
    2. The {{site.data.keyword.objectstorageshort}} accounts are listed under the SL Master account, and you can also order another {{site.data.keyword.objectstorageshort}} account. All {{site.data.keyword.objectstorageshort}} accounts that are requested by child accounts under the Master Account are visible to and accessible by all other child accounts. Ensure that only the appropriate {{site.data.keyword.objectstorageshort}} account is used.
    3. Select an {{site.data.keyword.objectstorageshort}} account. Then, select the data center, where the backup data is to be stored.
    4. The {{site.data.keyword.objectstorageshort}} data center cluster screen provides statistics on the usage within the account.
    5. Click **View Credentials** to get the account data needed for the QuantaStor configuration.

## Creating a Cloud Container

1. When the {{site.data.keyword.objectstorageshort}} credential is added, it appears under the **Cloud Storage Providers** pane in the **QuantaStor Cloud Containers** tab. Right-click the **credential**, and select **Create Cloud Container**.<br/>![Cloud Container](/images/cloud_container.png)
2. Enter **Name** and **Description** of the Cloud Container. Select the data center you want to use for the backup. After the Container is created, the **Container Name** appears under the credentials in the **Cloud Storage Provider** window.

   The **Enable NFS/CFS Access** check box needs to be selected for backups.
   {:important}

   ![Enabling NFS/CFS Access](/images/NFS_CFS.png)


## Configuring the backup policy

The cloud container that was created in the previous step now appears as one of the network shares in the **Storage Management** tab. The cloud container network share acts like a "network-attached storage (NAS) to {{site.data.keyword.objectstorageshort}} gateway" based on the CloudFuse open source gateway. It is allocated on the QuantaStor boot disk and is limited to 500-MB cache. This limit is significant if files that are being backed up exceed this size.<br/> ![backup](/images/backup.png)

2. Right-click the cloud storage gateway network share, and select **Create backup Policy**.

   The backup engine is not specifically for cloud storage. It can be configured to back up any NAS file system to any other NAS file system.
   {:important}
3. Select the cloud container network share as the location. Then, select the days and times when backup is to be completed.
4. Under remote CIFS/NFS source, select the IP address of the remote server and click **SCAN**. The **CIFS/NFS export field** is populated with the NAS exports that are visible from the designated device. If the NAS server is a remote device, the QuantaStor host needs to have permission to access the device. The NAS file system can be set to public, but security controls can also be configured by using the AD domain or local QuantaStor users database.

## Configuring Advanced Settings

**Backup Mode**
 - **All Files (Mirror)** - all changes to the source system are reflected in the backup at the next time the backup process runs. For example, if the file is deleted on the source, it is purged from the backup based on the purge policy.
 - **Sliding backup Window** - only those files that were created or modified during the retention period are backed up.

**Retention Period**
 - Retention period is the time when file backups are retained in the NAS/Cloud storage repository. It also affects which files are backed up, if the sliding backup window is used.

**Start Date**
 - By using a start date in the future, you can configure the backup policy now to come into effect later.

**Backup Concurrency**
 - Backup Concurrency controls the number of simultaneous file copy threads that are used to back up the data. Five settings are available. You need to be careful if you run parallel backups through the NAS – {{site.data.keyword.objectstorageshort}} gateway. The NAS/Cloud gateway cache is only 500 MB and highly parallelized backups might fill up the cache faster than the data can be uploaded into {{site.data.keyword.objectstorageshort}}.

**Purge Policy**
 - The purge policy controls handling of files in the backup. Four settings are available:
    - **Never Purge** – All backup copies are permanently maintained in the {{site.data.keyword.objectstorageshort}}.
    - **Purge Expired and Deleted After backup** – Any files with an expired retention policy, or which were deleted from the primary source, are deleted immediately following the backup.
    - **Purge Expired/Deleted File Daily** – Candidate files are deleted once a day. If the backup does not run daily, only expired files are purged until the next backup detects the files, which were deleted from the primary.
    - **Purge Expired/Deleted File Weekly**– Candidate files are deleted once per week. Expired files and files that were deleted from the primary are retained in the backup for one week after their deletion is detected in a backup.
