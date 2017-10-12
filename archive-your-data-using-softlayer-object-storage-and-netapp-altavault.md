---

copyright:
  years: 2017
lastupdated: "2017-10-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Archiving Your Data Using {{site.data.keyword.BluSoftlayer_notm}} {{site.data.keyword.objectstorageshort}} and NetApp AltaVault 

The continued growth of large, unstructured data is fueling the consumption of storage resources. This consumption has enterprises seeking to alleviate the capital and operational costs associated with storing infrequently accessed data sets and archives on high-performance storage and or tape libraries. Items in the data sets can include email archives (per regulation), product diagrams and manuals, medical images, and other unstructured data. {{site.data.keyword.BluSoftlayer_full}} {{site.data.keyword.objectstorageshort}} is one such solution that assists with reducing costs. It offers the same durability, protection, and access of traditional, monolithic storage arrays at a much lower price point and enhanced scale.


### Get to the Cloud

One of the issues with using {{site.data.keyword.objectstorageshort}} is the current methodology of using REST APIs to ingest (i.e., upload) and access data. As a result, businesses are faced with a decision to either write scripts or applications that incorporate REST APIs to use {{site.data.keyword.objectstorageshort}}. The other option is to keep large, infrequently used data sets on expensive, in-house storage arrays. AltaVault Cloud Gateway Appliance from NetApp (formerly Riverbed SteelStore) provides enterprises another choice. Together with {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, AltaVault lets customers effortlessly archive, manage, and serve large amounts of unstructured data. Additionally, {{site.data.keyword.BluSoftlayer}}’s pay-as-you-go pricing model and full integration with the content delivery network (CDN) provide the ability to store and distribute data in 24 geographically diverse nodes.

The NetApp AltaVault Cloud-Integrated Storage Appliance is a software solution that allows businesses to seamlessly integrate customer’s on-premises environment to private or public clouds. Subsequently, customers can simply deploy the appliance within their on-premises data center and safely send and migrate data to {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.

AltaVault can be deployed in two modes: archive (i.e., Cold Storage) and back up. This solution brief and how-to guide will focus on the end-to-end archiving architecture of AltaVault as shown in Figure 1. 

![Figure 1: AltaVault end-to-end flow](/images/altavault_fig1.png)


### AltaVault Cloud-Integrated Storage Appliance

AltaVault is considered a cloud-enabled storage appliance. It exposes a Network File System (NFS) and or Server Message Block (SMB)/Common Internet File System (CIFS) mount point on the front end. AltaVault then securely connects to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} interface on the backend. Customers can simply mount or point to the aforementioned mount points and begin copying data into the cloud as shown in Figure 2.

![Figure 2: AltaVault mounts to {{site.data.keyword.BluSoftlayer}}](/images/altavault_fig2.png)


Be aware that in archive, or cold-storage mode, AltaVault primarily uses the local disk assigned for metadata cache rather than local data cache. AltaVault also provides AES 256-bit encryption for data that is in-flight and at-rest on {{site.data.keyword.BluSoftlayer}}’s Object Store. The appliance features inline variable-length deduplication and compression, which reduces the amount of data needed to transfer and store at {{site.data.keyword.BluSoftlayer}}. Visit the [NetApp AltaVault page](http://www.netapp.com/us/products/protection-software/altavault/) for a more complete list of features and functions .

Since the data replicated by AltaVault is encrypted, users cannot directly access the same data residing on the {{site.data.keyword.objectstorageshort}} through the traditional {{site.data.keyword.objectstorageshort}} REST APIs or FTP. They must use one of two methods to access the data in {{site.data.keyword.objectstorageshort}}. The first method is to use the on-premises AltaVault to read, write, and delete data to, from, and in the cloud. The second, if accessing the data remotely, is to deploy another AltaVault appliance within {{site.data.keyword.BluSoftlayer}}, import the on-premises configuration (a built-in function), and access an NFS/SMB/CIFS mount presented by the AltaVault.
Deploy AltaVault

This section describes the process of deploying the AltaVault appliance both on-premises and at {{site.data.keyword.BluSoftlayer}}. Note that AltaVault can be purchased as a physical or virtual appliance. Only the deployment of the trial version VMware vSphere ESXi-based AltaVault virtual appliance is covered.


## Deploy AltaVault On-Premises

The necessary steps needed to deploy AltaVault as an on-premises archive solution to {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} are listed below.


### Requirements

Verify the following requirements have been met before proceeding:

 - Obtain a copy of the AltaVault Virtual Appliance [in Open Virtualization Appliance (OVA) format]. Contact your NetApp representative for this appliance, or download a 90-day trial version from [NetApp’s AltaVault](http://www.netapp.com/us/forms/cloud-backup-nurture-m3-offer2.aspx) website.
 - Available existing on-premises vSphere ESXi 5.5 environment with the minimum CPU, memory, and disk space for the AltaVault appliance. If using the trial version, the requirements are four virtual CPUs (vCPUs), 24GB of memory, and up to 8TB of disk space.
 - Available 2x10Gbps Network Interface Cards (NICs) within the vSphere environment. One NIC will be used for data ingest and the other used for data replication to {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.
 - Define two networks – replication and data access – within the vSphere environment in addition to the NICs. The replication network cannot be assigned to the same network as the data access network since it might create a loop.
 - Acquire the credentials used for {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} including the {{site.data.keyword.BluSoftlayer}} username, {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} username, and the API key associated with the {{site.data.keyword.BluSoftlayer}}username.
 - Knowledge of VMware Sphere terminology and administering vSphere ESXi environments. This knowledge includes, but is not limited to, use of the vSphere web client, vSphere client, and assignment of hardware resources including networking and storage.

### Deploy AltaVault OVA

Deploy the AltaVault OVA to the vSphere environment once all the requirements have been met. Instructions for OVA deployment can be found in the [NetApp AltaVault Installation and Service Guide](https://library.netapp.com/ecm/ecm_download_file/ECMLP2317733).

1. Go back and edit the AltaVault virtual machine (VM) once the deployment of the OVA has completed.
2. Modify the memory allocated to match the version of AltaVault in the edit window. If you are using the trial version, assign 24GB of memory and add a disk less than or equal to 8TB.
3. Make sure to assign different networks (i.e., VLANs) to the AltaVault appliance after the memory and disk configurations have been modified.

The NICs are assigned the following interface functions:

- Primary: Used as the management and or replication-to-the-cloud interface.
- e0a: An optional interface that can be used to replicated data to the cloud.
- e0b: An interface that can be used to export the mount point for the NFS/SMB/CIFS share.
- e0c: Another interface that can be used to export the mount point for the NFS/SMB/CIFS share.

In the example configuration we used, the AltaVault appliance uses the Primary interface as the cloud replication interface and e0b interface to export an NFS mount point. Note that you cannot use both an NFS share and SMB/CIFS share to access the same data. In other words, if you place data in an NFS share, you will not be able to access it via the SMB/CIFS share and vice versa.

![Figure 3: On-premises and {{site.data.keyword.BluSoftlayer}} overview](/images/altavault_fig3.png)

The [NetApp AltaVault Installation and Service Guide](https://library.netapp.com/ecm/ecm_download_file/ECMLP2317733) has more information on the installation of the OVA and configuration of the VM settings for the appliance.


### Initial Configuration of the AltaVault Appliance

After the AltaVault VM has been configured with the appropriate hardware, you can now power on the VM. Be aware that upon first boot, the boot process will take some time as the appliance is formatting the secondary metadata cache disk.

1. Log in to the console using **admin** as the **Username**, and **password** as the **Password** once the appliance has completed the boot process.
2. After logging into the appliance, the console displays a question whether you want to use the wizard for initial configuration. Enter **y**.
3. Use the information in Table 1 once you have entered the wizard.
   <table><tbody>
     <tr><td>Question</td><td>Answer</td></tr>
     <tr><td>Step 1: Admin password?</td><td>Enter a new admin password</td></tr>
     <tr><td>Step 2: Hostname?</td><td>Enter the hostname you wish to use</td></tr>
     <tr><td>Step 3: Use DHCP on primary interface?</td><td>Enter n</td></tr>
     <tr><td>Step 4: Primary IP Address?</td><td>Enter the primary network IP address.  In our configuration, this is the network used for cloud replication and appliance management (e.g., 192.168.64.5)</td></tr>
     <tr><td>Step 5: Netmask?</td><td>Enter the netmask (e.g., 255.255.255.0)</td></tr>
     <tr><td>Step 6: Default gateway?</td><td>Enter the default gateway (e.g., 192.168.64.1)</td></tr>
     <tr><td>Step 7: Primary DNS server?</td><td>Enter the primary DNS server in your environment</td></tr>
     <tr><td>Step 8: Domain name?</td><td>Enter the domain name of your environment (e.g., testenv.org)</td></tr>
   </tbody></table>
   Table 1: AltaVault initial configuration values
4. Press **Enter** to save your changes. You have completed the initial configuration of the appliance and can move onto the configuration of the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.

### Configure AltaVault for {{site.data.keyword.BluSoftlayer_notm}} {{site.data.keyword.objectstorageshort}}

The appliance will be configured to connect to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} Service in this step.

1. Open a web browser and enter the IP address of the AltaVault appliance primary interface (this was configured in the previous step).
2. Log in to the console with the admin credentials. Upon first log in, the **Wizard Dashboard** will be displayed as shown in Figure 4.
    <br/>![Figure 4: AltaVault Wizard Dashboard](/images/altavault_fig4.png)
3. Select **System Settings**. 
4. Verify that the information is correct on the next screen and adjust the time zone to reflect the time zone of your environment.
5. Click** Next > Save and Apply**. 
6. Select **Cloud Settings** once you are back on the Wizard Dashboard.
7. Select **{{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}** from the **Provider** drop-down menu on the **Cloud Settings Wizard**.
8. Select the **{{site.data.keyword.objectstorageshort}} Region** within {{site.data.keyword.BluSoftlayer}} that you want to use. Note that not all regions are displayed (e.g., Melbourne), however, the Hostname of the {{site.data.keyword.objectstorageshort}} Service can be modified using the Hostname field. For example, if you wish to use Melbourne as the region, you can select San Jose 1 from the Region drop-down menu and modify the Hostname field to mel01.objectstorage.softlayer.net.
9. Enter the **{{site.data.keyword.objectstorageshort}} Username** and **{{site.data.keyword.BluSoftlayer}} Username** in the **Username** field. The format of the username must be {{site.data.keyword.objectstorageshort}} Username:{{site.data.keyword.BluSoftlayer}} Username. For example: XXX-OS279888:lionelmessi. You can find your {{site.data.keyword.objectstorageshort}} Username under **Storage > {{site.data.keyword.objectstorageshort}}** in the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}.
10. Enter your API key and type in a Bucket Name to store the data. The bucket name is simply the container name where you wish to store the data in {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}}.
11. Enter Archive/Cold Storage mode by selecting **Yes** for **Enable Archiving**. Your configuration should look similar to Figure 5.
    <br/>![Figure 5: AltaVault Cloud Settings](/images/altavault_fig5.png)
12. Click **Next**.
13. Allow AltaVault to generate a new encryption key or enter an existing key you want to use to encrypt and decrypt the data.
14. Click **Next** to confirm the settings, then click **Finish and Apply**.

At this point, AltaVault will attempt to contact {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} Service using the inputs given in the wizard. If the connection fails, review your settings and make sure you have appropriate access to the service. Once the settings are correct, you will notice the Storage Optimization service is running and ready on the home screen. Note that this service restarts and may take a few minutes to update its status to ready (Figure 6).

![Figure 6: AltaVault Optimization Service](/images/altavault_fig6.png)


### Configure AltaVault for NFS Mount Point

Once the connection to {{site.data.keyword.BluSoftlayer}} has been established, the e0b interface needs to be configured so that an NFS/CIFS mount point can be created.

1. Select **Data Interfaces** from the **Settings** menu on the main screen of the AltaVault web console.
2. Expand **e0b** and select the **Enable Data Interface** checkbox.
3. Enter the **IP address, Subnet Mask**, and **Gateway** that will be used to mount the NFS/CIFS share. Although the default maximum transmission unit (MTU) is set to 1,500, you can modify it to 9,000 if you are using jumbo frames. Note that your ESXi host as well as physical infrastructure will also be required to support jumbo frames.
4. Click **Apply** when done.
5. The mount point is set up next. We will set up an NFS mount point. Note, however, that CIFS (also known as SMB) can be used for Microsoft-based environments. Use the following steps to configure the NFS mount point.
6. Select **Storage > NFS**, and click **NFS**.
7. Expand either the **NFS** or **NFSv4** share (depending on whether your NFS client supports NFS v3 or NFS v4). We used NFS v4.
8. Select the values shown in Figure 7 on the Edit Export tab.
    <br/>![Figure 7: AltaVault NFS Export](/images/altavault_fig7.png)
9. For the client access radio buttons, it is preferable to whitelist the clients that will utilize the NFS mount point. However, you may select Allow All Clients if security is not an issue.
10. Click Apply when done.

### Mount NFS Share and Begin Transfer

You will have a minimally configured the AltaVault appliance in your on-premises environment at this point. The next step is to mount the NFS share you previously configured.

1. Click on the **Mount Commands** tab on the **NFS** screen.
2. Enter the command shown on the AltaVault screen within a Linux machine in your environment.
    ![Figure 8: Commands](/images/altavault_fig8.png)
3. Use the AltaVault data interface IP address when establishing the mount.
4. Copy/write data to the mount point once the share is mounted. AltaVault will ingest the data, deduplicate, compress, and then transfer the data to the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} Service you previously configured.

### Save the On-Premises AltaVault Configuration

Once the data is archived in {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} Service, the on-premises AltaVault configuration needs to be exported so that you can access the data within a {{site.data.keyword.BluSoftlayer}} environment.

- Select the **Export Configuration** option within the Wizard Dashboard and click **Export Configuration** to initiate the download of the configuration of the AltaVault appliance. It is strongly recommended that you store this file in a location that can be accessed during a disaster recovery event.

## Deploy AltaVault at {{site.data.keyword.BluSoftlayer_notm}}

In order to access the data archived to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}}, you can request the files via the AltaVault appliance already located on-premises or through another AltaVault appliance located within {{site.data.keyword.BluSoftlayer}}. We will simulate a disaster recovery event at the on-premises location and will deploy another AltaVault appliance within {{site.data.keyword.BluSoftlayer}} to perform the recovery.

Note the representative environment in {{site.data.keyword.BluSoftlayer}} will consist of a single ESXi host with local storage to execute and house the AltaVault appliance. The infrastructure will be representative of the basic single-site architecture consisting of a single ESXi host managed by a vCenter server within a {{site.data.keyword.BluSoftlayer}} Virtual Service Instance (VSI). Click here if you require a more substantial infrastructure with shared storage and supporting features such as vSphere High Availability (HA), data retention services (DRS), and vMotion.

### Requirements

Before proceeding any further, verify the following requirements have been met:

- Make sure your environment consists of a single ESXi host managed by a vCenter server within a {{site.data.keyword.BluSoftlayer}} VSI or matches the single-site VMware reference architecture published on KnowledgeLayer.
- Obtain a copy of AltaVault Virtual Appliance (in OVA format) and that it resides on the utility server (provisioned when setting up either aforementioned VMware environment). Contact your NetApp representative for this appliance, or download a 90-day trial version on NetApp’s AltaVault website.
- Available existing vSphere ESXi 5.5 environment @ {{site.data.keyword.BluSoftlayer}} with the minimum CPU, memory, and disk space for the AltaVault appliance. If using the trial version, the requirements are four vCPU, 24GB of memory and up to 8TB of disk space.
- Available 2x10Gbps NICs, which are strongly recommended within the vSphere environment.
- Define two networks – replication and data access – within the vSphere environment in addition to the NICs. The replication network cannot be assigned to the same network as the data access network since it might create a loop. Preventing a loop is handled by ordering an additional portable IP block and is covered in the next step.
- Acquire the credentials used for {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, including the {{site.data.keyword.BluSoftlayer}}username, {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} username, and the API key associated with the {{site.data.keyword.BluSoftlayer}} username.
- Knowledge of VMware Sphere terminology and administering vSphere ESXi environments. This knowledge includes, but is not limited to, use of the vSphere web client, vSphere client, and assignment of hardware resources including networking and storage.
- Turn off the on-premises AltaVault appliance, or Suspend Replication using the **Replication >Storage > Cloud Settings** page. The on-premises AltaVault appliance cannot be actively replicating data or connected to the container/bucket you are going to use to access the archive in {{site.data.keyword.BluSoftlayer}}.
- Obtain a copy of the exported configuration file of the on-premises AltaVault or access it via a URL.

### Order Two Portable Private Networks and Configure vSphere

AltaVault requires the network interfaces to be on different networks within an environment. Therefore, we must order two portable private networks and configure the vSphere environment so that the networks are logically segregated.

1. Log in to the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} and click **Account > Place an Order**.
2. Select **Network > Subnets and IPs > Order**.
3. Click the drop-down menu and select **Portable Private** and choose the number of IP addresses you wish to order.
4. Note that you will need to take into account the number of {{site.data.keyword.BluSoftlayer}} reserved IP addresses, which are three to four IP addresses per subnet block. As a result, ordering four IP addresses will really net one IP address, or zero if the pod supports Hot Standby Ready Protocol. Click **Continue** and select the VLAN that you wish to use.
5. Click **Continue** and fill in the requested information on the next screen and click **Place Order**. The creation of the IP addresses is fairly quick and can be displayed by selecting **Network > IP Management > Subnets**. These are the addresses to be used for your VMs that will be placed on the default Virtual Machine Port Group.
6. Repeat this process so that you have two portable private IP address subnets.

   **Note**: It is important to keep track of the IP assignments. You can keep track by clicking on the **Notes** section of the IP address and entering the hostname or description of the machine assigned to the IP address.

Next, you will need to log in to your vSphere environment and create a Virtual Machine Port Group to reflect the addition of the portable IP block. In our environment, we created a Virtual Machine Port Group labeled **Share Network** to denote that it will be used for Eth0_0 to export an NFS mount point.

![Figure 9: {{site.data.keyword.BluSoftlayer}} ESXi Network](/images/altavault_fig9.png)

### Deploy AltaVault OVA

Deploy the AltaVault OVA to the vSphere environment using the utility server once all of the above requirements have been met.

1. Go back and edit the AltaVault VM when the deployment of the OVA is completed. Within the edit window, you may need to modify the memory allocated to match the version of AltaVault you have purchased. If you are using the trial version, assign 24GB of memory and a disk less than or equal to 8TB.
2. Make sure to assign different networks (i.e., portable private networks) to the AltaVault appliance after the memory and disk configurations have been modified. The NICs are assigned the following functions:

     - Primary: Used as the management and or replication-to-the-cloud/object store interface. In this environment, it is assigned the “Primary Network” port group.      
     - e0a: An optional interface that can be used to replicated data to the cloud.
     - e0b: An interface that can be used to export the mount point for the NFS/SMB/CIFS share. In this environment, it is assigned the “Share Network” port group.
     - e0c: Another interface that can be used to export the mount point for the NFS/SMB/CIFS share.

In the example configuration, the AltaVault appliance uses the Primary interface as the replicate-to-cloud/object store interface and e0b interface to export an NFS mount point. Remember, you must use the same type of protocol (i.e., NFS or SMB/CIFS) as you used on the on-premises AltaVault to replicate data to the cloud. For example, if you used an NFS share within the on-premises environment, you must use an NFS share to access the same data within {{site.data.keyword.BluSoftlayer}}.

![Figure 10: {{site.data.keyword.BluSoftlayer}} setup with VMware](/images/altavault_fig10.png)

See the [NetApp AltaVault Installation and Service Guide](https://library.netapp.com/ecm/ecm_download_file/ECMP12510040){:new_window} for more information on the installation of the OVA and configuration of the VM settings for the appliance.

### Initial Configuration of the AltaVault Appliance

After the AltaVault VM has been configured with the appropriate virtualized hardware, you can now power on the VM. Note that upon first boot, the boot process will take some time as the appliance is formatting the secondary metadata cache disk.

1. Log in to the console using **admin** as the **Username**, and **password** as the **Password** once the appliance has completed the boot process.
2.  After logging into the appliance, the console displays a question whether you want to use the wizard for initial configuration. Enter y.
3. Use the information in Table 2once you have entered the wizard. 
   <table><tbody>
     <tr><td>Question</td><td>Answer</td></tr>
     <tr><td>Step 1: Admin password?</td><td>Enter a new admin password</td></tr>
     <tr><td>Step 2: Hostname?</td><td>Enter the hostname you wish to use</td></tr>
     <tr><td>Step 3: Use DHCP on primary interface?</td><td>Enter n</td></tr>
     <tr><td>Step 4: Primary IP Address?</td><td>Enter the primary network IP address.  In our configuration, this is the network used for cloud replication and appliance management (e.g., 192.168.64.5)</td></tr>
     <tr><td>Step 5: Netmask?</td><td>Enter the netmask (e.g., 255.255.255.0)</td></tr>
     <tr><td>Step 6: Default gateway?</td><td>Enter the default gateway (e.g., 192.168.64.1)</td></tr>
     <tr><td>Step 7: Primary DNS server?</td><td>Enter the primary DNS server in your environment</td></tr>
     <tr><td>Step 8: Domain name?</td><td>Enter the domain name of your environment (e.g., testenv.org)</td></tr>
   </tbody></table>    
    Table 2: AltaVault Setup Wizard
4. Press the **Enter key** to save your changes. You have completed the initial configuration of the appliance and can move onto the AltaVault configuration of the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}.

### Set Up AltaVault for {{site.data.keyword.BluSoftlayer_notm}} {{site.data.keyword.objectstorageshort}}

In this step, the appliance will be configured to connect to {{site.data.keyword.BluSoftlayer}}’s {{site.data.keyword.objectstorageshort}} Service. For the on-premises configuration, we used the public DNS to connect to the {{site.data.keyword.objectstorageshort}} Service. For our example, we will use the internal DNS name to connect to the service.

1. Open a web browser and enter the IP address of the AltaVault appliance primary interface (this was configured in the previous step).
2. Log in to the console with the admin credentials. Upon first log in, the Wizard Dashboard will be displayed as shown in Figure 11.
    <br/>![Figure 11: AltaVault Wizard](/images/altavault_fig11.png)
3. Select **System Settings**. 
4. Verify that the information is correct on the next screen and adjust the time zone to reflect the time zone of your environment. For example, if the time zone in the configuration file is America/Chicago, select America/Chicago for this appliance as well.
5. Click **Next > Save and Apply > Exit**. You will be logged out of your browser session.
6. Log back in to the appliance and select Import Configuration from the AltaVault Wizard menu.
7. Click **Load File** if you have the configuration file of the on-premises AltaVault or select a URL to specify the location of the configuration file.
8. Leave the **Import Shared Data Only **checkbox selected because it is needed to configure a new IP address for e0b.
9. Enter the password of the encryption key you specified when you configured the on-premises AltaVault in the **Key Passphrase** text box. For example, if your password for the on-premises AltaVault is **Neymar11**, enter **Neymar11** in the Key Passphrase text box.
10. Click **Import Configuration > Exit** when done.

Although we have imported the on-premises configuration to the {{site.data.keyword.BluSoftlayer}} AltaVault appliance, the cloud settings within the appliance must be modified to access the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} Service through the private network. Use the following steps to make the modifications to the appliance.

1. Navigate to the **Cloud Settings** screen within the AltaVault appliance and modify the **Hostname** to reflect the private address of the {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}} Service. The private network name syntax is location.objectstorage.service.networklayer.com, where location designates the shortened data center name (e.g., mel01 for Melbourne 01 data center).
2. Click **Apply**.

You have configured the connection to {{site.data.keyword.BluSoftlayer}} object storage and will need to place the appliance in recovery mode so that it can sync the data from the {{site.data.keyword.objectstorageshort}}. Use the following steps to place the appliance in recovery mode.

 - Secure shell to the AltaVault appliance and enter the following commands upon log in:
   ```
   AltaVault > enable
   AltaVault # configure terminal
   AltaVault (config) # no service enable
   AltaVault (config) # datastore format local
   AltaVault (config) # replication recovery enable
   AltaVault (config) # service enable
   AltaVault (config) # show service
   ```

If the settings and setup are correct, you will notice the Storage Optimization service is running and ready on the home screen. Note that this service restarts and may take a few minutes to update its status to ready (Figure 12).

![Figure 12: AltaVault Service Status](/images/altavault_fig12.png)


### Configure AltaVault for NFS Mount Access

Once the connection to the internal {{site.data.keyword.objectstorageshort}} server has been established, the Eth0_0 interface needs to be configured so that an NFS/SMB/CIFS mount point can be accessed. Use the following steps to configure Eth0_0.

1. Select **Settings** > **Data Interfaces** from the main screen of the AltaVault web console.
2. Expand **e0b** and click the **Enable Data Interface** checkbox.
3. Enter the **IP Address**, **Subnet Mask**, and **Gateway** that will be used to mount the NFS/SMB/CIFS share once the data interface is enabled. Be sure to use a different subnet than what was used for the primary interface. This subnet should have been created before this step. Although the default MTU is set to 1,500, you can modify this value to 9,000 if you are using jumbo frames. Note that your ESXi host as well as physical infrastructure will also be required to support jumbo frames. By default, {{site.data.keyword.BluSoftlayer}} already supports MTU sizes of 9,000 so no configuration changes are required within {{site.data.keyword.BluSoftlayer}}.
4. Click **Apply**.

You now have a minimally configured AltaVault appliance in your {{site.data.keyword.BluSoftlayer}} environment. The next step is to mount the NFS share you previously configured.

1. Click on the **Mount Commands** tab on the **NFS** screen.
2. Enter the command on a Linux machine in your environment (see Figure 8.
3. Use the AltaVault data interface when establishing the mount. Once the export is mounted, you can then read data from the mount point to prove the disaster recovery capabilities of AltaVault.

## Conclusion

As large, unstructured data sets continue to grow, companies are seeking alternative ways to store and retain archives while lowering operational and capital expenditures. The economics of data archiving and retention become feasible with cloud {{site.data.keyword.objectstorageshort}}, but inject various hurdles involving the migration from traditional storage systems to the cloud. By using NetApp’s AltaVault Cloud-Integrated Storage Appliance, organizations can quickly realize the value of cloud {{site.data.keyword.objectstorageshort}}. It allows straightforward deployment, set up, and migration from on-premises to {{site.data.keyword.BluSoftlayer}} using the steps highlighted above.

For further reading about NetApp AltaVault, visit the [NetApp AltaVault website](http://www.netapp.com/us/products/protection-software/altavault/).

For more information regarding {{site.data.keyword.BluSoftlayer}} {{site.data.keyword.objectstorageshort}}, visit {{site.data.keyword.BluSoftlayer}}’s [{{site.data.keyword.objectstorageshort}} Site](https://www.ibm.com/cloud-computing/bluemix/cloud-object-storage).
