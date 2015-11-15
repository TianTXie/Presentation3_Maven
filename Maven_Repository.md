
#Maven Repository and Dependency Search

In this part, we are going to talk about maven repository and dependency search in the following sequences: 

 [<i class="icon-file"></i>What is a Maven Repository?](#what-is-a-maven-repository?)  

  [<i class="icon-file"></i>Local repository](#local-repository)  

  [<i class="icon-file"></i>Central repository](#central-repository)  

    [<i class="icon-file"></i>Remote repository](#remote-repository)  

 [<i class="icon-file"></i>Maven Dependency Search Sequence](#maven-dependency-search-sequence)  



    

##What is a Maven Repository?

Maven repositories are directories of packaged JAR files with extra meta data. The meta data are POM files describing the projects each packaged JAR file belongs to, including what external dependencies each packaged JAR has. It is this meta data that enables Maven to download dependencies of your dependencies recursively, until the whole tree of dependencies is download and put into your local repository.

Maven repositories are covered in more detail in the Maven Introduction to Repositories, but here is a quick overview.

Maven has three types of repository:     

- Local repository
- Central repository
- Remote repository

Maven searches these repositories for dependencies in the above sequence. First in the local repository, then in the central repository, and third in remote repositories if specified in the POM.

Here is a diagram illustrating the three repository types and their location:
 ![Alt text](/picture/maven_repositories.png)


##Local Repository
Maven local repository is a folder location on your machine. It gets created when you run any maven command for the first time.

Maven local repository keeps your project's all dependencies (library jars, plugin jars etc). When you run a Maven build, then Maven automatically downloads all the dependency jars into the local repository.It helps to avoid references to dependencies stored on remote machine every time a project is build.

Maven local repository by default get created by Maven in %USER_HOME% directory. To override the default location, mention another path in Maven settings.xml file available at %M2_HOME%\conf directory.

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 
   http://maven.apache.org/xsd/settings-1.0.0.xsd">
      <localRepository>C:/MyLocalRepository</localRepository>
</settings>

```
When you run Maven command, Maven will download dependencies to your custom path.

##Central Repository
Maven central repository is repository provided by Maven community. It contains a large number of commonly used libraries.

When Maven does not find any dependency in local repository, it starts searching in central repository using following URL: http://repo1.maven.org/maven2/

**Key concepts** of Central repository

- This repository is managed by Maven community.

- It is not required to be configured.

- It requires internet access to be searched.

To browse the content of central maven repository, maven community has provided a URL: http://search.maven.org/#browse. Using this library, a developer can search all the available libraries in central repository.

##Remote Repository
Sometime, Maven does not find a mentioned dependency in central repository as well then it stopped build process and output error message to console. To prevent such situation, Maven provides concept of **Remote Repository** which is developer's own custom repository containing required libraries or other project jars.

For example, using below mentioned POM.xml,Maven will download dependency (not available in central repository) from Remote Repositories mentioned in the same pom.xml.

```
<project xmlns="http://maven.apache.org/POM/4.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>
   <groupId>com.companyname.projectgroup</groupId>
   <artifactId>project</artifactId>
   <version>1.0</version>
   <dependencies>
      <dependency>
         <groupId>com.companyname.common-lib</groupId>
         <artifactId>common-lib</artifactId>
         <version>1.0.0</version>
      </dependency>
   <dependencies>
   <repositories>
      <repository>
         <id>companyname.lib1</id>
         <url>http://download.companyname.org/maven2/lib1</url>
      </repository>
      <repository>
         <id>companyname.lib2</id>
         <url>http://download.companyname.org/maven2/lib2</url>
      </repository>
   </repositories>
</project>
```

##Maven Dependency Search Sequence

When we execute Maven build commands, Maven starts looking for dependency libraries in the following sequence:

**Step 1** - Search dependency in local repository, if not found, move to step 2 else if found then do the further processing.

**Step 2** - Search dependency in central repository, if not found and remote repository/repositories is/are mentioned then move to step 4 else if found, then it is downloaded to local repository for future reference.

**Step 3** - If a remote repository has not been mentioned, Maven simply stops the processing and throws error (Unable to find dependency).

**Step 4** - Search dependency in remote repository or repositories, if found then it is downloaded to local repository for future reference otherwise Maven as expected stop processing and throws error (Unable to find dependency).
