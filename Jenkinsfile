<<<<<<< HEAD
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
                   withCredentials([string(credentialsId:'sonar_id', variable:'SONAR_TOKEN')]) {
                     withSonarQubeEnv('SONAR') {
                        sh """
                        mvn clean package sonar:sonar \
                        -Dsonar.projectKey=madhu16 \
                        -Dsonar.organization=madhu16\
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.login=$SONAR_TOKEN 
                        """
                    }
                }
            }
        }
=======
pipeline{
    agent{ label 'JAVA'}
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('Build & Sonar Scan'){
            steps{
                withCredentials([
                    string(credetailsId: 'SONAR', variable: 'SONAR_TOKEN')
                ]){
                   withSonarQubeEnv('sonar_id') {
                    sh '''
                    mvn clean package sonar:sonar \
                     -Dsonar.projectkey=gorigemadhu085-cmd_spring-petclinic \
                     -Dsonar.organization=gorigemadhu085-cmd-1 \
                     -Dsonar.host.url=https://sonarcloud.io \
                     -Dsonar.login=$SONAR_TOKEN
                     '''

                   } 
                }
            }
        }

>>>>>>> a34efe7 (added some lines in jenkinsfile)
    }
}