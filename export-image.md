---

copyright:
  years: 2017
lastupdated: "2017-10-25"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Exporting an Image to an {{site.data.keyword.objectstorageshort}} Account

The [Image Templates](/../docs/infrastructure/image-templates/image_index.html){:new_window} screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} allows users to export an [Image Template](/../docs/infrastructure/image-templates/image_about.html){:new_window} to an {{site.data.keyword.objectstorageshort}} account. The image export process takes a preexisting, private Standard [Image Template](/../docs/infrastructure/image-templates/image_about.html){:new_window} and coverts the image into an Image File that is stored in a specified location on an {{site.data.keyword.objectstorageshort}} account. The export process is currently not available on Flex Images. Follow the steps below to export an Image Template.

## Export an Image

 1. Access the Image Templates screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} by clicking **Devices** > **Manage** > **Images**
 2. Locate the desire Image Template in the list. 
 3. Select Export Image from the **Actions** drop down list for the desired Image Template.
 4. Enter the desired **File Name** for the image in the **File Name** field.
 5. Select the desired **{{site.data.keyword.objectstorageshort}} Account** from the **Account** drop down list.
 6. Select the desired **{{site.data.keyword.objectstorageshort}} Cluster** from the **Cluster** drop down list.
 7. Select the desired **{{site.data.keyword.objectstorageshort}} Container** from the **Container** drop down list.
 8. Click the **Export Image** button to export the image to the specified location in the {{site.data.keyword.objectstorageshort}} Account. Click the **Close** button to cancel the action.

## What Happens Next

After exporting an image, the image will remain in the list of [Image Templates](/../docs/infrastructure/image-templates/image_about.html){:new_window}, but will also be available as a file in the {{site.data.keyword.objectstorageshort}} location specified during the export process. Refer to [View and Edit {{site.data.keyword.objectstorageshort}} File Details](view-and-edit-object-storage-file-details.html) for more information on viewing a file exported to an {{site.data.keyword.objectstorageshort}} Account. Because each image is a different size and has different characteristics, the export process may take several minutes before it is complete. Our average export speed is 2 GB/minute. If several minutes lapse and the image is still not available on the {{site.data.keyword.objectstorageshort}} Account, please contact Support.
