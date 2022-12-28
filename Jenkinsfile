@Library('pipeline-library-demo')_
// def sayhello(String name){
//    echo "Hello, ${name}."
// }
pipeline {
    agent { label 'maven-label' }

    stages {
        stage('greet') {
            steps {
                sayHello "Ravi"
            }
        }
        stage('prepare') {
            steps {
                git branch: 'main', url: 'https://github.com/quick-abc/maven-sync.git'
            }
        }
        stage('build') {
            steps {
                //sh 'mvn clean deploy'
                sh 'mvn clean deploy org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=quick-abc_sync'
            }
        }
        stage('deploy-dev') {
            steps {
                echo "deploying an appln in devo"
            }
        }
         stage('deploy-stage') {
            steps {
                input 'give an approval'
                echo "deploying an appln in stage"
            }
        }
        stage('deploy-prod') {
            steps {
                input 'give an approval'
                echo "deploying an appln in prod"
            }
        }
    }
}
