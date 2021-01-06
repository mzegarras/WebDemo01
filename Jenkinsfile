
pipeline {
    agent {
        //docker { image 'node:latest' }
        docker { image 'mzegarra/ngbuilder:latest' }
        
    }

    stages {
        stage('Verify') {
            steps {
                sh '''
                    echo $pwd
                    ls -lta $pwd
                    ls -lta
                    npm run build --prod
                    '''
            }
        }
    }
}
