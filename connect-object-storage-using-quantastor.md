---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using QuantaStor 

The QuantaStor appliance available from {{site.data.keyword.BluSoftlayer_full}} offers a more permanent solution for accessing your {{site.data.keyword.objectstorageshort}} account. The QuantaStor appliance acts as a storage gateway and allows you to create nfs/cifs endpoints from your {{site.data.keyword.objectstorageshort}} clusters. The endpoints can then be mounted and accessed like any other nfs/cifs share. The QuantaStor appliance uses the S3QL Python library to access your {{site.data.keyword.objectstorageshort}} account and shares many of the same features, namely: data-deduplication, encryption, and compression. The QuantaStor appliance also provides the ability to schedule backups and push them to your {{site.data.keyword.objectstorageshort}} account.

<table><tbody>
<tr><td>Advantages:	</td><td>GUI, advanced features (encryption, compression, dedup, local caching), scheduled backup of volumes to {{site.data.keyword.objectstorageshort}}</td></tr>
<tr><td>Disadvantages:</td><td>{{site.data.keyword.objectstorageshort}} containers cannot be shared by multiple hosts, configuration options are lacking (defaults assumed by QuantaStor)
</td></tr>
<tr><td>Use Cases:	</td><td>Integrated solutions, Automated backup to the cloud, permanent storage mounts</td></tr>
</tbody></table>
	

## Setup QuantaStor storage gateway

1. Access your QuantaStor console.
2. Click on the **Cloud Containers** tab.
3. Click the **Add Credentials** button.
4. Select **SoftLayer Object Storage** as your cloud provider and [enter your {{site.data.keyword.objectstorageshort}} credentials](access-object-storage-screen.html) and click **OK**.
       ![Add Cloud Provider Credentials](/images/AddCloudProviderCredentials.png)
5. Click the **Create** button under the **Cloud Container** section.
6. Fill in the form with the required information and click **OK**:
      - **Name**: Enter a name for the container, e.g., CloudStorage.
      - **Cloud Provider**: Select the SoftLayer {{site.data.keyword.objectstorageshort}} value that has the credentials you just entered./li>
      - **Location**: Select the data center where your new store is to be created.
      - **Enable NFS/CIFS Access**: Click in the checkbox if not already checked.
      - **Encryption Key**: Enter a password for your storage encryption key. Re-enter it in the **Confirm Encryption Key** field.
7. In order to use the new container, mount it from a Linux machine. Open a new terminal and create a new directory to be used as our mount point: `mkdir /mnt/quanta`
8. Mount the cloud storage container:<br/>
      ``mount.nfs4 :/`` <br/>
      ``mount.nfs4 10.114.94.142:/CloudStorage /mnt/quanta``
9. Access the directory like any other local directory, with the difference being that it's backed by {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.
