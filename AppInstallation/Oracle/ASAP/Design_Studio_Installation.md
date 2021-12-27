https://docs.oracle.com/en/industries/communications/design-studio/7.4.2/install-guide/installing-prerequisite-software1.html#GUID-2ECEC6A7-A6B1-46A1-A3DF-E0B02E325385


### 1- Install Eclipse

### 2- Download the Java SE JDK
http://www.oracle.com/technetwork/java/javase/downloads/index.html

### 3- extract Oracle Enterprise Pack for Eclipse in eclipse directory

### 4- Copying Java Runtime Environment into Oracle Enterprise Pack for Eclipse
```
Locate the Java SE SDK installation folder.

The Java self-installing executable file defines the default installation location as c:\Program Files\Java.

Copy the jre1.8n folder (for example, jre1.8.0_121) into the Eclipse_Home folder, where Eclipse_Home is the directory in which Oracle Enterprise Pack for Eclipse is installed.
The jre1.8n folder must be copied to the same location where the eclipse.exe file is saved.

Rename the jre1.8n folder to jre.
```
### 5- Configuring Eclipse Startup Properties

eclipse.ini:
```
-startup
plugins/org.eclipse.equinox.launcher_1.5.0.v20180512-1130.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_64_1.1.700.v20180518-1200
-showsplash
org.eclipse.platform
--launcher.defaultAction
openFile
--launcher.appendVmargs
-vmargs
-XX:NewRatio=5
-XX:+UseAdaptiveSizePolicy
-XX:+UseParallelGC
-Xms128m
-Xmx1024m
-Dsun.lang.ClassLoader.allowArraySyntax=true
```
### 6- Verifying the Eclipse Installation
open eclipse and check version in (help>about )

### 7- Installing the Business Intelligence, Reporting, and Charting Feature
```
Help > Install New Software
-In the Work with field, click the menu and select the following update site:

Photon - http://download.eclipse.org/releases/photon

A list of features available from the site appears.

-Select Business Intelligence, Reporting and Charting.

-Click Next.

The Install Details dialog box appears.

-Review the installation details.

-Click Next.

The Review Licenses dialog box appears.

-Review and accept the license agreement.

-Click Finish.

-When prompted, click Yes to restart Eclipse.
```
### 8- Installing the Graphical Editing Framework Zest Visualization Toolkit Feature
```
Open the Oracle Enterprise Pack for Eclipse application.

From the Help menu, select Install New Software.

The Install dialog box appears.

In the Work with field, enter the following:

http://download.eclipse.org/tools/gef/updates/legacy/releases/

Press the Enter key.

Expand GEF (Graphical Editing Framework) and select Zest.

Click Next and accept the terms of the license agreement.

Click Finish.

Restart Eclipse.
```

### 9- Download Design Studio
https://edelivery.oracle.com/

