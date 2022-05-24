pipeline {
    agent any
    tools {
    maven 'M2' 
    }
    stages {
        stage ('Build') {
            steps {
                git 'https://github.com/Shi191099/JavaCode.git'
                sh 'mvn clean package'
            }
        }
        stage('Upload war to Nexus') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'maven-project', 
                        classifier: '', 
                        file: 'webapp/target/webapp.war', 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'Admin', 
                groupId: 'com.example.maven-project', 
                nexusUrl: '52.66.6.227:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'App_Release', 
                version: '1.0.0'
            }
        }
    }
}

