pipeline {
    agent { docker 'undera/taurus' } 

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        

        stage('Example Build') {
            steps {
                
                sh 'ls'
              sh 'bzt quick_test.yml'
            }
        }
    }
    
}
