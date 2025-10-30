pipeline {
    agent {
        docker { image 'node:18-alpine' }
    }

    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Archive test reports') {
            steps {
                junit 'reports/junit.xml'
            }
        }
    }

    post {
        success {
            echo '✅ Build succeeded !'
        }
        failure {
            echo '❌ Build failed !'
        }
    }
}
