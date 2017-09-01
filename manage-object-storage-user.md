---

copyright:
  years: 2017
lastupdated: "2017-08-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Manage Object Storage User Permissions

User permissions for Object Storage accounts require that several individual permissions be granted. In order to alleviate the need to grant a variety of permissions, the Manage Users feature for Object Storage allows the account administrator to manage users' Object Storage permissions by clicking a single check box. Additionally, multiple users may be managed at one time on the same screen.  It is important to note the following when updating an Object Storage user's permissions:

  - Access to each Object Storage Account and Cluster are impacted.  If access is removed, the user loses access to all Accounts and Clusters for Object Storage.
  - Object Storage permissions are derived from a combination of permissions from CDN and StorageLayer.  Granting access to Object Storage means giving users permissions from those sets.  Removing permissions for Object Storage results in the removal of permissions for CDN and StorageLayer.

Follow the steps below to manage an Object Storage user.

## Manage an Object Storage User

1. Access the Object Storage screen on the [Customer Portal](https://control.softlayer.com/). Refer to [Access the Object Storage Screen](access-object-storage-screen.html).
2. Click the **Manage Users** option in the Account tab.
3. Locate the desired user by scrolling through the list or typing the user's name in the Filter field.
4. Select the **Grant Access** check box to grant the user permission to view and manage the Object Storage account. Deselect the **Grant Access** check box to remove the user's permission set.
5. Repeat the previous two steps until all desired permissions have been updated.
6. Click the **Save** button to save the changes. Click the **Cancel** button to cancel the action.

## What Happens Next

After granting or removing permissions for Object Storage, the changes will be reflected in the following permissions for each user that was changed:

  - Manage CDN
  - Manage CDN File Transfer
  - Manage StorageLayer

If granting a user access for Object Storage, the user will have the ability to view and interact with the Object Storage cluster. If removing user access for Object Storage through this tool, all storage and CDN access will be removed. If the user should have access to either of these features, edit the user's permissions to manually grant the necessary permissions.
