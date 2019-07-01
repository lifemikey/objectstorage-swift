---

copyright:
  years: 2017, 2019
lastupdated: "2019-07-01"

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


# End of Support phases
{: #GettingStarted}

**Action Required: Object Storage OpenStack Swift is nearing the End of Support.**
{:important}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be purchased and provisioned after **10 December 2018**.
{:deprecated}

Effective of **31 March 2019**, IBM Cloud no longer supports the following Object Storage OpenStack Swift (infrastructure) features:
- Static Site Access
- Content Delivery Network (CDN)
- Search
- Image Templates import/export  


The following Object Storage OpenStack Swift (infrastructure) data center locations are being phased out of support.

Phase 1 - End of support completed on 31 March 2019.
- CHE01(Chennai)
- MEX01 (Mexico City)
- MON01 (Montreal)
- SEO01 (Seoul)
- OSL0 (Oslo)

Phase 2 - End of support completed on 30 June 2019.
- MEL01 (Melbourne)
- MIL01 (Milan)
- SAO01 (Sao Paulo)
- TOK02 (Tokyo)
- TOR01 (Toronto)
- WDC (Washington DC)

Phase 3 - End of support commences on 30 September 2019.
- AMS01 (Amsterdam)
- FRA02 (Frankfurt)
- LON02 (London)
- SNG01 (Singapore)
- SYD01 (Sydney)

Phase 4 - End of support commences on 1 December 2019.
- DAL05 (Dallas)
- HKG01 (Hong Kong)
- PAR01 (Paris)
- SJC01 (San Jose)

##  Action Required

Clients who have applications that use these features or data that is stored in those data center locations need to migrate to {{site.data.keyword.cos_full_notm}} service by the End of support date.
{:important}

  The following features are available on the {{site.data.keyword.cos_full_notm}} service.
  - CDN capability that is be provided through the {{site.data.keyword.cos_full_notm}} integration with Akamai. For more information, see [Solution Tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/tutorials/static-files-cdn.html#accelerate-delivery-of-static-files-using-a-cdn){:new_window}.
  - Image Templates import/export is also provided by using {{site.data.keyword.cos_full_notm}}. For more information, see [IBM Cloud Blogs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2018/11/speed-up-image-imports-to-ibm-cloud-infrastructure/){:new_window}.
  -Bucket name and object name search is provided through the {{site.data.keyword.cos_full_notm}} UI. Bucket and object metadata search is no longer available.

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
