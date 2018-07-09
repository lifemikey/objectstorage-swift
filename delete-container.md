---

copyright:
  years: 2017
lastupdated: "2018-07-09"

---
{:new_window: target="_blank"}

# Deleting a Container

At any point in time, a container may be deleted from the cluster, so long as the container holds no data (files or folders). Prior to deleted the container, all files and folders must also be [deleted](delete-object-cluster.html) or, if they are still needed, may be [copied, moved or downloaded](view-and-edit-object-storage-file-details.html) to another location. Follow the steps below to delete a container.

## Delete a Container

1. Access the {{site.data.keyword.objectstorageshort}} screen on the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Refer to [Access the {{site.data.keyword.objectstorageshort}} Screen](access-object-storage-screen.html).
2. Click the **Delete** icon. A **Delete Container** confirmation box will appear.
3. Click the **Yes** button to delete the container. Click **No** to cancel the request.


## What Happens Next

After a container has been deleted, it cannot be retrieved. It must be re-added and all files or folders that were within the container must also be added back to the cluster.
