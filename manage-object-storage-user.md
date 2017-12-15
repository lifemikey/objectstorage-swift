---

copyright:
  years: 2017
lastupdated: "2017-12-15"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Managing {{site.data.keyword.objectstorageshort}} OpenStack Swift User Permissions

User permissions for {{site.data.keyword.objectstorageshort}} accounts require that several individual permissions be granted. In order to alleviate the need to grant a variety of permissions, the Manage Users feature for {{site.data.keyword.objectstorageshort}} allows the account administrator to manage users' {{site.data.keyword.objectstorageshort}} permissions by clicking a single check box. Additionally, multiple users may be managed at one time on the same screen.  It is important to note the following when updating an {{site.data.keyword.objectstorageshort}} user's permissions:

  - Access to each {{site.data.keyword.objectstorageshort}} Account and Cluster are impacted.  If access is removed, the user loses access to all Accounts and Clusters for {{site.data.keyword.objectstorageshort}}.
  - {{site.data.keyword.objectstorageshort}} permissions are derived from a combination of permissions from Storage CDN and StorageLayer.  Granting access to {{site.data.keyword.objectstorageshort}} means giving users permissions from those sets.  Removing permissions for {{site.data.keyword.objectstorageshort}} results in the removal of permissions for Storage CDN and StorageLayer.

Follow the steps below to manage an {{site.data.keyword.objectstorageshort}} user.

## Manage an {{site.data.keyword.objectstorageshort}} User

1. Access the {{site.data.keyword.objectstorageshort}} screen on the  [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}. Refer to [Access the {{site.data.keyword.objectstorageshort}} Screen](access-object-storage-screen.html).
2. Click the **Manage Users** option in the Account tab.
3. Locate the desired user by scrolling through the list or typing the user's name in the Filter field.
4. Select the **Grant Access** check box to grant the user permission to view and manage the {{site.data.keyword.objectstorageshort}} account. Deselect the **Grant Access** check box to remove the user's permission set.
5. Repeat the previous two steps until all desired permissions have been updated.
6. Click the **Save** button to save the changes. Click the **Cancel** button to cancel the action.

## What Happens Next

After granting or removing permissions for {{site.data.keyword.objectstorageshort}}, the changes will be reflected in the following permissions for each user that was changed:

  - Manage Storage CDN
  - Manage Storage CDN File Transfer
  - Manage StorageLayer

If granting a user access for {{site.data.keyword.objectstorageshort}}, the user will have the ability to view and interact with the {{site.data.keyword.objectstorageshort}} cluster. If removing user access for  through this tool, all storage and Storage CDN access will be removed. If the user should have access to either of these features, edit the user's permissions to manually grant the necessary permissions. See also [Can a User Have CDN and StorageLayer Permissions Granted but be Prohibited from Accessing Object Storage?](https://console.bluemix.net/docs/infrastructure/content-deliver-network/FAQ.html#can-a-user-have-cdn-and-storagelayer-permissions-granted-but-be-prohibited-from-accessing-object-storage-){:new_window}.
