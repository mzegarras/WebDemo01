
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
                    zip zipFile: 'dist.zip', archive: false, dir: 'dist'
                    archiveArtifacts artifacts: 'dist.zip', fingerprint: true, onlyIfSuccessful: true
                }
            }
        }
    }
}
