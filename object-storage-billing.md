---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-09"

---
{:new_window: target="_blank"}


# Billing for {{site.data.keyword.objectstorageshort}} OpenStack Swift

{{site.data.keyword.Bluemix}} {{site.data.keyword.objectstorageshort}} is a pay-as-you-go service – you pay only for what you use. There's no minimum fee, nor are there any setup fees or commitments to begin using the service. {{site.data.keyword.objectstorageshort}} is charged in one of two ways – {{site.data.keyword.objectstorageshort}} usage per GB per month and public outbound bandwidth per GB per month.

{{site.data.keyword.objectstorageshort}} usage is billed based on storage usage throughout the billing cycle. For example, you use 1000 GB of {{site.data.keyword.objectstorageshort}} for one day. For the remainder of the month, you use 2000 GB per day. Your usage is averaged on a daily basis and then reported in the billing cycle.

Public outbound bandwidth charges apply when data is read from any of your object containers over the public network and is billed for all bandwidth that is used in a billing cycle.

Your cost per month might vary because your {{site.data.keyword.objectstorageshort}} usage for month can vary. {{site.data.keyword.Bluemix}} charges per GB used and prices also vary per data center. For up-to-date pricing information, see the [Order {{site.data.keyword.objectstorageshort}} page](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window}.

## {{site.data.keyword.objectstorageshort}}

Current pricing is available on the [Order {{site.data.keyword.objectstorageshort}} page](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window}.

For Capacity Usage per billing cycle, {{site.data.keyword.Bluemix}} gets the usage for every hour. An example billing cycle has 720(24x30) data points. The capacity for all of those data points is summed up, then divided by 720; this calculation gives the average use.

Another example is your workload that is split across two or more data centers – 5,000 GB is based in Dallas and 1,000 GB is in São Paulo. Your monthly cost is determined through location-based pricing.

<table role="presentation">
<tr><td>Monthly cost for Dallas-based {{site.data.keyword.objectstorageshort}}</td><td>$0.04 per GB x 5,000 GB 	= 	$200.00</td></tr>
<tr><td>Monthly cost for São Paulo-based {{site.data.keyword.objectstorageshort}}</td><td>$0.06 per GB x 1,000 GB 	= 	$60.00</td></tr>
<tr><td>Total {{site.data.keyword.objectstorageshort}} cost for the month:</td><td>  	= 	$260.00</td></tr>
</table>

*Not official pricing and prices subject to change.

## Pricing for Public Inbound Bandwidth

There's no additional charge for public inbound bandwidth. {{site.data.keyword.Bluemix}} also doesn’t charge for bandwidth on the private network nor between {{site.data.keyword.BluSoftlayer}} data centers. If you wanted to back up your data to another data center, you’d pay only for the storage at your backup site; not for the data transfer between the two data centers.

## Pricing for Public Outbound Bandwidth

Current pricing is available on the [Order {{site.data.keyword.objectstorageshort}} page](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window}.

This charge applies whenever data is read from any of your object containers over the public network. Again, the pay-as-you-go cost is per GB with bandwidth usage metered and totaled monthly. For example, you have 250 GB outbound daily for the first 15 days of the month and 500 GB outbound daily for the 15 days of the same month. Assuming a 30-day month, your usage is calculated as follows.

    (250 GB x 15 days) + (500 GB x 15 days) = 11,250 GB monthly total
    11,250 GB x $0.09 per GB = $1,012.50 for outbound bandwidth for the month

Another example: you have data in the Dallas and São Paulo data centers, and 10,000 GB and 7,500 GB data is downloaded monthly over the public network. Your billing cycle cost is determined through location-based pricing.

<table role="presentation">
<tr><td>Monthly cost for Dallas-based bandwidth</td><td>$0.09 per GB x 10,000 GB 	= 	$900.00</td></tr>
<tr><td>Monthly cost for São Paulo-based bandwidth</td><td>$0.25 per GB x 7,500 GB 	= 	$1,875.00</td></tr>
<tr><td>Total {{site.data.keyword.objectstorageshort}} cost for the month</td><td>  	= 	$2,775.00</td></tr>
</table>

*Not official pricing and prices subject to change

## Pricing for Data Requests

There's no additional charge for the following data requests.

 - PUT
 - COPY
 - POST
 - LIST
 - Get
 - All other requests
