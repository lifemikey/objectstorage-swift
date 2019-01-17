---

copyright:
  years: 2017, 2019
lastupdated: "2019-01-17"

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

<div>Effective of **31 March 2019**, IBM Cloud no longer supports the following Object Storage OpenStack Swift (infrastructure) features:
 <li> Static Site Access
 <li> Content Delivery Network (CDN)
 <li> Search
 <li> Image Templates import/export  
</div>
{:important}

In addition, effective 31 March 2019, the following Object Storage OpenStack Swift (infrastructure) data center locations are no longer supported.
- CHE01(Chennai),
- MEX01 (Mexico City),
- MON01 (Montreal),
- SEO01 (Seoul)
- OSL0 (Oslo)


##  Action Required

Clients who have applications that use these features or data that is stored in those data center locations need to migrate to {{site.data.keyword.cos_full_notm}} service by 31 March 2019.
{:important}

  Starting on **1 April 2019**, the following features are available on the {{site.data.keyword.cos_full_notm}} service.
  - CDN capability that is be provided through the {{site.data.keyword.cos_full_notm}} integration with Akamai. For more information, see [Solution Tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/tutorials/static-files-cdn.html#accelerate-delivery-of-static-files-using-a-cdn){:new_window}.
  - Image Templates import/export is also provided by using {{site.data.keyword.cos_full_notm}}. For more information, see [IBM Cloud Blogs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2018/11/speed-up-image-imports-to-ibm-cloud-infrastructure/){:new_window}.
  -Bucket name and object name search is provided through the {{site.data.keyword.cos_full_notm}} UI. Bucket and object metadata search is no longer available.
  -Any data that is stored in CHE01(Chennai), MEX01 (Mexico City), MON01 (Montreal), SEO01 (Seoul) and OSL0 (Oslo) can be migrated to {{site.data.keyword.cos_full_notm}} service in these same locations, or the locations of your choosing.

  {{site.data.keyword.cos_full_notm}} is available at a lower cost per GB than OpenStack Swift. {{site.data.keyword.cos_full_notm}} is designed to provide the performance, flexibility, and pricing that fits your workload demands and data access patterns. For more information, see https://www.ibm.com/cloud/object-storage ![External link icon](../../icons/launch-glyph.svg "External link icon").

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

##  Migration Assistance

Do you need migration help? For more information about the migration process and tool, see the [{{site.data.keyword.cos_full_notm}} documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/cloud-object-storage/tutorials/migrate.html#migrating-data-from-openstack-swift).

We’re here to help! Please, email us at swift-cos-migration@wwpdl.vnet.ibm.com, if you have any questions.
{:tip}

If you are not using Swift and do not need your data stored, please delete your Swift account from the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/storage/objectstorage){:new_window}. Click the red X to cancel your Swift account in all Swift clusters and delete all data. There is no recovery from this action.
