pipeline{

    agent any
    

    stages{

        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Desaivishal0206/CICD_Nexus_Jenkins_SonarQube.git']])
                sh 'mvn clean install'
            }
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