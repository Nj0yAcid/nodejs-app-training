pipeline{
    agent any
    stages{
        stage("dependancies install"){
            agent {docker {image 'node:14'}}
            steps{
                sh 'npm install'
            }
        }
    }
}