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

# Working with the VHD Uploader Scripts

{{site.data.keyword.BluSoftlayer_full}} allows customers to import customer-supplied virtual hard disks (VHDs) to the {{site.data.keyword.objectstorageshort}} offering. This option is a great for customers who might have special virtual machines that they spent hours perfecting.

{{site.data.keyword.BluSoftlayer}}'s {{site.data.keyword.objectstorageshort}} is an enhanced version of OpenStack Swift. Although {{site.data.keyword.BluSoftlayer}} added features to it, the API (on the whole) is still the same. Two requirements of particular importance to storing disk images are limitations and requirements on large files. Swift limits all files to be 5 GB or less. To support larger files, users need to create a manifest file that combines smaller files into one large file.

For example, to upload a 12 GB VHD, the user is expected to segment the file into at least three files and then create a manifest that brings them back together.

Since many people don’t have the time to learn the inner workings of Swift and would like to get VHDs running on their servers, {{site.data.keyword.BluSoftlayer}} created a set of scripts to simplify the process. The scripts handle the authentication, file segmentation, and dynamic manifest creation for you, so you can get up and running quickly. You can access them [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://gist.github.com/follower46/526a7fbc81880e6f2b7e){:new_window}.

You can use a Bash script or a Python 3 script. Both do the same thing, but depending on your environment you might prefer one over the other.

First, find your {{site.data.keyword.objectstorageshort}} user name and password.

1. Log in to [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}
2. Go to **Storage** > **{{site.data.keyword.objectstorageshort}}**, and select your cluster.
3. Click **View Credentials** in the upper left. A modal window appears that contains your user name and API Key (or password) for {{site.data.keyword.objectstorageshort}}.

## Running `ObjectStorageUploader.sh` - Bash Edition

The idea behind this script is to have as little user interaction as possible. By calling the script with the proper parameters, you are able to walk away and leave it to do its thing. Place the bash script in your directory of VHDs. Call the script by passing in the image you want to upload, the location to upload it (container/filename), and your Swift user name and password.

`$ ./ObjectStorageUpload.sh myOS.vhd 'myContainer/myOS.vhd' 'SLOS1234-1:SL1234' 'apikey'`

It begins the process of walking through the segments of the file and building up your object in {{site.data.keyword.objectstorageshort}}.

## Running `ObjectStorageUploader.py` - Python 3 Edition

Before you begin, make sure that you installed the most recent version of Python 3 that is located here: https://www.python.org/downloads/ ![External link icon](../../icons/launch-glyph.svg "External link icon")
Any Python 3 release works, but Python 3.4.0 was used for testing.

The idea behind this script is to walk you through the process of uploading a file to Swift. Use this script with supplied parameters, in interactive mode, or a combination of the two. This script is handy for users who are newer to scripting. Drop the script in the folder that contains your VHDs, run it, and let it guide you through uploading the image to {{site.data.keyword.objectstorageshort}}.

1. To run the script, place it in the directory where you store your VHDs and double-click it. Then, it prompts you to select the file that you want to upload.

2. Enter your Swift user name and password. After successful authentication, the list of containers in your cluster is presented.

3. Select the container that you want to upload to and the script begins uploading the VHD to {{site.data.keyword.objectstorageshort}}.

If you prefer the command-line arguments approach, you can pass in arguments to this script too. The signature is slightly different since all the opinions are optional.

`$ python ObjectStorageUpload.py -f myOS.vhd -t 'myContainer/myOS.vhd' -u 'SLOS1234-1:SL1234'`

## Importing Uploaded VHD as Image Templates

Now that your image is in {{site.data.keyword.objectstorageshort}} you can import your VHD into the {{site.data.keyword.BluSoftlayer}} template, so you can use it to provision a new virtual server!

1. Go to your image templates page in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} and click the **Import Image** tab.
2. Select the **Swift account**, **cluster**, **container**, and **file** that you uploaded.
3. Give your new template a name and some notes. Make sure to complete the Operating System information properly as this information is used when setting up your new server.
4. Click **Import.**
5. Lastly, after the VHD is processed by the system, you receive an email confirmation.
