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


# Billing for {{site.data.keyword.objectstorageshort}} OpenStack Swift
{: #OSSBilling}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}

{{site.data.keyword.Bluemix}} {{site.data.keyword.objectstorageshort}} is a pay-as-you-go service – you pay only for what you use. There's no minimum fee, nor are there any setup-fees or commitments to start the service. {{site.data.keyword.objectstorageshort}} is charged in 1 of 2 ways – {{site.data.keyword.objectstorageshort}} usage per GB per month and public outbound bandwidth per GB per month.

{{site.data.keyword.objectstorageshort}} usage is billed based on storage usage throughout the billing cycle. For example, you use 1000 GB of {{site.data.keyword.objectstorageshort}} for one day. For the remainder of the month, you use 2000 GB per day. Your usage is averaged daily, and then reported in the billing cycle.

Public outbound bandwidth charges apply when data is read from any of your object containers over the public network and is billed for all bandwidth that is used in a billing cycle.

Your cost per month might vary because your {{site.data.keyword.objectstorageshort}} usage for month can vary. {{site.data.keyword.Bluemix}} charges per GB used and prices also vary per data center. For up-to-date pricing information, see the [Order {{site.data.keyword.objectstorageshort}} page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window}.

The prices that are shown here are not official pricing, and prices can be subject to change.
{important}

## {{site.data.keyword.objectstorageshort}}

For Capacity Usage per billing cycle, {{site.data.keyword.Bluemix}} gets the usage for every hour. An example billing cycle has 720(24x30) data points. The capacity for all of those data points is summed up, then divided by 720; this calculation gives the average use.

Another example is your workload that is split across two or more data centers – 5,000 GB is based in Dallas and 1,000 GB is in São Paulo. Your monthly cost is determined through location-based pricing.

<table role="presentation">
<tr><td>Monthly cost for {{site.data.keyword.objectstorageshort}} in Dallas</td><td>$0.04 per GB x 5,000 GB 	= 	$200.00</td></tr>
<tr><td>Monthly cost for {{site.data.keyword.objectstorageshort}} in São Paulo</td><td>$0.06 per GB x 1,000 GB 	= 	$60.00</td></tr>
<tr><td>Total {{site.data.keyword.objectstorageshort}} cost for the month</td><td>  	= 	$260.00</td></tr>
</table>

## Pricing for Public Inbound Bandwidth

There's no additional charge for public inbound bandwidth. {{site.data.keyword.Bluemix}} also doesn’t charge for bandwidth on the private network nor between {{site.data.keyword.BluSoftlayer}} data centers. If you wanted to back up your data to another data center, you’d pay only for the storage at your backup site; not for the data transfer between the two data centers.

## Pricing for Public Outbound Bandwidth

This charge applies whenever data is read from any of your object containers over the public network. Again, the pay-as-you-go cost is per GB with bandwidth usage that is metered and totaled monthly. For example, you have 250-GB outbound daily for the first 15 days of the month and 500-GB outbound daily for the 15 days of the same month. Assuming a 30-day month, your usage is calculated as follows.

    (250 GB x 15 days) + (500 GB x 15 days) = 11,250 GB monthly total
    11,250 GB x $0.09 per GB = $1,012.50 for outbound bandwidth for the month

Another example, you have data in the Dallas and São Paulo data centers, and 10,000 GB and 7,500 GB of data is downloaded monthly over the public network. Your billing cycle cost is determined through location-based pricing.

<table role="presentation">
<tr><td>Monthly cost for bandwidth that is used in Dallas</td><td>$0.09 per GB x 10,000 GB 	= 	$900.00</td></tr>
<tr><td>Monthly cost for bandwidth that is used in São Paulo</td><td>$0.25 per GB x 7,500 GB 	= 	$1,875.00</td></tr>
<tr><td>Total {{site.data.keyword.objectstorageshort}} cost for the month</td><td>  	= 	$2,775.00</td></tr>
</table>


## Pricing for Data Requests

There's no additional charge for the following data requests.

 - PUT
 - COPY
 - POST
 - LIST
 - Get
 - All other requests
