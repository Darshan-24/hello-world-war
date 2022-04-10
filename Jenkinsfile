pipeline{
      agent { label 'slave1' }
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
      sh "docker build -t dayanand1991/docwarimage:1.0 ."
      }
      }
       stage('publish'){
                  steps{
                        sh "docker login -u dayananda1991 -p admin@123"
                        sh "docker push dayananda1991/docwarimage:1.0"
                  }
            }
            stage('deploy'){
                  agent { label 'slave1' }
                  steps{
                        sh "docker login -u dayananda1991 -p admin@123"
                        sh "docker pull dayananda1991/docwarimage:1.0"
                       //sh "docker rm -f trail1"
                        sh "docker run -d -p 8085:8080 --name trail1 dayananda1991/docwarimage:1.00"
                  }
            }
      }
    }
