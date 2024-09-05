pipeline{
    agent any
    stages{
        stage("dependancies install"){
            agent {docker {image 'node'}}
            steps{
                sh 'npm install'
            }
        }
    }
}