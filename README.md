# Continuous-Deployment-JenkinsAWS

Continuous Deployment with Jenskins on Elastic beanstalk Service on AWS.

## Set up Prerequisites
      * Jenkins running
      * AWSEB Deployment Jenkins Plugin
      * Java8+
      * Maven
  
### Start a Project

##### Access [Quarkus](https://code.quarkus.io/) to start a project

### Initial Setup Jenkins

##### On the Jenkins dashboard, click on Manage Jenkins and select Manage Plugins. Click on the Avaiable tab and install then Restart:
      * Github API Plugin
      * GitHub Plugin
      * AdoptOpenJDK installer Plugin

##### Configure Maven and JDK
     
- Go to Manage Jenkins -> Global Tool Configuration. 
- On **Maven Configuration** select **Use Maven Default configuration**
- On **JDK** set **Name: jdk_1.8.0** and **install with adoptopenjdk.net**

##### On the project create Jenkinsfile
```
pipeline {
    
    agent any
    tools {
        jdk 'jdk_1.8.0'
        maven 'Maven'
    }

    stages {
        stage('Compilando') {
            steps {
                sh 'mvn clean install -DskipTests' 
            }
        }

        stage('Testando') {
            steps {
                sh 'mvn verify'
            }
        }

    }
}
```
- then commit and push, your jenkins is running.
