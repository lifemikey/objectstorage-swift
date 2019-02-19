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

# Connecting to {{site.data.keyword.objectstorageshort}} with Cloudfuse
{: #OSSCloudfuse}

All instances of this service are deprecated. Existing instances can be used, but no new {{site.data.keyword.objectstorageshort}} accounts can be provisioned after **10 December 2018**.
{:deprecated}

{{site.data.keyword.BluSoftlayer}}'s {{site.data.keyword.objectstorageshort}} product can be mounted in Linux or Windows, and navigated as a native directory. You can interact with your {{site.data.keyword.objectstorageshort}} containers similar to a native file and folder structure. However, it is not recommended to run programs from this mount point.

1. Download the `cloudfuse` files.
   ```
   https://github.com/redbo/cloudfuse/tarball/master
   ```

2. Extract the files.
   ```
   tar -xzvf cloudfuse-0.1.tar.gz
   ```

3. Check system dependency for the compiling process. Install the following packages for your Linux system.
   - RHEL and CentOS - `gcc make fuse-devel curl-devel libxml2-devel openssl-devel fuse`
   - Debian and Ubuntu - `build-essential libcurl4-openssl-dev libxml2-dev libssl-dev libfuse-dev`

4. Compile the `cloudfuse` binary.
   ```
   ./configure
   make
   make install
   ```

5. Check that the `cloudfuse` binary is installed.
   ```
   which cloudfuse => /usr/local/bin/cloudfuse
   ```

6. Before you can mount your {{site.data.keyword.objectstorageshort}} account, you need to create a file in your home directory with your {{site.data.keyword.Bluemix}} {{site.data.keyword.objectstorageshort}} account details. The file must be named `.cloudfuse` and contain the following information.

   ```
   username=[your username]
   api_key=[key or password string]
   authurl=https://dal05.objectstorage.softlayer.net/auth/v1.0/
    ```

   Your `authurl` depends on the location of your {{site.data.keyword.objectstorageshort}}.
   {:tip}

7. Chmod the cloudfuse configuration file .cloudfuse, for proper permissions.
   ```
   chmod 600 /user/.cloudfuse
   ```
   {:pre}

8. Mount the directory on your filesystem.
   ```
   cloudfuse /path/to/mount
   ```
   {:pre}


You can set more option for the {{site.data.keyword.objectstorageshort}} mount. These options are located under the `USE:` section in the `README` file that is located in the `cloudfuse .tar` file. A common option is the following setting.

```
cache_timeout
```

This option sets the duration of directory caching. The default is 600 seconds.
{:note}

For more information, see [IBM Cloud Infrastructure + OpenStack Swift = Object Storage ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://blog.softlayer.com/2012/softlayer-openstack-swift-softlayer-object-storage/){:new_window}
