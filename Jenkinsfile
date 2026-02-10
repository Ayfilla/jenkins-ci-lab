pipeline {
    agent any

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ayfilla/jenkins-ci-lab.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                  echo "Build stage"
                  chmod +x app/app.sh
                  ./app/app.sh
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                  echo "Test stage"
                  chmod +x tests/test.sh
                  ./tests/test.sh
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline SUCCESS"
        }
        failure {
            echo "Pipeline FAILED"
        }
        always {
            cleanWs()
        }
    }
}

