pipeline {
    agent any
    
    environment {
        
        SCANNER_HOME = tool 'sonarscaner'
    }
   stages {
        stage('Git Checkout') {
            steps {
                git branch: 'latest', url: 'https://github.com/jaiswaladi246/10-Tier-MicroService-Appliction.git'
            }
        }
       stage('adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/adservice/') {
                                 sh "docker build -t gundala22reddy/adservice:latest ."
                                 sh "docker push gundala22reddy/adservice:latest"
								                 sh " docker rmi gundala22reddy/adservice:latest"
                        }
                    }
                }
            }
        }
   }
        
}
