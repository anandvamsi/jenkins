what is Maven
How to install Maven


Maven? what is need maven
-------
Maven is a build tool, under the Apache Licence.
Maven also helps in creating reports, documentation,Packaging 

Maven solves deps(jar files), thirdparty libs of the java project.
- mysql jars, selemium jars

what Maven solves:

problem 1:
without Maven we need to download all the jars from different websites and attach to the project
which is a manual tasks

problem2:-
if we want to upgrade the jars/lib we need to remove all the existing jars and download the latest
jars from different websites

Solution
------------
Above problems are solved by integrating maven as the part of the project which will downlod
deps/libs








pom.xml::- Two important sections of Pom.xml is the mention the deps and Package name
- deps
- plugins

## Maven commands
```bash
mvn clean install
```
- Clean: Removes the target directory.
- Compilation: Compiles the source code files (.java files) found in the project's source directory (src/main/java) into bytecode (.class files).
- Testing: Executes any tests configured in the project (usually located in the src/test/java directory).
- Packaging: Packages the compiled classes, along with any required resources, into an archive file (JAR, WAR, etc.), depending on the project's packaging configuration in its pom.xml file.
- Installation: Installs the generated artifact(s) into the local Maven repository.

```bash
mvn package
```
mvn clean install: Cleans the project, builds it, and installs the resulting artifacts into the local Maven repository for use in other projects.
mvn package: Cleans the project, builds it, and packages the resulting artifacts into an archive file, but does not install the artifacts into the local Maven repository.

- need to mention the dependencies
  - Group id:- com.anand
  - Artifactid :- demo
  - Package:- com.anand.demo.web
  
  whenever we work with maven, we need to make sure we do have internet do downloads the deps, for the first time all the deps are downloaded from internet
  and caches in the local reposiotry 
  But change in version/Upgration of the jar
  
