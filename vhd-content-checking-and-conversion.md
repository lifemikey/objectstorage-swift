---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-05"

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


# VHD content checking and conversion
{: #VHDChecking}

All instances of this service are deprecated. Existing accounts can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**. Effective of **31 March 2019**, IBM Cloud no longer supports the Image Templates import/export feature with Cloud Object Storage Swift.
{:deprecated}

Being able to import and deploy your own instance by using a custom VHD or ISO is one of the many benefits of the {{site.data.keyword.BluSoftlayer_full}}. By using these instructions you can verify that your VHD/ISO is the proper content type, convert it if the content type is incorrect, and even manually import an image if needed. For more information about the Image import option, see the following [article](/docs/infrastructure/image-templates?topic=image-templates-preparing-and-importing-images){:new_window}.

You can access the [{{site.data.keyword.objectstorageshort}} Screen](/docs/infrastructure/objectstorage-swift?topic=objectstorage-swift-OSSSLPortal) and click **View Credentials** to see your credentials.
{:tip}

1. Authenticate against the specific [{{site.data.keyword.objectstorageshort}} cluster you want to interact with.
   - Run the following command to authenticate against the Dallas {{site.data.keyword.objectstorageshort}} Cluster, substituting your own {{site.data.keyword.objectstorageshort}} credentials.

   ```
   curl -i -H "X-Auth-Key: <OBJECT STORAGE API KEY>" -H "X-Auth-User: <OBJECT STORAGE USERNAME>" https://dal05.objectstorage.service.networklayer.com/auth/v1.0/
   ```
   {: pre}

   - After you ran the authentication command, you get an output with your temporary Authentication token and URL. These values are used to interact with the containers and objects.

   ```
   HTTP/1.1 200 OK
   Content-Length: 1365
   X-Auth-Token-Expires: 22043
   X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2
   X-Storage-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2
   X-Storage-Url: https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx
   Content-Type: text/html; charset=UTF-8
   X-Trans-Id: txd681f1026a6040e9b8d19-00564f370f
   Date: Fri, 20 Nov 2015 15:06:55 GMT
   ```
   {: codeblock}

2. List containers.
   - By using the `X-Auth-Token` and `X-Storage-Url`, list the containers in the Cluster.

   ```
   curl -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx"

   HTTP/1.1 200 OK
   Content-Length: 84
   X-Account-Meta-Nas-Id: 4435697
   X-Account-Object-Count: 771
   X-Account-Storage-Policy-Standard-Container-Count: 8
   X-Timestamp: 1424893395.37346
   X-Account-Meta-Cdn-Id: 22873
   X-Account-Storage-Policy-Standard-Object-Count: 771
   X-Account-Bytes-Used: 109313871291
   X-Account-Container-Count: 8
   Content-Type: text/plain; charset=utf-8
   Accept-Ranges: bytes      
   X-Account-Storage-Policy-Standard-Bytes-Used: 109313871291
   X-Trans-Id: tx5fa5bb3224694c49bb3b7-0056797317
   Date: Tue, 22 Dec 2015 15:58:15 GMT

   images
   isos
   vhds    
   ```
   {: codeblock}

   If you want to see what is in a container, append the container name to the end of the `X-Storage-Url`. For example, if you want to view the contents of the container named `isos`, use the following command.
   {:tip}

   ```
   curl -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx/isos"
   ```
   {: pre}

3. Verify the content type.
   - If you are using a third-party application to upload objects in to {{site.data.keyword.objectstorageshort}}, you might run across an issue where the application sets the wrong content type. This error is caused by the software that is being used to upload the object not properly identifying the MIME type and uploading it as such.

   Example
   ```
   curl -s -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx/isos/centos.iso" -I |grep Content-Type

   Content-Type: application/octet-stream
   ```
   {: codeblock}

4. Correct the content type.
   - The correct Content-Type for an ISO is `application/x-iso9660-image`. To correct an erroneous content type, you can change the `Content-Type` header in {{site.data.keyword.objectstorageshort}} with an `HTTP POST`. In {{site.data.keyword.objectstorageshort}}, `PUT` is used to create and `POST` is used to modify. The following call modifies the Content-Type.

   ```
   curl -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" -H "Content-Type: application/x-iso9660-image" "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx/isos/centos.iso" -X POST
   ```
   {: pre}

5. Import the data manually
   - In rare circumstances, an ISO with the correct Content-Type doesn't show up for import under **Devices** > **Manage** > **Images** > **Import Image**. When this happens, you can manually import the ISO  with the following curl command.

   ```
   curl -sk "https://<SWIFT_USER>:<APIKEY>@api.softlayer.com/rest/v3/SoftLayer_Virtual_Guest_Block_Device_Template_Group/createFromExternalSource.json" -X POST -d '{"parameters": [{"name": "<CentOS>", "note": "Testing manual import of image", "operatingSystemReferenceCode": "<CENTOS_6_64>", "uri": "swift://<SWIFT_ACCOUNT>@<DC>/<CONTAINER_NAME>/<OBJECT_NAME_OF_IMAGE>"}]}'
   ```
   {: pre}

   - Replace `<SWIFT_USER>` and `<APIKEY>` with your {{site.data.keyword.BluSoftlayer}} account user name and API key.

   The command requires both parts of the user name. For example, in case of `SLOSXXXXX-35:johndoe` the `<SWIFT_USER>` entry is `johndoe` and the `<SWIFT_ACCOUNT>` entry is `SLOSXXXXX-35`.
   {:important}

   - Complete the parameters with the appropriate name and OS reference code, plus the appropriate container name, and image name in the URI section.
   The following example shows the full command that `johndoe` can use to import a CentOS ISO.

   ```
   curl -sk "https://johndoe:a5a9139ccb319795362785af5da02d244e76076d142f15b9d7bb95671b83XXXX@api.softlayer.com/rest/v3/SoftLayer_Virtual_Guest_Block_Device_Template_Group/createFromExternalSource.json" -X POST -d '{"parameters": [{"name": "CentOS", "note": "CentOS production image", "operatingSystemReferenceCode": "CENTOS_6_64", "uri": "swift://SLOSXXXXX-35@dal05/isos/centos_production_iso_image.iso"}]}'
   ```
   {: codeblock}
