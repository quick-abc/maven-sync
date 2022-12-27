pipeline {
    agent { label 'maven-label' }

    stages {
        stage('prepare') {
            steps {
                git branch: 'main', url: 'https://github.com/quick-abc/maven-sync.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean deploy'
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
