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

# Archiving Your Data Using {{site.data.keyword.BluSoftlayer_notm}} {{site.data.keyword.objectstorageshort}} and NetApp AltaVault

The continued growth of large, unstructured data is fueling the consumption of storage resources. This consumption has enterprises seeking to alleviate the capital and operational costs that are associated with storing infrequently accessed data sets and archives on high-performance storage and or tape libraries. Items in the data sets can include email archives (per regulation), product diagrams and manuals, medical images, and other unstructured data. {{site.data.keyword.BluSoftlayer_full}} {{site.data.keyword.objectstorageshort}} is one such solution that assists with reducing costs. It offers the same durability, protection, and access of traditional, monolithic storage arrays at a much lower price point and enhanced scale.


### Getting to the Cloud

One of the issues that is associated with using {{site.data.keyword.objectstorageshort}} is the current methodology of using REST APIs to ingest (that is, upload) and access data. As a result, businesses are faced with a decision to either write scripts or applications that incorporate REST APIs to use {{site.data.keyword.objectstorageshort}}. The other option is to keep large, infrequently used data sets on expensive, in-house storage arrays. AltaVault Cloud Gateway Appliance from NetApp provides enterprises another choice. Together with {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, AltaVault lets customers effortlessly archive, manage, and serve large amounts of unstructured data. Additionally, {{site.data.keyword.BluSoftlayer}}’s pay-as-you-go pricing model and full integration with the content delivery network (CDN) help you store and distribute data in 24 geographically diverse nodes.

The NetApp AltaVault Cloud-Integrated Storage Appliance is a software solution that allows businesses to seamlessly integrate customer’s on-premises environment to private or public clouds. Subsequently, customers can simply deploy the appliance within their on-premises data center and safely send and migrate data to {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.

AltaVault can be deployed in two modes: archive (also known as Cold Storage) and back up. This solution brief and how-to guide focuses on the end-to-end archiving architecture of AltaVault as shown in Figure 1.

![Figure 1 - AltaVault end-to-end flow](/images/altavault_fig1.png)


**AltaVault Cloud-Integrated Storage Appliance**

AltaVault is considered a cloud-enabled storage appliance. It exposes a Network File System (NFS) and or Server Message Block (SMB)/Common Internet File System (CIFS) mount point on the front end. AltaVault then securely connects to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} interface on the backend. Customers can simply mount or point to the aforementioned mount points and begin copying data into the cloud as shown in Figure 2.

![Figure 2 - AltaVault mounts to {{site.data.keyword.BluSoftlayer}}](/images/altavault_fig2.png)


In archive, or cold-storage mode, AltaVault primarily uses the local disk that is assigned for metadata cache rather than local data cache. AltaVault also provides AES 256-bit encryption for data that is in-flight and at-rest on {{site.data.keyword.BluSoftlayer}}’s Object Store. The appliance features inline variable-length deduplication and compression, which reduces the amount of data that is needed to transfer and store at {{site.data.keyword.BluSoftlayer}}. Visit the [NetApp AltaVault page](http://www.netapp.com/us/products/protection-software/altavault/) for a more complete list of features and functions.

Since the data replicated by AltaVault is encrypted, users cannot directly access the same data residing on the {{site.data.keyword.objectstorageshort}} through the traditional {{site.data.keyword.objectstorageshort}} REST APIs or FTP. They must use one of two methods to access the data in {{site.data.keyword.objectstorageshort}}. The first method is to use the on-premises AltaVault to read, write, and delete data to, from, and in the cloud. The second, if accessing the data remotely, is to deploy another AltaVault appliance within {{site.data.keyword.BluSoftlayer}}, import the on-premises configuration (a built-in function), and access an NFS/SMB/CIFS mount presented by the AltaVault.

This section describes the process of deploying the AltaVault appliance both on-premises and at {{site.data.keyword.BluSoftlayer}}. Note that AltaVault can be purchased as a physical or virtual appliance. Only the deployment of the trial version VMware vSphere ESXi-based AltaVault virtual appliance is covered.


## Deploying AltaVault On-Premises

### Verifying the Requirements for On-Premises

 - Obtain a copy of the AltaVault Virtual Appliance [in Open Virtualization Appliance (OVA) format]. Contact your [NetApp representative](https://www.netapp.com/us/products/cloud-storage/altavault-cloud-backup.aspx) for this appliance.
 - Available existing on-premises vSphere ESXi 5.5 environment with the minimum CPU, memory, and disk space for the AltaVault appliance. If you're using the trial version, the requirements are four virtual CPUs (vCPUs), 24 GB of memory, and up to 8 TB of disk space.
 - Available 2x10Gbps Network Interface Cards (NICs) within the vSphere environment. One NIC will be used for data ingest and the other used for data replication to {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.
 - Define two networks – replication and data access – within the vSphere environment in addition to the NICs. The replication network cannot be assigned to the same network as the data access network since it might create a loop.
 - Acquire the credentials used for {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} including the {{site.data.keyword.BluSoftlayer}} user name, {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} user name, and the API key associated with the {{site.data.keyword.BluSoftlayer}} user name.
 - Knowledge of VMware Sphere terminology and administering vSphere ESXi environments. This knowledge includes, but is not limited to, use of the vSphere web client, vSphere client, and assignment of hardware resources including networking and storage.

### Deploying AltaVault OVA for On-Premises

Deploy the AltaVault OVA to the vSphere environment once all the requirements have been met. Instructions for OVA deployment can be found in the [NetApp AltaVault Installation and Service Guide](https://library.netapp.com/ecm/ecm_download_file/ECMLP2317733).

1. Go back and edit the AltaVault virtual machine (VM) once the deployment of the OVA has completed.
2. Modify the memory allocated to match the version of AltaVault in the edit window. If you are using the trial version, assign 24 GB of memory and add a disk less than or equal to 8 TB.
3. Make sure to assign different networks (i.e., VLANs) to the AltaVault appliance after the memory and disk configurations have been modified.

The NICs are assigned the following interface functions:

- Primary: Used as the management and or replication-to-the-cloud interface.
- e0a: An optional interface that can be used to replicated data to the cloud.
- e0b: An interface that can be used to export the mount point for the NFS/SMB/CIFS share.
- e0c: Another interface that can be used to export the mount point for the NFS/SMB/CIFS share.

In the example configuration we used, the AltaVault appliance uses the Primary interface as the cloud replication interface and e0b interface to export an NFS mount point. Note that you cannot use both an NFS share and SMB/CIFS share to access the same data. In other words, if you place data in an NFS share, you will not be able to access it via the SMB/CIFS share and vice versa.

![Figure 3 - On-premises and {{site.data.keyword.BluSoftlayer}} overview](/images/altavault_fig3.png)

The [NetApp AltaVault Installation and Service Guide](https://library.netapp.com/ecm/ecm_download_file/ECMLP2317733) has more information on the installation of the OVA and configuration of the VM settings for the appliance.


### Setting up Initial Configuration of the AltaVault Appliance for On-Premises

After the AltaVault VM is configured with the appropriate hardware, you can power on the VM. On the first start, the boot process can take some time as the appliance is formatting the secondary metadata cache disk.

1. When the appliance completed the boot process, log in to the console by using `admin` as the user name, and `password` as the password.
2. After logging in to the appliance, the console displays a question whether you want to use the wizard for initial configuration. Enter `y`.
3. In the wizard, use the information that you see in Table 1.
   <table>
     <tr><th>Question</th><th>Answer</th></tr>
     <tr><td>Step 1. `Admin password?`</td><td>Enter a new admin password</td></tr>
     <tr><td>Step 2. `Hostname?`</td><td>Enter the host name that you want to use</td></tr>
     <tr><td>Step 3. `Use DHCP on primary interface?`</td><td>Enter n</td></tr>
     <tr><td>Step 4. `Primary IP address?`</td><td>Enter the primary network IP address.  In our configuration, this is the network used for cloud replication and appliance management (for example, 192.168.64.5)</td></tr>
     <tr><td>Step 5. `Netmask?`</td><td>Enter the netmask (for example, 255.255.255.0)</td></tr>
     <tr><td>Step 6. `Default gateway?`</td><td>Enter the default gateway (for example, 192.168.64.1)</td></tr>
     <tr><td>Step 7. `Primary DNS server?`</td><td>Enter the primary DNS server in your environment</td></tr>
     <tr><td>Step 8. `Domain name?`</td><td>Enter the domain name of your environment (for example, testenv.org)</td></tr>
   </table>
   Table 1: AltaVault initial configuration values
4. Press **Enter** to save your changes.

### Configuring AltaVault for {{site.data.keyword.BluSoftlayer_notm}} {{site.data.keyword.objectstorageshort}} for On-Premises

1. Open a web browser and enter the IP address of the AltaVault appliance primary interface (this was configured in the previous step).
2. Log in to the console with the admin credentials. On first login, the **Wizard Dashboard**  is displayed.
    <br/>![Figure 4 - AltaVault Wizard Dashboard](/images/altavault_fig4.png)
3. Select **System Settings**.
4. Verify that the information is correct on the next screen and adjust the time zone to reflect the time zone of your environment.
5. Click **Next**, then **Save and Apply**.
6. Select **Cloud Settings** when you are back on the wizard dashboard.
7. Select **{{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}** from the **Provider** menu on the **Cloud Settings Wizard**.
8. Select the **{{site.data.keyword.objectstorageshort}} Region** within {{site.data.keyword.BluSoftlayer}} that you want to use.

   Not all regions are displayed (for example, Melbourne). However, the host name of the {{site.data.keyword.objectstorageshort}} Service can be modified by using the host name field. For example, if you want to use Melbourne as the region, you can select San Jose 1 from the menu and modify the hostname field to `mel01.objectstorage.softlayer.net`.
   {:note}
9. Enter the {{site.data.keyword.objectstorageshort}} user name and {{site.data.keyword.BluSoftlayer}} user name in the **User name** field.

   The format of the user name must be `{{site.data.keyword.objectstorageshort}} User name:{{site.data.keyword.BluSoftlayer}} User name`. For example: `XXX-OS279888:lionelmessi`. You can find your {{site.data.keyword.objectstorageshort}} user name in **Storage > {{site.data.keyword.objectstorageshort}}** in the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window}.
   {:important}
10. Enter your API key and type in a bucket name to store the data. The bucket name is simply the container name where you want to store the data in {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}}.
11. Enter Archive/Cold Storage mode by selecting **Yes** for **Enable Archiving**. Make sure your configuration looks similar to Figure 5.
    <br/>![Figure 5 - AltaVault Cloud Settings](/images/altavault_fig5.png)
12. Click **Next**.
13. Allow AltaVault to generate a new encryption key or enter an existing key that you want to use to encrypt and decrypt the data.
14. Click **Next** to confirm the settings, then click **Finish and Apply**.

At this point, AltaVault attempts to contact {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} Service by using the inputs that were given in the wizard. If the connection fails, review your settings and make sure you have the appropriate access to the service. When the settings are correct, the Storage Optimization service starts running and is ready on the home screen.

This service restarts and can take a few minutes to update its status to ready (Figure 6).

![Figure 6 - AltaVault Optimization Service](/images/altavault_fig6.png)


### Configuring AltaVault for NFS Mount Point

When the connection to {{site.data.keyword.BluSoftlayer}} is established, the e0b interface needs to be configured so that an NFS/CIFS mount point can be created.

1. Select **Data Interfaces** from the **Settings** menu on the main screen of the AltaVault web console.
2. Expand **e0b** and select **Enable Data Interface**.
3. Enter the **IP address, Subnet Mask**, and **Gateway** that you plan to use to mount the NFS/CIFS share.

   Although the default maximum transmission unit (MTU) is set to 1,500, you can modify it to 9,000 if you are using jumbo frames. Note that your ESXi host and physical infrastructure also are required to support jumbo frames.
   {:important}
4. Click **Apply** when done.
5. Set up the mount point.

   These instructions are to set up an NFS mount point. Please note that CIFS (also known as SMB) can be used for Microsoft-based environments.
   {:note}
   1. Select **Storage** > **NFS**, and click **NFS**.
   2. Expand either the **NFS** or **NFSv4** share (depending on whether your NFS client supports NFS v3 or NFS v4).
   3. Select the values shown in Figure 7 on the Edit Export tab.<br/>![Figure 7 - AltaVault NFS Export](/images/altavault_fig7.png)
   4. For the client access radio buttons, it is preferable to `whitelist` the clients that you plan to use the NFS mount point. However, you can select **Allow All Clients** if security is not an issue.
   5. Click **Apply**.

### Mounting NFS Share and Beginning Transfer

You have a configured the AltaVault appliance in your on-premises environment. The next step is to mount the NFS share to the host.

1. Click the **Mount Commands** tab on the **NFS** screen.
2. Enter the command shown on the AltaVault screen within a Linux machine in your environment.</br> ![Figure 8 - Commands](/images/altavault_fig8.png)
3. Use the AltaVault data interface IP address to establish the mount.
4. Copy/write data to the mount point after the share is mounted. AltaVault ingests the data, deduplicates, compresses, and then transfers the data to the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} Service you previously configured.

### Saving the On-Premises AltaVault Configuration

Once the data is archived in {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}}, the on-premises AltaVault configuration needs to be exported so that you can access the data within a {{site.data.keyword.BluSoftlayer}} environment.

- Select the **Export Configuration** option within the Wizard Dashboard and click **Export Configuration** to initiate the download of the configuration of the AltaVault appliance.

It is strongly recommended that you store this file in a location that can be accessed during a disaster recovery event.
{:important}

## Deploying AltaVault at {{site.data.keyword.BluSoftlayer_notm}}

In order to access the data archived to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}}, you can request the files through the AltaVault appliance already located on-premises or through another AltaVault appliance located within {{site.data.keyword.BluSoftlayer}}. We can simulate a disaster recovery event at the on-premises location and deploy another AltaVault appliance within {{site.data.keyword.BluSoftlayer}} to perform the recovery.

Note the representative environment in {{site.data.keyword.BluSoftlayer}} consists of a single ESXi host with local storage to execute and house the AltaVault appliance. The infrastructure is representative of the basic single-site architecture consisting of a single ESXi host managed by a vCenter server within a {{site.data.keyword.BluSoftlayer}} Virtual Service Instance (VSI).

### Verifying Requirements for {{site.data.keyword.BluSoftlayer_notm}}

Before proceeding any further, verify the following requirements are met:

- Make sure your environment consists of a single ESXi host managed by a vCenter server within a {{site.data.keyword.BluSoftlayer}} VSI or matches the [Advanced Single-Site VMware Reference Architecture ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html){:new_window}.
- Obtained a copy of AltaVault Virtual Appliance (in OVA format) and it resides on the utility server (which was provisioned when you were setting up the previously mentioned VMware environment). Contact your NetApp representative for this appliance, or download a 90-day trial version on NetApp’s AltaVault website.
- Available existing vSphere ESXi 5.5 environment @ {{site.data.keyword.BluSoftlayer}} with the minimum CPU, memory, and disk space for the AltaVault appliance. If you're using the trial version, the requirements are four vCPU, 24GB of memory and up to 8 TB of disk space.
- Available 2x10Gbps NICs, which are strongly recommended within the vSphere environment.
- Define two networks – replication and data access – within the vSphere environment in addition to the NICs. The replication network cannot be assigned to the same network as the data access network because it might create a loop. Preventing a loop is handled by ordering an additional portable IP block and is covered in the next step.
- Acquire the credentials used for {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, including the {{site.data.keyword.BluSoftlayer}} user name, {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} user name, and the API key associated with the {{site.data.keyword.BluSoftlayer}} user name.
- Knowledge of VMware Sphere terminology and administering vSphere ESXi environments. This knowledge includes, but is not limited to, use of the vSphere web client, vSphere client, and assignment of hardware resources including networking and storage.
- Turn off the on-premises AltaVault appliance, or Suspend Replication by using the **Replication > Storage > Cloud Settings** page. The on-premises AltaVault appliance cannot be actively replicating data or connected to the container/bucket that you are going to use to access the archive in {{site.data.keyword.BluSoftlayer}}.
- Obtain a copy of the exported configuration file of the on-premises AltaVault or access it through a URL.

### Ordering Two Portable Private Networks and Configure vSphere

AltaVault requires the network interfaces to be on different networks within an environment. Therefore, you must order two portable private networks and configure the vSphere environment so that the networks are logically segregated.

1. Log in to the [{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} and click **Account > Place an Order**.
2. Select **Network > Subnets and IPs > Order**.
3. Click the menu and select **Portable Private** and choose the number of IP addresses you want to order.

   Take into account the number of {{site.data.keyword.BluSoftlayer}} reserved IP addresses, which are three to four IP addresses per subnet block. As a result, ordering four IP addresses really net one IP address, or zero if the pod supports the Hot Standby Ready Protocol.
   {:important}
4. Click **Continue** and select the VLAN that you want to use.
5. Click **Continue** and complete the requested information on the next screen, and click **Place Order**. The creation of the IP addresses is quick and can be displayed by selecting **Network > IP Management > Subnets**. These are the addresses to be used for your VMs that you plan to place in the default virtual machine port group.
6. Repeat this process so that you have two portable private IP address subnets.

   Keep track of the IP assignments. You can keep track by clicking on the **Notes** section of the IP address and entering the hostname or description of the machine assigned to the IP address.
   {:important}

Next, log in to your vSphere environment and create a VM port group to reflect the addition of the portable IP block. In our environment, we created a VM port group that is labeled **Share Network** to denote that it is going to be used for `Eth0_0` to export an NFS mount point.

![Figure 9 - {{site.data.keyword.BluSoftlayer}} ESXi Network](/images/altavault_fig9.png)

### Deploying AltaVault OVA for {{site.data.keyword.BluSoftlayer_notm}}

Deploy the AltaVault OVA to the vSphere environment by using the utility server after all of the previous requirements are met.

1. Go back and edit the AltaVault VM when the deployment of the OVA is completed. Within the edit window, you might need to modify the memory allocated to match the version of AltaVault that you purchased. If you are using the trial version, assign 24 GB of memory and a disk less than or equal to 8 TB.
2. Make sure to assign different networks (such as, portable private networks) to the AltaVault appliance after the memory and disk configurations are modified. The NICs are assigned the following functions:

     - `Primary`: Used as the management and or replication-to-the-cloud/object store interface. In this environment, it is assigned the “Primary Network” port group.      
     - `e0a`: An optional interface that can be used to replicated data to the cloud.
     - `e0b`: An interface that can be used to export the mount point for the NFS/SMB/CIFS share. In this environment, it is assigned the “Share Network” port group.
     - `e0c`: Another interface that can be used to export the mount point for the NFS/SMB/CIFS share.

In the example configuration, the AltaVault appliance uses the `Primary` interface as the replicate-to-cloud/object store interface and `e0b` interface to export an NFS mount point. you must use the same type of protocol (such as, NFS or SMB/CIFS) as the one that you used on the on-premises AltaVault to replicate data to the cloud. For example, if you used an NFS share within the on-premises environment, you must use an NFS share to access the same data within {{site.data.keyword.BluSoftlayer}}.
{:important}

![Figure 10 - {{site.data.keyword.BluSoftlayer}} setup with VMware](/images/altavault_fig10.png)

For more information about the installation of the OVA and the VM settings for the appliance, see the [NetApp AltaVault Installation and Service Guide ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://library.netapp.com/ecm/ecm_download_file/ECMP12510040){:new_window} .

### Setting up Initial Configuration of the AltaVault Appliance

After the AltaVault VM is configured with the appropriate virtualized hardware, you can power on the VM. At the first boot, the boot process can take some time as the appliance is formatting the secondary metadata cache disk.
{:note}

1. When the appliance completed the boot process, log in to the console by using `admin` as the user name, and `password` as the password.
2. The console displays a question whether you want to use the wizard for initial configuration. Enter `y`.
3. In the wizard, use the information in Table 2.
   <table>
     <tr><th>Question</th><th>Answer</th></tr>
     <tr><td>Step 1. `Admin password?``</td><td>Enter a new admin password</td></tr>
     <tr><td>Step 2. `Host name? </td><td>Enter the host name you want to use</td></tr>
     <tr><td>Step 3. `Use DHCP on primary interface?`</td><td>Enter n</td></tr>
     <tr><td>Step 4. `Primary IP address?`</td><td>Enter the primary network IP address.  In our configuration, this is the network used for cloud replication and appliance management (for example, 192.168.64.5)</td></tr>
     <tr><td>Step 5. `Netmask?`</td><td>Enter the netmask (for example, 255.255.255.0)</td></tr>
     <tr><td>Step 6. `Default gateway?`</td><td>Enter the default gateway (for example, 192.168.64.1)</td></tr>
     <tr><td>Step 7. `Primary DNS server?`</td><td>Enter the primary DNS server in your environment</td></tr>
     <tr><td>Step 8. `Domain name?`</td><td>Enter the domain name of your environment (for example, testenv.org)</td></tr>
   </table>    
    Table 2: AltaVault Setup Wizard
4. Press the **Enter key** to save your changes.

### Configuring AltaVault for {{site.data.keyword.BluSoftlayer_notm}} {{site.data.keyword.objectstorageshort}}

In this step, the appliance is configured to connect to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} Service. For the on-premises configuration, we used the public DNS to connect to the {{site.data.keyword.objectstorageshort}} Service. For this example, we use the internal DNS name to connect to the service.
{:note}

1. Open a web browser and enter the IP address of the AltaVault appliance primary interface (this was configured in the previous step).
2. Log in to the console with the admin credentials. At the first login, the Wizard Dashboard is displayed as shown in Figure 11.
    <br/>![Figure 11 - AltaVault Wizard](/images/altavault_fig11.png)
3. Select **System Settings**.
4. Verify that the information is correct on the next screen and adjust the time zone to reflect the time zone of your environment. For example, if the time zone in the configuration file is America/Chicago, select America/Chicago for this appliance as well.
5. Click **Next > Save and Apply > Exit**. As the result, you are logged out of your browser session.
6. Log back in to the appliance and select Import Configuration from the AltaVault Wizard menu.
7. Click **Load File** if you have the configuration file of the on-premises AltaVault or select a URL to specify the location of the configuration file.
8. Leave the **Import Shared Data Only** checked because it is needed to configure a new IP address for `e0b`.
9. In the **Key Passphrase** field, enter the password of the encryption key that you specified when you configured the on-premises AltaVault. For example, if your password for the on-premises AltaVault is **Neymar11**, enter **Neymar11**.
10. Click **Import Configuration > Exit**.

Although we imported the on-premises configuration to the {{site.data.keyword.BluSoftlayer}} AltaVault appliance, the cloud settings within the appliance must be modified to access the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} Service through the private network. Use the following steps to make the modifications to the appliance.

1. Browse to the **Cloud Settings** screen within the AltaVault appliance, and modify the **Hostname** to reflect the private address of the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}. The private network name syntax is `location.objectstorage.service.networklayer.com`, where location designates the shortened data center name (for example, `mel01` for Melbourne 01 data center).
2. Click **Apply**.

After you configured the connection to {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, place the appliance in recovery mode so that it can sync the data from the {{site.data.keyword.objectstorageshort}}. SSH to the AltaVault appliance and enter the following commands.

   ```
   AltaVault > enable
   AltaVault # configure terminal
   AltaVault (config) # no service enable
   AltaVault (config) # datastore format local
   AltaVault (config) # replication recovery enable
   AltaVault (config) # service enable
   AltaVault (config) # show service
   ```
   {:codeblock}

If the settings and setup are correct, you can see that the Storage Optimization service is running and is ready on the home screen. Note that this service restarts and can take a few minutes to update its status to ready (Figure 12).

![Figure 12 - AltaVault Service Status](/images/altavault_fig12.png)


### Configuring AltaVault for NFS Mount Access (for {{site.data.keyword.BluSoftlayer_notm}})

When the connection to the internal {{site.data.keyword.objectstorageshort}} server is established, the Eth0_0 interface needs to be configured so that an NFS/SMB/CIFS mount point can be accessed.

1. Select **Settings** > **Data Interfaces** from the main screen of the AltaVault web console.
2. Expand **e0b** and click **Enable Data Interface**.
3. Enter the IP address, Subnet Mask, and Gateway that you want to use to mount the NFS/SMB/CIFS share when the data interface is enabled.

   Use a different subnet than what was used for the primary interface. This second subnet must be created before this step. Although the default MTU is set to 1,500, you can modify this value to 9,000 if you are using jumbo frames. Your ESXi host and the physical infrastructure are required to support jumbo frames. By default, {{site.data.keyword.BluSoftlayer}} already supports MTU sizes of 9,000 so no configuration changes are required within {{site.data.keyword.BluSoftlayer}}.
   {:important}
4. Click **Apply**.

You now have a configured AltaVault appliance in your {{site.data.keyword.BluSoftlayer}} environment. The next step is to mount the NFS share you previously configured.

1. Click the **Mount Commands** tab on the **NFS** screen.
2. Enter the command on a Linux machine in your environment (see Figure 8.)
3. Use the AltaVault data interface when you establish the mount. When the export is mounted, you can then read data from the mount point to prove the disaster recovery capabilities of AltaVault.

## Closing notes

As large, unstructured data sets continue to grow, companies are seeking alternative ways to store and retain archives while lowering operational and capital expenses. The economics of data archiving and retention become feasible with cloud {{site.data.keyword.objectstorageshort}}, but inject various hurdles involving the migration from traditional storage systems to the cloud. By using NetApp’s AltaVault Cloud-Integrated Storage Appliance, organizations can quickly realize the value of cloud {{site.data.keyword.objectstorageshort}}. It allows straightforward deployment, set up, and migration from on-premises to {{site.data.keyword.BluSoftlayer}}.

For more information about NetApp AltaVault, see the [NetApp AltaVault website ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.netapp.com/us/products/protection-software/altavault/).

For more information about {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, visit {{site.data.keyword.BluSoftlayer}}’s [{{site.data.keyword.objectstorageshort}} Site ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/cloud-object-storage).
