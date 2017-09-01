---

copyright:
  years: 2017
lastupdated: "2017-07-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Export an Image

The Image Templates screen in the [Customer Portal](https://control.softlayer.com/) allows users to export an Image Template to an Object Storage account. The image export process takes a preexisting, private Standard Image Template and coverts the image into an Image File that is stored in a specified location on an Object Storage account. The export process is currently not available on Flex Images. Follow the steps below to export an Image Template.

## Export an Image

 1. Access the Image Templates screen in the [Customer Portal]((https://control.softlayer.com/)) by clicking **Devices** > **Manage** > **Images**
 2. Locate the desire Image Template in the list. 
 3. Select Export Image from the **Actions** drop down list for the desired Image Template.
 4. Enter the desired **File Name** for the image in the **File Name** field.
 5. Select the desired **Object Storage Account** from the **Account** drop down list.
 6. Select the desired **Object Storage Cluster** from the **Cluster** drop down list.
 7. Select the desired **Object Storage Container** from the **Container** drop down list.
 8. Click the **Export Image** button to export the image to the specified location in the Object Storage Account. Click the **Close** button to cancel the action.

## What Happens Next

After exporting an image, the image will remain in the list of Image Templates, but will also be available as a file in the Object Storage location specified during the export process. Refer to View and Edit Object Storage File Details for more information on viewing a file exported to an Object Storage Account. Because each image is a different size and has different characteristics, the export process may take several minutes before it is complete. Our average export speed is 2GB/minute. If several minutes lapse and the image is still not available on the Object Storage Account, please contact Support.
