pipeline {
    agent { label 'JAVA' }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/gorigemadhu085-cmd/spring-petclinic.git'
            }
        }

        stage('Build & Sonar Scan') {
            steps {
                withSonarQubeEnv('SONAR') {
                    withCredentials([string(credentialsId:'sonar_id', variable:'SONAR_TOKEN')]) {
                        sh '''
                        mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=gorigemadhu085-cmd_spring-petclinic \
                        -Dsonar.organization= gorigemadhu085-cmd \
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.login=$SONAR_TOKEN
                        '''
                    }
                }
            }
        }
    }
}