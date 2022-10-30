

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                withCredentials([usernameColonPassword(credentialsId: 'root', variable: 'docker')]) {
                    sh ''' docker build -t yogi9949/projectimg:$BUILD_NUMBER   
                    docker push yogi9949/projectimg:$BUILD_NUMBER   
                    docker rmi yogi9949/projectimg:$BUILD_NUMBER   
                    docker run -itd -p 80:80 --name httpd projectimg:$BUILD_NUMBER '''
                       
                  }
            }
        }
    }
}
