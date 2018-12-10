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


# Getting Started with {{site.data.keyword.objectstorageshort}} OpenStack Swift

{{site.data.keyword.objectstorageshort}} OpenStack Swift is a redundant and expandable cloud storage service. With {{site.data.keyword.objectstorageshort}} users can easily store, search, and retrieve data across the internet, with optional CDN connectivity, or across {{site.data.keyword.BluSoftlayer}}’s global private network. This offering was formerly known as SoftLayer {{site.data.keyword.objectstorageshort}}. {{site.data.keyword.objectstorageshort}} can be accessed through a RESTful API and through [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}. By using the {{site.data.keyword.slportal}} you can complete easy, point-and-click interactions with your account without making direct calls to the API.
{:shortdesc}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}

The Swift Object Storage service that is provisioned from and managed in the [{{site.data.keyword.BluSoftlayer_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/infrastructure){:new_window} is no longer available for purchase after **10 December 2018**.

Existing Swift accounts continue to be supported, but no new Swift accounts are created. The service is replaced by the [{{site.data.keyword.cos_full}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/object-storage){:new_window}, which is provisioned from and managed in the unified console alongside our PaaS offerings such as Containers and Watson services.

{{site.data.keyword.cos_full_notm}} is available at a lower cost per GB than OpenStack Swift. {{site.data.keyword.cos_full_notm}} is designed to provide the performance, flexibility, and pricing that fits your workload demands and data access patterns.

## {{site.data.keyword.cos_full_notm}} benefits
* Secure to the core
   - Integration with {{site.data.keyword.iamlong}} allows for granular access control at the bucket-level by using role-based policies.
   - All data is encrypted at-rest and in-flight by default.
   - Encryption keys are automatically managed by default but can optionally be self-managed or managed by using {{site.data.keyword.keymanagementservicelong}}.
* Built for all your applications
  - Select the best resiliency to store your data – “Cross Region”, “Regional”, and “Single Location” storage options are available.
  - Flexible data storage classes for Active, Less Active, Cold, and Dynamic workloads.
  - No charge for data ingress.
  - Lowest cost archive with lifecycle policies for long-term data retention.
  - Analyze data directly in {{site.data.keyword.cos_full_notm}} with {{site.data.keyword.sqlquery_full}}.

## Recommended Action

Migrate to {{site.data.keyword.cos_full_notm}} to take advantage of the superior cost-performance profile. Please, migrate your workloads to the [{{site.data.keyword.cos_full_notm}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/cloud-object-storage) at your earliest convenience.

For more information about how to perform the migration, see [Migrating data from OpenStack Swift](https://{DomainName}/docs/services/cloud-object-storage/tutorials/migrate.html#migrating-data-from-openstack-swift).
{:tip}

If you no longer use {{site.data.keyword.objectstorageshort}} OpenStack Swift and no longer need your data to be stored, please delete your Swift account from the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.

If you have questions, reach out to swift-cos-migration@wwpdl.vnet.ibm.com or raise a support case.
