
# Maven Job.

### Install git and maven in the jenkin server
```bash
yum install git -y
cd /opt ; wget https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz
unzip apache-maven-3.9.6-bin.tar.gz
mv apache-maven-3.9.6-bin maven
```


### Install and configure Maven plugin in Jenkins UI
Navigate to Jenkins Plugin Install the Plugin "MavenIntergration" this will create a new job type "Maven"
In the jenkins, Navigate Dashboard--> ManageJenkins-->Tools--> Maven ; Maven section, mention the home path of Maven "/opt/maven"
provide the gitpath "/usr/bin/git"

### Create a new Maven Job
In the Git repository mention the giturl and under the Maven section
- Root POM : pom.xml
- Goals and options :- clean install
Note::  clean install means it will clean old builds and install means it packages a new build

### Trigger build



