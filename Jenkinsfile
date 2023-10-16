pipeline {
    
	agent any
	
	tools {
        maven "Maven"
        jdk "OracleJDK8"
	
    }	
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "172.31.51.83:8081"
        NEXUS_REPOSITORY = "webapp-release"
	NEXUS_REPOGRP_ID    = "webapp-group"
        NEXUS_CREDENTIAL_ID = "nexuslogin"
        ARTVERSION = "${env.BUILD_ID}"
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
