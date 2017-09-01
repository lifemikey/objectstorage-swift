---

copyright:
  years: 2017
lastupdated: "2017-07-07"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# How to Mount Object Storage

IBM Bluemix's Object Storage product can be mounted in Linux or Windows and navigated as a native directory.  While you will be able to interact with your object storage containers similar to a native file/folder structure; it is not recommended to run programs from this mount point.

## To mount an object storage account:

1. Download the cloudfuse files.
   `https://github.com/redbo/cloudfuse/tarball/master`

2. Extract the files.
   `tar -xzvf cloudfuse-0.1.tar.gz`

3. Check system dependency for the compiling process.  Install the following packages for your Linux system.
   - RHEL/CentOS: gcc make fuse-devel curl-devel libxml2-devel openssl-devel fuse 
   - Debian/Ubuntu: build-essential libcurl4-openssl-dev libxml2-dev libssl-dev libfuse-dev

4. Compile the cloudfuse binary.
   ``./configure``
   ``make``
   ``make install``

5. Check that the cloudfuse binary was installed
   `which cloudfuse => /usr/local/bin/cloudfuse`

Before you can mount your object storage account you will need to create a file in your home directory with your SoftLayer object storage account details.  The file should be named ".cloudfuse" and contain the the following information:
     
    username=[your username]
    api_key=[key or password string]
    authurl=https://dal05.objectstorage.softlayer.net/auth/v1.0/

**Note**: Your "authurl" will be dependent on the location of your object storage.  The example above is for DAL05, there are also object storage end points in Singapore and Amsterdam.

There are additional options that you can set for the object storage mount.  These options are located under the **USE:** section in the README file found in the cloudfuse tar file.  A common option is:

    cache_timeout= This option sets the duration of directory caching, the default is 600 seconds.

 
You can read more about object storage at our blog:
http://blog.softlayer.com/2012/softlayer-openstack-swift-softlayer-object-storage/
