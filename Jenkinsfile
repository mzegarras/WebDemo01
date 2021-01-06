
pipeline {
    agent {
        docker { image 'node:latest' }
    }

    stages {
        stage('Verify') {
            steps {
                sh 'RUN npm run build --prod'
            }
        }
    }
}
