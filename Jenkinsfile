pipeline {
    agent any
    stages {
        stage('checkout') { 
            steps {
              sh "git clone https://github.com/Darshan-24/hello-world-war"
            }
        }
stage('build') { 
            steps {
              sh "mvn clean package"
            }
        }  
        stage('deploy') {
            steps {            
          sh "cp /var/lib/jenkins/workspace/firstpipelinejob/target/hello-world-war-1.0.0.war /opt/apache-tomcat-9.0.60/webapps/"
            }
        }

