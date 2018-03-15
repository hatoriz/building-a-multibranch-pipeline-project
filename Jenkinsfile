pipeline {
    agent{
        node{
            label 'macbook'
        }

        environment {
            PATH = "/usr/local/bin:$PATH;"
        }

        docker{
            image 'node:6-alpine'
            args '-p 3000:3000 -p 5000:5000'
        }
    }

    environment {
        CI = 'true'
    }

    stages {

        stage("Preparation")
        {
            steps {
                echo "PATH is: $PATH"
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps{
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
