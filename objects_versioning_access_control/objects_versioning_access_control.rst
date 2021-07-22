.. _objects_versioning_access_control:

-------------------------------------
Objects: Versioning and Access Controls
-------------------------------------

*The estimated time to complete this lab is 60 minutes.*

Overview
++++++++

Accessing & Creating Buckets With Objects Browser
+++++++++++++++++++++++++++++++++++++++++++++++++

In this exercise you will use Objects Browser to create and use buckets in the object store using your generated access key.

Download the Sample Images
..........................

#. Login to *Initials*\ **-Windows-ToolsVM** via RDP using the following credentials:

   - **Username** - NTNXLAB\\Administrator
   - **password** - nutanix/4u

#. `Click here <https://s3.amazonaws.com/get-ahv-images/sample-pictures.zip>`_ to download the sample images to your Windows-ToolsVM. Once the download is complete, extract the contents of the .zip file.

Use Object Browser to Create A Bucket
.....................................

#. From the Objects UI, Locate the **Objects Public IPs**.

   .. figure:: images/objects_06.png

#. In a new browser tab paste the **Objects Public IP**, and add port **7200**.

   .. figure:: images/objects_06b.png

#. Enter the following fields for the user created earlier, and click **Login** button:

   - **Access Key**  - *Generated When User Created*
   - **Secret Key** - *Generated When User Created*

   .. figure:: images/objects_08.png

#. Click the **+** and **Create bucket**.

   .. figure:: images/objects_08b.png

#. Enter the following name for your bucket, and click **Create**:

   - **Bucket Name** - *intials*-**Test-Bucket**

   .. note::

     Bucket names must be lower case and only contain letters, numbers, periods and hyphens.

     Additionally, all bucket names must be unique within a given Object Store. Note that if you try to create a folder with an existing bucket name (e.g. *your-name*-my-bucket), creation of the folder will not succeed.

   Creating a bucket in this fashion allows for self-service for entitled users, and is no different than a bucket created via the Prism Buckets UI.

#. Click into your *your-name*-**my-bucket** bucket, and Click the **+** and ***Upload file**.

#. Navigate to your downloads directory and find the Sample Pictures folder. Upload one or more pictures to your bucket.

#. That is how easy it is to use the Objects Browser.


Object Versioning
+++++++++++++++++

Object versioning allows the upload of new versions of the same object for required changes, without losing the original data. Versioning can be used to preserve, retrieve and restore every version of every object stored within a bucket, allowing for easy recovery from unintended user action and application failures.

#. Open Notepad in *Initials*\ **-Windows-ToolsVM**.

#. Type “version 1.0” in Notepad, then save the file.

#. In Objects Browser, upload the text file to your *your-name*-**my-bucket** bucket.

#. Make changes to the text file in Notepad and save it with the same name, overwriting the original file.

#. Upload the modified file to your bucket. If desired, you can update and upload the file multiple times.

#. Back in Prism Cental > Services > Objects, click on **Object Stores**.

#. look at the **Num. Objects** for your *your-name*-**my-bucket** bucket.

   .. note:: You will see that there is an Object counted for every version of your test file.


Takeaways
+++++++++

What are the key things you should know about **Nutanix Objects**?

- Nutanix Objects provides a simple and scalable S3-compatible object storage solution, optimized for DevOps, Long Term Retention and Backup Target use cases.

- Nutanix Objects can be deployed on an AHV cluster, with ESXi support on the roadmap.

- Nutanix Objects will be enabled and deployed from Prism Central.
