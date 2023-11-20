How to Download and Install DSpace 7.4 Back End on Ubuntu 22.04
===============================================================

Introduction
------------

Welcome to Reflims! In this hands-on video tutorial, we will learn how to download and install DSpace 7.4 back end on Ubuntu 22.04. In our previous video, we covered the installation of DSpace 7.4 front end on the same system, so now it's time to tackle the back end installation. Let's get started!

Updating and Upgrading the System
---------------------------------

The first step is to update and upgrade our system. Open your terminal and run the following commands:

`sudo apt-get update` `sudo apt-get upgrade`

Installing Prerequisites
------------------------

Next, we need to install some prerequisites: OpenJDK, Apache Maven, and PostgreSQL. Run the following commands:

`sudo apt-get install openjdk-11-jdk maven` `sudo apt-get install postgresql`

Configuring PostgreSQL
----------------------

Now, we need to configure PostgreSQL. First, enter the PostgreSQL directory:

`cd /etc/postgresql/`

Edit the configuration file:

`sudo nano postgresql.conf`

Add the following line at the end of the file to allow DSpace backend:

`host all all 0.0.0.0/0 trust`

Save the file and exit. Restart PostgreSQL:

`sudo systemctl restart postgresql`

Building DSpace Back End
------------------------

It's time to build the DSpace back end. Download the DSpace 7.4 source package and navigate to the build directory. Unpack the package and go into the build directory:

`cd /path/to/dspace-source/build`

Run the following command to start the build process:

`sudo mvn package`

This may take some time to complete. Once the build is successful, you can proceed to the next step.

Installing Tomcat
-----------------

Now, we need to install Tomcat. Run the following command to install the default Tomcat package:

`sudo apt-get install tomcat9`

Next, we need to set the environment variables. Open the Tomcat configuration file:

`sudo nano /etc/default/tomcat9`

Find the line starting with "JAVA\_HOME" and set the path to your Java installation. Save the file and exit.

Copying DSpace Web Apps
-----------------------

Copy the DSpace web apps to the Tomcat web apps directory:

`sudo cp -R /path/to/dspace-source/dspace/target/dspace-7.4 /var/lib/tomcat9/webapps/`

Configuring DSpace
------------------

Finally, we need to configure DSpace. Enter the DSpace installation directory:

`cd /var/lib/tomcat9/webapps/dspace-7.4/bin/`

Create the DSpace administrator:

`sudo ./dspace create-administrator`

Follow the prompts to provide the necessary information for the administrator account.

Starting the System
-------------------

Restart all the services:

`sudo systemctl restart postgresql` `sudo systemctl restart tomcat9`

That's it! You have successfully downloaded and installed DSpace 7.4 back end on Ubuntu 22.04. Now you can connect the back end to the locally installed front end and start using DSpace.

