.. _files_deploy:

.. title:: Nutanix Files Deploy

-------------
Files: Deploy
-------------

.. _deploying_files:

Deploy Files
++++++++++++

#. In **Prism > File Server**, click **+ File Server** to open the **New File Server Pre-Check** dialogue.

   .. figure:: images/1.png

   For the purpose of saving time, the Files has already been uploaded to your cluster. Files binaries can be downloaded directly through Prism Element > :fa:`cog` > Upgrade Software menu (option to uploaded manually is present as well).

   .. figure:: images/2.png

   Additionally, the cluster's **Data Services** IP Address has already been configured (*10.XX.YY.38*). In a Files cluster, storage is presented to the Files VMs as a Volume Group via iSCSI, hence the dependency on the Data Services IP.

   .. note::

     If staging your own environment, the Data Services IP can be easily configured by selecting :fa:`gear` **> Cluster Details**, specifying the **iSCSI Data Services IP**, and clicking **Save**. Currently, the Data Services IP must be in the same subnet as your CVMs.

   Lastly Files will ensure that at least 1 network has been configured on the cluster. A minimum of 2 networks are recommended to have segmentation between the client side and storage side networks.

#. Click **Continue** on Pre-Check window if it appears

   .. figure:: images/3.png

#. Fill out the following fields:

   - **Name** - *Intials*-Files (e.g. XYZ-Files)
   - **Domain** - ntnxlab.local
   - **File Server Size** - 1 TiB

   .. figure:: images/4.png

#. Click **Next**.

#. Select the **Secondary - Managed** VLAN for the **Client Network**.

   Each Files VM will consume a single IP on the client network.

   .. note::

     In the HPOC environment it is critical to use the secondary VLAN for the client network if using separate client and storage networks.

     It is typically desirable in production environments to deploy Files with dedicated virtual networks for client and storage traffic. When using two networks, Files will, by design, disallow client traffic the storage network, meaning VMs assigned to the primary network will be unable to access shares.

   .. note::

     As this is an AHV managed network, configuration of individual IPs is not necessary. In an ESXi environment, or using an unmanaged AHV network, you would specify the network details and available IPs as shown below.

     .. figure:: images/6.png

#. Specify your cluster's **Domain Controller** VM IP (found in :ref:`stagingdetails`) as the **DNS Resolver IP** (e.g. 10.XX.YY.40). Leave the default (cluster) NTP Server.

   .. raw:: html

     <strong><font color="red">In order for the Files cluster to successfully find and join the NTNXLAB.local domain it is critical that the DNS Resolver IP is set to the Domain Controller VM IP FOR YOUR CLUSTER. By default, this field is set to the primary Name Server IP configured for the Nutanix cluster, this value is incorrect and will not work.</font></strong>

   .. figure:: images/7.png

#. Click **Next**.

#. Select the **Primary - Managed** VLAN for the Storage Network.

   Each Files VM will consume a single IP on the storage network, plus 1 additional IP for the cluster.

   .. figure:: images/8.png

#. Click **Next**.

#. Fill out the following fields:

   - Select **Use SMB Protocol**
   - **Username** - Administrator@ntnxlab.local
   - **Password** - nutanix/4u
   - Select **Make this user a File Server admin**
   - Select **Use NFS Protocol**
   - **User Management and Authentication** - Unmanaged

   .. figure:: images/9.png

   .. note:: In unmanaged mode, users are only identified by UID/GID. In Files 3.5, Files supports both NFSv3 and NFSv4

#. Click **Next**.

   By default, Files will automatically create a Protection Domain to take daily snapshots of the Files cluster and retain the previous 2 snapshots. After deployment, the snapshot schedule can be modified and remote replication sites can be defined.

   .. figure:: images/10.png

#. Click **Create** to begin the Files deployment.

#. Monitor deployment progress in **Prism > Tasks**.

   Deployment should take approximately 10 minutes.

   .. figure:: images/11.png

   .. note::

     If you receive a warning regarding DNS record validation failure, this can be safely ignored. The shared cluster does not use the same DNS servers as your Files cluster, and as a result is unable to resolve the DNS entries created when deploying Files.

#. Go to **Prism > File Server** and select the *Initials*\ **-Files** server and click **Protect**.

   .. figure:: images/12.png

#. Observe the default Self Service Restore schedules, this feature controls the snapshot schedule for Windows' Previous Versions functionality. Supporting Previous Versions allows end users to roll back changes to files without engaging storage or backup administrators. Note these local snapshots do not protect the file server cluster from local failures and that replication of the entire file server cluster can be performed to remote Nutanix clusters. Click **Close**.

   .. figure:: images/13.png

Takeaways
+++++++++

What are the key things you should know about **Nutanix Files**?

- Files can be rapidly deployed on top of existing Nutanix clusters, providing SMB and NFS storage for user shares, home directories, departmental shares, applications, and any other general purpose file storage needs.
- Files is not a point solution. VM, File, Block, and Object storage can all be delivered by the same platform using the same management tools, reducing complexity and management silos.
