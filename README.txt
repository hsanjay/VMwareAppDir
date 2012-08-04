Demostration of SpringIntegraionSamples on VMware Application Directory
=======================================================================

What is it?
-----------
Demostrating setup and execution of SpringIntegraionSamples on VMware Application Directory. By way of demostrating a catalog of reuseable artifacts have developed.

Objective
----------
 - To run the SpringIntegrationSamples using Apache Maven and JDK 6.x.
 - Use external web server instead of default maven's inbuilt web server.

SetUp
-----
Spring_server - This will host Apache Maven, JDK and Spring Integration Samples. This VM will be used to build and execute the samples.

Spring_webserver - This will host tc-server on which spring intergration sample war would be deplpoyed.

Getting Started
---------------
On Spring_server VM
--------------------
01) IntializationScript01_INSTALL will install ftp and curl tools. We will be using curl to upload the war file built on to tc-server webapps folder.

02) Oracle_Java_JDK_INSTALL will install JDK 6.x, this is needed for compiling spring integratio samples.

03) Apache_Maven_INSTALL will install maven 3.0.4.

04) SpringIntegrationSamples_INSTALL will download and extract it in to a workspace.

05) SpringIntegrationSamples_CONFIGURE will build the samples using Maven and JDK. Hence there is dependency on Maven and JDK. The build artifact (war file) is uploaded to tc-server using curl for deployment.

06) There are two custom reusable scripts added
	- ConsoleAccess: which will allow you to change the root password so that we can access the console.
	- Spring_Integration_HTTP_Sample: This will execute the samples.

On Spring_webserver VM
-----------------------
01) IntializationScript01_INSTALL will install ftp and curl tools. We will be using curl to upload the war file built on to tc-server webapps folder.

02) IntializationScript01_CONFIGURE will configure ftp server.

03) IntializationScript01_START will ftp server.

04) vFabric_tc_serve_INSTALL/CONFIGURE/START will install and start tc-server.

05) WarINSTALL will deploy war and restart tc-server. This activity is dependent on SpringIntegrationSamples_CONFIGURE.

06) There are two custom reusable scripts added
	- ConsoleAccess: which will allow you to change the root password so that we can access the console.
	- Tomcat_Users: which will configure tomcat user. This script is added just before tc-server_START.

Reusable Artifacts in Catalog
-----------------------------
- Services
	- Apache Maven
	- Ftp Server
	- Oracle JDK
- Tasks
	- Tomcat_Users
	- ConsoleAccess
