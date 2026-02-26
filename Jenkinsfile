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

    }
}