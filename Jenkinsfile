pipeline{
    agent any
    
    stages{
        stage("dependancies install"){
            agent {docker {image 'node:14'} args '-u root:root'}
            steps{
               // sh 'sudo chown -R 995:993 "/.npm'
                sh 'npm install'
            }


        }
    }
}