pipeline{

    agent any
    tools{
        maven 'maven_3_5_0'
    }

    stages{

        stage('Build Maven'){
            sh 'mvn clean install'
        }

        stage('sonar quality check'){
            
            agent{

                docker {
                    image 'maven'
                }
            }
        
            steps{

                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {

                        sh 'mvn clean package sonar:sonar'
                    }



                }
            }
        }
    }
}