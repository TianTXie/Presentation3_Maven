#Maven Profiles and Properties
-----------------------------
##Maven Profiles
-----------------------
Maven build profiles enable you to build your project using different configurations. Instead of creating two separate POM files, you can just specify a profile with the different build configuration, and build your project with this build profile when needed.

You can read the full story about build profiles in the Maven POM reference under [Profiles](http://maven.apache.org/pom.html#Profiles). Here I will give you a quick overview though.

Maven build profiles are specified inside the POM file, inside the profiles element. Each build profile is nested inside a profile element. Here is an example:
```
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.companyname.project-group</groupId>
  <artifactId>project</artifactId>
  <version>1.0.0</version>

  <profiles>
      <profile>
          <id>test</id>
          <activation>...</activation>
          <build>...</build>
          <modules>...</modules>
          <repositories>...</repositories>
          <pluginRepositories>...</pluginRepositories>
          <dependencies>...</dependencies>
          <reporting>...</reporting>
          <dependencyManagement>...</dependencyManagement>
          <distributionManagement>...</distributionManagement>
      </profile>
  </profiles>

</project>
```
A build profile describes what changes should be made to the POM file when executing under that build profile. This could be changing the applications configuration file to use etc. The elements inside the *profile* element will override the values of the elements with the same name further up in the POM.

Inside the *profile* element you can see a activation element. This element describes the condition that triggers this build profile to be used. One way to choose what profile is being executed is in the *settings.xml* file. There you can set the active profile. Another way is to add *-P profile-name* to the Maven command line. See the profile documentation for more information.

##Maven Properties
You can specify properties in your build files and override them in on the command line. For example you can specify in your pom file that the test should be skipped during the build. This property and others are defined in the following snippet.
```
<properties>
<skipTests>true</skipTests>
<maven.build.timestamp.format>yyyyMMdd-HHmm</maven.build.timestamp.format>
<buildTimestamp>${maven.build.timestamp}</buildTimestamp>
<buildId>${buildType}${buildTimestamp}</buildId>
</properties>
```
On the command line you can override such parameters and demonstrated in the following listing.
```
mvn clean install -DskipTests=false
```

  
  [NEXT](Maven_Project_Templates.md)
