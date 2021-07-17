// Declarative //
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
	    stage ('Static Code Analysis'){
		    steps{
		    sh "mvn pmd:pmd"
			    sh "mvn checkstyle:checkstyle"
			    sh "mvn findbugs:findbugs"
		    }
	    }
 
	}
}
