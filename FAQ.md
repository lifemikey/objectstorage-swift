---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-08"

---
{:new_window: target="_blank"}
{:note: .deprecated}


# FAQs

## What Are the {{site.data.keyword.objectstorageshort}} Authentication Endpoints on the Public and Private Networks?

The authentication endpoints for {{site.data.keyword.objectstorageshort}} are cluster-specific. Use the public or private network endpoint that corresponds to the desired cluster. Endpoints are as follows.

<table>
<caption style="caption-side:bottom;">Table 1. shows the available endpoints for the {{site.data.keyword.objectstorageshort}} Swift API</caption>
<tr><th>Data Center</th><th>Network Endpoints</th></tr>
<tr><td>Amsterdam, Netherlands</td><td><li>Public Network: <code>`https://ams01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://ams01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Frankfurt, Germany</td><td><li>Public Network: <code>`https://fra02.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://fra02.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>London, United Kingdom</td><td><li>Public Network: <code>`https://lon02.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://lon02.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Milan, Italy</td><td><li>Public Network: <code>`https://mil01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://mil01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Paris, France</td><td><li>Public Network: <code>`https://par01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://par01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Montreal, Canada</td><td><li>Public Network: <code>`https://mon01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://mon01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Toronto, Canada</td><td><li>Public Network: <code>`https://tor01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://tor01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Dallas, TX, United States</td><td><li>Public Network: <code>`https://dal05.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://dal05.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>San Jose, CA, United States</td><td><li>Public Network: <code>`https://sjc01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://sjc01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Washington DC, United States</td><td><li>Public Network: <code>`https://wdc.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://wdc.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Mexico City, Mexico</td><td><li>Public Network: <code>`https://mex01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://mex01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Sao Paolo, Brazil</td><td><li>Public Network: <code>`https://sao01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://sao01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Chennai, India</td><td><li>Public Network: <code>`https://che01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://che01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Hong Kong, China</td><td><li>Public Network: <code>`https://hkg02.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://hkg02.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Melbourne, Australia</td><td><li>Public Network: <code>`https://mel01.objectstorage.softlayer.net/auth/v1.0`</li><li>Private Network: <code>`https://mel01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Sydney, Australia</td><td><li>Public Network: <code>`https://syd01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://syd01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Seoul, S. Korea</td><td><li>Public Network: <code>`https://seo01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://seo01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Singapore, Singapore</td><td><li>Public Network: <code>`https://sng01.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://sng01.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
<tr><td>Tokyo, Japan</td><td><li>Public Network: <code>`https://tok02.objectstorage.softlayer.net/auth/v1.0`</code></li><li>Private Network: <code>`https://tok02.objectstorage.service.networklayer.com/auth/v1.0`</code></li></td></tr>
</table>


## Can a Sub-User Access {{site.data.keyword.objectstorageshort}}?

Any [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} user with appropriate permissions may access and interact with {{site.data.keyword.objectstorageshort}}. If permissions have not been granted, the {{site.data.keyword.objectstorageshort}} menu option will not appear within the {{site.data.keyword.slportal}}. To grant or remove permissions for {{site.data.keyword.objectstorageshort}}, refer to [Managing an {{site.data.keyword.objectstorageshort}} User](interacting-in-portal.html).

## Can a User Have Edgecast CDN and StorageLayer Permissions Granted but be Prohibited from Accessing {{site.data.keyword.objectstorageshort}}?

If a user has the Manage CDN Account, Manage CDN File Transfers and Manage StorageLayer permissions, the user automatically has access to {{site.data.keyword.objectstorageshort}}, as well. At the current time, you can't grant access to CDN and StorageLayer while prohibiting access to {{site.data.keyword.objectstorageshort}}, or vice versa.

## What Is the File Upload Limit for {{site.data.keyword.objectstorageshort}}?

The upload limit is approximately 5 GB for a single file. You have to consider any device limitation - iOS (iPhone, iPod Touch, iPad) Android and Windows Phone are currently supported. If you require a file size larger than 5 GB, use segmentation. For more information regarding segmentation, see OpenStack’s [segmentation overview](http://docs.openstack.org/developer/swift/overview_large_objects.html) for swift.

## How Do I Interact with {{site.data.keyword.objectstorageshort}}?

Users access {{site.data.keyword.objectstorageshort}} through the {{site.data.keyword.slportal}}, {{site.data.keyword.BluSoftlayer_full}}’s API or a third party client. For best results, use the {{site.data.keyword.objectstorageshort}} through the API. Interacting with {{site.data.keyword.objectstorageshort}} through the API provides the most control over your files and greater flexibility when you use your {{site.data.keyword.objectstorageshort}} account.

## What Are the Best Uses for {{site.data.keyword.objectstorageshort}}?

The best uses are for long term static data that do not require frequent manipulation.  Examples include photographs, videos, backups, virtual machine images. {{site.data.keyword.objectstorageshort}} is not recommended for data sets that need to be manipulated often.

## Which Devices Can Connect and Upload to an {{site.data.keyword.objectstorageshort}} Account via the {{site.data.keyword.slportal}}?

Any mobile device currently supported by {{site.data.keyword.BluSoftlayer}} has the ability to connect and upload items to the user’s {{site.data.keyword.objectstorageshort}} account via the {{site.data.keyword.slportal}}. {{site.data.keyword.BluSoftlayer}} currently supports iOS (iPhone, iPod Touch, iPad) Android and Windows Phone through our mobile apps designed with each device in mind. To download the {{site.data.keyword.BluSoftlayer}} Mobile app for your device, go to the Mobile Apps page on {{site.data.keyword.BluSoftlayer}}’s website.

## What Type of Authentication Do I Need for {{site.data.keyword.objectstorageshort}}? 

Each {{site.data.keyword.objectstorageshort}} account requires the API Key for the master user account. These are available under View Credentials upon accessing the {{site.data.keyword.objectstorageshort}} section your {{site.data.keyword.slportal}}.


## How Do I Connect {{site.data.keyword.objectstorageshort}} to My Server for Backups?

Although {{site.data.keyword.objectstorageshort}} is a solution for archiving, it isn't the ideal solution for targeting your active backups. {{site.data.keyword.BluSoftlayer}} recommends utilizing [our EVault services](/docs/infrastructure/Backup/index.html#evault-backup) to ensure the best results when backing up your server. To use {{site.data.keyword.objectstorageshort}} as a mount point for archiving data, connect the server to the desired storage container and set up your archive process.  For example, run a database dump and then schedule a job to move the file to the object storage mount point.


## Do I Still Have to Adhere to the 5 GB per Object Limit When Using SFTP?

The 5 GB limitation for objects uploaded to {{site.data.keyword.objectstorageshort}} is still in place using SFTP. If an object greater than 5 GB should be uploaded, we recommend referring to the following articles provided by OpenStack to ensure the object is uploaded successfully and efficiently:

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

## Which Third Party Software Can I Use with {{site.data.keyword.objectstorageshort}}? 

There are currently two programs that {{site.data.keyword.BluSoftlayer}}  recognizes as a third party solution for {{site.data.keyword.objectstorageshort}}: [Gladinet Cloud](http://www.gladinet.com/){:new_window} and [Cyberduck](https://trac.cyberduck.io/wiki/help/en/howto/softlayer/){:new_window}.  Gladinet Cloud can be downloaded from the Gladinet website and setup instructions can be found on Gladinet’s [blog](http://gladinet.blogspot.com/2012/06/access-softlayer-object-storage-from.html){:new_window}.  Cyberduck is available on the Cyberduck website but must be configured to work properly with {{site.data.keyword.objectstorageshort}}.  Configuration instruction can be found on Cyberduck’s [wiki](http://trac.cyberduck.ch/wiki/help/en/howto/preferences#Hiddenconfigurationoptions) and in our [Connect to {{site.data.keyword.objectstorageshort}} with Cyberduck](connect-object-storage-using-cyberduck.html) article.   

## Will I Be Able to Expand Archives without Downloading Them within {{site.data.keyword.objectstorageshort}}? 

No. This feature is not supported by OpenStack’s Swift, the platform on which {{site.data.keyword.objectstorageshort}} is built. Currently, {{site.data.keyword.BluSoftlayer}} has no plans to implement this feature. 

## Is CDN integration Available on my {{site.data.keyword.objectstorageshort}} Account?

Yes, Edgecast CDN integration is a standard feature on all {{site.data.keyword.objectstorageshort}} OpenStack Swift accounts.  All interactions with the Storage CDN portion of your account must be managed through {{site.data.keyword.BluSoftlayer}}’s API and CDN integration must be activated on your account prior to its use.  For more information on interactions with the Edgecast CDN portion of your {{site.data.keyword.objectstorageshort}} account, refer to the article: [Attaching EdgeCast CDN account to {{site.data.keyword.objectstorageshort}} OpenStack Swift](/docs/infrastructure/content-deliver-network/attach-edgecast-cdn-account-sl-object-storage.html).
