
pipeline {
    agent {
        //docker { image 'node:latest' }
        docker { image 'mzegarra/ngbuilder:latest' }
        
    }

    stages {
        stage('Verify') {
            steps {
                sh 'npm run build --prod'
            }
        }
    }
}
