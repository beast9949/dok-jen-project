pipeline {
    agent {
        node {
            label "docker"
        }
    }

    stages {
        stage('docker build') {
            steps {
                 sh '''
                    docker stop httpd
                    docker rm httpd
                    docker build -t yogi9949/project1:$BUILD_NUMBER .
                       
                       '''
            }
        }
        stage('docker run') {
            steps {
                withCredentials([usernameColonPassword(credentialsId: 'root', variable: 'docker')]) {
                    sh '''    
                          
                          docker push yogi9949/project1:$BUILD_NUMBER  
                          docker run -itd -p 80:80 --name httpd yogi9949/project1:11
                          docker rmi yogi9949/project1:$BUILD_NUMBER'''
            }
        } 
        stage('cleaning workspace') {
            steps {
                 cleanWs()
             }
     
        }
      }
    }
}
