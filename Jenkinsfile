
pipeline {
    agent {
        //docker { image 'node:latest' }
        docker { image 'mzegarra/ngbuilder:latest' }
        
    }

    stages {
        stage('Verify') {
            steps {
                sh '''
                    pwd
                    ls -lta pwd
                    npm run build --prod
                    '''
            }
        }
    }
}
