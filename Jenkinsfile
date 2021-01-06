
pipeline {
    agent {
        docker { image 'node:latest' }
    }

    stages {
        stage('Verify') {
            steps {
                sh 'npm install -g @angular/cli && npm cache clean'
                sh 'npm run build --prod'
            }
        }
    }
}
