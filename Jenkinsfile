pipeline {
    // master executor should be set to 0
    agent any
    stages {
	stage("Pull Latest Image"){
	    steps{
		bat "docker pull rajasha/selenium-docker"
            }
        }
        stage("Start Grid") {
            steps {
                //sh
                bat "docker-compose up -d hub chrome firefox"
            }
        }
	stage("Run Test") {
	    steps {
                bat "docker-compose up book-flight-module2"
            }
        }	
    }
    post{
        always{
            archiveArtifacts artifacts: 'test-output/**/*.xml'  
            bat "docker-compose down"
        }
    }
}