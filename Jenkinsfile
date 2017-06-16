pipeline {
    agent { docker 'maven:3-alpine' } 

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Example Build') {
            steps {
                sh 'mvn -B clean verify'
            }
        }
    }
    
}
