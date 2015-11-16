#Maven Project Templates
-------------------

## What is archetype
--------------
Archetype is a Maven plugin whose task is to create a project structure as per its template. We are going to use quickstart archetype plugin to create a simple java application here.
##Using project Template
-----------
Maven provides users,a very large list of different types of project templates (1000+ in numbers) using concept of Archetype. Maven helps users to quickly start a new java project using following command
```
mvn archetype:generate
```
When you execute this mvm command, Maven will start processing and will ask to choose required archetype.
```
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] >>> maven-archetype-plugin:2.4:generate (default-cli) > generate-sources@ standalone-pom >>>
[INFO]
[INFO] <<< maven-archetype-plugin:2.4:generate (default-cli) < generate-sources@ standalone-pom <<<
[INFO]
[INFO] --- maven-archetype-plugin:2.4:generate (default-cli) @ standalone-pom ---
[INFO] Generating project in Interactive mode
[WARNING] No archetype found in remote catalog. Defaulting to internal catalog
[INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.
archetypes:maven-archetype-quickstart:1.0)
Choose archetype:
1: internal -> org.apache.maven.archetypes:maven-archetype-archetype (An archetype which contains a sample archetype.)
2: internal -> org.apache.maven.archetypes:maven-archetype-j2ee-simple (An archetype which contains a simplifed sample J2EE application.)
3: internal -> org.apache.maven.archetypes:maven-archetype-plugin (An archetypewhich contains a sample Maven plugin.)
4: internal -> org.apache.maven.archetypes:maven-archetype-plugin-site (An archetype which contains a sample Maven plugin site.
      This archetype can be layered upon an existing Maven plugin project.)
5: internal -> org.apache.maven.archetypes:maven-archetype-portlet (An archetype which contains a sample JSR-268 Portlet.)
6: internal -> org.apache.maven.archetypes:maven-archetype-profiles ()
7: internal -> org.apache.maven.archetypes:maven-archetype-quickstart (An archetype which contains a sample Maven project.)
8: internal -> org.apache.maven.archetypes:maven-archetype-site (An archetype which contains a sample Maven site which demonstrates
      some of the supported document types like APT, XDoc, and FML and demonstrates how
      to i18n your site. This archetype can be layered upon an existing Maven project.)
9: internal -> org.apache.maven.archetypes:maven-archetype-site-simple (An archetype which contains a sample Maven site.)
10: internal -> org.apache.maven.archetypes:maven-archetype-webapp (An archetype
 which contains a sample Maven Webapp project.)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 7:
```
Press Enter to choose to default option(7: maven-archetype-quickstart). Maven will ask for project detail. Enter project detail as asked.Press Enter if default value is provided. You can override them by entering your own value.
```
Define value for property 'groupId': : com.companyname.project-group
Define value for property 'artifactId': : project
Define value for property 'version': 1.0:
Define value for property 'package': com.companyname.project-group
Y:
```
Now Maven will start creating project structure and will display the following:
```
[INFO] -------------------------------------------------------------------------
---
[INFO] Using following parameters for creating project from Old (1.x) Archetype:
 maven-archetype-quickstart:1.1
[INFO] -------------------------------------------------------------------------
---
[INFO] Parameter: groupId, Value: com.companyname.project-group
[INFO] Parameter: packageName, Value: com.companyname.project-group
[INFO] Parameter: package, Value: com.companyname.project-group
[INFO] Parameter: artifactId, Value: project
[INFO] Parameter: basedir, Value: .\MVN
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] project created from Old (1.x) Archetype in dir: .\MVN\project
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 02:29 min
[INFO] Finished at: 2015-11-15T12:18:02+05:30
[INFO] Final Memory: 16M/247M
[INFO] ----------------------------------------------------------------------
```
Now go to **./MVN** directory. You'll see a java application project created named **project** which was given as artifactId at the time of project creation.

##
  
  [NEXT](Maven_Create&Build Project.md)
