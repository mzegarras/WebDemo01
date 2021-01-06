
pipeline {
    agent none

    stages {
        stage('Build') {
             agent {
                //docker { image 'node:latest' }
                docker { image 'mzegarra/ngbuilder:latest' }
                
            }
            steps {
                sh '''
                    npm install
                    npm run build 
                    '''
            }

            post{
                success {
                    sh 'ls -lta'
                    zip zipFile: 'dist.zip', archive: true, dir: 'dist/', overwrite: true
                    archiveArtifacts artifacts: 'dist.zip', fingerprint: true, onlyIfSuccessful: true
                    
                }
            }
        }
        
        stage('Docker Build') {
            agent any
            steps {

                script {
                  def props = readProperties file: 'config/dev.env'
                  env.APP = props.APP
                  env.APP_MODULE = props.APP_MODULE
                  env.DOCKER_REPOSITORY= props.DOCKER_REPOSITORY
                }

                sh 'echo  $DOCKER_REPOSITORY/$APP-$APP_MODULE'

                copyArtifacts filter: 'dist.zip',
                              fingerprintArtifacts: true,
                              projectName: '${JOB_NAME}',
                              flatten: true,
                              selector: specific('${BUILD_NUMBER}'),
                              target: 'data';

                unzip zipFile: 'dist.zip', dir: 'data'

                sh "docker build --file ./data/Dockerfile --tag $DOCKER_REPOSITORY/$APP-$APP_MODULE:${BUILD_NUMBER} ."
                sh "docker tag $DOCKER_REPOSITORY/$APP-$APP_MODULE:${BUILD_NUMBER}  $DOCKER_REPOSITORY/$APP-$APP_MODULE:latest"
            }
        }
    }
}
