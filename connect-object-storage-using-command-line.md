---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

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

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using the Command Line

{{site.data.keyword.BluSoftlayer_full}} {{site.data.keyword.objectstorageshort}} provides a low-cost storage solution that can be used for many applications. Unlike {{site.data.keyword.filestorage_short}} and {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.objectstorageshort}} manages data as objects. Each object includes the data itself, some metadata, and a globally unique identifier.

The command line is a powerful and flexible method to access {{site.data.keyword.objectstorageshort}}. There are several tools that can be installed and used from a Linux terminal. A common package is the [`python-swiftclient` ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://pypi.python.org/pypi/python-swiftclient). 

**Advantages and disadvantages of using the command line**
- Disadvantages include no advanced features (such as encryption, or compression), and no graphical interface.
- Advantages are that large files (bigger than 5 GB) and file segmentation are supported.

## Accessing {{site.data.keyword.objectstorageshort}}

The instructions use version 14.04 of Ubuntu. Steps can vary depending on your distribution.
{:note}

1. [Access the {{site.data.keyword.objectstorageshort}} Screen](interacting-in-portal.html)
2. Click **View Credentials** to view and record your credentials.
3. Access the server's command line.
4. Install the `python-swiftclient`. This command is for Ubuntu, your distribution's commands might vary.<br/>
   ```
   apt-get install python-swiftclient
   ```
   {:pre}
   
5. Export the authentication credentials to simplify the following steps.<br/>
   ```
   export ST_AUTH=     (https://tor01.objectstorage.softlayer.net/auth/v1.0/ )
   export ST_USER=     (IBMOS278685-10:######)
   export ST_KEY=      (#############)
   ```

6. Upload the files or directories that you want to the container.<br/>
   ```
   swift upload
   ```
   {:pre}
   
   Example 
   ```
   swift upload StorageContainer testfile.txt
   ```
   
7. {{site.data.keyword.objectstorageshort}} OpenStack Swift has a 5-GB single file upload limit. If you have files larger than this, you can upload them in segments with the following command. <br/>
    ```
    swift upload -s
    ```
    {:pre}
    
    Example 
    ```
    swift upload -s 1073741824 StorageContainer largefile
    ```
    
    This command breaks large files into 1-GB chunks.
    {:note}
    
8. Downloading a file follows the same format for swift download.<br/>
    
   ```
   swift download StorageContainer testfile.txt
   ```
