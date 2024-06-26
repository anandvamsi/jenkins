Jenkins Pipeline is a suite of plugins that supports implementing and integrating continuous delivery pipelines into Jenkins

Prerequistiess
Jenkins 2.x or later
Pipeline plugin, [2] which is installed as part of the "suggested plugins" 

Defining pipeliness
Both Declarative
Scripted Pipeline
are DSLs [1] to describe portions of your software delivery pipeline. Scripted Pipeline is written in a limited form of Groovy syntax.


Methods Pipeline implemenation 
1. Through the classic UI - you can enter a basic Pipeline directly in Jenkins through the classic UI.
2. SCM - you can write a Jenkinsfile manually, which you can commit to your project’s source control repository. [3]


Best practise
It is generally considered best practice to define the Pipeline in a Jenkinsfile which Jenkins will then load directly from source control.


### simple pipeline
```bash

pipeline {-------- TOP LEVEL
    agent any ------------- WHERE TO BUILD
    stages {
        stage('Stage 1') {----------- SECTION where work tasks are mentioned.
            steps {
                echo 'Hello world!' -------------WHAT TO BUILD
            }
        }
    }
}
```

## Agent
The agent directive can take different forms:

agent any: This directive allows the pipeline to run on any available agent. Jenkins will select an available agent to execute the pipeline based on its availability and workload.
agent none: This directive is used when the pipeline does not need to run on any agent. It's typically used for declarative pipelines that are only triggered manually or by external events.
agent {...}: You can specify a specific agent or label to run the pipeline. For example:
agent { label 'linux' }: Runs the pipeline on an agent with the label 'linux'.
agent { docker { image 'maven:3.6.3' } }: Runs the pipeline inside a Docker container with the specified image.


Notes:
agent instructs Jenkins to allocate an executor (on any available agent/node in the Jenkins environment) and workspace for the entire Pipeline.

##Example 2

Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}



###String interpolation
def singlyQuoted = 'Hello'
def doublyQuoted = "World"


def username = 'Jenkins'
echo 'Hello Mr. ${username}'
echo "I said, Hello Mr. ${username}"


###Using environment variables
BUILD_ID ::-The current build ID, identical to BUILD_NUMBER for builds created in Jenkins versions 1.597+
JOB_NAME ::-Name of the project of this build, such as "foo" or "foo/bar

pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
}



##Setting environment variables
Using the environment directive

Declarative Pipeline supports an environment directive

Example
pipeline {
    agent any
    environment { 
        CC = 'clang'
    }
    stages {
        stage('Example') {
            environment { 
                DEBUG_FLAGS = '-g'
            }
            steps {
                sh 'printenv'
            }
        }
    }
}

Notes:

An environment directive used in the top-level pipeline block will apply to all steps within the Pipeline.
An environment directive defined within a stage will only apply the given environment variables to steps within the stage.



###Handling credentials
Pipeline syntax has the credentials() helper method (used within the environment directive) which supports secret text, username and password, as well as secret file credentialsyumn


pipeline {
    agent {
        // Define agent details here
    }
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
    stages {
        stage('Example stage 1') {
            steps {
                // 
            }
        }
        stage('Example stage 2') {
            steps {
                // 
            }
        }
    }
}

Notes::
These credentials would have been configured in Jenkins with their respective credential IDs
jenkins-aws-secret-key-id and jenkins-aws-secret-access-key.




###Handling parameters
Declarative Pipeline supports parameters out-of-the-box, allowing the Pipeline to accept user-specified parameters at runtime via the parameters directive.

pipeline {
    agent any
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
    stages {
        stage('Example') {
            steps {
                echo "${params.Greeting} World!"
            }
        }
    }
}



pipeline {
    agent none 
    stages {
        stage('Example Build') {
            agent { docker 'maven:3-alpine' } 
            steps {
                echo 'Hello, Maven'
                sh 'mvn --version'
            }
        }
        stage('Example Test') {
            agent { docker 'openjdk:8-jre' } 
            steps {
                echo 'Hello, JDK'
                sh 'java -version'
            }
        }
    }
}


Notes:
Defining agent none at the top-level of the Pipeline ensures that an Executor will not be assigned unnecessarily. Using agent none also forces each stage section to contain its own agent section.
Execute the steps in this stage in a newly created container using this image.
Execute the steps in this stage in a newly created container using a different image from the previous stage





References
https://jenkins.io/doc/book/pipeline/syntax/
https://medium.com/@weblab_tech/how-to-publish-artifacts-in-jenkins-f021b17fde71
