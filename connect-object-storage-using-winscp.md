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

# Connecting to {{site.data.keyword.objectstorageshort}} with WinSCP
{: #OSSWinSCP}

**Action Required: Object Storage OpenStack Swift is nearing the End of Support.**
{:important}

While most commonly, people access Object Storage by using its REST API, you can also use WinSCP to upload files to your {{site.data.keyword.objectstorageshort}} account. Use this information to establish connection.

 - Protocol - SFTP
 - Port - 22
 - Host name - `(dc endpoint).objectstorage.softlayer.net`
 - User name - `SLOS(accountID)-2:(portal username)`
 - Password - (API Key)

 ![User Credentials](/images/Object_storage_credentials.png)
 ![OS WinSCP](/images/OS_WINSCP.png)
