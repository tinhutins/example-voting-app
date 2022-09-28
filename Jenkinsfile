pipeline {
    agent any
    
    tools {
     mavecn "Maven 3.8.6"
    }
    stages {
        stage('build') {
            steps {
                echo 'compiling worker app'
		dir ('worker'){
                sh ' mvn compile'
		}
            }
        }
        stage('test') {
            steps {
                echo 'Running unit tests'
            }
        }
        stage('package') {
            steps {
                echo 'Packaging worker app'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline for worker is completed.'
        }
    }
    
    
}
