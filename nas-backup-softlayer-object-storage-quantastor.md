---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Setting up NAS Backup to {{site.data.keyword.objectstorageshort}} OpenStack Swift With QuantaStor

The {{site.data.keyword.BluSoftlayer_full}} QuantaStor platform includes the ability to backup NAS network shares to a variety of cloud storage platforms, including {{site.data.keyword.objectstoragefull}}. The QuantaStor NAS backup capability can be used to back-up NAS network shares external to the QuantaStor platform. The back-up function operates using a “server-pull” mechanism, retrieving files through the NAS interface, caching them on the QuantaStor appliance and uploading the files into {{site.data.keyword.objectstorageshort}}. Backed up files are uploaded to the configured cloud storage container.


## Add Cloud Credential to QuantaStor

1. In the QuantStor Web Administration, select the Cloud Container Tab, the in the Cloud Storage Provider pane, right-click, and select Add Credentials. <br/> ![Add Credentials](/images/add_credentials.png)
2. Select **Softlayer Object Storage** in the **Cloud Provider** pull down, then enter the account credentials into the appropriate fields.
3. The {{site.data.keyword.objectstorageshort}} account information needed for the above configuration can be obtained from the  [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}.
    1. Select **{{site.data.keyword.objectstorageshort}}** under the Storage menu item pull down.
    2. The {{site.data.keyword.objectstorageshort}} accounts under the SL Master account will be listed, or you can order an additional {{site.data.keyword.objectstorageshort}} account. All {{site.data.keyword.objectstorageshort}} accounts requested by child accounts under the Master Account are visible to and accessible by all child accounts. Care should be taken to ensure only the appropriate {{site.data.keyword.objectstorageshort}} account is utilized.
    3. Select a specific {{site.data.keyword.objectstorageshort}} account, then select the data center for where the Backup data should be stored.
    4. The {{site.data.keyword.objectstorageshort}} Data Center Cluster screen provides statistics on the utilization within the account.
    5. Click on **View Credentials** to get the account data needed for the QuantaStor configuration.

## Create Cloud Container

1. When the {{site.data.keyword.objectstorageshort}} credential has been added, it will appear on under the **Cloud Storage Providers** pane in the **QuantaStor Cloud Containers** tab. Right-click on the **credential** and select **Create Cloud Container**. <br/> ![Cloud Container](/images/cloud_container.png)
2. Enter **Name** & **Description** of the Cloud Container. Select which data center to use for backups. After the Container Creation, the **Container Name** will appear under credential in the **Cloud Storage Provider**.
   **Note**: **Enable NFS/CFS Access** checkbox needs to be checked for configuring Backup. <br/> ![Enabling NFS/CFS Access](/images/NFS_CFS.png)

## Configure Backup Policy

1. Under the **Storage Management** tab, **Network Shares** pane, the cloud container created in the previous step will now appear as one of the network shares. The cloud contain network share is a NAS to {{site.data.keyword.objectstorageshort}} gateway based on the CloudFuse opensource gateway. It is allocated on the QuantaStor boot disk and is limited to 500 MB cache. This is significant if files being backed up exceed this size.<br/> ![Backup](/images/backup.png)
2. Right Click on the cloud storage gateway network share, and select **Create Backup Policy** from the pull down menu.
3. The Backup Policy defines location where the data is backed up into, in this case the network share for the Cloud storage gateway. The backup engine is not specifically for cloud storage. It can be configured to back up any NAS file system to any other NAS file system. This configuration just happens to be pointed at a NAS gateway that is mapped to {{site.data.keyword.objectstorageshort}} based on which NAS share was clicked on. Then elect the days and times when Backup is to be performed.
4. Under remote CIFS/NFS source, select the IP address of the remote server and click the **SCAN** button. The **CIFS/NFS Export field** pull down will be populated with the NAS Exports visible from the designated device. If the NAS server is a remote device, the QuantaStor host will need to have been given permission to access the device. In this example, the NAS file system has been set to public, but security controls using A/D domain or local QuantaStor users database can also be configured.

## Advanced Settings

Under Advanced Settings options are available for Backup Mode: All Files (Mirror) or Sliding Backup Window.

 - For All Files, all changes to the source system are reflected in the back up at the next back up –e.g., if the file is deleted on the source, it will purged from the backup based on the purge policy. Purge never can be used to maintain all copied of all files forever.
 - For Sliding Backup Window, only those files created or modified during the retention period will be backed up.
 - Retention period is the time file backups will be retained in the NAS/Cloud storage repository. Also affects the which files are backed up if the Sliding Backup Window is used.
 - Start Date allows policy to be configured but not go into effect until some future date.
 - Backup Concurrency controls the number of simultaneous file copy threads used to backup the data. Five settings are available. For Backups to the NAS – {{site.data.keyword.objectstorageshort}} gateway, care should be used with parallel backups. The NAS/Cloud gateway cache is only 500 MB and highly parallelized backups could fill up the cache faster than the data can be uploaded into {{site.data.keyword.objectstorageshort}}.
 - Purge Policy - controls handling of files in the backup. Four settings are available:
    - Never Purge – All Backup copies are permanently maintained in the object storage.
    - Purge Expired & Deleted After Backup – Any files whose retention policy has expired or which were deleted from the primary source are deleted immediately following the backup.
    - Purge Expired/Deleted File Daily – Candidate files are deleted once per day. If the backup does not run on a daily basis, only expired files will be purged until the next backup detects the files which have been deleted from the primary.
    - Purge Expired/Deleted File Weekly– Candidate files are deleted once per week. Expired files and files deleted from the primary will be retained in the back up until 1 week after their deletion was detected in a backup.
