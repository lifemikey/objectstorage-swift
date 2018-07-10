---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-10"

---
{:new_window: target="_blank"}

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using WinSCP

{{site.data.keyword.objectstorageshort}} is a useful utility for backing up data and using your own images (See: [Import an image](https://console.bluemix.net/docs/infrastructure/image-templates/import-image.html)). While most commonly, people access Object Storage by using its REST API, you can also use WinSCP to upload files to your {{site.data.keyword.objectstorageshort}} account. Use this information to establish connection.

 - Protocol - SFTP
 - Port - 22
 - Host name - `(dc endpoint).objectstorage.softlayer.net`
 - User name - `SLOS(accountID)-2:(portal username)`
 - Password - (API Key)

 ![User Credentials](/images/Object_storage_credentials.png)
 ![OS WinSCP](/images/OS_WINSCP.png)
