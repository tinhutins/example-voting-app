pipeline {
    agent any
    
    tools {
     maven "Maven 3.8.6"
    }
    stages {
        stage('build') {
            when {
              changeset "**/worker/**"
	    }
            steps {
                echo 'compiling worker app!'
		dir ('worker'){
                sh ' mvn compile'
		}
            }
        }
        stage('test') {
            when {
              changeset "**/worker/**"
	    }
            steps {
                echo 'Running unit tests'
                dir ('worker'){
                sh 'mvn clean test'
                }  
	  }
        }
        stage('package') {
            when {
	      branch 'master'
              changeset "**/worker/**"
	    }
            steps {
                echo 'Packaging worker app'
                dir ('worker'){
		sh 'mvn package -DskipTests'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline for worker is completed.'
        }
    }
    
    
}
