pipeline {
    agent any
    
    tools {
     maven "Maven 3.8.6"
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
                dir ('worker'){
                sh 'mvn clean test'
                }  
	  }
        }
        stage('package') {
            steps {
                echo 'Packaging worker app'
                dir ('worker'){
		sh 'mvn package -DskipTests'
                }
            }
        }
    }
    
    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            echo 'Pipeline for worker is completed.'
        }
    }
    
    
}
