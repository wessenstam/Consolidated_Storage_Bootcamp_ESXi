.. _files_manager:

.. title:: Files: Files Manager

---------------------
Files: Files Manager
---------------------

Smart DR feature for Files share replication is activated and maintained in Prism Central using Files Manager. In this section we will configure Smart DR requirements in Prism Central.

The Files Manager lets you view and control all of your file servers from a single control plane. Clicking a file server directs you to Nutanix Files in Prism Element (PE) where you can manage the shares, exports, and configurations of the file server. File server alerts for all registered file servers appear in a single pane for consolidated viewing, as do file server events.

The Files Manager provides the Smart DR service for Nutanix Files, which lets you protect file servers at the share-level.

Enabling the Files Manager
---------------------------

Enable the Files Manager service on PC

#. Log on to Prism Central

#. Click the collapsed menu icon

#. In the **Services** > **Files**

   .. figure:: images/files_manager.png 

#. Read the information on enabling the Files Manager and click **Enable Files**

#. In the Enable Service dialog box, click **Enable**

Upgrading Files Manager
------------------------

Files Manger introduces new features and bug fixes with updates. For example, Files Manager version 2.0.0 inroduced Smart DR (Disaster Recover) feature.

You can perform Files Manager upgdates using the Life-Cycle Manager (LCM).

We  will verify the current version of Files Manager in Life Cycle Management.

#. In Prism Central, use the search window to search for **Life Cycle Manager** 

   .. figure:: images/lcm_search.png 

#. Select **Life Cycle Manager** from the search result 

#. In **Life Cycle Manager**, click on **Inventory**

#. If **Inventory** doesn't show any existing software versions, click on **Perform Inventory** 

   ..  figure:: images/lcm_perform_inventory.png

#. Click on **Proceed** in the confirmation window

   .. note:: 
  
     The Inventory operation may take up to 30 minutes

#. Once the Inventory operation is finished, Click on **LCM  > Updates > Software** to check the available updates for software in your Nutanix clusters

   .. figure:: images/lcm_inventory_result.png

#. Here you can notice that Files Manager version ``2.0.0`` is available and you can also see that the current version ``1.0.1``

#. Select the check-box nex to **Files Manager** and click on **Update**

   .. figure:: images/files_manager_update.png

#. **Life Cycle Manager** will now generate update plans and present an option to apply updates.

   .. figure:: images/files_manager_apply_update.png

#. Click on **Apply 1 Updates**
   
   .. note::

    The number of updates to apply might vary from your choice of software that you choose to upgrade. Since Files Manager is the only software we are upgrading in this labs, so it is showing 1 update.

#. Confirm that the updates are succesful 

   .. figure:: images/lcm_update_success.png

#. After the updates are applied, go back to **Life Cycle Manager** and perform and **Inventory**
 
#. Verify that Files Manager is of version ``2.0.0``  (or whichever is latest at the time).

   .. figure:: images/files_manager_updated_version.png 

#. Go back to **Prism Central** > **Services** > **Files**

#. Verify that the Data Protection features are present
 
   .. figure:: images/files_manager_data_protection.png

#. You can now proceed with the :ref:`files_replication` lab

    

   