what is jenkins 
what is  CI/CD process
Installation of Jenkins
Jenkins Job
Pipelines jobs

## what is jenkins
jenkins is a popular tool for implementing CI/CD pipelines. 
CI/CD pipelines allow developers to automatically build, test, and deploy their code changes, helping them to deliver software faster and with fewer errors

what is CI/CD?
Continious Integration:
when jenkins will pull the code and build the code using maven/other build tools::- automatically

Continious deployment :
when we deploy the code automatically till the production environemnt

Continious delivery
when we deploy till stagging environment and seeks approvals for production environemnt


## Points of Jenkins

#### Continuous integration (CI) and continuous delivery (CD): 
Jenkins is a popular tool for implementing CI/CD pipelines. CI/CD pipelines allow developers to automatically build, test, and deploy their code changes, 
helping them to deliver software faster and with fewer errors.

### Pipeline as code: 
Jenkins supports pipeline as code, which means that the CI/CD pipeline can be defined using code (usually Groovy or YAML). 
This makes it easy to version control the pipeline and reuse it across multiple projects.

### Plugins: Jenkins has a rich ecosystem of plugins that extend its functionality.
There are plugins for almost everything, from building and testing code, to deploying applications, to integrating with other tools and services.

### Distributed builds: 
Jenkins can be configured to run builds on multiple machines, allowing developers to scale their CI/CD pipelines and reduce the build time.

### Security: Jenkins has a number of security features, such as user authentication,
access control, and secure communication, to help organizations protect their CI/CD pipelines and the software they are building.

### Monitoring and reporting: Jenkins provides a number of tools and features to help developers monitor and troubleshoot their CI/CD pipelines, 
including real-time build logs, integration with test results and coverage reports, and trend analysis

### Jenkins Job
Jenkins CI allows developers to ```automate building, testing, and deploying code effortlessly```. Also, it hones the capabilities to handle any build or continuous integration. 
Jenkins Jobs focuses on ```building and testing code continuously so that any changes made in the source code are easily integrated into the build```. 
Best of all, Jenkins makes it easy to catch up on errors quickly, which is otherwise strenuous and time-consuming using manual processes.


## Jobs in Jenkins 

### Freestyle: 
This is the most basic and common job type in Jenkins. It allows users to configure various options and settings for their build, test, and deploy processes.

### Pipeline: 
This job type allows users to define their build, test, and deploy processes as code using Jenkins' pipeline DSL (domain-specific language).

### Multi-configuration: 
This job type allows users to run the same build with different configurations.
Testing Multipe environments, windows/Linux

#### External Job: 
This job type allows users to run jobs outside of Jenkins, such as a script on a remote machine.

#### Folder: 
This job type allows users to organize other Jenkins jobs into a single folder, making it easier to manage and maintain large numbers of jobs.

### Github organization: 
This job type allows users to automatically build and test pull requests and branches from a Github organization.

### Jenkinsfile: 
This job type allows users to define and execute their Jenkins pipeline in a Jenkinsfile.

## Important Plugins in Jenkins

### Git plugin
Provides integration with Git version control system.

### Maven plugin
Provides integration with Apache Maven build tool.

### Pipeline plugin
Allows you to define your build pipeline as code.

### Docker plugin
Provides integration with Docker containers.

### Ansible plugin
Provides integration with Ansible playbook.

### Slack plugin
Allows you to send notifications to Slack channels


### Jenkins installation in Amazon Linux
```bash
mount -o remount,size=5G /tmp/
dnf install java-17-amazon-corretto -y
wget -O /etc/yum.repos.d/jenkins.repo     https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
dnf install jenkins -y
systemctl enable jenkins
systemctl start jenkins
```

- Go with suggested plugin
- Grab the password  /var/jenkins_home/secrets/initialAdminPasswor



#Installation of Jenkins using docker.
docker run -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
Notes:- password will be available during the container creation/spin 

jenkins password locations
cat /var/jenkins_home/secrets/initialAdminPassword #inside the container

#Plugins installation 
Install the suggested plugins 


Jenkins Jobs
#Different types of jobs in jenkins 

FreeStyle Project 
---------------
Usecase:- when you want execute any shell scripts, more lile stopping/starting servers
ssh scripts,backups

Pipelines:- Earlier know as pipelines
---------------------------------------
Run more jobs one after other or parallel builds

Multi-Configruration Project
------------------------------
Testing Multipe environments, windows/Linux

Folders
--------
seperate namespace for different types of projects.

Github Organizations
--------------------
It can scan entire respository of the user Account

Multibranch pipelines
----------------------
It will create seperate pipelines for each branch created in the SCM


 



FreeStyle project
------------------
select Free Style project
Under the Execute shell , Execute the command echo "Hello from jenkins"
Build now



#maven installation
docker exec -it -u root 295b714294c3 /bin/bash :- login to docker as the root user
apt-get update
apt-get install maven



Pipelines jobs vs freeStyle jobs 
--------------
Helps to combines all the free style jobs into single into a single defination as a code
Another different is , pipeline jobs resumes back even if the jenkins got killed whereas freestyle job won't 
Free style jobs dont have clue what was running before/prior 
Durable::- Pipeliness can survicve both planned and unplanned restarts of your jenkins controller
Pausable::- Pipelines can optionally pause stop/wait for human output
Extensible::- Pipelines plugins suports custom extentions to its DSL



