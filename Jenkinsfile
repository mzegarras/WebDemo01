
pipeline {
    agent {
        //docker { image 'node:latest' }
        docker { image 'mzegarra/ngbuilder:latest' }
        
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                    npm install
                    npm run build 
                    '''
            }

            post{
                success {
                    archiveArtifacts artifacts: 'dist/', fingerprint: true, onlyIfSuccessful: true
                }
            }
        }
    }
}
