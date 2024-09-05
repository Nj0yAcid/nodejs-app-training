pipeline{
    agent{
       docker { image 'node:14' }
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
    }
}