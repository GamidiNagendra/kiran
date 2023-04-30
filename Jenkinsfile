pipeline {
    agent any

    stages {
        stage('Git clone') {
            steps {
              git branch: 'main', url: 'https://github.com/GamidiNagendra/kiran.git'
            }
       }
        stage('maven build') {
            steps {
             sh 'mvn clean install'
            }
        }
        stage('nexus Deploy') {
            steps {
             nexusArtifactUploader artifacts: [[
                 artifactId: 'myweb', 
                 classifier: '', 
                 file: 'target/myweb-8.3.5.war', 
                 type: 'war']], 
                 credentialsId: 'fff24505-ee24-4e35-8694-56f3cab7e800', 
                 groupId: 'in.javahome', 
                 nexusUrl: '54.221.24.27:8081', 
                 nexusVersion: 'nexus3', 
                 protocol: 'http', 
                 repository: 'kiran', 
                 version: '8.1.1'
            }
        }
    }
 }
