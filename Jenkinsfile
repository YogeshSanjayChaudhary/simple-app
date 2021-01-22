pipeline {
    agent any
    tools {
        maven 'M2_HOME'
        jdk 'JAVA_HOME'
    }  
    stages {
        stage("git clone") {
            steps {
                git 'https://github.com/YogeshSanjayChaudhary/simple-app.git'
            }
        }
        stage("Maven Build") {
            steps {
                sh 'pwd'
                sh 'mvn clean install package'
            }
        }
        stage("Upload Artifacts To Nexus") {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: 'target/simple-app-1.0.0.war', 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'nexus', 
                groupId: 'in.javahome', 
                nexusUrl: '52.66.67.239:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'http://52.66.67.239:8081/repository/mymavenrepo/', 
                version: '1.0.0'
                
               
            }
        }
    }
}
