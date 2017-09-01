---

copyright:
  years: 2017
lastupdated: "2017-07-05"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Connect to Object Storage using WinSCP

Object Storage is a useful utility for backing data up as well as using the ability to use your own images (See: [Import an image](import-image.html)). While most commonly, you'll access Object Storage using it's REST API, you are also able to use WinSCP to upload files to your Object Storage account. You'll simply need a couple of pieces of information to perform this.

 - Protocol - SFTP
 - Port - 22
 - Host name - (dc endpoint).objectstorage.softlayer.net
 - Username - SLOS(accountID)-2:(portal username)
 - Password - (API Key)
 
 ![User Credentials](/images/Object_storage_credentials.png)
 ![OS WinSCP](/images/OS_WINSCP.png)
 
