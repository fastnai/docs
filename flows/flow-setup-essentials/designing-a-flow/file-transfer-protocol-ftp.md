---
description: Transfer files between systems using FTP, FTPS, or SFTP connections.
---

# File Transfer Protocol (FTP)

The **File Transfer Protocol** component allows you to upload, download, list, delete, or rename files on remote servers securely and efficiently.

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

### **How to Configure?**

* **Select Connection Type**\
  Choose the connection mode based on your use case: **FTP**, **FTPS**, or **SFTP**.

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

* **Connect or Create Account**
  * You can **connect an existing FTP/FTPS/SFTP account** if already configured.
  * Or, enable the **Manual** toggle to create your own credentials.

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

* **Select Operation**\
  Choose what you want the component to do:
  * **Upload** a file to the remote server
  * **Download** a file from the remote server
  * **List** files in a directory
  * **Delete** a file from the server
  * **Rename** a file
* **Set File Path**\
  Specify the target **path** for the file or directory where the operation should be performed.

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

* **Run the Flow**\
  Save and run the flow. The selected file operation will execute automatically.

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

### **How It Helps?**

* Transfer files securely across systems using **FTP**, **FTPS**, or **SFTP**.
* Perform multiple operations like **upload, download, or list** files in one flow.
* Enable **manual credentials** for flexible setup when predefined accounts aren’t available.
* Works seamlessly in **tenant-based environments**, each tenant’s FTP account is isolated and managed securely.
* Solves the limitation where FTP connections cannot list files directly by adding a **List operation** for better file visibility.
