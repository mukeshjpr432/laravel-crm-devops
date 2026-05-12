pipeline {

    agent any

    tools {
        sonarQubeScanner 'sonar-scanner'
    }

    environment {
        IMAGE_NAME = "krayin-crm:latest"
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/mukeshjpr432/laravel-crm-devops.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {

                withSonarQubeEnv('sonar') {

                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=laravel-crm \
                    -Dsonar.sources=app \
                    -Dsonar.host.url=http://host.docker.internal:9000 \
                    -Dsonar.login=$SONAR_AUTH_TOKEN
                    '''
                }
            }
        }

        stage('Composer Install') {
            steps {
                sh 'composer install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Trivy Scan') {
            steps {
                sh 'trivy image $IMAGE_NAME'
            }
        }
    }
}