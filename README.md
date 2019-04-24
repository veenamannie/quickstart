# Quickstart Guide
## ownCloud - Scope, Need and Benefits

### Scope
ownCloud is an open source and free software that is used to create your own cloud storage solution. ownCloud server can be created on Windows as well as Linux platforms. The client side of the system supports a range of devices such as Windows, Mac OSX, Android and iPhone.

### Need
OwnCloud operates as a very simple way to set up your own syncing cloud storage system on your own server or web site. It is also quick and easy to set up, and does not require advanced technical knowledge. Unlike other cloud storage solutions that provide only file synchronization, ownCloud is a powerful software that allows creating and sharing apps that run on ownCloud including text editors, task lists, and much more.

### Benefits
- Share files with everybody including non-ownCloud users.
- Synchronize files from multiple devices including smartphones and tablets.
- Live collaboration with ownCloud in real time.
- Universal file access from ownCloud from multiple locations like Windows shared-drives, SharePoint, S3  buckets and so on.
- Bookmark favorite files for quick access.
- Active directory and LDAP AD integration for corporate users.

# Install and Configure an ownCloud Server

## System Requirements

| Requirement | Description|
| --- | --- |
| Memory | Depends on the numbers of users, files, and volume of server activity. Minimum 128MB RAM, but a recommended minimum of 512MB. |
| Setup (recommended) | Ubuntu 16.04, MySQL/MariaDB, PHP 7.0, Apache 2.4 with mod_php |

## Install ownCloud Server
This section walks you through installing ownCloud using a tar file or a zip file.
> **Note:** The installation using the ownCloud tarball is best suited for production environments and is also the common installation option. The installation procedure is for experienced administrators and it offers a customizable installation method.

To install ownCloud server, follow these steps:
1. Go to the [ownCloud download page](https://owncloud.org/download/).

2. From the **Resources** section, download either the **Tar file** or **Zip file**. Based on your preference, a file downloads with the name `owncloud-x.y.z.tar.bz2` (tar installation) or `owncloud-x.y.z.zip` (zip installation), where *x.y.z* is the version number.

3. Download the corresponding checksum file. The supported options are md5 and sha256.

4. Verify the MD5 or SHA256 sum.

    **Tar:**
     <code>
      md5sum -c owncloud-x.y.z.tar.bz2.md5 < owncloud-x.y.z.tar.bz2<br>
      sha256sum -c owncloud-x.y.z.tar.bz2.sha256 < owncloud-x.y.z.tar.bz2
     </code>

    **Zip:**
     <code>
      md5sum  -c owncloud-x.y.z.zip.md5 < owncloud-x.y.z.zip<br>
      sha256sum  -c owncloud-x.y.z.zip.sha256 < owncloud-x.y.z.zip
     </code>

5. Download the PGP signature file. The supported format is asc.

6.	Verify the PGP signature.

      <code>
       wget https://download.owncloud.org/community/owncloud-x.y.z.tar.bz2.asc <br>
       wget https://owncloud.org/owncloud.asc <br>
       gpg --import owncloud.asc <br>
       gpg --verify owncloud-x.y.z.tar.bz2.asc owncloud-x.y.z.tar.bz2 <br>
      </code>

7. Extract the archived contents.

    **Tar:**
    <code>
    tar -xjf owncloud-x.y.z.tar.bz2 <br>
    </code>
    
    **Zip:**
    <code>
    unzip owncloud-x.y.z.zip <br>
    </code>

The content is unpacked to an `owncloud` directory. Copy this directory to a destination of your preference. 

8. Run the Apache HTTP server to install ownCloud in your Apache document root.

> **Note:** On HTTP servers, it is recommended to install ownCloud outside of the document root.

   <code>
    cp -r owncloud /path/to/webserver/document-root
   </code>

The path is replaced by the document root of your web server:

   <code>
    cp -r owncloud /var/www
   </code>

# Connect to ownCloud Server using LDAP

The LDAP configuration panel helps to configure server details, and enable its connectivity to users with access.

**Prerequisites:**
Before you begin, ensure that you have enabled the **LDAP user and group backend app** on the Apps page in ownCloud. 

To enable users to connect to the ownCloud server, perform the following steps:
1. In the Admin page, navigate to the LDAP basic settings.  

     ![ldap-server](https://user-images.githubusercontent.com/49917749/56632022-731d0800-6675-11e9-910a-8132fda6c12d.png)

2. In LDAP window, set the following settings under the Server tab:
  1. `Host:` Enter the IP address of the LDAP server.  
  2. `Port:` Set the port number to **8080** to connect to the LDAP server. 
  3. Click **Detect Port**.
  4. `User DN and Base DN:` Enter the name as DN of a user with permissions to do searches in the LDAP directory. Enter the base DN of LDAP, from where all users and groups can be reached.
  5. `Password:` Set the password for the user. For anonymous access, leave the field empty.
3. Click **Test Configuration**.

# Create a New User Account
To provide controlled access to the configurations on the server, create user profiles with assigned privileges, add them to groups, and also assign storage quota for each user.
To create a user account:
1. Open ownCloud server, and login using administrator credentials.
2. In the User administration page, click the dropdown menu beside the account name, and select **Users**.
3. Enter the login name and their initial password.
Login names can contain letters (a-z, A-Z), numbers (0-9), and special characters. The password cannot be the character 0. 
4. Assign users to one or more existing groups or create a new group using **Groups** option.
5. Click **Create**.
After creating the user, the user or the administrator can change the name using the **Full Name** field, if required.
7. Check **Send email to new user** option in the control panel on the lower left sidebar. Enter the new user’s email address, and ownCloud automatically sends a notification with the login information. 

# Connect to ownCloud Server Using a Desktop or Mobile Client 
ownCloud supports availability of client extensions (called Apps) for Windows, OS X, Linux desktops, Android and iOS devices. The desktop clients are available in the [ownCloud web page](https://owncloud.org/install). The apps for mobile devices are available on Google Play and the Apple App Store.

**Prerequisites:**
Before you begin, ensure you have installed the desktop client for your operating system.

To connect to ownCloud server using desktop or mobile client and sync data, follow these steps:
1. Launch the ownCloud desktop client.
2. In the connection wizard, enter the IP address of your server, and click **Next**. 
3. If you did not setup HTTPS support on your server, use `http://` and not `https://`. 
4. In the Server Address field, enter the IP address of the owncloud server.
5. Enter your username and password, and click **Next**.
6. Choose a synchronization option with the server from one of these choices: 
   - Sync everything from server (size)
   - Choose what to sync
  
In addition, choose a synchronization option with the local folder from one of these choices:
   - Keep local data
   - Start a clean sync (Erases the local folder)
  
7. Click **Connect**.
8. After the connection is established, click **Finish** to save the settings.





  



