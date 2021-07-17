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
		    bat "mvn pmd:pmd"
			    bat "mvn checkstyle:checkstyle"
			    bat "mvn findbugs:findbugs"
		    }
	    }
 
	}
}
