# Setting Up Apache Tomcat for Running a Web Application

This guide will walk you through the process of setting up Apache Tomcat to run a web application. Apache Tomcat is a popular Java-based application server used for hosting Java web applications.

## Prerequisites

Before you begin, ensure you have the following:

1. **Java Development Kit (JDK):** Tomcat is a Java-based application, so you need to have a JDK installed. You can download the latest version of JDK from the [Oracle website](https://www.oracle.com/java/technologies/javase-downloads.html) or use an open-source alternative like OpenJDK.

## Installation and Configuration

1. **Download Tomcat:** Download the latest version of Apache Tomcat from the [official Apache Tomcat website](https://tomcat.apache.org/download-10.cgi).

   ```shell
   wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.92/bin/apache-tomcat-8.5.92.tar.gz

  I am using version 8.5.92 
  
2. **Extract Tomcat:** Extract the downloaded Apache Tomcat archive to a directory of your choice.

   ```shell
   tar -xvfx apache-tomcat-<version>.tar.gz

3. Navigate to following Directory

    ```shell
    cd /home/<user>/apache-tomcat-<version>/bin/

4. Start Tomcat: To start Tomcat, use the following command:

    ```shell
    ./startup.sh

Your Tomcat server will be up and running

5. Navigate to following direectory

    ```shell
    /home/<user>/apache-tomcat-<version>/webapps/host-manager/META-INF/
    
6. You will have context.xml, use your file editor(vim) to delete the following contents in context.xml
   
    ```shell
    <Valve className="org.apache.catalina.valves. RemoteAddrValve="127\. \d+\. \d+\. \d+|::110:0:0:0:0:0:0:1"/>

7. Navigate to following direectory

    ```shell
    /home/<user>/apache-tomcat-<version>/webapps/manager/META-INF/

8. Repeat the same, here also you will have context.xml, go and delete the same content you did before.

   You are doing this to access Tomcat Manager App from diffrent instance(your system), if you need to access it only from the Instance where Tomcat is installed you no need to make these changes.

10. Navigate to following directory

    ```shell
    cd /home/<user>/apache-tomcat-<version>/conf/

11. You will have tomcat-users.xml, add following to it.

     ```shell
    <role rolename="manager-gui"/>
    <role rolename="manager-script"/>
    <role rolename="manager-jmx"/>
    <role rolename="manager-status"/>
    <user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
    <user username="deployer" password="deployer" roles="manager-script" />
    <user username="tomcat" password="s3cret" roles="manager-gui"/>

  To login to Manager App, username and password is "admin", you can modify this if required in the above.

  ## Congrulations, Now you can upload your war file and Deploy.
