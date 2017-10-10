---

copyright:
  years: 2017
lastupdated: "2017-10-10"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# IBM Cloud Object Storage (Swift) FAQ

## Can a Sub-User Access Object Storage?

Any [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} user with appropriate permissions may access and interact with Object Storage. If permissions have not been granted, the Object Storage menu option will not appear within the {{site.data.keyword.slportal}}. To grant or remove permissions for Object Storage, refer to [Manage an Object Storage User](manage-object-storage-user.html).

## Can a User Have Edgecast CDN and StorageLayer Permissions Granted but be Prohibited from Accessing Object Storage?

If a user has the Manage CDN Account, Manage CDN File Transfers and Manage StorageLayer permissions granted, the user automatically has access to Object Storage, as well. At the current time, granting access to CDN and StorageLayer while prohibiting access to Object Storage, or vice versa, is not an option.

## What Is the File Upload Limit for Object Storage?

The upload limit is approximately 5GB for a single file. You will also have to take in consideration any device limitation - iOS (iPhone, iPod Touch, iPad) Android and Windows Phone are currently supported. If you require a file size larger than 5GB, utilize segmentation. For more information regarding segmentation, review OpenStack’s [segmentation overview](http://docs.openstack.org/developer/swift/overview_large_objects.html) for swift.

## How Do I Interact with Object Storage?

Users access Object Storage through the {{site.data.keyword.slportal}}, {{site.data.keyword.BluSoftlayer_full}}’s API or a third party client. For best results, use the Object Storage through the API. Interacting with Object Storage through our API allows the most control over your files and greater flexibility when utilizing your Object Storage account.

## What Are the Best Uses for Object Storage?

The best uses are for long term static data that do not require frequent manipulation.  Examples include photographs, videos, backups, virtual machine images. Object Storage is not recommended for data sets that need to be manipulated often.

## Which Devices Can Connect and Upload to an Object Storage Account via the {{site.data.keyword.slportal}}?

Any mobile device currently supported by {{site.data.keyword.BluSoftlayer_full}}  has the ability to connect and upload items to the user’s Object Storage account via the Portal. {{site.data.keyword.BluSoftlayer_full}} currently supports iOS (iPhone, iPod Touch, iPad) Android and Windows Phone through our mobile apps designed with each device in mind. To download the {{site.data.keyword.BluSoftlayer_full}} Mobile app for your device, go to the Mobile Apps page on {{site.data.keyword.BluSoftlayer_full}}’s website.

## What Type of Authentication Do I Need for Object Storage? 

Each Object Storage account requires the API Key for the master user account. These are available under View Credentials upon accessing the Object Storage section your {{site.data.keyword.slportal}}.

## What Are the Object Storage Authentication Endpoints on the Public and Private Networks?

The authentication endpoints for Object Storage are cluster-specific. Use the public or private network endpoint that corresponds to the desired cluster. Endpoints are as follows:

<table><tbody><tr><th>Data Center</th><th>Network Endpoints</th></tr>
<tr><td>Amsterdam, Netherlands</td><td><li>Public Network: https://ams01.objectstorage.softlayer.net/auth/v1.0 </li><li>Private Network: https://ams01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Frankfurt, Germany</td><td><li>Public Network: https://fra02.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://fra02.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>London, United Kingdom</td><td><li>Public Network: https://lon02.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://lon02.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Milan, Italy</td><td><li>Public Network: https://mil01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://mil01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Paris, France</td><td><li>Public Network: https://par01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://par01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Montreal, Canada</td><td><li>Public Network: https://mon01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://mon01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Toronto, Canada</td><td><li>Public Network: https://tor01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://tor01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Dallas, TX, United States</td><td><li>Public Network: https://dal05.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://dal05.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>San Jose, CA, United States</td><td><li>Public Network: https://sjc01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://sjc01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Washington DC, United States</td><td><li>Public Network: https://wdc.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://wdc.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Mexico City, Mexico</td><td><li>Public Network: https://mex01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://mex01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Sao Paolo, Brazil</td><td><li>Public Network: https://sao01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://sao01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Chennai, India</td><td><li>Public Network: https://che01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://che01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Hong Kong, China</td><td><li>Public Network: https://hkg02.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://hkg02.objectstorage.service.networklayer.com/auth/v1.0 </li></td></tr>
<tr><td>Melbourne, Australia</td><td><li>Public Network: https://mel01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://mel01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Sydney, Australia</td><td><li>Public Network: https://syd01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://syd01.objectstorage.service.networklayer.com/auth/v1.0  </li></td></tr>
<tr><td>Seoul, S. Korea</td><td><li>Public Network: https://seo01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://seo01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Singapore</td><td><li>Public Network: https://sng01.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://sng01.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
<tr><td>Tokyo, Japan</td><td><li>Public Network: https://tok02.objectstorage.softlayer.net/auth/v1.0</li><li>Private Network: https://tok02.objectstorage.service.networklayer.com/auth/v1.0</li></td></tr>
</tbody></table>


## How Do I Connect Object Storage to My Server for Backups?

Although Object Storage is a solution for archiving, it isn't the ideal solution for targeting your active backups. {{site.data.keyword.BluSoftlayer_full}} recommends utilizing our EVault services to ensure the best results when backing up your server. To use Object Storage as a mount point for archiving data, connect the server to the desired storage container and set up your archive process.  For example, run a database dump and then schedule a job to move the file to the object storage mount point.


## Do I Still Have to Adhere to the 5 GB per Object Limit When Using SFTP?

The 5 GB limitation for objects uploaded to Object Storage is still in place using SFTP. If an object greater than 5 GB should be uploaded, we recommend referring to the following articles provided by OpenStack to ensure the object is uploaded successfully and efficiently:

- [Create Large Objects](http://docs.openstack.org/user-guide/cli_swift_large_object_creation.html)
- [Chunked Transfer Encoding](http://docs.openstack.org/developer/python-swiftclient/swiftclient.html)

## How Long Does It Take for My Files to Replicate across the Clusters?

Replication time across clusters varies.  During the replication process, a single directory is compared to all other directories at each replication point.  When this process is complete, all missing (or superfluous) data is updated through a sync, which refreshes the data (both addition and removal) across all replication points.  Because data levels and clusters vary between accounts, we are unable to estimate the time it takes for replication to happen.

## What Are Some of the More Commonly Used SFTP Clients?

The use of SFTP clients is primarily based on the device's OS and user preference. The following SFTP clients are popular with a wide range of users:

 - [Sftp](https://www.linux.com/learn/tutorials/442424-transfer-files-securely-with-sftp) for Linux
 - [WinSCP](http://winscp.net/eng/index.php) for Windows
 - [Cyberduck](http://cyberduck.io/) for Mac and Windows
 - [FileZilla](https://filezilla-project.org/) for all platforms

## Which Third Party Software Can I Use with Object Storage? 

There are currently two programs that {{site.data.keyword.BluSoftlayer_full}}  recognizes as a third party solution for Object Storage: [Gladinet Cloud](http://www.gladinet.com/){:new_window} and [Cyberduck](https://trac.cyberduck.io/wiki/help/en/howto/softlayer/){:new_window}.  Gladinet Cloud can be downloaded from the Gladinet website and setup instructions can be found on Gladinet’s [blog](http://gladinet.blogspot.com/2012/06/access-softlayer-object-storage-from.html){:new_window}.  Cyberduck is available on the Cyberduck website but must be configured to work properly with Object Storage.  Configuration instruction can be found on Cyberduck’s [wiki](http://trac.cyberduck.ch/wiki/help/en/howto/preferences#Hiddenconfigurationoptions) and in Bluemix Docs' [Connect to Object Storage with Cyberduck](connect-object-storage-using-cyberduck.html).   

## Will I Be Able to Expand Archives without Downloading Them within Object Storage? 

No. This feature is not supported by OpenStack’s Swift, the platform on which Object Storage is built. Currently, {{site.data.keyword.BluSoftlayer_full}}  has no plans to implement this feature. 

## Is CDN integration Available on my Object Storage Account?

Yes, Edgecast CDN integration is a standard feature on all Swift Object Storage accounts.  All interactions with the CDN portion of your account must be managed through SoftLayer’s API and CDN integration must be activated on your account prior to its use.  For more information on interactions with the Edgecast CDN portion of your Object Storage account, refer to the article [Attaching EdgeCast CDN account to SL Object Storage](/docs/infrastructure/content-deliver-network/attach-edgecast-cdn-account-sl-object-storage.html) or the [Object Storage CDN](http://sldn.softlayer.com/reference/Object-Storage-CDN){new_window} reference page of the SLDN.
