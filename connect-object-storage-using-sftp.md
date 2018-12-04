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

# Connecting to {{site.data.keyword.objectstorageshort}} with SFTP

To connect to {{site.data.keyword.objectstorageshort}} by using SFTP, you need the following login information.

- Protocol - SFTP
- Port - 22
- Host name - `(dc endpoint).objectstorage.softlayer.net`
- User name - `SLOS(account ID)-2:(portal user name)``

  The user name can also start with IBMOS in some cases. Check the Object Storage page in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} to confirm.
  {:tip}
- Password - `(API Key)`

For more information about available endpoints, see the [{{site.data.keyword.objectstorageshort}} authentication endpoints](FAQ.html).
