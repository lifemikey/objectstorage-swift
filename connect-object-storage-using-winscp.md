---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-10"

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

# Connecting to {{site.data.keyword.objectstorageshort}} with WinSCP

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}

{{site.data.keyword.objectstorageshort}} is a useful utility for backing up data and storing OS images. (For more information, see [Import an image](https://{DomainName}/docs/infrastructure/image-templates/import-image.html)). While most commonly, people access Object Storage by using its REST API, you can also use WinSCP to upload files to your {{site.data.keyword.objectstorageshort}} account. Use this information to establish connection.

 - Protocol - SFTP
 - Port - 22
 - Host name - `(dc endpoint).objectstorage.softlayer.net`
 - User name - `SLOS(accountID)-2:(portal username)`
 - Password - (API Key)

 ![User Credentials](/images/Object_storage_credentials.png)
 ![OS WinSCP](/images/OS_WINSCP.png)
