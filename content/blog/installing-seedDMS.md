---
title: Installation of Seed DMS
date: 2019-07-31T12:02:56
excerpt: Seed DMS is open sourse free Document Management System. It offers various features to user like creating full index for files, Managing Users repective to their Group. Apart from this, it helps user to have a complete statistics of files uploaded by every user, Whether it is about consuming usage by files or making changes to file after uploading. 
---

Seed DMS is open sourse free Document Management System. It offers various features to user like creating full index for files, Managing Users repective to their Group. Apart from this, it helps user to have a complete statistics of files uploaded by every user, Whether it is about consuming usage by files or making changes to file after uploading. You can download SeedDMS directly by clicking [Here](https://sourceforge.net/projects/seeddms/files/)

## Steps to Install SeedDMS

1. Download the folder from this [Link](https://sourceforge.net/projects/seeddms/files/)


2. Extract the folder directly to the root directory of server(Example in Xampp software root directory is xampp/htdocs/ . If you are using LAMP in linux then extract to directory /var/www/html/)


3. Now start the Server


4. Open from the root folder of server i.e. SeedDMS51x/seeddms-5.1.12/install/install.php


**NOTE** SeedDMS5.1.12 is the version which I had used while installling


5. After opening this path. It will show an error to create a file named ‘ENABLE_INSTALL_TOOL’ Note: The file does’nt have any kind of extension.


6. Create that file in folder named ‘conf’ which will be present on main path of the software (Use command `$ touch ENABLE_INSTALL_TOOL`)


7. Then run the file again(install.php)


8. It will set your home directory automatically


9. If the home directory is not got changed and errors are showing on the screen. Do some customizations


10. Open the file conf/settings.xml change the root directory in this small file everywhere you see and change database credentials to yours.


11. It is recomended to create database(If you are creating it in mysql then change the sqlite to mysql)


12. Then run the install.php file(Location: seeddms51x/seeddms-5.1.12/install/install.php)


13. Your installation will be started and completed soon


**Note:** In case you are unable to open install.php file even after making changes to settings.xml file then you have issue with server


14. Now delete the file conf/ENABLE_INSTALL_TOOL


15. You will automatically be redirected to the login portal


16. Use `admin` and `admin` as defalut username and password if you not set it earlier


17. Boom! You are done with the installation 🙂


### If you have any other error or need any help. I would be happy to help you.