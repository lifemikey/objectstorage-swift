---

ccopyright:
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

# Connecting to {{site.data.keyword.objectstorageshort}} with SFTP
{: #OSSSFTP}

**Action Required: Object Storage OpenStack Swift is nearing the End of Support.**
{:important}

To connect to {{site.data.keyword.objectstorageshort}} by using SFTP, you need the following login information.

- Protocol - SFTP
- Port - 22
- Host name - `(dc endpoint).objectstorage.softlayer.net`
- User name - `SLOS(account ID)-2:(portal user name)``

  The user name can also start with IBMOS in some cases. Check the Object Storage page in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} to confirm.
  {:tip}
- Password - `(API Key)`

For more information about available endpoints, see the [{{site.data.keyword.objectstorageshort}} authentication endpoints](FAQ.html).
