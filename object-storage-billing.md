---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-18"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# How Billing for {{site.data.keyword.objectstorageshort}} OpenStack Swift Works

{{site.data.keyword.Bluemix}} {{site.data.keyword.objectstorageshort}} is a pay-as-you-go service – you only pay for what you use. There is no minimum fee nor are there any set up fees or commitments to begin using the service. {{site.data.keyword.objectstorageshort}} is charged in one of two ways – {{site.data.keyword.objectstorageshort}} usage per GB per month and public outbound bandwidth per GB per month.

{{site.data.keyword.objectstorageshort}} usage is billed based on storage usage throughout the billing cycle. For example, you use 1,000 GB of {{site.data.keyword.objectstorageshort}} for one day. For the remainder of the month, you used 2,000 GB per day; your usage is averaged on a daily basis and then reported in the billing cycle.

Public outbound bandwidth charges apply when data is read from any of your object containers over the public network and is billed for all bandwidth consumed in a billing cycle.

Your cost per month may vary because your {{site.data.keyword.objectstorageshort}} usage for month may vary. {{site.data.keyword.Bluemix}} charges per GB used and prices do vary per data center. Please be sure to visit the [Order {{site.data.keyword.objectstorageshort}} page](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window} for up-to-date pricing information.

## {{site.data.keyword.objectstorageshort}}

Current pricing is available on the [Order {{site.data.keyword.objectstorageshort}} page](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window}.

For Capacity Usage per billing cycle, we get the usage every hour. In an example billing cycle we have 720(24x30) data points. We sum the capacity for all of those data points, then divide by 720; this gives the average use.

Another example is your workload is split across two or more data centers – 5,000 GB is based in Dallas and 1,000 GB is in Sao Paolo. Your monthly cost is determined through location-based pricing 

<table><caption>Table 1. shows an example of how the cost is calculated when data is split between different locations</caption>
<tr><td>Monthly cost for Dallas-based {{site.data.keyword.objectstorageshort}}:</td><td>$0.04 per GB x 5,000 GB 	= 	$200.00</td></tr>
<tr><td>Montly cost for Sao Paolo-based {{site.data.keyword.objectstorageshort}}:</td><td>$0.06 per GB x 1,000 GB 	= 	$60.00</td></tr>
<tr><td>Total {{site.data.keyword.objectstorageshort}} cost for the month:</td><td>  	= 	$260.00</td></tr>
</table>

*Not official pricing and prices subject to change

## Public Inbound Bandwidth

There is no additional charge for public inbound bandwidth. We also don’t charge for bandwidth on the private network nor between {{site.data.keyword.BluSoftlayer}} data centers. If you were to back up your data to another data center, you’d only pay for the storage at your backup site; not for the data transfer between the two data centers.

## Public Outbound Bandwidth

Current pricing is available on the [Order {{site.data.keyword.objectstorageshort}} page](https://www.ibm.com/cloud-computing/bluemix/pricing-object-storage#swift){:new_window}.

This charge applies whenever data is read from any of your object containers over the public network. Again, the pay-as-you-go cost is per GB with bandwidth usage metered and totaled monthly. For example, you have 250 GB outbound daily for the first 15 days of the month and 500 GB outbound daily for the 15 days of the same month. Assuming a 30-day month, your usage is calculated as follows:

    (250 GB x 15 days) + (500 GB x 15 days) = 11,250 GB monthly total
    11,250 GB x $0.09 per GB = $1,012.50 for outbound bandwidth for the month

Another example is you have data in the Dallas and Sao Paolo data centers and 10,000 GB and 7,500 GB respectively is downloaded monthly over the public network. Your billing cycle cost is determined through location-based pricing:

<table><caption>Table 2. shows an example of how the cost is calculated when data is split between different locations</caption>
<tr><td>Monthly cost for Dallas-based bandwith:</td><td>$0.09 per GB x 10,000 GB 	= 	$900.00</td></tr>
<tr><td>Montly cost for Sao Paolo-based bandwith:</td><td>$0.25 per GB x 7,500 GB 	= 	$1,875.00</td></tr>
<tr><td>Total {{site.data.keyword.objectstorageshort}} cost for the month:</td><td>  	= 	$2,775.00</td></tr>
</table>

*Not official pricing and prices subject to change

## Data Requests

There is no additional charge for the following data requests:

 - PUT
 - COPY
 - POST
 - LIST
 - Get
 - All other requests
