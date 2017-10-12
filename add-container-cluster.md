---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Adding a Container to a Cluster

A container houses data associated with an {{site.data.keyword.objectstorageshort}} account and is associated with an {{site.data.keyword.objectstorageshort}} cluster. At least one container must exist per account; however, multiple containers may be made and maintained according to the user's needs. Follow the steps below to add a container to a cluster.

## Add a Container

1. Access the **{{site.data.keyword.objectstorageshort}}** screen in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Refer to [Access the {{site.data.keyword.objectstorageshort}} screen](access-object-storage-screen.html).
2. Click the **Add Container** link. A field will appear prompting the entry of the new container name.
3. Enter the name of the container in the **Container Name** field. Container names must be 256 characters or less after URL encoding and cannot contain a forward slash (/).
2. Click the **OK** button to create your container. Your new container will appear as the first container within the cluster.

## What Happens Next

After adding a new container, [files may be added](add-object-file.html) as desired. Additional containers may be added to house files of like kind and [folders may be added](add-folder-container.html) to containers to further assist in organization of data. If at any time data needs to be located quickly, [search within a cluster](search-within-cluster.html) for the data using keywords.
