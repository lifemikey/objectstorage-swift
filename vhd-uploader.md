---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# VHD Uploader Instructions

{{site.data.keyword.BluSoftlayer_full}} has option to import customer-supplied Virtual Hard Disks (VHDs) to our {{site.data.keyword.objectstorageshort}} offering. This is a great option for our customers who may have special virtual machines that they have spent hours perfecting.

{{site.data.keyword.BluSoftlayer_full}}'s {{site.data.keyword.objectstorageshort}} is an enhanced version of OpenStack Swift. Although we’ve added features to it, the API (on the whole) is still the same. Two requirements of particular importance to storing disk images are limitations and requirements on large files. Swift limits all files to be 5 GB or less. To support larger files users need to create a manifest file that combines smaller files into one large file.

For example, to upload a 12 GB VHD, the user is expected to segment the file into at least three files and then create a manifest that brings them back together.

## Easier Importing

Since many people don’t have the time to learn the inner workings of Swift and would just like to get VHDs running on their servers, we created a set of scripts to simplify the process. They handle the authentication, file segmentation, and dynamic manifest creation for you, so you can get up and running quickly. You can easily access them [here](https://gist.github.com/follower46/526a7fbc81880e6f2b7e){:new_window}.

You can use a Bash script or a Python 3 script. Both do the same thing, but depending on your environment you may prefer one over the other.

But before we jump into the scripts, you’ll need to find your {{site.data.keyword.objectstorageshort}} username and password.

To get those, log in to http://control.softlayer.com, go to **Storage** > **{{site.data.keyword.objectstorageshort}}**, select your cluster , and then click **View Credentials** in the top left of the page. You will be presented with a modal window containing your username and API Key (or password) for {{site.data.keyword.objectstorageshort}}.

## ObjectStorageUploader.sh - Bash Edition

The idea behind this script is to have as little user interaction as possible. By calling the script with the proper parameters, you are able to walk away and let it do its thing. Simply place the bash script in your directory of VHDs. Call the script by passing in the image you want to upload, the location to upload it (container/filename), and your Swift username and password.

`$ ./ObjectStorageUpload.sh myOS.vhd 'myContainer/myOS.vhd' 'SLOS1234-1:SL1234' 'apikey'`

It will begin the process of walking through the segments of the file and building up your object in {{site.data.keyword.objectstorageshort}}.

## ObjectStorageUploader.py - Python 3 Edition

Before we begin, make sure you have installed the latest version of Python 3 located here: https://www.python.org/downloads/
Any Python 3 release will work, but we used Python 3.4.0 for testing.

The idea behind this script is to actually walk you through the process of uploading a file to Swift. Use this script with supplied parameters, in interactive mode, or a combination of the two. This is particularly handy for Windows users who are newer to scripting. Simply drop the script in the folder containing your VHDs, run it, and let it guide you through uploading the image to {{site.data.keyword.objectstorageshort}}.

1. To execute the script, place it in the directory where you store your VHDs and double click it. It will then prompt you to select the file you want to upload.

2. Enter your Swift username and password when prompted. Authentication will be attempted and, if successful, the list of containers in your cluster will be presented.

3. Select the container you want to upload to and the script will begin uploading the VHD to {{site.data.keyword.objectstorageshort}}.

If you prefer the command line arguments approach, you can pass in arguments to this script too. The signature is slightly different since all the opinions are optional.

`$ python ObjectStorageUpload.py -f myOS.vhd -t 'myContainer/myOS.vhd' -u 'SLOS1234-1:SL1234'`

## Importing Uploaded VHD as Image Templates

Now that your image is in {{site.data.keyword.objectstorageshort}} you can import your VHD into the {{site.data.keyword.BluSoftlayer}} template, so you can use it to provision a new virtual server!

1. Go to your image templates page in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} and click the  **Import Image** tab. 
2. Select the **Swift account**, **cluster**, **container**, and **file** that you uploaded. 
3. Give your new template a name and some notes. Make sure to fill out the Operating System information properly as this is used when setting up your new server,.
4. Click **Import.**
5. Lastly, you will be emailed after the VHD has been processed by our system.
