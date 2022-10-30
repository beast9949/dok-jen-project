

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                 sh '''docker build -t yogi9949/project1:$BUILD_NUMBER .
                       '''
                withCredentials([usernameColonPassword(credentialsId: 'root', variable: 'docker')]) {
                    sh '''    
                          docker push yogi9949/project1:$BUILD_NUMBER  
                          docker rmi yogi9949/project1:$BUILD_NUMBER'''
                  }
            }
        }
    }
}
