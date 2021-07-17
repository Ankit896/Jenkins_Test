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
        stage('Static code analysis') {
            steps {
                //Use parallel method for parallel processing
                parallel(
                    'Static code analysis' : {
                        gradlew 'check -x test'

                        //You can specify the current directory with the dir method
                        dir(reportDir) {
                            step([
                                $class: 'CheckStylePublisher',
                                pattern: "checkstyle/*.xml"
                            ])
                            step([
                                $class: 'FindBugsPublisher',
                                pattern: "findbugs/*.xml"
                            ])
                            step([
                                $class: 'PmdPublisher',
                                pattern: "pmd/*.xml"
                            ])
                            step([
                                $class: 'DryPublisher',
                                pattern: "cpd/*.xml"
                            ])
                
                            archiveArtifacts "checkstyle/*.xml"
                            archiveArtifacts "findbugs/*.xml"
                            archiveArtifacts "pmd/*.xml"
                            archiveArtifacts "cpd/*.xml"
                        }
                    },
    }
}

