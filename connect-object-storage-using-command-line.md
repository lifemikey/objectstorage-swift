---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-21"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift using the Command Line

{{site.data.keyword.BluSoftlayer_full}} {{site.data.keyword.objectstorageshort}} provides a low cost storage solution that can be used for many applications. Unlike {{site.data.keyword.filestorage_short}} and {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.objectstorageshort}} manages data as objects, with each object including the data itself, some metadata, and a globally unique identifier. For more information about the right storage solution for your application, please read [Which storage solution is best for your project?](http://blog.softlayer.com/2014/which-storage-solution-best-your-project){:new_window}. 

The command line is a powerful and flexible method to access {{site.data.keyword.objectstorageshort}}. There are several tools that can be installed and used from a Linux terminal. A common package is [python-swiftclient](https://pypi.python.org/pypi/python-swiftclient) used with the latest version of Ubuntu (14.04) for this example. Steps may vary depending on your distribution.
<table>
  <caption>Table 1. shows the advantages and disadvantages of using the Command Line</caption>
<tr><td>Disadvantages:	</td><td>No advanced features (encryption, compression, etc.), No graphical interface</td></tr>
<tr><td>Advantages:</td><td>Large files (> 5 GB) are supported, File segmentation is supported.</td></tr>
<tr><td>Use Cases:	</td><td>Access when no graphical interface is available, uploading and downloading large files</td></tr>
</table>

## Access by Command Line (Linux)

1. [Access the {{site.data.keyword.objectstorageshort}} Screen](access-object-storage-screen.html)
2. Click the **View Credentials** link (record your credentials).
3. Access the server's command line.
4. Install the python swift client (this command is for Ubuntu, your distribution's commands may vary):<br/>
   ```apt-get install python-swiftclient```
5. Export the authentication credentials to simplify later steps:<br/>
     ```export ST_AUTH=     (https://tor01.objectstorage.softlayer.net/auth/v1.0/ )``` <br/>
     ```export ST_USER=     (IBMOS278685-10:######)```  <br/>
     ```export ST_KEY=      (#############)```

6. Upload any files or directories you wish to the container you created earlier:<br/>
   ``swift upload ``<br/>
   Example: ``swift upload StorageContainer testfile.txt``
7. {{site.data.keyword.objectstorageshort}} OpenStack Swift has a 5 GB single file upload limit. If you have files larger than this, you can upload them in segments with the following command: <br/>
   ``swift upload -s `` <br/>
  Example: `swift upload -s 1073741824 StorageContainer largefile` <br/>
  **Note**: This command will break large files into 1 GB chunks.
8. Downloading a file follows the same format swift download <br/>
   Example: `swift download StorageContainer testfile.txt`
