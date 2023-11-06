pipeline {
    agent {
        label 'dev'
    }
  triggers { pollSCM('* * * * *') }  

    stages {
        stage('Fetch code') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravi560909/jgsu-spring-petclinic.git']])
            }
        }
        stage('clean and build') {
            steps {
                script {
                    sh 'mvn clean compile package'
                }
            }
        }
        stage('backup') {
            steps {
                archiveArtifacts artifacts: 'server/target/*.jar', followSymlinks: false
            }
        }
    }
}
