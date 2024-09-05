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
                sh 'npm pack'
            }
        }
        stage("Upload the artifact in JFrog"){
            sh 'curl -uadmin:AP8gcgmmset5jeYChTJYDN6XmDd -T \
            my-app-*.tgz "http://ec2-54-167-127-179.compute-1.amazonaws.com:8081/artifactory/nodejs-app/myapp_${BUILD_ID}"'
        }
    }
}