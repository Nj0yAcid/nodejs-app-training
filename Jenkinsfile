pipeline{
    agent{
        docker {
            image 'node:14'
            args '-u root:root'
       }
    }
    stages{
        stage("dependancies install"){
            steps{
                sh 'npm install'
            }
        }
        stage('package'){
            steps{
                sh 'rm -rf my-app-*.tgz || echo ""'
                sh 'npm pack'
            }
        }
        stage("Upload the artifact in JFrog"){
            steps{
            sh 'curl -uadmin:AP8gcgmmset5jeYChTJYDN6XmDd -T \
            my-app-*.tgz "http://ec2-98-80-5-149.compute-1.amazonaws.com:8081/artifactory/nodejs-app/myapp_${BUILD_ID}.tgz"'
            }
        }
    }

    post {
        success {
            emailext (
                to: 'e.vitateka@gmail',
                subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build ${env.JOB_NAME} #${env.BUILD_NUMBER} was successful.\n\nCheck the details here: ${env.BUILD_URL}"
            )
        }
        failure {
            emailext (
                to: 'e.vitateka@gmail.com',
                subject: "Build FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build ${env.JOB_NAME} #${env.BUILD_NUMBER} failed.\n\nCheck the logs: ${env.BUILD_URL}",
                attachLog: true  // Attacher les logs du build pour plus d'informations
            )
        }
    }
    
}
