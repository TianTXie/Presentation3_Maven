
#Maven Environment Setup

Maven is Java based tool, so the very first requirement is to have JDK installed on your machine.


 [<i class="icon-file"></i>System Requirement](#system-requirement)  
 
  [<i class="icon-file"></i>Set Up Maven](#set-up-maven)  
  

##System Requirement
     
 Items     | Requirement
-------- | ---
JDK|1.5 or above.
Memory|no minimum requirement.
Disk Space|	no minimum requirement.
Operating System|no minimum requirement.

  
 
##Set Up Maven
Let us follow the steps to set up Maven on our machine: 

##Step 1 - Install Java
If you do not have Java installed, install the Java Software Development Kit (SDK) from http://www.oracle.com/technetwork/java/javase/downloads/index.html. We are assuming Java 1.7.0_75 as installed version here. 

Then set the JAVA_HOME environment variable to point to the base directory location where Java is installed on your machine. For example:

 OS     | Output
-------- | ---
Windows|Set the environment variable JAVA_HOME to C:\Program Files\Java\jdk1.7.0_75
Mac|export JAVA_HOME=/Library/Java/Home


Then, append Java compiler location to System Path.
 OS     | Output
-------- | ---
Windows|Append the string ;C:\Program Files\Java\jdk1.7.0_75\bin to the end of the system variable, Path.
Linux|export PATH= \$PATH:$JAVA_HOME/bin/
Mac|not required

##Step 2. Download Maven archive
Download Maven 3.3.3 from http://maven.apache.org/download.cgi


OS     | Archive name
-------- | ---
Windows|apache-maven-3.3.3-bin.zip
Linux|apache-maven-3.3.3-bin.tar.gz
Mac|apache-maven-3.3.3-bin.tar.gz


##Step 3: Extract the Maven archive

Extract the archive, to the directory you wish to install Maven 3.3.3. The subdirectory apache-maven-3.3.3 will be created from the archive.  


 OS     | Location (can be different based on your installation)
-------- | ---
Windows|C:\Program Files\Apache Software Foundation\apache-maven-3.3.3
Linux|/usr/local/apache-maven
Mac|/usr/local/apache-maven

##Step 4: Set Maven environment variables
Add M2_HOME, M2, MAVEN_OPTS to environment variables.

 OS     | Output
-------- | ---
Windows|Set the environment variables using system properties. 1. M2_HOME=C:\Program Files\Apache Software Foundation\apache-maven-3.3.3 2. M2=%M2_HOME%\bin 3. MAVEN_OPTS=-Xms256m -Xmx512m
Linux|Open command terminal and set environment variables. 1. export M2_HOME=/usr/local/apache-maven/apache-maven-3.3.3   2. export M2=$M2_HOME/bin   3. export MAVEN_OPTS=-Xms256m -Xmx512m
Mac|Open command terminal and set environment variables. 1. export M2_HOME=/usr/local/apache-maven/apache-maven-3.3.3  2. export M2=$M2_HOME/bin  3. export MAVEN_OPTS=-Xms256m -Xmx512m


##Step 5: Add Maven bin directory location to system path

Now append M2 variable to System Path

 OS     | Output
-------- | ---
Windows|Append the string ;%M2% to the end of the system variable, Path.
Linux|export PATH=\$M2:$PATH
Mac|export PATH=\$M2:$PATH


##Step 6: Verify Maven installation

Now open console, execute the following mvn command.

 OS     | Command
-------- | ---
Windows|c:\> mvn --version
Linux|$ mvn --version
Mac|machine:~ joseph$ mvn --version


Finally, verify the output of the above commands, which should be something as follows:
![Alt text](/picture/maven_setup.png)

[NEXT](Maven POM Files.md)

