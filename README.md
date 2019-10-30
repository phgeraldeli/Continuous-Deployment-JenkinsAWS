# Continuous-Deployment-JenkinsAWS

Java Application with Continuous Deployment on Elastic beanstalk Service using Jenkins.

## Set up Prerequisites
      * Java8+
      * Maven
  
### Start a Project

##### Access [Quarkus](https://code.quarkus.io/) to start a project

### Initial Setup Jenkins

##### Create Jenkins

- Go to http://aws.amazon.com/ and create a EC2 Instance.
- Connect to your instance with ssh

- Use following command:
```
Install Java8
sudo yum install java-1.8.0

Update
sudo yum update –y

Install Jenkins
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
sudo rpm — import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
sudo yum install jenkins -y

Start Jenkins
systemctl start jenkins.service
systemctl enable jenkins.service

```
- Get AWS EC2 instance IP Address and access IP:8080


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
-commit and push, your jenkins is running.

### Setup Elastic beanstalk instance.

>>> Em construção <<<

### Deploying

>>> Em construção <<<
