---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-19"

---
{:new_window: target="_blank"}
{:note: .deprecated}
{:shortdesc: .shortdesc}

# VHD Content Checking and Conversion 

Being able to import and deploy your own instance using a custom VHD or ISO is one of the many benefits of the {{site.data.keyword.BluSoftlayer_full}}. In this guide we will show you how to verify that your VHD/ISO is the proper content type, show how to convert it if the content type is incorrect, and even manually import an image if needed. If you are unfamiliar with the Image import option please see the following [article](https://console.bluemix.net/docs/infrastructure/image-templates/import-image.html){:new_window} .

## Prerequisites

1.  [Access the {{site.data.keyword.objectstorageshort}} Screen](access-object-storage-screen.html)
2.  Click the **View Credentials** link (record your credentials).

## Basic Operations

The first step to interacting with {{site.data.keyword.objectstorageshort}} from the command line is to authenticate against the specific ObjectStorage cluster you will be interacting with. For our examples we will be using the Dallas 05 cluster.

### Authentication

Run the following command to authenticate against the Dallas {{site.data.keyword.objectstorageshort}} Cluster, substituting your own {{site.data.keyword.objectstorageshort}} credentials.

`curl -i -H "X-Auth-Key: <OBJECT STORAGE API KEY>" -H "X-Auth-User: <OBJECT STORAGE USERNAME>" https://dal05.objectstorage.service.networklayer.com/auth/v1.0/`

Once you have run the authentication command you will get output with your temporary Authentication token and URL. These values will be used going forward to interact with our containers and objects.
     
      HTTP/1.1 200 OK
      Content-Length: 1365
      X-Auth-Token-Expires: 22043
      X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2
      X-Storage-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2
      X-Storage-Url: https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx
      Content-Type: text/html; charset=UTF-8
      X-Trans-Id: txd681f1026a6040e9b8d19-00564f370f
      Date: Fri, 20 Nov 2015 15:06:55 GMT

### List Containers

Using the X-Auth-Token and X-Storage-Url from our Authentication step we can now list the containers in our Cluster:


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

If we want to see what is in a container we simply append the container name to the end of the X-Storage-Url. For example if we wanted to view the contents of the container named isos our command would look like this:

`curl -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx/isos"`

### Verifying content type

If you are using a third party application to upload objects in to {{site.data.keyword.objectstorageshort}} you may run across an issue where the application sets the wrong content type. This is caused by the software being used to upload the object not properly identifying the MIME type and uploading it as such. Here you can see the Content-Type is not set correctly on an ISO:

      curl -s -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx/isos/coreos.iso" -I |grep Content-Type
      
      Content-Type: application/octet-stream

### Correcting content type

The correct Content-Type for an ISO is application/x-iso9660-image. To correct this, you can change the 'Content-Type' header in object storage with an HTTP POST. In {{site.data.keyword.objectstorageshort}}, PUT is used to create and POST is used to modify. Here is the call to modify the Content-Type:

      curl -i -H "X-Auth-Token: AUTH_tkcxxxxxxxxxxxxxxxxxxxxxxxx1d2a2a2" -H "Content-Type: application/x-iso9660-image"
      "https://dal05.objectstorage.service.networklayer.com/v1/AUTH_xxxxxxxx-d4a2-xxxx-xxxx-xxxxxxxxxx/isos/coreos.iso" -X POST

### Manual import

In very rare circumstances an ISO with the correct Content-Type will not show up for import under **Devices** > **Manage** > **Images** > **Import Image**. When this happens you can manually import the ISO using the following command. You will need to replace **APIUSER** and **APIKEY** with your {{site.data.keyword.BluSoftlayer}} account username and API key, and fill in the appropriate container name, and image name in the uri section. You will only use the first part of your {{site.data.keyword.objectstorageshort}} username in the command. For example if your full {{site.data.keyword.objectstorageshort}} name was SLOSXXXXX-35:johndoe you would only use SLOSXXXXX-35 in the import command.

`curl -sk https://<APIUSER>:<APIKEY>@api.softlayer.com/rest/v3/SoftLayer_Virtual_Guest_Block_Device_Template_Group/createFromExternalSource.json -X POST -d '{"parameters": [{"name": "templatename", "note": "exmaplenotes", "uri": "swift://<OBJECT STORAGE USER>@dal05/container/imagename.iso"}]}'`

Here is what the full command would look like if I wanted to import my CoreOS ISO in to the customer portal:

`curl -sk "https://<APIUSER>:<APIKEY>@api.softlayer.com/rest/v3/SoftLayer_Virtual_Guest_Block_Device_Template_Group/createFromExternalSource.json" -X POST -d '{"parameters": [{"name": "CoreOS", "note": "Testing manual import of ISO", "uri": "swift://<OBJECT_STORAGE_USER>@dal05/isos/coreos.iso"}]}'`
