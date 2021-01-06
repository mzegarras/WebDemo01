
pipeline {
    agent {
        docker { image 'node:latest' }
    }

    stages {
        stage('Verify') {
            steps {
                sh 'npm run build --prod'
            }
        }
    }
}
