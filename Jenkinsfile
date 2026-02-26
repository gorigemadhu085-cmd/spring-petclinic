pipeline {
    agent { label 'JAVA' }

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Sonar Scan') {
            steps {
                withCredentials([
                    string(credentialsId: 'sonar_id', variable: 'SONAR_TOKEN')
                ]) {
                    withSonarQubeEnv('SONAR') {
                        sh '''
                        mvn clean package sonar:sonar \
                        -Dsonar.projectKey=gorigemadhu085-cmd_spring-petclinic \
                        -Dsonar.organization=gorigemadhu085-cmd-1 \
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.login=$SONAR_TOKEN
                        '''
                    }
                }
            }
        }
    }
}