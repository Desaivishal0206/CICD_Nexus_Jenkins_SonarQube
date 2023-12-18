pipeline{

    agent any
    

    stages{

        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Desaivishal0206/CICD_Nexus_Jenkins_SonarQube.git']])
                def mvnHome = tool name: 'maveninstall', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
            }
        }

        // stage('sonar quality check'){
            
        //     agent{

        //         docker {
        //             image 'maven'
        //         }
        //     }
        
        //     // steps{

        //     //     script{
        //     //         withSonarQubeEnv(credentialsId: 'sonar-token') {

        //     //             sh 'mvn clean package sonar:sonar'
        //     //         }



        //     //     }
        //     // }
        // }
    }
}