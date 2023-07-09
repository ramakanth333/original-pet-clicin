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
                      sleep 30s
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
