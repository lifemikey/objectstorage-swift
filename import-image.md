---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Importing an Image from an {{site.data.keyword.objectstorageshort}} OpenStack Swift Account

The Image Templates screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} allows users to upload an existing image from a Swift based {{site.data.keyword.objectstorageshort}} account.  After being imported as an Image Template, images may be used to provision or boot an existing virtual server. Images imported from an {{site.data.keyword.objectstorageshort}} account may be either VHDs or custom ISOs. VHD imports are restricted to the following 64-bit operating systems:
 - CentOS 6 and 7
 - RedHat Enterprise Linux 6 and 7
 - Ubuntu 14.04, and 16.04
 - Microsoft Server Standard 2012, R2 2012, and 2016

VHD imports are limited to 100 GB disks. VHDs should be named as follows: `filename.vhd-0.vhd`.

## Converting images to VHD

VHD format is the only supported image format for {{site.data.keyword.BluVirtServers_full}}. To convert images to VHD, please use the following:

    qemu-img 2.7.0 or newer convert
    convert image -> qemu-img convert -f <image format> <image name> -O vpc -o force_size <image name>
        example: qemu-img convert -f qcow2 test -O vpc -o force_size test

If more information is required, please see https://en.wikibooks.org/wiki/QEMU/Images#Converting_image_formats

##  ISO Templates

At this time, only {{site.data.keyword.BluSoftlayer_full}} Supported Operating Systems can be used to load an ISO Template onto a VSI. A list of Supported Operating Systems can be found here: [{{site.data.keyword.cloud}} Server Software](https://www.ibm.com/cloud-computing/bluemix/cloud-server-software){:new_window}

ISOs imported using this tool must be bootable in order for the image to be eligible for import.

## Configure an Image for Virtual Servers

{{site.data.keyword.BluVirtServers_full}} require images to be configured to the following specifications below:

    /boot must be first partition
    /boot and / must be ext3 or ext4 file system
    /etc  and /root must be on the same partition as /
    /etc/fstab -> LABEL=SWAP-xvdb1 swap swap : to mount swap disk we attach to the system
    wget must be installed
    Latest xe-guest-utilities Xen tools must be installed
        https://github.com/xenserver/xe-guest-utilities

Please follow the steps below to import an image in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}.

## Import an Image

1. Locate and record the following details for the image from the {{site.data.keyword.objectstorageshort}} account. Refer to [View and Edit {{site.data.keyword.objectstorageshort}}File Details](view-and-edit-object-storage-file-details.html).
   - Account Name
   - Cluster
   - Container
   - Image Filename
2. Access the **Image Templates** screen in the Customer Portal via **Devices** > **Manage** > **Images**.
3. Click the **Import Image** tab to open the Import tool.
4. Select the **{{site.data.keyword.objectstorageshort}} Account** for the desired image from the **Account** drop down list.
5. Select the **{{site.data.keyword.objectstorageshort}} Cluster** for the desired image from the **Cluster** drop down list.
6. Select the **{{site.data.keyword.objectstorageshort}} Container** for the desired image from the **Container** drop down list.
7. Select the **Image Filename** as it is listed in **{{site.data.keyword.objectstorageshort}}** from the **Image** File drop down list.
8. Enter the desired **Image Name** for the new Image Template in the **Image Name** field.
9. Enter any applicable notes in the **Notes** text box, if desired.
10. Select the image's Operating System from the **Operating System** drop down list. <br/>
    **Note**: The Operating System drop down list will be grayed out if the image for import is a custom ISO. This step is only required when the import involves a VHD.
11. Click the **Import** button to import the image to the Image Templates screen. Click **Cancel** to cancel the action.

## What Happens Next

After the import has begun, the system will located the image file in the {{site.data.keyword.objectstorageshort}} account using the specified path (**Account > Cluster > Container > Image File**) and will import the image file as an image template, which will be stored on the Image Templates screen. After the import has completed, the image may be used to order a new device or to boot an existing device. Additionally, the image may be deleted at any time. Image import times vary based on file size, but generally take several minutes.

Please read [VHD Content Checking and Conversion](vhd-content-checking-and-conversion.html) for more information regarding image handling.
