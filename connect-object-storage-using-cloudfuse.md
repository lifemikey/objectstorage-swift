---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-09"

---
{:new_window: target="_blank"}
{:note: .deprecated}

# Connecting to {{site.data.keyword.objectstorageshort}} OpenStack Swift by using Cloudfuse

{{site.data.keyword.BluSoftlayer}}'s {{site.data.keyword.objectstorageshort}} product can be mounted in Linux or Windows, and navigated as a native directory. While you can interact with your {{site.data.keyword.objectstorageshort}} containers similar to a native file/folder structure; it isn't recommended to run programs from this mount point.

1. Download the `cloudfuse` files.
   ```
   https://github.com/redbo/cloudfuse/tarball/master
   ```

2. Extract the files.
   ```
   tar -xzvf cloudfuse-0.1.tar.gz
   ```

3. Check system dependency for the compiling process. Install the following packages for your Linux system.
   - RHEL/CentOS - `gcc make fuse-devel curl-devel libxml2-devel openssl-devel fuse`
   - Debian/Ubuntu - `build-essential libcurl4-openssl-dev libxml2-dev libssl-dev libfuse-dev`

4. Compile the `cloudfuse` binary.
   ```
   ./configure
   make
   make install
   ```

5. Check that the `cloudfuse` binary was installed.
   ```
   which cloudfuse => /usr/local/bin/cloudfuse
   ```

Before you can mount your {{site.data.keyword.objectstorageshort}} account, you need to create a file in your home directory with your {{site.data.keyword.Bluemix}} {{site.data.keyword.objectstorageshort}} account details. The file must be named `.cloudfuse` and contain the following information.

```
username=[your username]
api_key=[key or password string]
authurl=https://dal05.objectstorage.softlayer.net/auth/v1.0/
```

**Note** - Your `authurl` is dependent on the location of your {{site.data.keyword.objectstorageshort}}.

You can set more option for the {{site.data.keyword.objectstorageshort}} mount. These options are located under the **USE:** section in the README file found in the cloudfuse tar file. A common option is the following setting.

```
cache_timeout
```

This option sets the duration of directory caching, the default is 600 seconds.
