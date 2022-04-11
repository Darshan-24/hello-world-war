pipeline{
      agent { label 'slave1' }
      environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerpassword')
    }
      stages{
      stage('check out'){
                  steps{
                  sh "rm -rf hello-world-war"
                  sh "git clone https://github.com/Dayanandachari/hello-world-war.git"
                   
                  }
                  }
      stage('build'){
      steps{
      sh "pwd"
      sh "ls"
      sh "cd hello-world-war"
      sh "docker build -t dayanand1991/docker:${BUILD_NUMBER} ."
      }
      }
       stage('publish'){
                  steps{
                        sh "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
                        sh " docker tag dayanand1991/docker:${BUILD_NUMBER} dayanand1991/docker_repo_1991:${BUILD_NUMBER}"
                        sh "docker push dayanand1991/docker_repo_1991:${BUILD_NUMBER}"
                        
                  }
            }
            stage('deploy'){
                  agent { label 'slave1' }
                  steps{
                        sh "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
                        sh "docker pull dayanand1991/docker_repo_1991:${BUILD_NUMBER}"
                        sh "docker rm -f trail1"
                        sh "docker run -d -p 8085:8080 --name trail1 dayanand1991/docker_repo_1991:${BUILD_NUMBER}"
                  }
            }
      }
    }
