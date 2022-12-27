pipeline {
    agent any

    tools {
        
        maven "M3"
    }

    stages {
        stage('Build') {
            steps {
               
                git 'https://github.com/jglick/simple-maven-project-with-tests.git'

                
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

            }

            post {
               
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
