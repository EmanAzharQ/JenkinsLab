pipeline{
    
    agent any

    enviroment{
        DOCKERHUB_CREDENTIALS=credentails('jenkins_lab123')
    }

    stages{
        stage('build'){
            steps{
                sh 'npm install'
            }
        }

        stage('test'){
            steps{
                sh 'echo "Test is running"'
            }
        }

        stage('Docker build'){
            steps{
                sh 'docker build -t emanazharq/jenkins-integration:latest .'
            }
        }

        stage('login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('push'){
            steps{
                sh 'docker push emanazharq/jenkins-integration:latest'
            }
        }

        stage('deploy'){
            steps{
                sh 'echo "deploying the application"'
            }           
        }
    }
}