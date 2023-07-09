// to run this project we need jdk-17 and maven 3.8.6
// install jdk-17 (sudo apt install openjdk-17-jdk -y)
// install maven 3.8.7


pipeline{
    tools{
        maven 'maven_3.8.7'
    }
    agent any;
    stages{
        stage('git cloning from main branch'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ramakanth333/original-pet-clicin.git']])
            }
        }
        stage('maven packeging'){
            steps{
                sh '''
                      mvn clean package
                   '''
            }
        }
        stage('junit testing'){
            steps{
                junit '**/target/surefire-reports/*.xml'
            }
        }
        stage('artifact'){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
            }
        }
    }
}
